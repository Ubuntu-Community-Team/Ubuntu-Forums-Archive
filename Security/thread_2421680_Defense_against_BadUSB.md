---
title: "Defense against BadUSB?"
date: 2019-06-25
forum: Security
---

### Post by VanillaMozilla on 2019-06-25
The existence of BadUSB is well known, or should be well known to all.  The USB standards allow any USB device to be used to infect your computer and possibly any USB device that is subsequently plugged into it.  This article presents a brief overview of the threat:  [https://lmgsecurity.com/bad-usb-very-bad-usb/](https://lmgsecurity.com/bad-usb-very-bad-usb/) .  Mark Shuttleworth called firmware "a trojan horse of monumental proportions" ( [https://en.wikipedia.org/wiki/Firmware#Security_risks](https://en.wikipedia.org/wiki/Firmware#Security_risks) ).  Anyone who still has doubts should probably read that section.  If you reply, please do not claim that there is little or no risk unless you can tell me what countermeasures have been taken.  BadUSB has been widely known since at least 2014, and there are numerous exploits in the wild.

My problem is what do about it.  The very common, but terrifying scenario is that you need to share data with the outside world, so you need to mount a USB drive with an unknown history.  This could include, for example, pictures from a friend that you want to see.  The only preventative security measures I have seen involve whitelisting, blacklisting, or requiring a password to mount.  These measures are completely ineffective against a device with an unknown history.

Ideally, a USB drive would not require trust.  Ideally it would just identify the file system (and not much else), and the system would choose the appropriate driver.

So just WHAT DO I DO?  And what do WE do?  Is there any way of drastically trimming the capabilities of a USB port to perform only safe functions?  Any solution needs to be simple and straightforward so even I can understand it.

---

### Post by DuckHook on 2019-06-25
It's true that BadUSB is a nasty attack vector. It is also true that compromised firmware is another known, subtle, attack vector. But these are just instances of a larger set of vulnerabilities that are just as widely known and just as nasty. For example, Firewire has unfettered access to system memory. Bluetooth has known structural holes that have been exploited by scumbags for years. Side channel attacks of modern CPUs via speculative execution (Spectre, Meltdown, et al) are especially pernicious and hard to defend against. When it comes to HW vulnerabilities, the list is as long as my arm.

The point is not that BadUSB and firmware attacks should be underestimated, but that they must be measured against the much larger universe of nasties that infest the computing sphere. Just because BadUSB and opaque proprietary firmware are vulnerabilities is no reason to go around claiming that the sky is falling.

USB is poorly designed. It does not have safeguards against the sort of HID spoofing that is used for BadUSB. In my opinion, proprietary (non FOSS) firmware is even worse because, so long as it remains the prevailing philosophical model for HW design, we have no choice but to accept hidden exploits as the price of usability.

You can mitigate potential BadUSB attacks by defining udev rules that shut down new HID devices as per [this strategy]("https://security.stackexchange.com/questions/64524/how-to-prevent-badusb-attacks-on-linux-desktop#64552"). But it's just an awkward kludge, and until USB is redesigned to be more secure by default, there really isn't much that any of us can do.

As for compromised opaque proprietary firmware? There isn't *anything* we can do about it other than to use as little of it as possible and support/agitate for libre firmware. You can start by buying kit from companies like Purism or Libre Computing. Be prepared for less than stellar performance because the big OEMs like AMD, nVidia, Broadcom and Intel just don't believe in libre, especially with their newest or best stuff.

> **VanillaMozilla said:**
> &#8230;Any solution needs to be simple and straightforward so even I can understand it.

You can't have your cake and eat it too. As already stated, the problem is not poor software design, but poor HW design. Whenever software is being used to mitigate poor HW design, it cannot be "simple and straightforward". Just like the Spectre/Meltdown mitigation, the solution is complex, convoluted and can only ever be partial.

---

### Post by VanillaMozilla on 2019-06-26
> **DuckHook said:**
> You can mitigate potential BadUSB attacks by defining udev rules that shut down new HID devices as per [this strategy]("https://security.stackexchange.com/questions/64524/how-to-prevent-badusb-attacks-on-linux-desktop#64552"). But it's just an awkward kludge, and until USB is redesigned to be more secure by default, there really isn't much that any of us can do.

Thanks very much for the reply.  I really appreciate it.  It's a shame that this has been known for years, and almost nothing has been done about it.

The link advocates the following:
[INDENT]"...create a file /etc/udev/rules.d/10-usbblock.rules with the content:

#ACTION=="add", ATTR{bInterfaceClass}=="03" RUN+="/bin/sh -c 'echo 0 >/sys$DEVPATH/../authorized'"

If you want to block other classes too, then look up the class number, and copy the line, and change the class.
Now you can block all new HID devices using the command

sed -i 's/#//' /etc/udev/rules.d/10-usbblock.rules; udevadm control --reload-rules

and unblock with:

sed -i 's/^/#/' /etc/udev/rules.d/10-usbblock.rules; udevadm control --reload-rules

Before you shut down, always unblock, as the setting is persistent, and your "good" HID devices would be rejected on reboot.".[/INDENT]

Are you saying that if I do exactly that, it will protect against a BadUSB attack?  More importantly, is the unblocking command guaranteed to work correctly?  I don't understand the syntax, and I have almost no way of debugging it.  It looks like an easy way to at least temporarily brick my computer if anything goes wrong.

I will be very much in need of temporary protection in the near future.  Kludge or not, I think we all need it.

---

### Post by DuckHook on 2019-06-26
> **VanillaMozilla said:**
> …Are you saying that if I do exactly that, it will protect against a BadUSB attack?
Like all results from Internet searches, you will have to do your own research and draw your own conclusions. I pointed you to a site that is generally reliable and has been up-voted a fair number of times. I have not implemented this and have no intention of doing so, since I judge the BadUSB attack to be a minimal concern.
> …More importantly, is the unblocking command guaranteed to work correctly?
No idea. See previous comment.
> …I don't understand the syntax, and I have almost no way of debugging it.
Teaching you about *sed* and *udev* is far beyond the scope of this thread. I have already stated that no easy solution exists yet because the problem is in HW and not SW.
> …It looks like an easy way to at least temporarily brick my computer if anything goes wrong.
This is probably an accurate assessment. Make a backup of the file before editing it. Have a LiveUSB handy to boot up into and reverse the change if necessary.
> …Kludge or not, I think we all need it.
I respectfully disagree. I think very few need it. BadUSB is a difficult exploit to pull off because it is a physical attack that must be custom tailored to each USB device and even then, only if the device is sufficiently sophisticated to house a rather complex firmware replacement. In other words, you have to be a high-value target (possessing govt or industry secrets) for a bad actor to be interested in you.

I'm far more concerned about highly general and easy to implement threats like phishing attacks, cross-site scripting, ransomware, social engineering attacks, identity theft, remote hijacking, spoofing attacks, etc, all of which most people are clueless about. BadUSB is a distant secondary threat compared to these.

As you yourself have noted, the hazards for this fix are high, which—in my opinion—makes it a bad trade for a vulnerability that has been blown out of proportion to its real world threat.

---

### Post by VanillaMozilla on 2019-06-27
Thank you for your candid opinions.  That sounds like a good suggestion, and I'll consider it.

I know that some people share your opinion that a BadUSB attack is difficult to pull off, but I'm not so sure.  Spread of infection across devices and across platforms has been demonstrated (also to Linux), and by 2010 Stuxnet had successfully infected 60% of computers in Iran and 1.6% of U.S. computers, despite being throttled ([https://en.wikipedia.org/wiki/Stuxnet#cite_note-wired-51](https://en.wikipedia.org/wiki/Stuxnet#cite_note-wired-51)).  Using even that low figure, if I mount a random sampling of 10 untrusted flash drives, I have about a 1 in 6 chance of infection, which could affect my entire network.  Weaponized components are available, and the attacks typically install rootkits, and are therefore supposed to be almost impossible to detect.  That's not something I want to take lightly.

Unfortunately, the usual advice about BadUSB is that (1) an attack is unlikely, and (2) don't plug an untrusted USB drive into your computer.  That's rather self-contradictory, and also impractical.

I did find a hardware solution ([https://github.com/robertfisk/USG/wiki](https://github.com/robertfisk/USG/wiki)) from someone named Robert Fisk.  Do you know anything about it?

---

### Post by uRock on 2019-06-27
I think the thought of someone handing me a USB drive to share files to be impractical. 99% of the time people upload files to Google Drive, then share the folder with me or attach the files to an email,  The other 1% is someone handing me a MicroSD card they've pulled out of their camera or smart phone. In those cases, I use my laptop, because it gets OSes reinstalled almost monthly.

The USG device is USB 1.0, which means one would likely go with the Armadillo device for USB 2. That device costs $250. I'd rather tell someone to upload to Google Drive than spend so much money on a device that I might only use once or twice.

---

### Post by TheFu on 2019-06-27
Don't plug in USB devices you don't know everything about in advance. This applies to SDHC devices too.  For me, this is very easy.  My computers aren't usually in any public space and I don't use USB ports very often that aren't devices purchased by me, randomly.  

If you are a student, I can see where this just isn't possible. In 2013 I was hosting an InstallFest at a local University. At the time we were using a USB drive to pass around the Ubuntu .iso file.  There were about 20 people in the room passing around my USB flash drive.  By the time it was returned to me, there were at least 3 Windows viruses on it. Such is life in a campus environment.

Short of using a glue gun to physically block all USB ports or buying computers with locked cases blocking access to any external ports, there isn't much that can be done.  I've worked at businesses which did both glue and cases with port locks.  They even disconnected the optical drives on all their workstations before deploying them. This was when optical drives were $400+ each on $15K-$30K workstations.

Firewire and DisplayPort are even more dangerous, since they provide direct bus access to the computer. Everyone knows this, but nothing is done and DisplayPort is being updated to handle even more data.

---

### Post by DuckHook on 2019-06-27
> **VanillaMozilla said:**
> …I did find a hardware solution ([https://github.com/robertfisk/USG/wiki](https://github.com/robertfisk/USG/wiki)) from someone named Robert Fisk.  Do you know anything about it?
I know nothing about this but it looks intriguing. Of course, it raises the natural question: "How can you trust them or the NZ OEM contracted to put this gadget together?" but trust has to start somewhere, else we may as well stop using computers.

If you decide to spring for it, do let us know how it works out. Is it transparent to any device hooked up to it, or does it cause timing/access/format/execution problems? If it works seamlessly, it may be a good item to start including as part of standard security advice.

---

### Post by DuckHook on 2019-06-28
> **uRock said:**
> …The USG device is USB 1.0, which means one would likely go with the Armadillo device for USB 2. That device costs $250. I'd rather tell someone to upload to Google Drive than spend so much money on a device that I might only use once or twice.
&#8593;+1&#8593;

Both *Naked Security* and *The Register* ran a story some months ago about a bad guy who successfully penetrated a high value organization by leaving USB sticks lying on the ground and on benches just outside the premises. Human nature being what it is, sure enough, a staff member picked up the USB stick and infected the entire organization's network with malware. BadUSB played no part in this exploit. Just a garden variety scripting attack hidden in a zip/pdf file, counting on the fact that, given an entire organization's head count, it is practically a certainty that someone will not be able to resist his/her inner voyeur, will pick up that USB stick and, contrary to all security sanity, will nose around inside files that don't belong to them.

This was not even spearphishing. It was just a garden variety phishing attack that exploited a clever insight into human nature.

These things happen with depressing regularity. This week's municipal casualty is Key Biscayne, the third Florida municipality to be locked out of its entire network this month.

Let me repeat: in the state of Florida alone, in just the month of June, just among municipalities, this is the *third* victim.

Why does a bad guy need something as sophisticated as BadUSB when the pickings are this rich without it???

I think that vulnerabilities need to be weighed within a reasonable context. Like you, I want the whole USB subsystem to be fixed. I want it hardened by default so that workarounds like USG are not needed. But until then, I am relegating BadUSB to secondary concern while I address more primary—and therefore more pressing—concerns.

---

### Post by VanillaMozilla on 2019-07-02
I've found some more information.  I'm astonished that there isn't more discussion of this.  It was news in 2014; after that, discussion of it is rare, despite the fact that it infected 60% of Iranian computers by 2010.

Kaspersky claims to have a defense, but it appears from their patent that it doesn't protect against a device with an unknown history.  You have to start with a trusted device, and then it detects changes.

USBGuard appears to be exactly what's needed.  It works by restricting the functions of a USB device.  You can define a rule so that if it's supposed to be storage, then it's *only* storage.  Unfortunately, the Ubuntu repository source is incomplete:  [https://launchpad.net/ubuntu/+source/usbguard](https://launchpad.net/ubuntu/+source/usbguard) .

The man pages are here:  [http://manpages.ubuntu.com/manpages/disco/en/man1/usbguard.1.html](http://manpages.ubuntu.com/manpages/disco/en/man1/usbguard.1.html) .
The documentation here is a bit more helpful:
[https://usbguard.github.io/documentation/compilation.html](https://usbguard.github.io/documentation/compilation.html)
and there are some very good rule examples here:
[https://usbguard.github.io/documentation/rule-language.html](https://usbguard.github.io/documentation/rule-language.html) .

---

### Post by VanillaMozilla on 2019-11-23
It's time for a follow-up.  I have had mixed results with USBGuard.  The 32-bit PPA I am using works on one computer, but the 64-bit version does not.  There may be a workaround, which I have not tested.  This leaves three choices (suggestions welcome):
1. Troubleshoot
2. One of the GoodUSB devices
3. Denial

Here's the short version.
	I can't recommend USBGuard at this time, because of bugs.  My own PPA 64-bit installation on Xenial ( [https://launchpad.net/~pmjdebruijn/+archive/ubuntu/usbguard](https://launchpad.net/~pmjdebruijn/+archive/ubuntu/usbguard) ) is apparently safe to install and use, but works for a while and then fails to allow additional drives.  The UI lists commands but is otherwise unresponsive to commands.  Furthermore, it makes the computer hang on shutdown, and the hard drive restores data from journal after a hard shutdown.  Possibly due to Redhat Bug 1751861 ( [https://bugzilla.redhat.com/show_bug.cgi?id=1751861](https://bugzilla.redhat.com/show_bug.cgi?id=1751861) ).  A possible workaround:  adding '/usr/sbin/usbguard-daemon -K -s &' (without quotes) to /etc/rc.d/rc.local on the line above the lines enabling wakeup on usb ( [http://www.murga-linux.com/puppy/viewtopic.php?t=110820&sid=62271dca207d90dff77ad7d02f2a372a](http://www.murga-linux.com/puppy/viewtopic.php?t=110820&sid=62271dca207d90dff77ad7d02f2a372a) ).
	
	Previously I found the same PPA to work normally for one or two boot cycles, but then fail to start at boot time because of an unspecified parse error in rules.conf.  The 32-bit version appears to run correctly on another computer.
	
	Other versions are affected by a nasty bug ( [https://github.com/USBGuard/usbguard/issues/261](https://github.com/USBGuard/usbguard/issues/261) ) which blocks the keyboard and mouse.  PPA versions for Disco and later appear to have a patch applied, but Bionic apparently does not ( [https://launchpad.net/ubuntu/+source/usbguard](https://launchpad.net/ubuntu/+source/usbguard) ).  I don't think I can recommend those versions at this time, because they appear to require a poorly documented, or undocumented special procedure for initialization, in order to whitelist the keyboard and mouse.  The DeBruijn PPA version for Xenial explicitly does this automatically on installation.


Other bugs:
[https://forums.fedoraforum.org/showthread.php?315828-USBGuard-not-working-on-kernel-4-13-5-100](https://forums.fedoraforum.org/showthread.php?315828-USBGuard-not-working-on-kernel-4-13-5-100)
[https://forum.mxlinux.org/viewtopic.php?t=42443](https://forum.mxlinux.org/viewtopic.php?t=42443)
[https://github.com/USBGuard/usbguard/issues/246](https://github.com/USBGuard/usbguard/issues/246)

---

### Post by c0n7r4 on 2019-12-14
I wrote this a while back, it's cross-platform, very simple program. it needs sudo apt-get install libusb-1.0-dev to compile or you can grab the source code and compile the libusb yourself. 
you will need to add all your whitelisted vid: pid pairs to the "const char *mlist[] = {" part to customize it to you needs. compile like this:

$ gcc -Wno-comment -Wall -o killswitch killswitch.c -lusb-1.0

cheers


[https://github.com/slacker69/killswitch](https://github.com/slacker69/killswitch)

---

### Post by VanillaMozilla on 2020-01-03
> **c0n7r4 said:**
> I wrote this a while back, it's cross-platform, very simple program. it needs sudo apt-get install libusb-1.0-dev to compile or you can grab the source code and compile the libusb yourself. 
you will need to add all your whitelisted vid: pid pairs to the "const char *mlist[] = {" part to customize it to you needs. compile like this:

$ gcc -Wno-comment -Wall -o killswitch killswitch.c -lusb-1.0

cheers


[https://github.com/slacker69/killswitch](https://github.com/slacker69/killswitch)



That's nice but it appears to solve a completely different problem.

---

