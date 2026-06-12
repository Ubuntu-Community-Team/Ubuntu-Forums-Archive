---
title: "lubuntu 12.10"
date: 2012-08-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by linuxusersince2008 on 2012-08-14
i seen the preview of lubuntu 12.10 and i'm not impressed i thought lubuntu suppose to be lightweight but every new release i feel it's getting slower or is it me.:(

---

### Post by nothingspecial on 2012-08-14
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by TenPlus1 on 2012-08-14
Lubuntu runs very well on my Acer Aspire Revo and in a way I prefer it over Xubuntu...

I would like to see the e-mail client change from Sylpheed to Claws Mail in the next release as Claws seems lighter and faster with more features...

---

### Post by linuxusersince2008 on 2012-08-14
i see, also would the non-pae kernel apply to lubuntu as well?

---

### Post by MG&amp;TL on 2012-08-14
> i seen the preview of lubuntu 12.10 and i'm not impressed i thought lubuntu suppose to be lightweight but every new release i feel it's getting slower or is it me.

Not really. Just for you, I stuck in an old 11.04 CD and saw no visible difference between that and 12.10 on a Pentium IV.

One also has to bear in mind that technology moves on. While we're still supporting old computers, we still have to draw the line somewhere, currently "A Pentium II or Celeron system with 128 MB of RAM is probably a bottom-line configuration.".

> **linuxusersince2008 said:**
> i see, also would the non-pae kernel apply to lubuntu as well?

Yes. Unfortunately, Lubuntu is a (small-ish) group of volunteers, and we just don't have the manpower to run a separate kernel to the rest of the *buntu family. We probably could, but then the rest of it would go to pot.

> Lubuntu runs very well on my Acer Aspire Revo and in a way I prefer it over Xubuntu...

I would like to see the e-mail client change from Sylpheed to Claws Mail in the next release as Claws seems lighter and faster with more features...

Feel free to pop this on the mailing list, we DO listen to users, y'know. :P 

I think someone's working on Sylpheed to make it more awesome though.

---

### Post by kansasnoob on 2012-08-14
> **linuxusersince2008 said:**
> i see, also would the non-pae kernel apply to lubuntu as well?

I don't think any of our flavors will have official non-pae support beyond 12.04, but there is an ongoing discussion here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)

Sadly no actual dev has replied :(

---

### Post by ventrical on 2012-08-14
I can't get gnome-classic or cairo-doc to work right with the new 3.5.0-10 kernel but I am able to install them on precise.

 Only Lubuntu desktop will work normally with  quantal so far.

---

### Post by linuxusersince2008 on 2012-08-14
if this the case then i'll be looking for a new distribution, linux seems to keep there users happy. i don't get why the kernel can't automatically detect if the hardware supports pae or not it would save alot users but i see ubuntu is going vista on there users, i'm using lubuntu now and it's not very stable. what a shame i do have a pentium 2 350mhz that still works very well but i would be able to upgrade to 12.10. oh well linux mint, vector linux or wattos
seems to be my last choice or go back to windows 2000 pro.

---

### Post by jerrylamos on 2012-08-14
> One also has to bear in mind that technology moves on. While we're still supporting old computers, we still have to draw the line somewhere, currently "A Pentium II or Celeron system with 128 MB of RAM is probably a bottom-line configuration.".My IBM Thinkpad T40, 768 MB ram, 1.5 gHz Ubuntu support stopped with 12.04.  During boot, 12.10 checks for pae flag and stops there.  Actually, early in Alpha 12.04 the pae check wasn't working so the T40 Unity 2D ran fine.  Then the check was put back in so I'm running 12.04 non-pae lubuntu on it.  Tried upgrading to 12.10 some packages updated some didn't.  Not worth the bother.

I'm running Debian Wheezy LXDE desktop Midori browser on my Raspberry Pi 256 MB.  I don't expect Ubuntu will be interested since their development efforts are more toward touchscreen tablets.

Jerry

---

### Post by linuxusersince2008 on 2012-08-14
true, they have to realize not everyone want a tablet, gnome 2 was fine the way it was, matter of fact that reminds me ubuntu 8.04 was great i just tried it on my current setup and compiz works very well but when i upgraded to 10.04 it didn't work anymore ubuntu has been going downhill since then adding features i don't need. lubuntu is suppose to be for older hardware removing non-pae kernel remove that purpose.

---

### Post by cariboo on 2012-08-14
> **jerrylamos said:**
> My IBM Thinkpad T40, 768 MB ram, 1.5 gHz Ubuntu support stopped with 12.04.  During boot, 12.10 checks for pae flag and stops there.  Actually, early in Alpha 12.04 the pae check wasn't working so the T40 Unity 2D ran fine.  Then the check was put back in so I'm running 12.04 non-pae lubuntu on it.  Tried upgrading to 12.10 some packages updated some didn't.  Not worth the bother.

I'm running Debian Wheezy LXDE desktop Midori browser on my Raspberry Pi 256 MB.  I don't expect Ubuntu will be interested since their development efforts are more toward touchscreen tablets.

Jerry

Please stop spreading FUD (Fear, Uncertainty, Doubt) [Linaro]("http://www.linaro.org/") builds distributions that run on Arm cpu's, most tablets use an Arm processor. Canonical is a Linaro [partner]("http://www.linaro.org/partners"). The Arm version is totally different from running a i386 or AMD64 version.

---

### Post by linuxusersince2008 on 2012-08-14
i don't think it's fear, i think it's the truth admin.

---

### Post by cariboo on 2012-08-15
This is getting way off topic, it's partly my fault. The op of this thread was complaining that Lubuntu is getting to be bloated. Bloat is different for different people. For some it's programs installed by default, that they don't use, for others, it is the additions that are added to most of the  Ubuntu derivatives, that aren't included in a plain vanilla Debian install.

If you have a system that won't run the latest version of the Ubuntu derivatives, you still have several options. There are several Debian based distributions that work quite well on older hardware, one is [Mepis]("http://www.mepis.org/"), it is still based on Debian, so you don't have to learn anything to in order to use it. There is also Debian stable, I run it on an Apple G4 with a 350Mhz cpu and 90MiB ram with zero problems.

Another option is compiling your own kernel, for more info look [here]("https://help.ubuntu.com/community/Kernel/Compile/").

A final option is installing from the mini.iso, where you only install what you want, this may take a bit of research, [here]("https://help.ubuntu.com/community/Installation/MinimalCD/"), is some documentation on the wiki.

---

### Post by linuxusersince2008 on 2012-08-15
i just installed peppermintos 3 it's not bad. i'm just upset that ubuntu abandon there roots ubuntu used to be for desktops and laptops i remember using ubuntu 8.04 which was my first linux distro i ever used and loved it. compiz even worked. but 10.04 didn't. :( i just don't it why can't they support old and new hardware? and have pae auto detect hardware instead having it enabled by default. ubuntu lost me with unity and alot of my friends hate too even today i can't get used to it, and still hate it. ubuntu is losing popularity fast.

---

### Post by mcellius on 2012-08-15
> **linuxusersince2008 said:**
> i just installed peppermintos 3 it's not bad. i'm just upset that ubuntu abandon there roots ubuntu used to be for desktops and laptops i remember using ubuntu 8.04 which was my first linux distro i ever used and loved it. compiz even worked. but 10.04 didn't. :( i just don't it why can't they support old and new hardware? and have pae auto detect hardware instead having it enabled by default. ubuntu lost me with unity and alot of my friends hate too even today i can't get used to it, and still hate it. ubuntu is losing popularity fast.

I suspect this subject has already been discussed in these forums *ad nauseam*, especially with regard to Unity, so I respond with some hesitation.

I run Ubuntu on desktops and laptops, and don't see any evidence that those platforms are being abandoned.  In fact, its development seems to me to be focused on those platforms, where it works better all the time.  It's stable and efficient, and the Quantal alphas show a great deal of work and progress.  I am very impressed!

As for Unity, repeated surveys seem to show it as the most popular of the DEs for Ubuntu.  I like it and in fact prefer it, and find that I am very productive with it (and I think it's fun, too).  Of course, I understand that people have different preferences, so it's nice to know that Ubuntu doesn't force Unity upon its users, as it can run just about any other DE, too: Gnome, Gnome Classic, Mint, Cinnamon, KDE, etc., including Xubuntu and Lubuntu.  (I've tried them all and still prefer Unity, but don't claim it's the best: it's simply the best for me right now.)

Finally, as for Ubuntu "losing popularity fast," well I don't see that, either.  At least, I've never seen numbers to support that claim (except for DW's hitlist, which has numbers that disagree greatly with everyone else's to a great degree and are likely the result of intentional misrepresentation).

---

### Post by ventrical on 2012-08-15
I don't see where the tablet mentality is with Lubuntu. Looks like the same desktop to me as in past versions.  Of course there are going to be problems with most processors 400MHz and under.  Also , this is beta testing where we try to iron out bugs and such and make suggestions. .

---

### Post by linuxusersince2008 on 2012-08-15
unity isn't useful to me. i liked gnome 2 and still do it's faster then unity and doesn't get in the way for me.

---

### Post by VinDSL on 2012-08-15
> **linuxusersince2008 said:**
> i just installed peppermintos 3 it's not bad. i'm just upset that ubuntu abandon there roots ubuntu used to be for desktops and laptops.[...]
> **linuxusersince2008 said:**
> unity isn't useful to me. i liked gnome 2 and still do it's faster then unity and doesn't get in the way for me.
Interesting.

You have a foot in both camps.  So does Lubuntu, so-called.  And, Peppermint OS, as well.

Personally, I'm rolling my own LXDE/Ubu combination.  It works so well (even on older hardware) that I've thought about publishing my own distro -- but why bother?!?!?

IMO, based on lots of testing:  "Peppermint TWO OS" is the perfect Ubu-based distro for ancient iron.  That's what I'm currently running on all my portables of various pedigree -- laptop, netbook, USB thumb drives, blah, blah, blah.

For my production machine (circa. 2005 - see my sig) I'm running my own custom blend of LXDE/Openbox on top of Ubu 12.10

If you're incapable of building your own distro, but are unhappy with the direction Canonical is going, I would strongly suggest installing Peppermint **[COLOR="DarkRed"]Two[/COLOR]** OS.

Nothing against Lubuntu, but it's a moving target.  Some ppl like that - some ppl don't.

Peppermint OS moves at a glacial pace, which would probably suit your personality better.

Basically, Peppermint is a forward-thinking Lubuntu fork running on  top of an older kernel...  ;)

---

### Post by ventrical on 2012-08-15
> **VinDSL said:**
> Interesting.

You have a foot in both camps.  So does Lubuntu, so-called.  And, Peppermint OS, as well.

Personally, I'm rolling my own LXDE/Ubu combination.  It works so well (even on older hardware) that I've thought about publishing my own distro -- but why bother?!?!?



 I would give it a run. :) I did this weird experiment with Lubuntu. I copied all the Lucid sources to the souces.list , then  updated and installed gnome-session-fallback and it worked beautiful on this older machine *WITH* compiz too.

---

### Post by linuxusersince2008 on 2012-08-15
i'm not a programmer but if i was i would modify ubuntu 8.04 with a updated kernel and update the software sources. the rest can stay the same.:popcorn:

---

### Post by cariboo on 2012-08-15
> **linuxusersince2008 said:**
> i'm not a programmer but if i was i would modify ubuntu 8.04 with a updated kernel and update the software sources. the rest can stay the same.:popcorn:

You don't have to be a programmer to roll your own, all it takes is a bit of learning. When I first started using Linux (1998), I had to learn how to compile a kernel, as SMP (dual cpu support) was not included in any default kernel. I had a server that ran dual 223Mhz cpu's and supported up to 1GiB ram. In order to get the full benefit of the system I spent days compiling kernels and trying them out, using a single cpu it took about 3.5 hours to compile a kernel, using both cpu's compile times went down to just over an hour.

Anything is possible, it's just a matter of how much time you want to spend learning how to do what you want.

---

### Post by linuxusersince2008 on 2012-08-15
do you have a how to video?

---

### Post by cariboo on 2012-08-15
> **linuxusersince2008 said:**
> do you have a how to video?

I linked to the wiki in a previous post, I think the subject is a bit more complicated, than what can be covered in a howto video.

[LIST]
[*][Mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD/")
[*][Kernel Compile]("https://help.ubuntu.com/community/Kernel/Compile/")
[/LIST]

---

### Post by linuxusersince2008 on 2012-08-16
i see.

---

### Post by jerrylamos on 2012-08-16
With Unity 2D gone, I'm not sure where to start - take the quantal .iso, install LXDE, then remove Unity 3D?  Does that work?

Or start with Lubuntu and add packages in as I need them?

Thanks, Jerry

p.s. Lubuntu up and running, now comparing to Ubuntu 3D.  Replaced Chromium with (smaller) Firefox.  On this Acer Aspire 5253 On this 64 GB dual processor 2 GB memory I'm having to learn that when I boot 3D, be patient...... it's not dead, it'll be along some time....

---

### Post by cariboo on 2012-08-16
> **jerrylamos said:**
> With Unity 2D gone, I'm not sure where to start - take the quantal .iso, install LXDE, then remove Unity 3D?  Does that work?

Or start with Lubuntu and add packages in as I need them?

Thanks, Jerry

You'd probably be best starting with the mini.iso, and only add what you want.

---

### Post by jerrylamos on 2012-09-01
Long live lubuntu.  Being lazy, I just install Quantal then do a
sudo apt-get install lxde
running fine.  Since lxde is a debian desktop not dependent on canonical, so long as ubuntu can still install debian packages, I'm set.

I did try a synaptic install of lxde-desktop which brought in a whole bunch of stuff I don't use.  So I don't do that.

I've got lxde with Firefox, Libre, samba, network drives, gedit, on and on all that stuff I usually use.

---

### Post by cariboo on 2012-09-01
> **jerrylamos said:**
> Long live lubuntu.  Being lazy, I just install Quantal then do a
sudo apt-get install lxde
running fine.  Since lxde is a debian desktop not dependent on canonical, so long as ubuntu can still install debian packages, I'm set.

I did try a synaptic install of lxde-desktop which brought in a whole bunch of stuff I don't use.  So I don't do that.

I've got lxde with Firefox, Libre, samba, network drives, gedit, on and on all that stuff I usually use.

If you try installing Debian packages on your Ubuntu install you are going to break it. All the packages in the Ubuntu repositories are modified by the developers, as dependencies are different, and Ubuntu branding is added. Please do some research, before making statements that can be proven wrong.

---

### Post by ratcheer on 2012-09-01
Here's another idea, if I'm not going too far off topic. Try **Siduction Linux**. It is a leading edge Debian-based distro with LXDE. It is extremely light on resources; I think it is the lightest distro I have, which includes Arch Linux. I've been running it for a few months and it is very high on my list.

Tim

---

### Post by jerrylamos on 2012-09-01
> **cariboo907 said:**
> If you try installing Debian packages on your Ubuntu install you are going to break it. All the packages in the Ubuntu repositories are modified by the developers, as dependencies are different, and Ubuntu branding is added. Please do some research, before making statements that can be proven wrong.

I did a sudo apt-get install lxde.  I assume that will go somewhere in /etc/apt/sources.list.  The point I was trying to make, maybe not successfully, that 2D lost support and vanished.  Perhaps some other packages that have life outside of canonical will continue to be available to apt-get, perhaps not.  I'm not a developer so I may not use the words people expect.

Do note in bug shooting I've installed the Debian kernel from Debian onto Quantal to see if it would help on my wireless WPA autoconnect bug.  The Debian kernel ran fine on Quantal, except for the bug which was still present.  Debian development looked at the problem, and pointed to ubuntu.  Clearly to them as soon as ubuntu asked they went ahead and connected easily first try.  The question of why ubuntu isn't asking for connect is still open in the bug.  Round about way to say a big piece of Debian would still work with ubuntu.  No guarantees of course.

---

### Post by kalehrl on 2012-10-17
Any new information regarding PAE and Lubuntu 12.10?
Will 12.10 support it or is 12.04 the end of the road for us with non-pae CPUs?
Will people running 12.04 who try to update the distribution be warned at least that they can't update?

---

