---
title: "VMware packages: malformed Release file"
date: 2012-07-25
forum: Virtualisation
---

### Post by mlanner on 2012-07-25
Hi,

I'm trying to install VMware tools in my Ubuntu 10.04 Server guest, following these instructions:

[https://help.ubuntu.com/community/VMware/Tools]("https://help.ubuntu.com/community/VMware/Tools")

However, after adding the repository and running an apt-get update, I get a "(malformed Release file?)" error:

```
W: Failed to fetch http://packages.vmware.com/tools/esx/5.0latest/ubuntu/dists/lucid/Release  Unable to find expected entry  restricted/binary-amd64/Packages in Meta-index file (malformed Release file?)
```

I've reviewed my /etc/apt/sources.list file multiple times and I can't find anything wrong in there.

If anyone has an idea of what else could be causing this, I would appreciate any feedback.

Thanks in advance.

---

### Post by dcstar on 2012-07-27
> **mlanner said:**
> Hi,

I'm trying to install VMware tools in my Ubuntu 10.04 Server guest, following these instructions:

[https://help.ubuntu.com/community/VMware/Tools]("https://help.ubuntu.com/community/VMware/Tools")

However, after adding the repository and running an apt-get update, I get a "(malformed Release file?)" error:

```
W: Failed to fetch http://packages.vmware.com/tools/esx/5.0latest/ubuntu/dists/lucid/Release  Unable to find expected entry  restricted/binary-amd64/Packages in Meta-index file (malformed Release file?)
```

I've reviewed my /etc/apt/sources.list file multiple times and I can't find anything wrong in there.

If anyone has an idea of what else could be causing this, I would appreciate any feedback.

Thanks in advance.

And **you** manually removed the "deb-src" entry as specified in that HOWTO?

---

### Post by nothingspecial on 2012-07-27
*Thread moved to **Virtualization**.*

---

### Post by efpob on 2012-08-02
Just had the same issue. Not sure what happened, but there is no "restricted" in the vmware repository.

Remove that part from the end of the repository line in /etc/apt/sources.list so it just reads

```
deb http://packages.vmware.com/tools/esx/5.0latest/ubuntu lucid main
```

---

