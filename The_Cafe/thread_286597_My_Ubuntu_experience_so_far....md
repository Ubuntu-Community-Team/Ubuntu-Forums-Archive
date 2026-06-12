---
title: "My Ubuntu experience so far..."
date: 2006-10-27
forum: The Cafe
---

### Post by ubu_n00b69 on 2006-10-27
I have been a Windows Power user for years. This has actually hampered me so far.

Linux is not Windows, and Vice Versa...

2 weeks ago I installed Ubu on a fairly new machine with NVIDIA NV14 On Board Graphics chipset. I couldnt change my screen resolution from 640X480 to save my Life.:evil: 

So...I started reading, and asking questions on the forums, and what everyone suggested, I already did from Info gained from different sources, Web, Forums and such. For 3 Days, I tinkered around, and to no avail, still no luck changing my resolution.:-k 

So...I grabbed an old dual processor server board, and a couple of PIII's sitting on the shelf saying "Use me, Use me"...:-D 
Tossed it all together, with a sound card, abd an old ATI Rage 3D Video Card.

Did my Install of Ubu, and everything worked out of the Box, Email, Web, Removeable Storage, USB Support and so on and so forth. I even had the Dual Proc Support in less than 30 mins of Install, Hummin' right along.

I still have'nt figured out how to do a "Tarball" the right way, of Install the correct codecs for Video and Audio, but this all takes time.:-k 

I truly Appreciate the time all of the Programmers took to give me the ability to have a choice. That is a great undertaking on their part, and IMHO, this Install was easier, and faster than any WIN XP Install I have ever done.:D 

I havent figured out the NV14 deal yet, but I will.](*,) 

I want to let anyone trying this that it took a long time to become a Win Power User, and I think if you take the time to learn, read and be persistent, you will, like me, not be discouraged into your Linux Venture.

Office Users, Open Office will surprise you.
Evolution is nice for mail, no problems with it.
As for having to run WIN programs in Linux, I understand the WINE is the way to go. I will be looking at it, since my Power Quality software only runs under WIN.

I am only 3 weeks in, and IMHO, So Far, So Good...

Good Luck to all the n00bs like me :-D

---

### Post by ~LoKe on 2006-10-27
=)

Generally, tarballs contain the source of an application.  Let's say you downloaded the tarball for Firefox.  You'd extract it to wherever you'd like, let's say... /home/user/.  To "compile" the source, you'd enter the directory.  To do this, open up your terminal and type the following...

```
cd /home/user/firefox/
```
Then, to compile the source...
```
make && sudo make install
```
This will make the install file, then install it.  Sometimes there'll be a step before that, if "make" gives you complaints about there not being a makefile, you need to type something like...
```
./configure && make && sudo make install
```
or...
```
./autogen.sh && make && sudo make install
```

Then your package is installed!  Some would suggest using checkinstall instead, so that you can easily remove the package later.  It creates a .deb file and installs it, so, you can uninstall it by typing...
```
sudo dpkg -r firefox
```

---

### Post by Naralas on 2006-10-27
If you are looking for how to do basically anything with Ubuntu then:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

If your using Dapper then they also have a dapper guide at (you guessed it:
[http://ubuntuguide.org/wiki/Ubuntu_Dapper](http://ubuntuguide.org/wiki/Ubuntu_Dapper)

---

### Post by mips on 2006-10-28
To reconfigure your X-server do:
```
sudo dpkg-reconfigure xserver-xorg
```
This will allow you to specify your monitors horz/vert sync rates as wll as the supported resolutions.

You could also manually edit your  /etc/X11/xorg.conf  file and add the supported modes. Remeber to BACKUP the xorg.conf file before editing it just in case you do something wrong.

If you get stuck just copy and paste your xorg.conf file here

**Why are you trying to install tarballs ???** Everything you need is in the repositories and can be install via synaptic/adept/apt-get/aptitude.
You are making things more difficult for yourself than they have to be.
Just enable all your repositories and add the PLF repository.

Get the pgp key:

```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```

Add the following to your /etc/apt/sources.list file
```

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free
```


I suggest you look at [http://easylinux.info/wiki/Ubuntu_Edgy](http://easylinux.info/wiki/Ubuntu_Edgy) as it will show you how to install most things.

If you have an ati or nvidia video card follow this guide to install the proprietory driver for 3d acceleration and overall better gfx
[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

