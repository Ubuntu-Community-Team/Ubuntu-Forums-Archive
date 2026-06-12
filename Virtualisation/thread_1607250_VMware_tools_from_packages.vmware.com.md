---
title: "VMware tools from packages.vmware.com"
date: 2010-10-27
forum: Virtualisation
---

### Post by STARDOUSER on 2010-10-27
The Ubuntu documentation for VMware tools ([https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)) describes how the installation can be done from packages.vmware.com:
> apt-add-repository 'deb [http://packages.vmware.com/tools/esx/4.1latest/ubuntu](http://packages.vmware.com/tools/esx/4.1latest/ubuntu) lucid main restricted'
wget [http://packages.vmware.com/tools/VMWARE-PACKAGING-GPG-KEY.pub](http://packages.vmware.com/tools/VMWARE-PACKAGING-GPG-KEY.pub) -q -O- | \
    apt-key add -
# (The above links to the ESX "4.1latest" builds of VMware-tools; however, 
# these packages should be compatible with all VMware servers, not just ESX 4.1)

apt-get update
apt-get install vmware-open-vm-tools-kmod-source
...
However, after adding the repository and doing "apt-get update" as described, the following error occurs:
> W: Failed to fetch [http://packages.vmware.com/tools/esx/4.1latest/ubuntu/dists/lucid/Release](http://packages.vmware.com/tools/esx/4.1latest/ubuntu/dists/lucid/Release) Unable to find expected entry main/source/Sources in Meta-index file (malformed Release file?)
The next "apt-get install.." command doesn't work after that.
VMware key is installed (confirmed with "apt-key list")

Apologies in advance if this is the wrong place to discuss issues with documentation.

---

### Post by AndyCee on 2010-10-28
I just checked, and I get the same results with "Malformed Release File".

---

### Post by AndyCee on 2010-10-28
I just checked, and I get the same results with "Malformed Release File".

---

### Post by Cr0n_J0b on 2010-12-19
I'm seeing this too.

---

### Post by ErroneousBee on 2011-04-08
I got around this by removing the appropriate deb-src entry from /etc/apt/sources.list

---

