---
title: "accidentally updated into developpement branch. Need help to go back to 22.04"
date: 2024-01-29
forum: Ubuntu Development Version
---

### Post by gerbal on 2024-01-29
Hello,
I hope I am in the right place. I somehow included  developement branch in my list and made an update. I did not make a  dist-update however. I was copy/pasting stuff from forums to try to fix a  dual boot issue and using boot-repair (dual boot is fixed). I am stuck  with no network adapters on this noble numbat distribution with a  6.6.0-14-generic kernel.
I didn't find a way to reinstall 22.04 on  this partition while keeping my home directory untouched. I think I can  follow tutorials to manually downgrade but I don't find anything on  getting back some network connection to access repositories. All I seem  to have is loopback.

So my question is : is there some solution  better than copying my home on usb, and reinstalling from scratch  everything. I don't even know how to probe my system for info, every  command line I tried tell me some package is missing and of course  failing to install.

Thank you for any help

---

### Post by #&amp;thj^% on 2024-01-29
First include this, so we see how deep you went:
```
inxi -r
```
If inxi is not installed use:
```
tac /etc/apt/sources.list

```
And:
```
tac /etc/apt/sources.list.d
```

EDIT Lets get the whole shebang so we don't have to keep asking for returns
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details
```
And paste back the URL or Link it gives you back here please.

---

### Post by gerbal on 2024-01-30
Thank you for your help:

here are the sources, unfortunately the whole shebang is not available due to no network, is there a way to get it using a usb stick instead of internet?

inxi not installed

I removed the commented lines
> moi@monpc:~$ tac /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) noble main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jammy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jammy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jammy-security main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jammy multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jammy-updates universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jammy universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jammy-updates main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jammy main restricted

moi@monpc:~$ tac /etc/apt/sources.list.d/*               (I added the /* because there was no return without it)
deb [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) bionic main
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) bionic main
deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main
deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main 
deb [http://ppa.launchpad.net/inkscape.dev/stable/ubuntu](http://ppa.launchpad.net/inkscape.dev/stable/ubuntu) bionic main
deb [http://ppa.launchpad.net/js-reynaud/kicad-5.1/ubuntu](http://ppa.launchpad.net/js-reynaud/kicad-5.1/ubuntu) bionic main
deb [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu/](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu/) jammy main
deb [https://apt.syncthing.net/](https://apt.syncthing.net/) syncthing stable
deb [https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/](https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/) jammy main

[EMAIL="moi@monpc:/etc/apt/sources.list"]moi@monpc:/etc/apt/sources.list[/EMAIL].d$ wget -N -t 5 -T 10 https:\\github.com/UbuntuForums/system-info/raw/main/system-info && \
> chmod +x system-info && \
> ./system-info --details
--2024-01-30 10:54:14--  [ftp://https/%5Cgithub.com/UbuntuForums/system-info/raw/main/system-info](ftp://https/%5Cgithub.com/UbuntuForums/system-info/raw/main/system-info)
           => &#8216;.listing&#8217;
Resolving https (https)... failed: Temporary failure in name resolution.
wget: unable to resolve host address &#8216;https&#8217;


---

### Post by #&amp;thj^% on 2024-01-30
Wow this is more of mess than I thought....Dang it my first impulse is to suggest a fresh install.

Why, you now have a mix of bionic jammy and noble.
What Link was you following? And Back-ups are a religion for me.
All your PPA's have a source for jammy so best to use the Jammy namesake for those PPA's

And with no access to internet the re-install is just the right thing to now.....sorry about that.:(

---

### Post by gerbal on 2024-01-30
I am not sure when the noble repository was added (I think it was when I clicked the "update grub to latest version" in boot-repair. but then I accepted a 1.2GB update that was clearly a mistake.
Last time I fully grenaded my system was trying to set up a complete system backup, so now I backup data and the rest is postponed to "one day" sadly yesterday arrived before this "one day"
New install it is then... Most of the configs I was hoping to save seem to be already gone anyways...

Thank you for your help :)

---

### Post by MAFoElffen on 2024-01-30
Get a very good backup...

User 'guiverc' came up with a good write-up on how to do a non-destructive reinstall: [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

Use the Ubuntu 22.04.3 ISO installer Live USB for that... Or whichever ISO represents the flavor and release you were on.

---

### Post by #&amp;thj^% on 2024-01-30
> **MAFoElffen said:**
> Get a very good backup...

User 'guiverc' came up with a good write-up on how to do a non-destructive reinstall: [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

Use the Ubuntu 22.04.3 ISO installer Live USB for that... Or whichever ISO represents the flavor and release you were on.

+1 That is a very good link, nicely done guivrec. :popcorn:

---

### Post by gerbal on 2024-01-31
Well, it didn't work, I got a non booting system with almost complete data loss. However the explications of how it works helped me re-inject most of my backup into a clean install. Only some packages to manually download and was able to reuse most of my "blindly tweaked until functioning" configs for not so common embedded electronics. 

Thanks

---

