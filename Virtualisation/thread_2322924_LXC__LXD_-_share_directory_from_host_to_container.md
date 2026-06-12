---
title: "LXC / LXD - share directory from host to container"
date: 2016-05-01
forum: Virtualisation
---

### Post by u571kills on 2016-05-01
Hello,

I'm trying to solve a problem with my LXC containers. I would like to map / mount / share a directory from my host to LXC container. If these were real machines I could mount with NFS and be done. However, reading old posts it's not possible or easy to NFS mount between LXC and the host. I've read a few older articles about accomplishing this but so far they haven't worked. 

Specs: Ubuntu 16.04 x64 with ZFS backed LXC/LXD

Details: 
The directory I'd like to share to multiple containers is "core/big_data_drive".
The container names are bigdata1 and bigdata2 both with their respective ZFS drives at "core/lxd/containers/bigdata1"

Regards,
Martin

---

### Post by u571kills on 2016-05-01
Dang, easier than I thought. I wish a website existed that simply documented the "lxc" command options..

> lxc config device add bigdata1 sdb disk source=/core/big_data_drive path=big_data_drive

This will mount the host's directory "/core/big_data_drive" into the container's filesystem at "/big_data_drive"

---

### Post by andresi on 2016-09-13
Thanks for this simple solution. 

Is it possible to make the shared folder readable and writable by the guest vm? It seems that it is owned by nobody:nogroup.

---

### Post by redger on 2016-09-13
try this code [https://gist.github.com/bloodearnest/ebf044476e70c4baee59c5000a10f4c8]("https://gist.github.com/bloodearnest/ebf044476e70c4baee59c5000a10f4c8")

This will create new entries in /etc/subgid and /etc/subuid with a mapping of root to 1000:1 and create a new lxd profile through which root in the container will have the same file access as your host user.

Basically download the code and run it, to create a brand new profile

to launch a container using this profile:
```
lxc launch ubuntu:<version> -p $USER -p default <container-name>
```

to add an additional bind mount
```
lxc config device add <container> <device name> disk source=/path/on/host path=path/in/container
```
If your user has write access on the host, then root will have write access in the container.

Alternately you could grant "world" access to the directories / files in question on the host, the container will then also have access .... but this is hardly ideal

Here's my slightly modified version (I didn't want to mount my home directory)
```
#!/bin/bash
ID=400000  # some large uid outside of typical range, and outside of already mapped ranges in /etc/sub{u,g}id
_UID=$(id -u)
GID=$(id -g)
GROUP=$(id -gn)

# give lxd permission to map your user/group id through (for me to become root !)
sudo usermod --add-subuids ${_UID}-${_UID} --add-subgids ${GID}-${GID} root

# create a profile to control this, name it after $USER
lxc profile create $USER &> /dev/null || true

# configure profile
# this will rewrite the whole profile
cat << EOF | lxc profile edit $USER
name: $USER
description: allow home dir mounting for $USER
config:
  # this part maps the special uid/gid in the container to the correct host uid/gid
  raw.lxc: |
    lxc.aa_profile=unconfined
    lxc.id_map = u $ID $_UID 1
    lxc.id_map = g $ID $GID 1
  # this is cloud-init config that will create a user of the correct name and special uid/gid
  # in the container on first boot. Also gives passwordless sudo access to that user.
  user.user-data: |
    #cloud-config
    users:
      - name: $USER
        primary-group: $ID
        uid: $ID  # only works in xenial
        groups: sudo
        shell: $SHELL
        sudo: ['ALL=(ALL) NOPASSWD:ALL']
    ## ========= Commented out  – Not using Trusty ============ #
    ## cloud init in trusty can't specify uids (bug lp:1396362), so we do it manually
    ## this is a noop in xenial, as uid is already $ID
    ## note, depending on timing, the usermod may trigger a chown of some files in your bind-mounted $HOME.
    ## Annoying, but harmless, as it's chowning them to the same uid.
    runcmd:
      #- "groupmod -g $ID $GROUP"
      #- "usermod -u $ID $USER"
## AND WE DON’T WANT TO MOUNT OUR HOME DIR IN THE CONTAINER
## this section adds your $HOME directory into the container. This is useful for vim, bash and ssh config, and such like.
#devices:
#  home:
#    type: disk
#    source: $HOME
#    path: $HOME
# ======================================================= #
EOF
```

I also found there are some operations which will cause the profile to be "lost" from the container definition, so I went and added them manually to the container definition and then removed the additional profile.

In mys case i run a Mythtv server in an LXD container. passing through some USB tuners and host disk storage for content. All works very nicely and has been stable for a few months now (Ubuntu Xenial)

---

