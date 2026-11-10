# Patches

Changes applied on top of each upstream stable release before building the image.

- Make the change on a branch of the fork `oonid/hermes-agent` based on the upstream release tag,
  then export it with `git format-patch`. The same branch can become a pull request upstream.
- One `git format-patch` file per change, named `NNNN-short-description.patch`, applied in name
  order with `git am` by `image/prepare.sh`. Files that do not end in `.patch` are ignored.
- A patch that no longer applies fails the image build; nothing is published. Rebase it onto the
  new release (or drop it if upstream fixed the problem) and push.
- Delete a patch once its fix is in an upstream release.
- Changing the `*.patch` files (or the image recipe) changes the build hash, so the next run builds
  a new image.

The series starts empty: no change is needed yet to run Hermes under PRoot on the current release.
