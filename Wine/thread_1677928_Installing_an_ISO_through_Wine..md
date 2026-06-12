---
title: "Installing an ISO through Wine."
date: 2011-01-29
forum: Wine
---

### Post by Danger Fox on 2011-01-29
SO, for a class I'm in I need to run Visual Studio 2010. The way they give it to us is by giving us a link to where we download the ISO. However, my netbook that I use on the move is running ubuntu. Is there a way to run and install the ISO through Wine?

---

### Post by DoktorSeven on 2011-01-29
There's a utility in the repositories called gisomount that can mount them, or you can just do it the direct way via a terminal:

```

sudo mkdir /mnt/mountpoint
sudo mount -t iso9660 -o loop /path/to/your/file.iso /mnt/mountpoint/

```

Then just run the executable from the mountpoint directory as normal using Wine, and **sudo umount /mnt/mountpoint** when you're done.

(As an aside, WineHQ says that VS2010 and Wine doesn't work.  You might try running Windows in a virtual machine and running it from there, though I'm not sure how well your netbook can do that.)

---

