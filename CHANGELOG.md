# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [3.0.2] - 2020-05-26
### Fixed
- Resolved Burst compiler errors (unresolved symbols on macOS) by setting correct native library reference (fixes #18)

## [3.0.1] - 2021-05-21
### Fixed
- AOT Burst compilation errors

## [3.0.0] - 2021-05-18
### Changed
- `DracoMeshLoader`'s coordinate space conversion from right-hand (like in glTF) to left-hand (Unity) changed. Now this is performed by inverting the X-axis (before the Z-axis was inverted). Compared to the previous behaviour, meshes are rotated 180° along the up-axis (Y). This was done to better conform to the glTF specification.

## [2.0.1] - 2021-05-21
### Fixed
- AOT Burst compilation errors

## [2.0.0] - 2021-05-17
### Added
- Experimental encoding support (ability to convert Unity Meshes into compressed Draco)
- Performance improvements
  - Two-step decoding allows to do more work of step two in threaded Jobs
  - Utilizes Advanced Mesh API
  - Uses `MeshDataArray` to shift more work to Jobs (Unity 2020.2 and newer) 
- Burst
- Unit tests
- Require Normals/Tangents parameter (necessity when using Advanced Mesh API). If true, even if the draco mesh does not have the required vertex attributes, buffers for them will get allocated and the values are calculated.
- Parameter for coordinate space conversion (was on by default before)
### Changes
- API is now async/await based
- Updated native Draco libraries (based on version 1.4.1) 

## [1.4.0] - 2021-01-31
### Added
- Support for Apple Silicon on macOS
- Support for Universal Windows Platform (x86,x64,ARM and ARM64)
### Changed
- Re-built all libraries with updated environments (Xcode, Android NDK, Emscripten, etc.)
- WebAssembly lib is now built by draco CI as well
### Fixed
- macOS library is now excluded from other platform builds (thanks Cameron Newnham <cam@fologram.com>)

## [1.3.0] - 2020-09-17
### Added
- Support for bone weights and joints by providing attribute IDs. Needed for glTF skinning.

## [1.2.0] - 2020-02-24
### Changed
- Performance improvement: CreateMesh does not calculate missing normals or tangents anymore. Instead it provides its caller with all info necessary to decide for itself, if calculations are needed.

## [1.1.3] - 2020-02-22
### Added
- Support for Universal Windows Platform (not verified/tested myself)

## [1.1.2] - 2020-02-01
### Fixed
- Removed in-Editor error by adding missing Profiler.EndSample call

## [1.1.1] - 2019-11-22
### Fixed
- Calculate correct tangents if UVs are present (fixes normal mapping)

## [1.1.0] - 2019-11-21
### Changed
- Assume Draco mesh to be right-handed Y-up coordinates and convert the to Unity's left-handed Y-up by flipping the Z-axis.
- Unity 2018.2 backwards compatibility
### Fixed
- Reference assembly definition by name instead of GUID to avoid package import errors

## [1.0.1] - 2019-09-15
### Changed
- Updated Draco native library binaries
- iOS library is now ~15 MB instead of over 130 MB

## [1.0.0] - 2019-07-28
### Changed
- Recompiled dracodec_unity library with BUILD_FOR_GLTF flag set to true, which adds support for normal encoding and standard edge breaking.
- Opened up interface a bit, which enables custom mesh loading by users.

## [0.9.0] - 2019-07-11
- Initial release
