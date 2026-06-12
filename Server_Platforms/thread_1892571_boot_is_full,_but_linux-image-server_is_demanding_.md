---
title: "/boot/ is full, but linux-image-server is demanding to install a new kernel anyway!"
date: 2011-12-08
forum: Server Platforms
---

### Post by Tokeli on 2011-12-08
Hi, server guys! I've got a little problem. Apt-get is demanding that I install the new kernel dependencies for linux-image-server, yet I don't really want to. We're not even running on the other updated kernels its downloaded. My only problem is that I can't just install it and ignore the update, because our /boot/ drive is 100% full (which is another issue). Is there a way to manually remove the old kernels to save space, or just make linux-image-server stop demanding I download a new kernel?


```

You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-server : Depends: linux-image-2.6.38-13-server but it is not installed
E: Unmet dependencies. Try using -f.
root@server1:~# apt-get -f install

...

(Reading database ... 94318 files and directories currently installed.)
Unpacking linux-image-2.6.38-13-server (from .../linux-image-2.6.38-13-server_2.6.38-13.52_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.38-13-server_2.6.38-13.52_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/abi-2.6.38-13-server': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-13-server /boot/vmlinuz-2.6.38-13-server
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-13-server /boot/vmlinuz-2.6.38-13-server
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.38-13-server_2.6.38-13.52_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Lars Noodén on 2011-12-08
You need to clear [font=Courier New]/boot[/font] by removing the older kernels.  You can find which kernels you have installed manually using [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html)

```

dpkg --get-selections linux-image-*

```

From there you can use [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html) to uninstall the old ones.

---

### Post by volkswagner on 2011-12-09
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1890147").  There is  link to a nice how to for removing old kernels.

---

### Post by Lars Noodén on 2011-12-09
> **volkswagner said:**
> Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1890147").  There is  link to a nice how to for removing old kernels.

Thanks.  I should have included a search for the headers, too.

```

dpkg --get-selections linux-image-* linux-headers-*

```

---

