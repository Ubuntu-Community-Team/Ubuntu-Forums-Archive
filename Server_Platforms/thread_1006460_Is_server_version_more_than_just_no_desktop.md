---
title: "Is server version more than just no desktop?"
date: 2008-12-09
forum: Server Platforms
---

### Post by halgar on 2008-12-09
Hi,

How does the server version differ from the desktop?  If I use the server version, but install ubuntu-desktop (just to ease configuration) am I still getting some nice server benefits as opposed to just running the desktop version as a server?  For my purposes, I do not need to install any of the server components that are offered at install time.   

thanks,
halgar

---

### Post by Krupski on 2008-12-09
> **halgar said:**
> Hi,

How does the server version differ from the desktop?  If I use the server version, but install ubuntu-desktop (just to ease configuration) am I still getting some nice server benefits as opposed to just running the desktop version as a server?  For my purposes, I do not need to install any of the server components that are offered at install time.   

thanks,
halgar

The server version is different than simply a "desktop version without a GUI".

From [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)


```

The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.

Pre-emption is turned off in the Server Edition.

The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.

The Server Edition is optimized for i686 processors while the Desktop Edition is optimized for both the i586 and i686.

Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.

Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.

For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.

When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.

```

Fortunately, the CODE is better quality than the SPELLING. I corrected several spelling errors directly in the cut-n-paste I did from the Ubuntu website.

-- Roger

---

### Post by cdenley on 2008-12-09
Those are the differences between the default kernels, but you can use either kernel on either version.
desktop kernel:
```

sudo apt-get install linux-generic

```
server kernel:
```

sudo apt-get install linux-server

```

In addition to the server install not installing a desktop, it also lets you select from a few default server configurations. However, you can always do this after the install, or on the desktop version.
```

sudo tasksel

```

---

### Post by halgar on 2008-12-09
Thanks Krupski, thats just what I needed to know.

cdenley,
My goal is to have Ubuntu's best production server, but have a GUI to deal with it like I do RHEL and SLES.

My attempts to install the desktop on the server version is taking hours, perhaps a slow mirror.

Are you saying I could just install the desktop and then the server kernel and get just as good a server?  That's facinating!  There is probably a way to boot to a non-GUI level later if needed.

Also, are there any reasons in a production environment where support may be purchased to stay away from 8.10 and go with 8.04 because of the longer support period of 8.04?

thanks, 
halgar

---

### Post by cdenley on 2008-12-09
> **halgar said:**
> Thanks Krupski, thats just what I needed to know.

cdenley,
My goal is to have Ubuntu's best production server, but have a GUI to deal with it like I do RHEL and SLES.

My attempts to install the desktop on the server version is taking hours, perhaps a slow mirror.

Are you saying I could just install the desktop and then the server kernel and get just as good a server?  That's facinating!  There is probably a way to boot to a non-GUI level later if needed.

Also, are there any reasons in a production environment where support may be purchased to stay away from 8.10 and go with 8.04 because of the longer support period of 8.04?

thanks, 
halgar

I believe you can buy support from Canonical, but I don't know anything about that. Either way, I would suggest the 8.04 release since LTS release are typically more stable.

Disabling the GUI is easy.
```

sudo update-rc.d -f gdm remove

```
then you can always start it manually if needed.
```
sudo invoke-rc.d gdm start
```

Ubuntu is Ubuntu. Whether you install the desktop version or server version, it is the same thing with a different default configuration. If you install all the desktop packages over the internet, that is probably a few hundred MB of packages to download.

---

### Post by Iowan on 2008-12-09
There's a difference between a basic GUI and a full-blown desktop-install (which includes applications you may/not want/need).  
[This]("http://ubuntuforums.org/showthread.php?t=973076") thread (also includes a link to [this]("http://ubuntuforums.org/showthread.php?t=772796") one) discusses some GUI options.

---

