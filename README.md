# bazzite-deck-plasma-mobile &nbsp; [![bluebuild build badge](https://github.com/randomrooster/bazzite-deck-plasma-mobile/actions/workflows/build.yml/badge.svg)](https://github.com/randomrooster/bazzite-deck-plasma-mobile/actions/workflows/build.yml)

This is a fork of the bazzite-deck image from the Bazzite OS project, attempting to add the KDE Plasma Mobile shell to it, because the Steam Deck is basically a tablet with a controller glued to it. I'm testing this live on GitHub because I am too lazy to learn how to do it on private infra. If you didn't get the hint, at time of writing I don't know if this image works.  
Below follows the original README.

---

See the [BlueBuild docs](https://blue-build.org/how-to/setup/) for quick setup instructions for setting up your own repository based on this template.

After setup, it is recommended you update this README to describe your custom image.

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/randomrooster/bazzite-deck-plasma-mobile:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/randomrooster/bazzite-deck-plasma-mobile:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/randomrooster/bazzite-deck-plasma-mobile
```
