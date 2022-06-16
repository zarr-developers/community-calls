# May the 4th

Attending: Sanket Verma (SV), Ryan Abernathey (RA), Josh Moore (JM), Ishan Bansal (IB), John Kirkham (JK), Hailey Johnson (HJ), Shivank (SH), Brianna Rita Pagán (BRP), Dennis Heimbigner (DH), Jeremy Maitin-Shepard (JMS), Parth Tripathi (PT), Eric Perlman (EP), Jonathan Striebel (JS), Martin Durant (MD), Greg Lee (GL), Matt McCormick (MM), Davis Bennett (DB)

Introductions (new things & favorite places)
- Brianna: tech. lead at NASA for migrating data & services to the cloud

Updates (SV):
- ZEP is on the verge of acceptance & merging. Check [here](https://github.com/zarr-developers/governance/pull/16)
- ZIC invites sent. Check issues [here](https://github.com/zarr-developers/governance/labels/ZIC)
- Merged PRs:
    - Adding environment variable for Zarr V3 by Greg. Check [here](https://github.com/zarr-developers/zarr-python/pull/1007)
    - Performance improvement while appending data to Zarr array in S3 by Hailiang Zhang. Check [here](https://github.com/zarr-developers/zarr-python/pull/1014)
    - Pre-commit check by Shivank. Check [here](https://github.com/zarr-developers/zarr-python/pull/1015) and [here](https://github.com/zarr-developers/zarr-python/pull/1016)
- Suggestions for the Zarr Community. Add [here](https://hackmd.io/7jV1cE3pQeWXWI4e8siXng)
- Please have a look at the recent poll [here](https://twitter.com/zarr_dev/status/1521755830051389441)
- Thoughts on recording the community calls?
  - EP: more no (except presentations)
  - JK: more no
- IV: R implementation?
  - https://github.com/zarr-developers/community/issues/18
  - https://github.com/zarr-developers/community/issues/18
- JM: a libzarr out of netcdf-c
  - DH: possibly. (need to look at turning NC3 off)
  - WF: if we had someone to maintain it, then it's a no-brainer
  - DH: what API would we use. NC API is a pretty good match.
  - IV: good tooling for wrapping python in R. works almost seamlessly.
  - JM: libzarr would also get us MATLAB
  - WF: It would be a lot of work, and we have the code in the netCDF-C repo is available for poaching.  Collaborating to create a pure C Zarr library would be in our (Unidata/netCDF-C)'s interest and an easier lift than splitting it out/maintaining it ourself
  - WF: license, etc. should not be an issue.
  - IV: there were some C++ folks on the bioconductor side
  - JK: invite bioconductor to next meeting?


Topics:
- ZEP process:
  - MD: approve :tada:
  - etc. etc.
  - _ergo_ ZEP 0 merged :tada:
- BRP: geospatial standards (matching to https://cfconventions.org/)
  - RA: read the [OGC document](https://portal.ogc.org/files/?artifact_id=100727&version=1)?
  - BRP: No, gone through geozarr
  - RA: started mapping via xarray cf to zarr
  - RA: OGC is voting on accepting zarr, wrapper with a preface on conventions (named dimensions, netcdf data model, coordinate reference systems)
  - RA: NASA really cares about OGC and zarr is on track to be accepted
  - RA: [geozarr](https://github.com/christophenoel/geozarr-spec/) is newer and more proscriptive
  - BRP: battling with CRS since it's not in cf
  - RA: unidata would say there's a way.
  - BRP: but it's not required
  - RA: suggest getting behind geozarr (1 person at ESA)
- ...add stuff here...
- RA: What's ZEP 1 going to be? start wih JMS' comments on breakingness?
  - see: https://github.com/zarr-developers/zarr-specs/issues/140
  - MD: list of chunks!
    - non-breaking is passing a range of a chunk to the backend storage ("simple sharding")
  - RA: like being able to push selections to the store
  - MD: in v2 getitems (that's fsstore only)
  - JS: in sharding proposal, there are other methods for getting ranges for keys & multiple keys at once and as a combination (pre-requisite for efficient sharding)
  - MD: want to uncompress things that you don't know anything about
  - JS: there are hooks for blosc, e.g.. Adding this interface would help, since it's currently quite hacked.
  - MD: simple enough and nice that will enable sharding? good for prototying ZEP
  - JMS: there are breaking changes that don't change the data model in a significant way; **"feature-flags"** as important breaking addition
  - JS: transformer infrastructure also
  - RA: does anyone expect current v3 implementations to break?
  - JMS: v3 isn't a huge change; mostly isomorphic
  - RA: _explicit_ extensibility of the protocol? (on top of the re-org)
  - JK: `None` fill value etc. that just needed cleaning up
    - also moving towards sparse arrays. please for people to explore.
  - RA: tl;dr
    - ZEP1 to get motivation (co-editors welcome)
    - ZEP2 e.g. sharding
    - ZEP3 e.g. variables chunks
    - SV: doesn't need to be sequential editing but sequential merging!
  - RA: worried about fragmentation
    - will say in ZEP1, but want a strong core that all should implement
    - avoid driving people away
  - JS: happy to help with the spec, but not great for the ZEP
  - JMS: also happy to help with the spec
  - RA: will reach out to Alistair (SV: was waiting on ZEP0 to be merged)
  - RA: THANKS SANKET!
- SV: Davis from April meeting, propose to add "auto" setting
 - DB: "inaction item". Perhaps by the end of the week.
- Misc
  - new teams any comments? :thumbsup:
  - build docs for PRs? good idea.
- SV: pyscript!
  - MD: super interesting for Zarr. friendly for the browser. no sockets. no threads. suggestion that it might lead to a lot of hype. involved for the IO conversations. (couple of years until its really usable for heavy data workloads)
  - links
    - https://github.com/WebAssembly/wasi-sockets
    - https://github.com/WebAssembly/threads
    - https://github.com/pyscript/pyscript
  - DB: performance? MD: good, except for populating the browser (it's a VM)
    - DB: had seen 2.5x in favor of native
    - MD: more browser as the interface so that you don't need an ipython kernel running somewhere
    - MD: long-term talking about how to run numba in the browser (acceleration tricks that make regular python fast). could be that numpy in the browser is <50% slower
    - JK: fortran is a problem (e.g. scipy is hard to build)
    - MD: not a ton of javascript stuff around zarr. either:
      - tile servers are good enough for pure visualization
      - and/or people using zarr are doing data processing (parallelism)
    - DB: an
    
