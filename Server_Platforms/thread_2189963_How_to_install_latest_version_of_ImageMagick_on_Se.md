---
title: "How to install latest version of ImageMagick on Server 12.04?"
date: 2013-11-25
forum: Server Platforms
---

### Post by johnrb68 on 2013-11-25
How do you correctly install the latest version of ImageMagick (and Image::Magick for Perl) on Ubuntu Server 12.04?

The version in the repository for Ubuntu is an older version with bugs (v6.6.9-7).

I want to use a newer if not the newest version (v6.8.7-7).

I have tried several suggested ways of installing the never versions, but none of them seem to be working.

Does anyone know if there is a way to do this correctly?
It's really frustrating to not be able to easily install an up to date version of ImageMagick on Ubuntu Server.

Thanks for any help that you may be able to offer!

John

---

### Post by Dreamer Fithp Apprentice on 2013-11-25
> **johnrb68 said:**
> How do you correctly install the latest version of ImageMagick (and Image::Magick for Perl) on Ubuntu Server 12.04?Correctly? Well, the meaning of that word may be debatable, but the short answer is you don't. There are lots of ways you CAN try to install later versions than the latest one in your issue-official repository. Sometimes they work. Sometimes they don't. Sometimes they work, kinda sorta. Sometimes they bork your system. You seem to have already at least partly found this out. You can add a repository for a later Ubuntu, like Saucy, or even some other Debian-like distro altogether. Proceed at your own risk. You can sometimes download a someprogram.deb file from a website associated with the program and install it using the program gdebi which is in the repositories. Some programs maintain their own repository. If that is the case for a particular one there will be instructions at the program's website. I've done all of those things. None of them are gauranteed to work. I wouldn't reccomend doing any of them unless your system is backed up or you are prepared to reinstall from scratch if it screws up. You can almost always download the source code and compile it yourself locally. I've never done that. My impression is that it isn't terribly hard but can be time consuming.

---

### Post by johnrb68 on 2013-11-25
Thank you.

So, (sorry I am a bit new to this aspect) am I correct that Saucy (13.10) has ImageMagick v6.7.7-10?

If that is the case, that is at least close to the same version that was on my shared host.  I am trying to move a project to a VPS Host because I need more bandwidth. I can kill the 12.04 build I just started and start a new build with 13.10 I guess.  I thought I would be better off with the LTS build, but I guess not.

---

### Post by Dreamer Fithp Apprentice on 2013-11-26
> **johnrb68 said:**
> am I correct that Saucy (13.10) has ImageMagick v6.7.7-10?"8:6.7.7.10-5ubuntu3" is what synaptic calls it. I haven't noticed a version number with a ":" in it that I recall. Until now that is. Not sure what that means.> **johnrb68 said:**
> I can kill the 12.04 build I just started and  start a new build with 13.10Or shrink a partition with gparted  to make space for another system and have both. That's what I have atm.  Precise and Saucy. I've made these systems pretty lean. Under 3 gb for  the Precise, under 4 for the Saucy. It's very doable. Or try one of the  um ... non-standard, yeah, that's a good word, non-standard techniques  mentioned earlier to install the imagemagic on Precise if you want to.  If you don't keep any important data on the same partition with the  system, the worst that can happen is you bork it totally and have to  reinstall, which you are contemplating anyway.> **johnrb68 said:**
> I thought I would be better off with the LTS  build, but I guess not.Hard to say. I've never made a firm  policy for myself. You'd think the LTS would be less buggy. I think  maybe on the whole it is, but I have no statistics, that may be  perception colored by expectation, and whatever the case actually is,  the difference doesn't seem to be dramatic. I usually keep several  systems at a time (hey, it's FREE software, right?) and things evolve  somewhat chaotically. For example I borked my previous Precise trying to  trick it into running a more recent pcmanfm. So I replaced it with  Raring, since upgraded to Saucy. But in the meantime I find I couldn't  make remastersys work in raring so I replaced my LMDE (mint flavored  Debian) with another Precise. And so it goes. When I have more drive  space, I have more systems. I try to keep them backed up with fsarciver  so wiping out a system doesn't seem that big a deal to me since I can  always restore it. Unless I wipe it out accidentally and have been to  lazy to back it up rfecently. Then I just cuss a lot.

---

### Post by rubylaser on 2013-11-26
Compiling your own ImageMagick isn't complicated, dangerous, or super time consuming if you follow a few simple steps.  I just installed Ubuntu 12.04 Server in Virtualbox and ran these steps to compile the latest version of ImageMagick.

```

sudo -i
cd
apt-get install build-essential checkinstall && apt-get build-dep imagemagick -y
wget http://www.imagemagick.org/download/ImageMagick-6.8.7-7.tar.gz
tar xzvf ImageMagick-6.8.7-7.tar.gz
cd ImageMagick-6.8.7-7/
./configure --prefix=/opt/imagemagick-6.8 && make
checkinstall

```
Total time to compile in a virtual machine on my Haswell MacBook Air was less than 5 minutes.

One of the main benefits of checkinstall is that programs installed with it can be removed like any other package with the package manager.  When you run checkinstall, it will ask you for a package name, I just used ImageMagick 6.8.7-7 Source Install (you can see that below), and accepted the defaults for the rest of the prompts.

Since it's installed to /opt/, this is not in your $PATH, so I made a few symlinks to /usr/bin
```

ln -s /opt/imagemagick-6.8/bin/animate /usr/bin/
ln -s /opt/imagemagick-6.8/bin/compare /usr/bin/
ln -s /opt/imagemagick-6.8/bin/composite /usr/bin/
ln -s /opt/imagemagick-6.8/bin/conjure /usr/bin/
ln -s /opt/imagemagick-6.8/bin/convert /usr/bin/
ln -s /opt/imagemagick-6.8/bin/display /usr/bin/
ln -s /opt/imagemagick-6.8/bin/identify /usr/bin/
ln -s /opt/imagemagick-6.8/bin/import /usr/bin/
ln -s /opt/imagemagick-6.8/bin/mogrify /usr/bin/
ln -s /opt/imagemagick-6.8/bin/montage /usr/bin/
ln -s /opt/imagemagick-6.8/bin/stream /usr/bin/

```

After doing this, you can call all of the commands from a prompt or check this version like this.
```

root@magic-test:~# convert --version | grep Version
Version: ImageMagick 6.8.7-7 Q16 x86_64 2013-11-26 http://www.imagemagick.org

```


checkinstall will allow you to manage the compiled install with dpkg like this.
```

root@magic-test:~# dpkg --list | grep ImageMagick
ii  imagemagick-6.8.7                 7-1                                                 [COLOR=#ff0000]**ImageMagick 6.8.7-7 Source Install**[/COLOR]

```

You can easily remove ImageMagick at a later date using dpkg like this.
```

dpkg -r imagemagick-6.8.7

```

In regards to LTS vs. standard releases, the main difference isn't stability, the LTS stands for Long Term Support, and they provide package updates for 5 years from their release date vs. 1 year for a standard release. For instance, the 12.04 LTS will be End of Life (EOL) in April 2017 vs. 13.10 that will be EOL in July 2014.  For a server that stability and longevity is a major focus, an LTS is a no-brainer.

---

### Post by Dreamer Fithp Apprentice on 2013-11-29
Thanks for commenting RubyLaser - that's interesting. I've been detered from compiling anything because I'd gotten the false impression it took hours. You have advanced my education. I'll try it the next time it is an option.

---

