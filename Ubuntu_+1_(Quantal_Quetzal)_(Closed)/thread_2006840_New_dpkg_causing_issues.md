---
title: "New dpkg causing issues?"
date: 2012-06-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ScislaC on 2012-06-19
I was upgrading packages in synaptic and synaptic conked out right after it did it's thing on the dpkg 1.16.3 package.

Now, it says wine1.4 is broken, and it refuses to even let me remove it. Synaptic keeps failing with the following:

```
dpkg: error: file triggers record mentions illegal package name `libglib2.0-0' (for interest in file `/usr/lib/x86_64-linux-gnu/gio/modules'): ambiguous package name 'libglib2.0-0' with more than one installed instance
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: file triggers record mentions illegal package name `libglib2.0-0' (for interest in file `/usr/lib/x86_64-linux-gnu/gio/modules'): ambiguous package name 'libglib2.0-0' with more than one installed instance
```

Anyone have any thoughts?

---

### Post by diesch on 2012-06-19
See [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329)

---

### Post by sammiev on 2012-06-19
> **ScislaC said:**
> I was upgrading packages in synaptic and synaptic conked out right after it did it's thing on the dpkg 1.16.3 package.

Now, it says wine1.4 is broken, and it refuses to even let me remove it. Synaptic keeps failing with the following:

```
dpkg: error: file triggers record mentions illegal package name `libglib2.0-0' (for interest in file `/usr/lib/x86_64-linux-gnu/gio/modules'): ambiguous package name 'libglib2.0-0' with more than one installed instance
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: file triggers record mentions illegal package name `libglib2.0-0' (for interest in file `/usr/lib/x86_64-linux-gnu/gio/modules'): ambiguous package name 'libglib2.0-0' with more than one installed instance
```

Anyone have any thoughts?

Dido, same here on updating using ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by pferraro on 2012-06-19
Try this:

sudo nano /var/lib/dpkg/triggers/File

Replace the following lines:

/usr/lib/x86_64-linux-gnu/gio/modules libglib2.0-0
/usr/lib/gio/modules libglib2.0-0
/usr/share/glib-2.0/schemas libglib2.0-0

With this:

/usr/lib/x86_64-linux-gnu/gio/modules libglib2.0-0:amd64
/usr/lib/gio/modules libglib2.0-0:amd64
/usr/share/glib-2.0/schemas libglib2.0-0:amd64

Then run:

sudo dpkg --configure -a

---

### Post by ScislaC on 2012-06-19
> **diesch said:**
> See [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329)

Thank you! I ran the commands recommended in the report and now it's fixed (I then downgraded dpkg in the meantime).

---

### Post by kevpan815 on 2012-06-20
No problems here installing Ubuntu Mainline Kernel 3.5.0-999 with DPKG today.

---

