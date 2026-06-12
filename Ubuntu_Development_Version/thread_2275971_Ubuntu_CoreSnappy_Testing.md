---
title: "Ubuntu Core/Snappy Testing"
date: 2015-04-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-04-29
*note to mods*

Can we discuss Snappy development/testing here in this forum?

Thanks

Regards..

---

### Post by QIII on 2015-04-29
Is Snappy Ubuntu?

(That's rhetorical)

Maybe this area isn't the best choice.  I'll see what the rest of the staff thinks.

---

### Post by QIII on 2015-04-29
Ya.  Go ahead and fire away in this area.

---

### Post by dino99 on 2015-04-29
Seems it is too young to get really used  [https://bugs.launchpad.net/snappy-ubuntu](https://bugs.launchpad.net/snappy-ubuntu)

---

### Post by oldfred on 2015-04-29
At least preliminary plans are to have one version of 15.10 as a Snappy version.

[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-DEB-To-Snap](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-DEB-To-Snap)

---

### Post by ventrical on 2015-04-29
Great read!

Here's how to install on a local kvm.

[https://developer.ubuntu.com/en/snappy/start/#snappy-local](https://developer.ubuntu.com/en/snappy/start/#snappy-local)

and some commands to run..


[https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/](https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/)

Regards..

---

### Post by ventrical on 2015-10-06
Snappy Core stable now released:

@cariboo - should I start another thread on this?

> 
                        Hi all,
 
we are excited to announce a new Snappy Ubuntu Core stable release
(image 6 at 15.04/stable)!
 
Highlights of this release include:
- fix crash if coreconfig gets invalid config
- add basic support for uefi firmware updates
 
The stable images were also updated
([http://releases.ubuntu.com/15.04/](http://releases.ubuntu.com/15.04/)) to reflect the latest image
available in the stable channel (you can also find them at
[http://cdimage.ubuntu.com/ubuntu-snappy/15.04/stable/20151006/](http://cdimage.ubuntu.com/ubuntu-snappy/15.04/stable/20151006/))
 
If you find any issue please make sure to use
[https://bugs.launchpad.net/snappy/+filebug](https://bugs.launchpad.net/snappy/+filebug) to report them, including
the device and image revision you're currently using.
 
 
Happy snapping,
 
 - Michael and the snappy team
 

---

### Post by ventrical on 2015-10-09
With a lot of work in terminal and using snappy-core I was able to install LXD for containers and import the ubuntu cloud image ,which, btw, apt-get can be used inside the container. After about 2 hours of working on this I was finally able to:

```

sudo apt-get install htop

```

then drop into root container and just type htop and .. yep .. it popped right up , colour and all:)


Next will try to install low end   desktop and see if I can run that.

This was one of my target goals! Mission accomplished! and with much help from this webpage:

[https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)

---

### Post by ventrical on 2015-10-15
htop and mc work really well. The only problem is is that snappy-ubuntu-core will not relent an xsession to the new container. There is a long list of images that can be imported to ldx containers. Once inside the container you can  sudo apt-get most anything from the repos. But there is an console error and if you try to start an xsession it will fail to tty0  and that it cannot find a console. If you move to another terminal with ctrl+alt +F(n) you will , of course, get another instance of snappy-ubuntu-core. It looks very promising and current /wily/ development version image can be imported also.

 i am not sure but I think an .iso image can be imported from a USB to a container.. but I'm not there yet.


Regards..

---

### Post by ventrical on 2016-02-01
Ok... here is the tread where I mentioned I had some success with LXD. I wonder if we can do some experiments and see if we can break or build some stuff.

This is required reading:

[https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)

regards..

edit: whoops .... those programs are now in the xenial repos so you do not need ppas! ahhh .. but read down that page a bit and you will see how to install LXD into snappy-core.

---

