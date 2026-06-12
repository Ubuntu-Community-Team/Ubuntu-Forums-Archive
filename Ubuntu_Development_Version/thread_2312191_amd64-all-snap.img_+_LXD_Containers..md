---
title: "amd64-all-snap.img + LXD Containers."
date: 2016-02-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-02-02
It has been confirmed that there will be no snappy (personal_x86.img) until May but I thought there may be some early adopters who may want to  continue on with the LXC -> LXD convergence. Graham has had some success with this (LXC).  Over a month or so ago I was able to import a trusty image and install debian packages htop and midnightcommander which worked excellently from cli. Perhaps we may even be able to contrive a working desktop:)

You do not have to use kvm or virtual machine. You can just download the image and use gnome 'disks' to restore the image to an attached hdd and then put that hdd on another bare-metal desktop and experiment from there.

 Also  I am not totally sure how the new amd64-all-snap.img will work with LXD but it worked just fine with snappy-core so be forewarned that some of this is edge testing.

 I am also going to see if the new grub layout will allow me to install a conventional ubuntu distro. 

I will put some links up.

Regards..

---

### Post by ventrical on 2016-02-02
Here is the best place to start:

[https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)

Just scroll down and you will see how to install LXD on snappy.

Regards..

---

### Post by ventrical on 2016-02-02
lxd failed to install! I think there are problems with this image.  I think that the snappy core image has to be used for LXD.

---

### Post by ventrical on 2016-02-02
I completed an install of xenial mate-desktop and it broke the writeable grub. ..So I rebooted and Mate install came up .. so I am going to try :

```

sudo update-grub

```

and see what happens.

edit:

Ok .. installing a conventional ubuntu flavour will break writeable snappy grub partiton but it gives you an option to exit and then the installed flavour of ubuntu will load.

I think it is an UEFI problem although I never chose that as an install option from BIOS.

---

### Post by QDR06VV9 on 2016-02-02
Watching with Keen interest..

---

### Post by grahammechanical on 2016-02-02
> LXD is available for Ubuntu Core as a Snap package in the store.

Now, that is interesting. And so is this.
> 
If you already have a lxd-compatible image file, you can import it with:

 lxc image import \<file\> --alias my-alias



I am hoping that means I can import the image from my hard disk and install it in a container. Otherwise we are limited to images that the devs have included in their image store. Which the last time I tried this were distributions but not flavours and leaning towards server OS.

Regards.

It is possible to test out the LXD commands in a 30 min session online here

[https://linuxcontainers.org/lxd/try-it/](https://linuxcontainers.org/lxd/try-it/)

EDIT 2: My first experiment ended with it loading to inittramfs. Which I think happened before. I downloaded amd64-all-snap.img from https:people.canonical.com/~mvo/all-snaps/ and used Disk Restore image to put it on USB stick and it loads to busybox initramfs. It is missing something to do with systemd. I will try another way.

EDIT 3: My second exercise was more successful if not any more useful. I re-install personal_x86.img. Of course, it is still at version 121 on wily code and no new image to update to but at least it is snappy core + Mir + Unity 8. And I was able to install LXD on it. Now, the issue I have with LXD is that the developers are thinking server & cloud images and not desktop images. And LXD is command line through & through.

I also tried to install webdm but I got a package not found reply. So, there we are. More research to do.

---

### Post by ventrical on 2016-02-03
Hi graham and ruckus,

 I installed the 15.04 amd64 snappy core img to a hard drive using restore from disks. I then was able to boot into it. I got the video blind mode.. but after a few seconds it loaded up and I got prompt.

Logged in with:
ubuntu
ubuntu

Then:

```

sudo snappy update

```

and webdm automagically installs.

Then:

```

sudo snappy install lxd.stgraber

```

and it installed.

 I then:
```

lxc remote add images images.linuxcontainers.org

```

Then:
```

lxd-images import ubuntu --alias ubuntu

```

Then:

```

lxc launch ubuntu first

```
and it will start a container: read here > [https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)

To get to the trusty operating system container (which is baked stable trusty server) do:

```

lxc exec first -- /bin/bash

```

You are then inside a privlidged container. You can install htop and midnight commander:

```

sudo apt-get install htop
sudo apt-get install mc

```

and they will run directly from the root# terminal. However , remember.. we are dealing with a headless server. So we have to install xserver and all other components. (I installed lightdm etc) and tried to run those programs but  you will get 'cannot find display' error. Stephan Graber shows how to put X on the headless server using  (ssh) so there is a lot of fangling with code but I think it is cool to experiment with. If we keep experimenting we may find some room for discovery and be able to get some kind of reasonable and working snappy with mir and unity8 container.

 The thing that perplexes me is why does graphical mc and htop run on this container. Are there not simple desktop manager or DEs that can do the same from cli?

Regards..

---

### Post by ventrical on 2016-02-03
> **runrickus said:**
> Watching with Keen interest..

In a sense .. I am grabbing at straws here .. :) .. if you see anything or find any links in your travels feel free to drop em here ;)

thanks

Regards..

---

### Post by ventrical on 2016-02-03
@graham

Please read here> [https://newspaint.wordpress.com/2015/09/14/how-do-i-get-x11-applications-running-in-a-lxc-container/](https://newspaint.wordpress.com/2015/09/14/how-do-i-get-x11-applications-running-in-a-lxc-container/)

It will not work because lxc-create does not work with LXD but it gives you the fundemental pervious method of how you can run Firefox as a standalone app in an LXD container. I hope it helps. I am still researching  it.

Regards..

---

### Post by QDR06VV9 on 2016-02-03
> **ventrical said:**
> In a sense .. I am grabbing at straws here .. :) .. if you see anything or find any links in your travels feel free to drop em here ;)

thanks

Regards..
Will do that for sure..But yes grabbing at straws here also...:D
You did give me a hint: just wait a bit longer for things to happen
> [COLOR=#000000] got the video blind mode.. but after a few seconds it loaded up and I got prompt.[/COLOR]
I have a feeling we will get somewhere on this shortly...
Regards

---

### Post by grahammechanical on 2016-02-03
Last year I experimented with LXC and reported my results in the cafe or Linux discussion section and what stopped me was although I was able to install desktop environments in the container and I could start the container the desktop environment was not running when I switched to tty8 and so on. And I failed to over come this without using this package

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

It is a brilliant piece of code. Install that and start a container and then switch to tty8 and there is a working instance of Ubuntu. It is mini ubuntu with ubuntu-desktop but not the default applications.

I do not know about lxd but lxc & this lxc-desktop work from templates. And what templates are available is what limits the usefulness. But I do believe it is possible to use the default templates as a pattern and create templates that will install Xubuntu and the others. I succeeded in that to a limited extent. This is where the relevant files were stored about a year ago.

LXC
> 
/usr/share/lxc/lxc.functions
/usr/share/lxc/lxc-patch.py
/usr/share/lxc/lxc-restore-net
/usr/share/lxc/config/
/usr/share/lxc/hooks/
/usr/share/lxc/selinux/
/usr/share/lxc/templates/
/usr/share/lxc/config/desktop.conf
/var/lib/lxc/container name/config

lxc-desktop

> /home/lxc-desktop/README.md
/home/lxc-desktop/.gitignore
/home/lxc-desktop/debian
/home/lxc-desktop/usr
/home/lxc-desktop/.git


I doubt if lxc-desktop will install on snappy core because it is not a snap package. It might install in a container. Can we have nested containers?

Regards.

---

### Post by ventrical on 2016-02-03
> **grahammechanical said:**
> 

I also tried to install webdm but I got a package not found reply. So, there we are. More research to do.

I think

```


sudo snappy install webdm.canonical_0.9_multi.snap

```

or

```

wget https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap

```

err.. I think you do the last one first and the first one last :)

  ahhh .. that is for personal_x86.img

Regards..

---

### Post by ventrical on 2016-02-03
> **grahammechanical said:**
> 



I doubt if lxc-desktop will install on snappy core because it is not a snap package. It might install in a container. Can we have nested containers?

Regards.

LXD is the new norm for snappy. The 'lxc-create' option has been excised out.  We don't have to go back to square one on this new LXD framework. Just some new stuff to learn. I am going to keep trying to bust it , tweak it and get some other 'graphical programs' running. It is good training ground for when the new snappy personal images start rolling out in May.

Regards..

---

### Post by ventrical on 2016-02-03
Might as well start fresh.

> 

Hello Snappy Enthusiasts,
 
We are pleased to announce that there are updated all-snap images
availalbe at:
 
  [https://people.canonical.com/~mvo/all-snaps]("https://people.canonical.com/%7Emvo/all-snaps") [1]
 
This is a pretty big update and we recommend that you reflash your
image (we expect this is the last disruptive transition). The most
important change is that we moved to the new internal `meta/snap.yaml`
format which makes it partly incompatible with the previous images
that used the `meta/packages.yaml` format. If you have been using
snapcraft 2.0 to build your snaps you will be mostly compatible
already.
 
The highlights:
- new snap.yaml format
- new `snap` command that will replace `snappy` eventually
- the `snappy search` command is replaced with `snap find`
- the rpi2 uses `ubuntu-core` as the name for the core snap
 
This also means that most applications are now switched to the new
`meta/snap.yaml` format in rolling. Snapcraft also supports this out
of the box. The old rolling images that are based on the previous
system-image-architecture will not handle this change. We recommend
that you reflash those with the latest all-snap images.
 
Please let us know if you find any issues!
 
Cheers,
 Michael


---

