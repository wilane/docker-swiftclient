# docker-swiftclient

Source for automated builds of a docker image containing the swift client.

This is useful for copying data from docker volumes to Swift based storage.

The built image is available at https://registry.hub.docker.com/u/pallet/swiftclient/

The image is based on the latest base ubuntu image, but with
swiftclient installed.

Run a docker container specifying openstack credentials, backing up a file from
a volume to a Swift service:

```
/usr/bin/docker run --rm \
  -e SETTINGS_FLAVOR=swift \
  -e OS_CONTAINER=docker-registry \
  -e OS_USERNAME=your-username \
  -e OS_PASSWORD=your-password \
  -e OS_AUTH_URL=https://identity.api.rackspacecloud.com/v2.0/ \
  -e OS_REGION_NAME=DFW \
  -e OS_TENANT_NAME=MossoCloudFS_nnnnn \
  --volumes-from your-container
  --name backup-file \
  pallet/swiftclient
  swift upload mycontainer myfile-from-volume
```

## License

Copyright © 2014 Hugo Duncan

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
