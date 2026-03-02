### build
podman build -t localhost/centos-bootc:latest .

### build ISO 
sudo podman run --rm -it --privileged \
   -v /var/lib/containers/storage:/var/lib/containers/storage \
   -v /home/stella/bootc/config.toml:/config.toml:ro \
   -v $(pwd)/output:/output \
   quay.io/centos-bootc/bootc-image-builder:latest \
   --type anaconda-iso \
   --config /config.toml \
   localhost/centos-bootc:latest

### prune
sudo podman system prune --all
