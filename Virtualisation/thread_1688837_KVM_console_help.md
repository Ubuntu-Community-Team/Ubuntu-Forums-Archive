---
title: "KVM console help"
date: 2011-02-15
forum: Virtualisation
---

### Post by jhogarth on 2011-02-15
I've setup an Ubuntu 10.10 server with KVM and tried to create a first virtual guest using vmbuilder.  The guest is created, but I cannot connect to it using virsh console.  I did add the serial and console sections to the XML for the guest.  

When I try to connect, the message about the escape characters shows, but not login.  The session appears to hang there.  I also cannot ping the server from the host.  I think I'm missing something simple, but fail to see it.  Here's my vmbuilder command:

vmbuilder kvm  ubuntu \
--suite=maverick \
--flavour=virtual \
--arch=i386 \
--libvirt=qemu:///system \
--part=vmbuilder.partition \
--templates=mytemplates \
--user=administrator \
--name=Administrator \
--pass=test1 \
--addpkg=vim \
--addpkg=unattended-upgrades \
--addpkg=acpid \
--firstboot=/vm/ubuntu/boot.sh \
--mem=256 \
--hostname=dt04 \
--bridge=virbr0 \
--ip=192.168.1.165 \
--mask=255.255.255.0 \
--net=192.168.1.0 \
--bcast=192.168.1.255  \
--gw=192.168.1.1 \
--dns=192.168.1.1 \
--overwrite \
--verbose \
--debug

The server does not have X installed.

Any suggestions will be appreciated!

Thanks.

---

### Post by pkuriakose on 2011-04-05
bump

---

### Post by falko on 2011-04-07
Does virbr0 exist? Do you see it in the output of ```
ifconfig
```, and is virbr0 in the correct subnet?

---

