---
title: "ChromeOS builds"
date: 2010-12-23
forum: The Cafe
---

### Post by sandyd on 2010-12-23
I got interested in chromeos a while ago (again) due to the google chromeos netbook giveaway.

So I compiled it.... 
and here it is....

Vmware image
[http://dl.dropbox.com/u/3593659/ChromiumOS/chromiumos.vmsd](http://dl.dropbox.com/u/3593659/ChromiumOS/chromiumos.vmsd)
[http://dl.dropbox.com/u/3593659/ChromiumOS/chromiumos.vmx](http://dl.dropbox.com/u/3593659/ChromiumOS/chromiumos.vmx)
[http://dl.dropbox.com/u/3593659/ChromiumOS/chromiumos.vmxf](http://dl.dropbox.com/u/3593659/ChromiumOS/chromiumos.vmxf)
[http://dl.dropbox.com/u/3593659/ChromiumOS/ide.vmdk](http://dl.dropbox.com/u/3593659/ChromiumOS/ide.vmdk)

Download all the files listed above, and simply stick them in the same folder before pointing vmware player/server towards it.

Ill be rebuilding this every weekend.

*NOTE I only have the vmware images because the virtualbox images don't work due to 
```

Guest Log: BIOS: KBD: unsupported int 16h function 03

```It might be because of my keyboard, but until I figure this out, I won't use bandwidth (and the storage in my dropbox account) to host the virtualbox image.

P.S. If the build fails (their done automatically), first check the waterfall
([http://build.chromium.org/p/chromiumos/waterfall](http://build.chromium.org/p/chromiumos/waterfall)) for build issues
If it still doesn't work, check this out
[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

---

### Post by Matthewthegreat on 2010-12-23
Is it possible to get a iso for my 901 eeepc? I would love to get it on my netbook!

---

### Post by Captain Smiley Pants on 2010-12-23
Haven't really kept up on the whole ChromeOS news, but you are able to do this right? As in, sharing the data and not having some lawyer come by get pissed at ubuntuforums.org?

---

### Post by sandyd on 2010-12-23
> **Matthewthegreat said:**
> Is it possible to get a iso for my 901 eeepc? I would love to get it on my netbook!
check out
[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

the livecd has an install button ;)

---

### Post by sandyd on 2010-12-23
> **Captain Smiley Pants said:**
> Haven't really kept up on the whole ChromeOS news, but you are able to do this right? As in, sharing the data and not having some lawyer come by get pissed at ubuntuforums.org?
[http://en.wikipedia.org/wiki/BSD_license](http://en.wikipedia.org/wiki/BSD_license)

I havent removed the copyrights, their still there.

---

### Post by Matthewthegreat on 2010-12-23
> **sandyd said:**
> check out
[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

the livecd has an install button ;)

Thanks!:popcorn:

---

### Post by Dragonbite on 2010-12-23
I'm one of those lucky ones to get the Chrome OS laptops.  For the most part it's alright, though not much more than an OS and browser.

Some of the advantage with the ChromeOS and laptop is that since they know the hardware it is going to run on they removed the hardware detection process and have it immediately boot up to the kernel.

The down side of this seem to be USB pen drives and digital cameras are not recognized at this point.

---

### Post by Quadunit404 on 2010-12-30
> **sandyd said:**
> check out
[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

the livecd has an install button ;)

That isn't Chrome OS, though... it's just a rebranded OpenSuSE with Chrome as the default browser.

---

