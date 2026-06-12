---
title: "Juju won't bootstrap on private OpenStack installation"
date: 2013-07-11
forum: Ubuntu Cloud and Juju
---

### Post by DaveVoorhis on 2013-07-11
I have a working private OpenStack installation and am trying to use juju.  As follows:

```
dave@dave-D945GTP:~$ **juju version**
1.11.2-raring-amd64

dave@dave-D945GTP:~$ **juju sync-tools**
listing the source bucket
found 6 tools
found 6 recent tools (version 1.10.0)
listing target bucket
found 0 tools in target; 6 tools to be copied
copying tools/juju-1.10.0-precise-amd64.tgz, download 2205kB, uploading
copying tools/juju-1.10.0-precise-i386.tgz, download 2306kB, uploading
copying tools/juju-1.10.0-quantal-amd64.tgz, download 2209kB, uploading
copying tools/juju-1.10.0-quantal-i386.tgz, download 2311kB, uploading
copying tools/juju-1.10.0-raring-amd64.tgz, download 2208kB, uploading
copying tools/juju-1.10.0-raring-i386.tgz, download 2312kB, uploading
copied 6 tools

```


So far, all seems good.  However, it fails to bootstrap:

```
dave@dave-D945GTP:~$ **juju -v bootstrap**
2013-07-11 09:34:17 INFO juju provider.go:117 environs/openstack: opening environment "openstack"
2013-07-11 09:34:17 INFO juju provider.go:467 environs/openstack: bootstrapping environment "openstack"
2013-07-11 09:34:27 INFO juju tools.go:25 environs: reading tools with major version 1
2013-07-11 09:34:27 INFO juju tools.go:52 environs: filtering tools by series: precise
2013-07-11 09:34:27 INFO juju tools.go:75 environs: picked newest version: 1.10.0
2013-07-11 09:34:28 ERROR juju supercommand.go:234 command failed: cannot start bootstrap instance: no "precise" images in RegionOne with arches [amd64 i386]
error: cannot start bootstrap instance: no "precise" images in RegionOne with arches [amd64 i386]

```
A swift container named 'juju-cece0b9817a68cba4780784bf0663e45' containing a tools "directory" (with the six files obtained via juju sync-tools) and a bootstrap-verify file is successfully created.

My .juju/environments.yaml is as follows:

```

default: openstack


environments:
  ## https://juju.ubuntu.com/get-started/openstack/
  openstack:
    type: openstack
    # Specifies whether the use of a floating IP address is required to give the nodes
    # a public IP address. Some installations assign public IP addresses by default without
    # requiring a floating IP address.
    use-floating-ip: true
    admin-secret: sekret
    default-series: precise
    # Globally unique swift bucket name
    control-bucket: juju-cece0b9817a68cba4780784bf0663e45
    # Usually set via the env variable OS_AUTH_URL, but can be specified here
    auth-url: http://10.103.8.1:5000/v2.0/
    # override if your workstation is running a different series to which you are deploying
    # The following are used for userpass authentication (the default)
    auth-mode: userpass
    # Usually set via the env variable OS_USERNAME, but can be specified here
    username: admin
    # Usually set via the env variable OS_PASSWORD, but can be specified here
    password: sekret
    # Usually set via the env variable OS_TENANT_NAME, but can be specified here
    tenant-name: admin
    # Usually set via the env variable OS_REGION_NAME, but can be specified here
    region: RegionOne

```


Any suggestions?  I suspect I need a pre-existing "precise" image for bootstrap to launch, but which one and/or from where?

---

### Post by DaveVoorhis on 2013-07-11
After further reading, I determined that I apparently need to upload a "precise" image and run** juju image-metadata**.  I created the metadata as follows...
```
dave@dave-D945GTP:~/.juju$ **juju image-metadata -a amd64 -e http://10.103.8.1:5000/v2.0 -i d7e2ea12-cb50-4687-b5e1-d90f0656164a -n openstack -r RegionOne -s precise**
```
...and moved the resulting files to "streams/v1" in the juju-cece0b9817a68cba4780784bf0663e45 container.

**juju bootstrap -v** produced exactly the same result.

I also tried copying openstack-index.json and openstack-imagemetadata.json to index.json and imagemetadata.json, respectively, based on some content I found in a (probably irrelevant) bug report.

Again, **juju bootstrap -v** produced exactly the same result.

---

