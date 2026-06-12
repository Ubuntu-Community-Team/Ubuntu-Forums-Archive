---
title: "HOWTO:  Fully functional Lexmark X1100 series Printer Scanner"
date: 2012-01-26
forum: Tutorials
---

### Post by N00b-un-2 on 2012-01-26
I realize that the Lexmark X1100 series of printer/scanners is getting pretty old.  So old in fact that they've been discontinued and are no longer supported by Lexmark (not that they were terribly well supported to be begin with).  But I still own one as do many other people and there is still plenty of life left in these old printers.

The process to get the printer drivers for the X1100 is covered in detail here [http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+x1150]("http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+x1150") so I won't go into great detail.
However, I will note that the driver for Red Hat that Lexmark once offered from their support site is no longer available, so it must be gotten from elsewhere.
At one point, it used to be necessary to use alien to extract the drivers from the .rpm package but thankfully someone has packaged the driver as a [.deb available here ]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=get&target=lexmark.z600-0.4.deb").

Aside from the driver itself, you need libstdc++5.

Now here's the real trick:  Getting the scanner to work.  Some Lexmark scanners work out of the box on Ubuntu, some don't.  I happen to have a Lexmark X1150 which is supposed to work on Ubuntu, but since 7.10 I've never been able to get it to function until now.

The trick is to install sane-backends-1.0.18.  You will have to install a couple dependencies and then compile from source.

```

sudo apt-get install -y libsane* xsane build-essentials
mkdir lexmark
cd lexmark
wget https://alioth.debian.org/frs/download.php/1669/sane-backends-1.0.18.tar.gz
tar -xvzf sane-backends-1.0.18.tar.gz
cd sane-backends-1.0.18
./configure --prefix=/usr
make
sudo make install

```

Once you're done compiling the source and installing, fire up Xsane and try it out.

NOTES:  You will need to calibrate the color and page size before it will be useful, but if like me this is the first time that you've gotten your Lexmark scanner to work on Ubuntu then go ahead and do a victory dance.
Also, Simple Scan does not seem to work because you can't set the page size but Xsane works fine, as does the Gimp plugin.
:guitar:

---

