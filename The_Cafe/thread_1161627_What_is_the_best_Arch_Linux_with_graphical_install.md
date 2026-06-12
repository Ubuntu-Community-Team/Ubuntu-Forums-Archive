---
title: "What is the best Arch Linux with graphical installer CD?"
date: 2009-05-16
forum: The Cafe
---

### Post by gymophett on 2009-05-16
I'm putting Arch on an old laptop. What is the best LiveCD or whatever for Arch. The real Arch installer is too complicated for me.

---

### Post by kerry_s on 2009-05-16
to complicated? are you sure arch is what you want?

when you say "old laptop" what kinda specs are ya talking.

---

### Post by Mehall on 2009-05-16
using anyhting other than the default Arch installer means you won't understand ANYTHING about how your arch runs, and that's necessary for runnign Arch. Try Crunchbang, it's Ubuntu based but runs on anything Arch does, and well.

---

### Post by Icehuck on 2009-05-16
> **gymophett said:**
> I'm putting Arch on an old laptop. What is the best LiveCD or whatever for Arch. The real Arch installer is too complicated for me.

I highly recommend not using any type of graphical installer for Arch. I am very far from an advanced linux user but after reading the documentation carefully I was able to do it. I went from installing Ubuntu for the first time to installing Arch(to learn) right away.  Just take it slow and read the documentation carefully and you will be fine. 

I will say I'm glad I didn't have a graphical install because I now have an idea of what is going on in my system.

---

### Post by gymophett on 2009-05-16
It wasn't exactly complicated, I just sort of needed a good guide through, can someone give me one? Arch wasn't installing right and it kept screwing up. My CD burner was messed up at the time though, and I know much more about Linux than when I tried to install Arch. I want to use Arch to learn that side of Linux.

---

### Post by Mehall on 2009-05-16
> **gymophett said:**
> It wasn't exactly complicated, I just sort of needed a good guide through, can someone give me one? Arch wasn't installing right and it kept screwing up. My CD burner was messed up at the time though, and I know much more about Linux than when I tried to install Arch. I want to use Arch to learn that side of Linux.

Remember: if the laptop is pre-PIII era, (i686) then Arch won't install on it, neither will Ubuntu.

[Beginners Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

[Install Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

The Arch Wiki is the best Documentation I have ever seen for anything EVER.

---

### Post by PrimoTurbo on 2009-05-16
I think it's not the worst idea to have a graphical version of Arch, provided that the installer allows the user to read in a simple way what exactly it is doing.

But Arch really is designed to be installed a certain way.

BTW I have not seen any graphic installers live cds for Arch.

---

### Post by Icehuck on 2009-05-16
> **Mehall said:**
> Remember: if the laptop is pre-PIII era, (i686) then Arch won't install on it, neither will Ubuntu.

[Beginners Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

[Install Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

The Arch Wiki is the best Documentation I have ever seen for anything EVER.

Follow that beginners guide word for word and you'll do fine. The live CD will also give you the location of the Install Guide that you can run in another terminal session (ALT-F2, ALT-F3) etc.

---

### Post by PrimoTurbo on 2009-05-16
Also I want to mention the best way to get the hang of installing Arch.

I remember when I first installed Arch linux, I did it in virtual box while reading the guide at the same time.

This allowed me to learn the process, Arch is actually very simple to install. It's very straight forward, the guide is also very well written.

So I suggest you do that if you are afraid to mess up.

---

### Post by gymophett on 2009-05-16
When I say old I mean 1.6 GHZ and 256MB Ram.

---

### Post by gymophett on 2009-05-16
> **Icehuck said:**
> The live CD will also give you the location of the Install Guide that you can run in another terminal session (ALT-F2, ALT-F3) etc.

This should be really simple then! :D
Thanks guys! I'll keep this thread going. I _will_ need help along the way.

---

### Post by crossfirevirus on 2009-05-16
Chakra makes one, no?

[http://chakra-project.org/download-iso.html](http://chakra-project.org/download-iso.html)

---

### Post by gymophett on 2009-05-16
> **crossfirevirus said:**
> Chakra makes one, no?

[http://chakra-project.org/download-iso.html](http://chakra-project.org/download-iso.html)

Buggy and still in Alpha.

---

### Post by chris4585 on 2009-05-17
Install arch like 3+ times, you start to remember the details.

---

### Post by binbash on 2009-05-17
there is chakra but it is buggy.

---

### Post by infoseeker on 2009-05-17
> **chris4585 said:**
> Install arch like 3+ times, you start to remember the details.

That's how I finally managed to install Gentoo  ;)

---

### Post by gjoellee on 2009-05-17
Check out this video: [http://video.google.co.uk/videoplay?docid=6213347420565640601](http://video.google.co.uk/videoplay?docid=6213347420565640601)

Watch it, learn it, and suddenly the installation of Arch is not as complicated as you think!

You should also check out [www.archux.com](www.archux.com)

NOTE: If you are having a hard time just to install Arch, Arch may not be the distro for you. However if yo put in some effort, decide to have up to two weeks with a lot of pain in your a**, you will learn a lot!

---

### Post by dspari1 on 2009-05-17
The Chakra Project is the only Live CD version of Arch. If you've already done the Arch installation before, I see no reason not to use it.

---

### Post by chris200x9 on 2009-05-17
> **dspari1 said:**
> The Chakra Project is the only Live CD version of Arch. If you've already done the Arch installation before, I see no reason not to use it.

not the only: [ larchix ](http://www.larchix.linuxdistroofthemonth.com) anyone? I think my intaller is borked though :P

> **infoseeker said:**
> That's how I finally managed to install Gentoo  ;)

I still need to read the manual and it's been 3+ times...:(

---

### Post by omar8 on 2009-05-17
If you have only one computer (so no access to beginners guide while installing).
Before you do anything, first read the beginners guide a couple times just to make sure you understand what is going on.
Install Arch using the CD/USB - this bit is the most straight forward, usually you just need to set the partitions (using a screen not that much more difficult than partitioning with windows XP), then install the default files, I am sure you can do that bit.
The hardest bit is configuring and this is relatively easy:
You can usually manage with only editing a few files (rc.conf, hosts, mirrorlist)

rc.conf - usually you just need to edit the hostname and the eth0 (if you have a router then usually it will be eth0="dhcp" so you can comment out the default suggestion).
```
eg,
HOSTNAME="desktop"

#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255"
eth0="dhcp"

```

hosts - just need to add your hostname to this file in the format:
```
127.0.0.1   localhost.localdomain   localhost **yourhostname**

```
so for my rc.conf it would be:
```
127.0.0.1   localhost.localdomain   localhost desktop

```

For the mirror list just delete all the URLS which arent in your country.

Then just set the password for the root account.

Install Grub.

Once you have installed it, reboot into arch (you will get a command line interface) - at this screen login to root using the password you set and do the following:
```
pacman -Syu
pacman -S elinks
```

Run "elinks" and browse to wiki.archlinux.org and click on the beginners guide - once you have it loaded up you should be ok. Then you will be able to switch to a new Command Line (Alt+F2) and just follow the guide.

---

### Post by chucky chuckaluck on 2009-05-17
arch is actually easier than it's made out to be. there are a number of automated options in the installation process. arch is just more detailed (like driving a stick compared to automatic). i'm just a humble end user and i reinstalled it, drunk, the other night in about 20 minutes, incluing X and a wm. the documentation is vividly clear and, thankfully, to the point. if you want to use arch, you should give the 'arch way' a chance. otherwise, there might be something far more suitable for your needs.

---

### Post by SuperSonic4 on 2009-05-17
The beginner's guide is also on the live cd although I'm not sure where it is but you can use less to view it like a text file.

Chakra is a live cd but is in alpha and it might not run on a system that old. If you do get it installed then in theory you can run ```
pacman -Rd kdemod-uninstall
``` which should give your arch without KDEmod packages.

Be very careful when it comes to the xorg section, one mistake can break X especially if input hotplugging is skipped over. Of course if you want a CLI system that doesn't matter.

Also pacman is an epic package manager

---

### Post by Pixel on 2009-05-17
> **gymophett said:**
> I'm putting Arch on an old laptop. What is the best LiveCD or whatever for Arch. The real Arch installer is too complicated for me.
If the default installer is too complicated then Arch is not for you.

---

### Post by nothingspecial on 2009-05-17
Does it have to be Arch?

It took me a couple of gos to do it, but then I normally do these sort of things when the wife is out for the night and I can inebriate myself to my hearts content.

Crunchbang, Zenwalk even Xubuntu will probably do it for you.

Arch is not hard if you can see the screen straight. However, although I applaud the ideas behind it, I`ve got a business to run and a wife and kids. I don`t see the benefit of installing it other than a learning process.

Therefore I reiterate what others have said. If you need a gui, use something else. If you want to use Arch, then do it properly. In my experience Zenwalk is faster anyway..........That being said *buntu is best - if you want to build from the ground up see 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
 Not exactly arch but a whole lot easier.

> In my experience Zenwalk is faster anyway but then I used gnome with my Arch install.

---

### Post by gymophett on 2009-05-27
> **chucky chuckaluck said:**
> arch is actually easier than it's made out to be. there are a number of automated options in the installation process. arch is just more detailed (like driving a stick compared to automatic). i'm just a humble end user and i reinstalled it, drunk, the other night in about 20 minutes, incluing X and a wm. the documentation is vividly clear and, thankfully, to the point. if you want to use arch, you should give the 'arch way' a chance. otherwise, there might be something far more suitable for your needs.

I know how to do many things via command line. The installation always messes up somewhere though. :(

---

### Post by mips on 2009-05-27
In all honestty I don't think Arch is for you. A simplified installer might hide the original install procedure but when things go wrong you might find yourself lost as you really have to learn what is going on. I'm not saying it is hard but it aint no Ubuntu and it requires a bit of motivation on your part. Stick to the original install cd.

---

### Post by snowpine on 2009-05-27
+1 to Chucky C. -- installing Arch is easier after a couple of pints.
I had my first successful install last night. It was much easier than I expected from all the moaning I read on the forums. The Arch beginners guide and wiki are both amazing.

---

### Post by aeiluindae on 2010-02-26
Actually, for some of us, graphical installs seem necessary. By way of example, the command line arch install and ubuntu server installs do not really work for me because of some weird quirk in my residence's network connection where the login info I pass via a web page doesn't seem to let the package manager through from the command line. Basically, I can install the OS fine, but I can't download updates or new packages at all. In contrast, graphical installs (the Chakra Live CD/DVD/USB is a good one) work perfectly. I have a hunch it might have something to do with different virtual terminals and such, but its just easier to do the graphical install when I know how to install Arch already.

---

### Post by chris200x9 on 2010-02-26
if you need graphics to read along, try nstalling it the chroot way.

---

### Post by gymophett on 2010-02-26
> **aeiluindae said:**
> Actually, for some of us, graphical installs seem necessary. By way of example, the command line arch install and ubuntu server installs do not really work for me because of some weird quirk in my residence's network connection where the login info I pass via a web page doesn't seem to let the package manager through from the command line. Basically, I can install the OS fine, but I can't download updates or new packages at all. In contrast, graphical installs (the Chakra Live CD/DVD/USB is a good one) work perfectly. I have a hunch it might have something to do with different virtual terminals and such, but its just easier to do the graphical install when I know how to install Arch already.

I agree. I see no reason why Arch could have no graphical installer. Even if it's just to boot into a basic CLI system.
But since I created this thread, almost a year ago, I have successfully installed Arch quite a few times. All I had to do was follow the beginners guide and it was a piece of cake. After the first few times, it was like flickin' a light switch.

I think that's what you meant. xD
I'm all confused ATM.

---

### Post by handy on 2010-02-26
Arch is great to try, it doesn't take very long to work out whether it is for you or not.

If you do find Arch suits you, & you do stick with it, it just gets easier (of course), it's inherent simplicity certainly helps in this regard, & it continues to become more & more the way you like it, as it doesn't experience consistent interruptions like most other distro's do.

Due to the rolling release system, you don't have to keep on reinventing the wheel, insofar as doing regular rebuilds due to a new distro release just doesn't happen anymore. This saves spending all that time adjusting the system to suit you (if you are that way inclined anyway). Of course a hardware failure can force you to rebuild if you don't have a system backup of some kind. :(

Most Arch users aren't all that familiar with the installation process, as rarely do they ever have to do it.

Thankfully the Beginners Guide is so incredibly well written & designed.

I think Misfit138 has had an enormous amount to do with the ongoing refinement of the BG, for which all Arch users are grateful. :KS

I say *that* after having a look at the BG history, Misfit138 is the most common name in the edits, for just the thousands that I skimmed over.  He obviously knows how important that first taste of Arch is for the potentially new Arch user, so he has to also continually police the changes made by users who quite often (by the look of the number of names in red) come in & deteriorate the quality of the BG one way or another.

---

### Post by PhoHammer on 2010-03-01
> **chucky chuckaluck said:**
>  i'm just a humble end user and i reinstalled it, drunk, the other night in about 20 minutes, incluing X and a wm.

Oh the joys of playing with Linux distros after you've had a few!:D

Edit: BTW, I'm installing Arch right now (I've tried before and failed), but apparently I picked a bad
mirror. It's horribly slow and it's not even the throttled one they warn you about...

---

### Post by SomeGuyDude on 2010-03-01
If you skip the text installer, you're going to be flying blind once you're actually using it.

Do NOT skip it. The ONLY reason for ANYONE to use one of those things is if they already know how to install Arch and just want something for the convenience.

---

### Post by snowpine on 2010-03-01
> **PhoHammer said:**
> Edit: BTW, I'm installing Arch right now (I've tried before and failed), but apparently I picked a bad
mirror. It's horribly slow and it's not even the throttled one they warn you about...

Case in point: this **exact** topic is covered, in detail, in the Arch Beginners Guide. :)

[http://wiki.archlinux.org/index.php/Beginners%27_Guide#Pacman-Mirror](http://wiki.archlinux.org/index.php/Beginners%27_Guide#Pacman-Mirror)

---

### Post by hhh on 2010-03-01
There is one reason to look for a Live CD installer of Arch... wireless. I have a common/crappy Belkin USB adapter and a communal wireless connection... and that's it. I have tried numerous times to install Arch using the installer and always setting up the adapter was a deal breaker.

Those who say there is no installable Live Cd are wrong, I know of 3 other than the ones mentioned...

Kahel OS, I wouldn't bother with this one.

Archbang just released RC-1 which has an installer for both 32 and 64 bit systems, uses Openbox/tint2 and has a pretty minimal set of installed packages, but again I  could not get my wireless network to come up...

[http://bbs.archlinux.org/viewtopic.php?id=89627](http://bbs.archlinux.org/viewtopic.php?id=89627)
[http://wiki.archlinux.org/index.php/ArchBang](http://wiki.archlinux.org/index.php/ArchBang)

Finally, Godane has been working hard on Archiso Live which uses XFCE, is installable, has a fuller selection of packages and detected my wireless adapter and network out of the box (though I haven't installed it, as my Karmic Openbox/tint2 setup is brand new and working perfectly for me)...

[http://godane.wordpress.com/](http://godane.wordpress.com/)
[http://godane.wordpress.com/faqs/](http://godane.wordpress.com/faqs/)
[http://arch-live.isawsome.net/iso/archiso/20100217/packages.list](http://arch-live.isawsome.net/iso/archiso/20100217/packages.list)

If you do go the conventional route, and addition to the install guides already mentioned, here is a quick guide to setting up Arch using Openbox as the window manager, written by the Archbang developer...

[http://willensky.blogspot.com/](http://willensky.blogspot.com/)

HTH

---

### Post by maestrobwh1 on 2010-03-01
[http://chakra-project.org/](http://chakra-project.org/)

BUT it installs kde4 so if you are looking for "light" it probably won't be what you want.

It runs well on a 900 MHz celeron tho.

---

### Post by SomeGuyDude on 2010-03-01
FWIW, the easiest way to set up wireless on Arch is just to follow the directions for Wicd. As long as you can hardwire the machine during the installation itself, you'll be golden. 

[http://wiki.archlinux.org/index.php/Wicd](http://wiki.archlinux.org/index.php/Wicd)

---

### Post by hhh on 2010-03-02
@SomeGuyDude, I specifically said that I only have a wireless connection. A hardwire connection would require me to move my desktop tower to another residence.

-edit- Thanks for that link though, that's very helpful and might allow me to figure out wireless on Archbang. :)

---

### Post by PhoHammer on 2010-03-02
> **snowpine said:**
> Case in point: this **exact** topic is covered, in detail, in the Arch Beginners Guide. :)

[http://wiki.archlinux.org/index.php/Beginners%27_Guide#Pacman-Mirror](http://wiki.archlinux.org/index.php/Beginners%27_Guide#Pacman-Mirror)

What do you mean "case in point"?
I specifically said I chose a mirror that was NOT archlinux.org, which is the only one they warn you about. BTW, I read the beginners' guide before installing...

---

### Post by SomeGuyDude on 2010-03-02
> **hhh said:**
> @SomeGuyDude, I specifically said that I only have a wireless connection. A hardwire connection would require me to move my desktop tower to another residence.

-edit- Thanks for that link though, that's very helpful and might allow me to figure out wireless on Archbang. :)

Haha, sorry about that. That said, you CAN get wireless going, at least for the duration of the installation. Just takes some more finagling.

---

### Post by Grifulkin on 2010-03-03
> **gymophett said:**
> It wasn't exactly complicated, I just sort of needed a good guide through, can someone give me one? Arch wasn't installing right and it kept screwing up. My CD burner was messed up at the time though, and I know much more about Linux than when I tried to install Arch. I want to use Arch to learn that side of Linux.

Can I just say that Arch doesn't teach you linux, Arch teaches you Arch.  The rc.conf is nothing like the normal linux distro.  I personally use Arch but it doesn't really teach you much, it teaches you very little in the big scheme of things.  Slackware on the other hand (which I have yet to setup) teaches linux way more than Arch ever could.  Just saying.

---

### Post by snowpine on 2010-03-03
> **PhoHammer said:**
> What do you mean "case in point"?
I specifically said I chose a mirror that was NOT archlinux.org, which is the only one they warn you about. BTW, I read the beginners' guide before installing...

There is a difference between reading the guide before you install vs. carefully following it step by step. I think you missed a step (but if I am wrong I apologize).

> Build a mirrorlist using the rankmirrors script

/usr/bin/rankmirrors is a python script which will attempt to detect uncommented mirrors specified in /etc/pacman.d/mirrorlist which are closest to the installation machine based on latency. Faster mirrors will dramatically improve pacman performance, and the overall Arch Linux experience. This script may be run periodically, especially if the chosen mirrors provide inconsistent throughput and/or updates. Note that rankmirrors does not test for throughput. Tools such as wget or rsync may be used to effectively test for mirror throughput after a new /etc/pacman.d/mirrorlist has been generated.

Force pacman to refresh the package lists

After creating/editing /etc/pacman.d/mirrorlist, (manually or by /usr/bin/rankmirrors) issue the following command:

# pacman -Syy

Passing two --refresh or -y flags forces pacman to refresh all package lists even if they are considered to be up to date. Issuing pacman -Syy whenever a mirror is changed, is good practice and will avoid possible headaches.

Then we use pacman to install python:

# pacman -S python 

    * If you get an error at this step, use the command "nano /etc/pacman.d/mirrorlist" and uncomment a server that suits you. 

cd to the /etc/pacman.d/ directory:

# cd /etc/pacman.d

Backup the existing /etc/pacman.d/mirrorlist:

# cp mirrorlist mirrorlist.backup

Edit mirrorlist.backup and uncomment all mirrors on the same continent or within geographical proximity to test with rankmirrors.

# nano mirrorlist.backup

Run the script against the mirrorlist.backup with the -n switch and redirect output to a new /etc/pacman.d/mirrorlist file:

# rankmirrors -n 6 mirrorlist.backup > mirrorlist

-n 6: rank the 6 closest mirrors

Now that we have the best mirrors, we upgrade the pacman database:

# pacman -Syy

---

### Post by PhoHammer on 2010-03-03
> **snowpine said:**
> There is a difference between reading the guide before you install vs. carefully following it step by step. I think you missed a step (but if I am wrong I apologize).

I apologize, you are correct. I thought you were saying that I chose the archlinux.org mirror. 

And I didn't check for the best mirror before installing, so that
 must have been my problem. I simply followed the "Official Arch 
Linux Install Guide", which, I believe, does not contain the tip
 about the mirror script. Perhaps they didn't want that guide to
 be overly verbose. I should have went over the Beginners' Guide 
more thoroughly. A learning experience! :p

But I have Arch up and running, with Gnome (after I changed the
 mirror, which I plan on checking for the best one for me soon). 
Just have to work out a few more kinks and read up about Arch 
maintenance!

---

### Post by snowpine on 2010-03-03
> **PhoHammer said:**
> But I have Arch up and running, with Gnome 

I love Arch+Gnome, it is a great combination! I especially love how easy it is to NOT install evolution (if you don't need it). I haven't done any objective testing, but Arch+Gnome seems as fast as Ubuntu+Openbox on my machine. Best of luck.

---

### Post by handy on 2010-03-03
I haven't read this thread, & I'm sure that someone has already said ArchBang.

Which is a LiveCD - Arch/Openbox, boots surprisingly quickly & has an inbuilt install option, which will ultimately allow you to have ArchBang installed on your HDD.

However you choose to install Arch, you are still going to have to learn how Arch works, because that is just how it is, with Arch.

---

