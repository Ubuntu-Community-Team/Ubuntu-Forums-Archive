---
title: "Important Update"
date: 2006-09-14
forum: System76 Support
---

### Post by crichell on 2006-09-14
Hello everyone.

Today there was a kernel update which seems to be causing some problems.  If you haven't updated today please DO NOT UPGRADE.  If you have please let me know of any problems you are having.  We are working to resolve the know issues now.

I will keep everyone posted here.

Thanks

Carl Richell
System76

---

### Post by jdong on 2006-09-14
Ouch... [http://www.ubuntu.com/usn/usn-346-1](http://www.ubuntu.com/usn/usn-346-1) this is the update you speak of.


What kind of trouble has it been causing? It should've been a relatively straightforward security update with a few bugfixes mixed in.

EDIT: Apparently the nvidia kernel module is broken by the update. I'm not sure what else.

---

### Post by crichell on 2006-09-14
You right - the nVidia kernel module and also the following ethernet card:

> lspci
0000:05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 11)

It's strange - the card doesn't even show up in HAL after the update.

Sound was also effected on one machine; however, our sound driver restores it.

---

### Post by jdong on 2006-09-14
Hmm, strange. They know about the nvidia issue and are rolling out a new kernel update with an ABI bump (so linux-restricted-modules is properly rebuilt) this time.

I'm gonna probe into that network card a bit.

UPDATE: [http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=c615082cb9073ec25c230e082c79d16cf85cff50](http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commit;h=c615082cb9073ec25c230e082c79d16cf85cff50)

It does seem like there was a bit of updating done to the sk98lin driver. Still trying to get the devs attention on the issue.

---

### Post by Tom Tiger on 2006-09-14
Same problem here,  the new kernel update broke the Nvidia proprietary drivers,  sound and network are ok (ASUS P4P800 with gigabit ethernet)
I switch my xorg.conf back to the standard nv driver and everything works again. Nvidia driver is bust... I probably need to reinstall that one...

---

### Post by crichell on 2006-09-14
We're still running through our line - I may

---

### Post by jdong on 2006-09-14
> **Tom Tiger said:**
> Same problem here,  the new kernel update broke the Nvidia proprietary drivers,  sound and network are ok (ASUS P4P800 with gigabit ethernet)
I switch my xorg.conf back to the standard nv driver and everything works again. Nvidia driver is bust... I probably need to reinstall that one...

You shouldn't need to install the nvidia driver again, though if you're in that much of a hurry to use your 3d acceleration, then fine.

A new linux-restricted-modules package should be up in a few hours that'll solve the nvidia mess.

---

### Post by crichell on 2006-09-14
Where is our edit key :)

We're still running through our line - I may have more but so far it's down to nvidia, the network card and sound.

The sound may also be of interest.  On this particular model our driver adds microphone support but not support for all of the sound cards functionality.  

After the kernel update the entire card was wiped.  Our driver restored the card but other people with the "14f1 ID 5045" codec may lose sound.

If anyone has this codec and is effected by the update I'd be happy to provide our driver for you (it's adds microphone functionality too).

---

### Post by bencollins on 2006-09-14
> **crichell said:**
> You right - the nVidia kernel module and also the following ethernet card:



It's strange - the card doesn't even show up in HAL after the update.

Sound was also effected on one machine; however, our sound driver restores it.


The nvdia problem is being resolved, and it will be available as an update to linux-restricted-modules-2.6.15 within hours from now.

As for the Marvell issue, I'm very surprised that you had this card working at all. The sky2 driver has been a major issue in dapper since it's release. The last update included a change from the new sky2 driver, to the known working sk98lin driver we had in breezy (a direct forward port).

Can you verify whether the sk98lin is loaded? (lsmod | grep sk98lin). If not, please run "sudo modprobe sk98lin".

---

### Post by crichell on 2006-09-14
sk98lin is not loaded.  The card isn't visible in HAL after loading the module.

The card worked out of the box up until todays update.

---

### Post by bencollins on 2006-09-14
> **crichell said:**
> sk98lin is not loaded.  The card isn't visible in HAL after loading the module.

The card worked out of the box up until todays update.

Can you email me the full output of dmesg (after trying to load the card).

Also the output of these commands:

lspci -vv
lspci -vvn

[email]bcollins@ubuntu.com[/email]

---

### Post by bruceliz on 2006-09-15
The 14 September kernel security update caused me (running Dapper) data loss:

/boot/grub/menu.lst was rewritten in the update process, preserving all the Ubuntu entries (including a manually-entered one for a custom-built 2.6.17.3), but _wiping my Debian etch entries_ for a parallel installation on another set of partitions, thus requiring a manual edit of menu.lst to repair the damage.

Now that's some wicked Debian-unfriendliness!;)

---

### Post by jdong on 2006-09-15
Well, that's an annoyance certainly, but I wouldn't call that 'data loss' ;)

---

### Post by Leif on 2006-09-16
Not sure whether **crichell** needs the solidarity, but my Marvell ethernet connection got broken too, so I'll be checking here, hoping for a solution soon.

---

### Post by Leif on 2006-09-16
Um, sorry for the double post, but there seems to be no edit option in the subforum. I'm not using a system76 laptop, so apologies if I'm intruding :roll:

---

### Post by crichell on 2006-09-16
Hi Leif - your not intruding - we're here to help out.  I received a message from Ubuntu devs last night.  They have uploaded a new kernel that includes support for our Marvel card.  I haven't seen it come down yet but as soon as it does we'll be back in business.

---

### Post by Tux Aubrey on 2006-09-17
I experienced a problem with the kernel update on 14 September and have been trawling the forum for something similar.  It is not a graphics driver problem - I dont have nvidia graphics (SIS on an ABIT board). 

Booting with the new kernel (2.6.15-26-386) hangs when trying to load the root filesystem.  After 4 or 5 minutes waiting, it drops to a command line screen and says my primary linux partition (/dev/hda2) does not exist.  (This is a dual boot XP/Windows P4 machine that has been working fine till now.)  

My GRUB entries look fine.

This is the problem entry: 

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

Yet this still works fine:

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

Strangely, booting with the "old" kernel after hanging with the new one results in a very unstable session - apps closing for no reason, freezes etc.  A reboot seems to recover everthing OK.

Is there an option of re-installing the -26-386 kernel just to test whether  it was a dirty install?  

BTW. I have tried various work arounds suggested elsewhere (the noapci, pci=biosirq and the UUID rick) but none made any difference.

This is my first post and first time using Ubuntu, so be gentle with me.

---

### Post by Tux Aubrey on 2006-09-17
Sorry - wrong forum I guess (Wots System 76?)  

I'll try in the Stupid NOOBS forum if I can find it.

---

### Post by missmoondog on 2006-09-17
yep that update has foobarred my nvidia TNT2 on one machine and i'm not positive about my i845 machine, but no matter what settings i put in the display section of kcontrol, it doesn't stick. doesn't work if i do it manually either. i have to restart xserver to get it to load the settings i want, so it does remember the settings somewhere, otherwise always starts with a screen size of 640x480 (if that's the right numbers).

---

### Post by missmoondog on 2006-09-17
so, when is this new patch coming out? what's with all the foobarred updates lately? don't they bother testing any of this stuff anymore? no wonder they say there will be support for dapper 3 years! easy to support something that doesn't get tested!

---

### Post by crichell on 2006-09-17
The nVidia issues has been resolved (in our testing).  The restricted modules update that came out shortly after the kernel update cleared up the issue.

Tux Aubrey - [www.System76.com](www.System76.com) - that's us - no problem with posting here though.  I ran into the same problem on a prospective laptop in the past.  It seems to boil down to a certain hard drive SATA adapter that causes the problem (for us at least).  It's strange that this update caused the problem for you.  You can see the Launchpad bug report [here]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48556").

---

### Post by Leif on 2006-09-19
The sky2 network issue has been resolved (at least for me) with today's kernel update. Cheers to the devs ! And to the bug reporters !

---

### Post by ampop on 2006-09-19
Today I upgrade to 2.6.15-27-386. And now my sound is dead.
Any else with this problem.

---

### Post by jdong on 2006-09-19
*bang head on desk*

Don't you love it when a fix restores sound for some and breaks sound for others?

---

### Post by ampop on 2006-09-19
My problem it's solved. I have a brand new acer laptop, when I installed Ubuntu, I had no sound. In this forum it's explained how to patch the kernel to have sound.
Every time I upgrade the kernel, I must run the patch.

---

### Post by crichell on 2006-09-19
ampop - your sound problem will probably be fixed with Edgy.  We run into sound support issues often so we build drives to enable support - generally an ALSA upgrade with a patch takes care of it.

Edgy will use a newer ALSA with which each release adds support for additional cards.

---

### Post by ampop on 2006-09-19
> **crichell said:**
> ampop - your sound problem will probably be fixed with Edgy.  We run into sound support issues often so we build drives to enable support - generally an ALSA upgrade with a patch takes care of it.

Edgy will use a newer ALSA with which each release adds support for additional cards.

Well, maybe the best way it's wait for Edgy and don't accept more kernel upgrades. Do you agree?
Thank you for the advise.

---

### Post by jdong on 2006-09-19
It's not advisable to skip kernel upgrades -- they usually fix a security issue that's important enough to warrant an upgrade being issued.

Just remember to install your ALSA drivers again after the upgrade -- it's as simple as that.

---

### Post by crichell on 2006-09-19
That's a tough call - kernel updates may plug security holes or add functionality.

You can just use a script to install ALSA whenver you get a kernel update.  I've attached a sample script.  Extract the archive and then modify the /this/is/the/path/to/alsa/folder/ portion with the path to your downloaded alsa version.  You may want to move it to /opt/alsa/ or someplace like that.

To run the script open a terminal and type

```
sudo install_alsa.sh
```

---

### Post by Kaloma on 2006-09-19
I have a Serval Performance, and my sound stopped working today after the latest kernel updates.  I have tried reinstalling both the system76 drivers and ALSA, but to no avail.

Any other suggestions, besides wait?  I can certainly get by without if need be, since I mostly use this laptop for work (development, teaching, presentations).  My use of sound with this laptop is recreational, at present.

-Matthew-

---

### Post by Kaloma on 2006-09-19
False alarm!

I though I had reinstalled ALSA correctly, but I guess I missed a step.  Once I noticed the script Carl posted, I gave it a try and that did the trick.  I'll need to look more closely at the script since I'd like to understand what is really going on in there and what I overlooked myself.

Anyhow, thanks again!  Sound is back!

-Matthew-

---

### Post by ampop on 2006-09-19
> **crichell said:**
> That's a tough call - kernel updates may plug security holes or add functionality.

You can just use a script to install ALSA whenver you get a kernel update.  I've attached a sample script.  Extract the archive and then modify the /this/is/the/path/to/alsa/folder/ portion with the path to your downloaded alsa version.  You may want to move it to /opt/alsa/ or someplace like that.

To run the script open a terminal and type

```
sudo install_alsa.sh
```

Thank you very much.

---

### Post by bluetoothfairy on 2006-09-19
Today's kernel update brought back sky2 and my Marvell 88E8036 ethernet is messed up. It worked perfectly with sk98lin from the previous update. I'm losing connection again, anyone else having similar issues? This is really annoying, does anyone know if next kernel update will bring back sk98lin and what's the deal with this bug?

---

### Post by jdong on 2006-09-19
> **bluetoothfairy said:**
> Today's kernel update brought back sky2 and my Marvell 88E8036 ethernet is messed up. It worked perfectly with sk98lin from the previous update. I'm losing connection again, anyone else having similar issues? This is really annoying, does anyone know if next kernel update will bring back sk98lin and what's the deal with this bug?

How fascinating once again.... Some people say sk98lin works, others (like what happened earlier this thread) says that introducing sk98lin makes it break.

---

### Post by crichell on 2006-09-19
> **Kaloma said:**
> False alarm!

I though I had reinstalled ALSA correctly, but I guess I missed a step.  Once I noticed the script Carl posted, I gave it a try and that did the trick.  I'll need to look more closely at the script since I'd like to understand what is really going on in there and what I overlooked myself.

Anyhow, thanks again!  Sound is back!

-Matthew-

Hi Matthew - this is particularly interesting because the Serval works with Dapper's version of ALSA out of the box.

---

### Post by ndv_ubu on 2006-09-22
Hello.

My sound broke too ...
It stopped working with some update in the last 2 weeks and it doesn't work with kernels *.23 (the first that i had), *.26, *.27 ..

Any solutions already ?


Thanks a lot in advance !

---

### Post by crichell on 2006-09-22
what is your sound card codec?  check by:

right click on your speaker > Open Volume Control
click File > Change Device
What is the name of the second listed device (the actual codec used by your sound card)?

---

### Post by ndv_ubu on 2006-09-23
I have two options in the list :

- HDA Intel (Alsa Mixer)
- Realtek Alc260 (OSS Mixer)

The first one was selected. After reading your answer, I tried the second one but there was no sound too ..

---

### Post by ndv_ubu on 2006-09-23
My sound is back !

In the VolumeControl (right click on your speaker > Open Volume Control), in the 'options' tab, there is an option 'Headphone jack mode'. The option that was choosen was 'Line in'. I changed it to 'Headphone out' .. and the sound was back !
I don't know how that option changed itself to 'Line in', but i never messed up in the Volume Control applet.

Well, the sound is back .. that's what matters.

Thanks a lot to Carl, for the tip "right click on your speaker > Open Volume Control .... ". The solution for my problem was near there :)

---

