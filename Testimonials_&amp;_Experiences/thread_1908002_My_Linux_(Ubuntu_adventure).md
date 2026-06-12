---
title: "My Linux (Ubuntu adventure)"
date: 2012-01-12
forum: Testimonials &amp; Experiences
---

### Post by MrAlex on 2012-01-12
So, for professional reasons I need to program something in Linux so I decided it's a good time to install some new distro on my home PC. I never had one of those since my college days: I studied computer science so I did reluctantly used to have a dual boot with Fedora and Windows, but I reduced by time as much as possible. That was about 6 years ago so I was curious to see what the Linux chaps have been up to in all those years.

Now, mind you, I am a programmer by trade and formation so I generally am computer savvy and also I have occasionally ssh'ed to a linux machine and did this-or-that so I am also familiar with a shell, but other than this I hope I can approach Linux with an open mind.

Now, I started writing this after 48 hours of installing Ubuntu so I will not go into much details, but hopefully people will find this interesting and perhaps suggest solutions to the (many) issues I ran into... (to be continued)

---

### Post by MrAlex on 2012-01-12
Part 1 installation:

Well, I did a quick search and people kept recommending Ubuntu and Mint. Both of these did not exist last time I tried linux, so after some more googling I decided to go with ubuntu (to be honest the clincher was that the ubuntu website looked a lot more professional and the "live demo" didn't hurt either. Thumbs up to who's in charge of that, really looks appealing.

Now, I had a very pleasant surprise in that wubi thingie. I stumbled on it quite by chance (should be made more obvious IMHO) but it worked perfectly. Mind you, last time I installed a linux, I had to use stuff such as Partition Magic to resize one of my Windows partitions, then suffer through endless text installer that were not exactly user friendly... Wubi was just what the doctor ordered... a nice clean directory in Windows and a painfree instalation (watched an episode of Dexter while that downloaded and installed). This feature has to take a 5 stars.

I do have a question here... is there any downside to using wubi instead of a proper linux instalation on it's own ext whatever partition? (to be continued)

---

### Post by Paddy Landau on 2012-01-12
WUBI has two downsides.

1. It's a little slower than a native installation.

2. It's less reliable; it can be prone to sudden fatal failure, especially with updates.

---

### Post by tersogar on 2012-01-12
It works slower since it run inside windows but is a simple way to explore Ubuntu.

---

### Post by MG&amp;TL on 2012-01-12
You might be interested to know, that while (aside from Wubi and virtualisation), you still have to partition to run a different OS, the installer has become a lot more professional (no text interface,for a start.)

This is an old image: [http://www.google.co.uk/imgres?q=ubuntu+installer&um=1&hl=en&sa=N&biw=1366&bih=655&tbm=isch&tbnid=_OE5p_Ytve-PhM:&imgrefurl=http://www.techdrivein.com/2010/08/massive-changes-coming-to-ubuntu-1010.html&docid=pjJTG91uy-jirM&imgurl=http://4.bp.blogspot.com/_JSR8IC77Ub4/TGwVWw4sZYI/AAAAAAAAA9g/yhu_nZjlIzM/s1600/d9m38bd_276cvt72tdc_b.png&w=1000&h=800&ei=C1YPT6X-J4eyhAeL06CQAg&zoom=1&iact=hc&vpx=930&vpy=343&dur=1101&hovh=201&hovw=251&tx=92&ty=167&sig=102233243155194550030&page=1&tbnh=137&tbnw=171&start=0&ndsp=18&ved=1t:429,r:16,s:0]("http://www.google.co.uk/imgres?q=ubuntu+installer&um=1&hl=en&sa=N&biw=1366&bih=655&tbm=isch&tbnid=_OE5p_Ytve-PhM:&imgrefurl=http://www.techdrivein.com/2010/08/massive-changes-coming-to-ubuntu-1010.html&docid=pjJTG91uy-jirM&imgurl=http://4.bp.blogspot.com/_JSR8IC77Ub4/TGwVWw4sZYI/AAAAAAAAA9g/yhu_nZjlIzM/s1600/d9m38bd_276cvt72tdc_b.png&w=1000&h=800&ei=C1YPT6X-J4eyhAeL06CQAg&zoom=1&iact=hc&vpx=930&vpy=343&dur=1101&hovh=201&hovw=251&tx=92&ty=167&sig=102233243155194550030&page=1&tbnh=137&tbnw=171&start=0&ndsp=18&ved=1t:429,r:16,s:0")

---

### Post by MrAlex on 2012-01-12
Part two - initial impressions

I have to say my initial impression of the desktop environment was good. I like the clean brush look, the color scheme, even the launchbar/taskbar thingie on the left side of the screen (will get a bit of use-to). A first (for me at least) was that the graphic card worked quite nicely out of the box (I use a rather complex setup with both a high-DPI TV and a monitor). I also liked how it invited me to install updated drivers for my ATI card.

Sadly this is where the fairy tale ended. When I wanted to install these 2 drivers that were recommended from ATI the thing failed with not much indication of what went wrong (it invited me to have a look at some log file but I couldn't discern what's wrong).

I gave up on the graphics card and decided to try out the browsing experience. I noticed my old friend Firefox over there (I used to use Firefox on windows until Chrome came along). All went well until I needed flash (which nowadays takes like 30 seconds). It said it needs some package from the net. This brought me to the android-market-like app which I found very interesting. However, installing the pack containing flash, codecs, java and other quite necessary things failed miserably! Again, not much of an error, and this is on a stock Ubuntu 11.10 install, I didn't even get a chance to do anything to it...

This took me about an hour to crack (most people would have given up on linux by now to be honest, but I'm stubborn)... I did manage to get to the bottom of it. Basically the problem was that Ubuntu was lying to me, telling me it's up to date... I had to go to software update and force it to check. Once I did that no more than 300 MB of updates came (that took a while). After installing these, the flash/java/codecs pack installed fully, and also the first of the ATI drivers also installed (not the post-release ones).

I like to point out that I think it's quite unfortunate that the update didn't work... this kind of things should work smoothly since it was on a stock install...

Well, with those things installed I wasted the next 4 hours playing around with different apps from the software center thingie. That was a fun thing to do, but I noticed most of the things starting with K (I guess those are intended for KDE) do not work properly since they have no menu options anywhere. Apparently they don't like the Apple-like bar with menu options. Unfortunately they are not marked as incompatible, which makes for a little waste of times. I don't remember having problems with running KDE apps under GNOME back in the day, but I guess things changed... I sadly had to let go of Kate (which was my lightweight IDE of choice for smallish homework in college) but I think Geany will make for a good replacement.

The conclusion for this part is:
- I love the way I didn't have to edit any text files and/or recompile the kernel (gone are the days, lol) to get the graphics card working at good resolutions.
- loved the software center thingie
- hated how things do not install properly out of the box. Having to guess that Ubuntu needed to be updated before I can intall flash is definitely unfortunate.
- ATI drivers still do not install. After 20 restarts I just gave up on 'em.
- incompatible apps are not marked as such in software center (see Kate for example)

(to be continued)

---

### Post by MrAlex on 2012-01-12
> **Paddy Landau said:**
> WUBI has two downsides.

1. It's a little slower than a native installation.

2. It's less reliable; it can be prone to sudden fatal failure, especially with updates.
Aaah... it's a good thing I asked here then because I was planning to hang on to this install... but I guess I will have to man-up and fire up that partition magic, eh? :)

---

### Post by GangrN on 2012-01-12
Did not try the wubi thing. I directly made a new partition for ubuntu and install was clean and easy. I am the computer-savvy type so maybe it was easier for me than for the average user, but I am no programmer. So I think that dual-boot will be easy for you to configure. A grub will be made fresh out of the MBR and it should work right out of the box.
Be sure to install latest version or don't try to upgrade, I have been experiencing issues while trying to upgrade kubuntu natty narwhal. As for you ati proprietary drivers, I must say it's often confusing. I don't use them at all and I have no issues with open driver, but maybe it depends of your video card (see ubuntu documentation: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) for list of supported cards).

Ther is also a bug with fglrx update (fglrx = proprietary driver)

---

### Post by OGpmpdog on 2012-01-12
Hi and welcome back to Ubuntu!

1) You could go to "Add ons" in Firefox, and search for (and install)
"Flash Aid"...this plug-in will enable you to install flash/shockwave within 3 minutes...restart FF, and you are good to go.

2) For ubuntu, Nvidia graphic cards work better than ATI...Ask yourself if it is worth 30-50 bux for better graphic capability.

Peace.


> **MrAlex said:**
> Part two - initial impressions

I gave up on the graphics card and decided to try out the browsing experience. I noticed my old friend Firefox over there (I used to use Firefox on windows until Chrome came along). All went well until I needed flash (which nowadays takes like 30 seconds). It said it needs some package from the net. This brought me to the android-market-like app which I found very interesting. However, installing the pack containing flash, codecs, java and other quite necessary things failed miserably! Again, not much of an error, and this is on a stock Ubuntu 11.10 install, I didn't even get a chance to do anything to it...


(to be continued)

---

### Post by Tamlynmac on 2012-01-12
> MrAlex

Just an observation:

This section is not a support section (see this [sticky]("http://ubuntuforums.org/showthread.php?t=1343965") and the sectional guidelines at the top of the T&E page) of the forums and the thread could be closed should the staff decide that support questions are being asked.

My recommendation is to maintain the thread as a testimonial of your install and not ask questions here regarding assistance. It's been my experience that the staff is very tolerant. However, they will close the thread. IMHO members should advise you to ask questions in the appropriate support section(s) and not respond to them here - jeopardizing your thread.

But that's just my $0.02

---

### Post by Paddy Landau on 2012-01-13
> **MrAlex said:**
> ... I noticed most of the things starting with K (I guess those are intended for KDE) do not work properly since they have no menu options anywhere.There is a small bug where if you install a new program, sometimes the menu does not catch up until you log out and in again (you don't have to reboot; just log out and in).

> **MrAlex said:**
> ... I will have to man-up and fire up that partition magic, eh? :)
If you accept the standard installation, Ubuntu will do all the "partition magic" for you. If you want a slightly different installation, you can still partition from the installer. But, as always, do **back up all your data first**. Although the installer has been so thoroughly tried-and-tested that it is very reliable, there is always a small chance of data loss. Also, uninstall WUBI and check that Windows is working correctly before you do a native installation.

---

### Post by bizz101 on 2012-01-14
From my expirience: Unless you need accelerated HD playback or something like that you don't need proprietary ATI drivers and even if you install it's better to download latest drivers from ati website. I have several ubuntu with ati cards setups and have proprietary drivers installed only at my mediacentre PC (ubuntu + xbmc) for playing HD content with acceleration and even that requires some tweaks like installing vaapi, disabling tearing ... For 'normal' user open-default drivers are great.

---

