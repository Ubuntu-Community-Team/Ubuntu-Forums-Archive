---
title: "64bit media installing 32bit version"
date: 2008-10-22
forum: Server Platforms
---

### Post by rgb129 on 2008-10-22
I am trying to install Hardy on a test box here.  Currently, we are running Gutsy 64bit on these same machines.

I have tried several times to install Hardy from 64bit media and each time it installs the 32bit version.  It is an Athalon 64 X2 4600+ processor on a Tyan S2925.  Again, I had no problem doing this with Gutsy on this same box.

Any ideas?

---

### Post by ajwak95 on 2008-10-22
is your bios up to date?

---

### Post by rgb129 on 2008-10-22
Yes, the bios is up to date.  I also was just able to install gutsy 64bit successfully on the box.  I suppose I could just do the upgrade via apt.  It just doesn't make sense why 64bit installation media would install a 32bit OS.  The worst part about it is you have to wait until it fully installs to find out.

---

### Post by cdenley on 2008-10-22
Are you sure you didn't download the 32-bit version by accident? I don't think it is possible for a 64-bit disc to install 32-bit binaries. What is the md5 checksum of the image you downloaded?
```

md5sum ubuntu-8.04-desktop-amd64.iso

```

Are you sure it installs the 32-bit version?
```

uname -m

```

---

### Post by rgb129 on 2008-10-22
I wouldn't think so either.

rgb$ md5 ubuntu-8.04.1-server-amd64.iso 
MD5 (ubuntu-8.04.1-server-amd64.iso) = e7351d79903588699a383ae77854f734

---

### Post by cdenley on 2008-10-22
> **rgb129 said:**
> I wouldn't think so either.

rgb$ md5 ubuntu-8.04.1-server-amd64.iso 
MD5 (ubuntu-8.04.1-server-amd64.iso) = e7351d79903588699a383ae77854f734

That is the 64-bit installer, now what makes you think it is installing a 32-bit kernel?

---

### Post by rgb129 on 2008-10-22
> **cdenley said:**
> That is the 64-bit installer, now what makes you think it is installing a 32-bit kernel?

The first way I noticed is when I tried to run on of our apps that is compiled on a 64bit machine.  It fails on this install.  Then a uname -a returns a i686 kernel.  I can't get the output of uname -a until the morning when I am back in the office.  Someone else said the used that same media to install on a 32bit intel box and it worked there.  Seems odd...

---

