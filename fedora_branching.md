# Situations to improve
## glibc

The glibc upstream relies on Fedora's master branch (Rawhide) for development.
They regularly push snapshots of the next glibc release into Rawhide to validate it in a real-world environment.
At the Toolchain Meetup in Montreal this week, Carlos O'Donell asked me if there was any way we could make the Branch point be earlier in the cycle.
The reason for this is that glibc wants to be able to maintain stabilization and new feature branches while retaining the ability to actually deliver the latter to Rawhide.
At present, since they rely on Rawhide for integration testing, there's a long period between upstream's feature freeze point and our Branch point.
The effect of this is that new-feature development ends up being held off and not merged until after Fedora branches, usually around a month of lost time.

## Packagers tracking upstream in all releases

One common packaging strategy in Fedora is to always track the latest version from upstream and pushing it to all active releases.
For many leaf packages, graphical applications and libraries with a strong history of maintaining compatibility it is far easier to just constantly rebase all active releases to the latest upstream version.
Right now, that means:

1. Pull down the tarball into master/Rawhide
1. Update the spec file
1. Build for Rawhide
1. Switch to another release branch
1. Merge master to the release branch
1. Build for the release branch
1. Repeat the previous three steps for all active releases

# Proposed new branching policy
