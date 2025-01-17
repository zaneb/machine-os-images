# Machine OS Images

This repo builds a container image that contains the latest CoreOS ISO and can
regurgitate it or the corresponding PXE files (kernel, initrd, rootfs).

## Building the image

By default, the ISO is downloaded from the lookaside cache available only in
OpenShift CI. To download directly (for local builds, or OKD), set the arg
`DIRECT_DOWNLOAD=true` (the `make build` target sets this for you).

## Retrieving the Machine OS

The scripts `/bin/copy-iso` and `/bin/copy-pxe` can be used to copy the ISO and
PXE files respectively to a volume that is bound into the container. Pass the
destination path as an argument. For example:

    podman run --rm -v .:/data:bind /bin/copy-iso /data
