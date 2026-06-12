---
title: "Encrypting Ubuntu - Protecting Assets"
date: 2020-09-17
forum: Security
---

### Post by Nightwalker07 on 2020-09-17
Hello all,

I'm familiar with full disk encryption whether that be through TrueCrypt, VeraCrypt or Bitlocker, file containers or full disk encryption. I'm less well versed in how Linux handles encryption but I want to learn.

I have a scenario I would like to pitch to you to see if it is possible to overcome to the problem whilst maintaining good security and relative ease of use:

Let's say I have a remote workshop that I want to install a PC into, I fear the PC could be at risk at being stolen at some point but I care more about the digital data than I do the hardware. So I would like to be able to protect the Browser and its associated logins, WiFi credentials, SSH keys and other data that may be on the computer.

Full disk encryption jumps to mind, **however** I'm also in a position where I might need to remotely control the system via VNC and perform reboots. So it would be nice to not have the system sat at a password prompt just after POST and inaccessible remotely.

Is there a way in which I can encrypt a home partion (will that be enough?) but I'm still taken to the usual Ubuntu login screen which I can access remotely?

Or is there an approach to full disk encryption, that can allow for or accomidate a one-off reboot where a password isn't required? I'm not aware of such a thing but I wondered if perhaps you had the system in a decrypted state perhaps if there was a mechanism which could be flipped where it could save/stash something during a warm-reboot whereby it might circumvent or decrypt the partition upon request?

How do others implement security and encryption but still manage remote control after rebooting? Thank you for your time and help.

---

### Post by CharlesA on 2020-09-17
You would need some sort of out of band management such as IPMI or iDRAC or something else in order to enter the encryption key on boot.

There are some ways around that by proving the key via SSH, but I haven't tried that before.

See here: [https://hamy.io/post/0009/how-to-install-luks-encrypted-ubuntu-18.04.x-server-and-enable-remote-unlocking/#gsc.tab=0](https://hamy.io/post/0009/how-to-install-luks-encrypted-ubuntu-18.04.x-server-and-enable-remote-unlocking/#gsc.tab=0)

---

### Post by TheFu on 2020-09-17
Encrypted storage is only secure when it is 100%, completely, at rest.  When mounted, it is just like any other storage, unlocked, and open to anyone else.  This "unlocked" applies for hibernation and standby modes too.  For this reason, if you use any encryption, don't use those other modes whenever changing buildings.  This applies to portable devices.

For non-portable devices, it isn't nearly so easy.  LUKS is the standard for Linux encryption and it works below the volume manager or file system.  If you don't encrypt everything, then you've lost the war since swap can easily have keys to open and access the encrypted storage once it has been opened.

> Or is there an approach to full disk encryption, that can allow for or accomidate (sic) a one-off reboot where a password isn't required? No. that would defeat the purpose of using encryption. You'd need a remote console into the system, as CharlesA states.  These almost always have terrible security and never should be placed onto the internet, but you could setup another system with keys on the network. Inside enterprises, they use the network key methods and have multiple network key stores.  I've not set this up and don't know how it may integrate with LUKS, but I do know that a challenge/response method does with with LUKS storage.  I use a yubikey 5c in challenge/response mode for one of the LUKS slots.  There are 8 slots available.  The others use a passphrase+long static code from a HID device and the last one uses a 75+ character passphrase that I doubt I could type in correctly. It is there as a backup to the backup.  I've considered setting up a key file on a USB storage device.

If this is for a business, you need an IPMI remote console anyway, so only deploy systems which support that.  I suppose a raspberry-pi could be used as a console with minicom.  I have a USB-2-serial port connector for those sorts of requirements. Ubuntu doesn't come pre-built for console booting. Enabling it shouldn't be THAT hard. I'd expect some grub options.

With a stable server, you really shouldn't have any need for unplanned reboots. If you can physically visit the system a few times a month, that would be sufficient and cheaper than a DRAC/RIBLO/IPMI setup, but sometimes it is just better to pay to have a known-good solution.

VNC won't be any issue. It is only the boot that will be a problem.  You can read more in the **cryptsetup** manpage.

---

### Post by scorp123 on 2020-09-18
> **Nightwalker07 said:**
>  Let's say I have a remote workshop that I want to install a PC into, I fear the PC could be at risk at being stolen at some point but I care more about the digital data than I do the hardware. So I would like to be able to protect the Browser and its associated logins, WiFi credentials, SSH keys and other data that may be on the computer. 

I had that scenario once when I was working as IT Consultant. I needed to have a little server installed at a school but they were unable to put the system into a secure room. The best they could do was a "PC Pool" room where still 100's of their students had access to. So this little server getting stolen was a real possibility. 

What I did:

[LIST]
[*]Installed Oracle VirtualBox
[*]installed their "Virtualbox Extensions Pack"
[*]installed Teamviewer so I could remotely access this system
[*]installed a VM with encrypted disks (Virtualbox can do that)
[*]installed the things I wanted to run inside that encrypted VM
[/LIST]

So... the phyiscal hardware only served the purpose of running Teamviewer and letting me remotely access the installation. The actual service was delivered by the VM that was installed onto encrypted disks inside Virtualbox. 

If someone were to steal the physical server and tried to run the VM they'd get stopped at the Virtualbox password prompt and can't get past it. Whatever is stored inside the VM remains encrypted in that case.

Downside was that whenever they had e.g. a power failure and the physical server was rebooted I needed to remotely login and type in the VM password or the VM wouldn't start, but I found that acceptable.

Upside was that by having everything in a VM gave me the possibility of e.g. snapshotting its state and rolling back when needed; or switching out this VM with a newer version that had patches and newer software releases already installed.

After a few weeks when the project ended and I went back there to pick up my hardware this little server was still there, but sure enough the screen, the keyboard and the mouse were gone XD.

---

### Post by TheFu on 2020-09-18
I use VMs for almost everything. My main desktop runs inside a VM, for example. 

The VM method is intriguing, but it has problems and some mitigations.  Please consider the issues before going in this direction. If the hostOS is not encrypted, the beachhead will be lost.  Complete access to any running process is available.

With physical access to an unencrypted Unix machine, complete pwn'ership is a reboot, if that, away. There are multiple methods to gain root from the console. The only real protection against this is using whole disk encryption, if physical access cannot be locked down. That's why data centers have different rooms, different cages, and different locked racks. It is about restriction of access as much as possible.

Dumping RAM to disk isn't hard. Use dd. If you've never dumped the RAM for any programs, I'd encourage it. Then use the 'strings' command on that dumped file.  Dumping the RAM for a running VM works from the hostOS. After all, a VM is just a larger running process.

If someone is on-site who can plug in a flash drive, then using that method for the key-based hostOS may be an option. This assumes that person can be trusted to secure the flash device.  I do something like this with my family's trust/will documents on flash media, just split into physical access knowledge and decryption knowledge between a few trusted family members.

Be a skeptic about any proposed answers. Consider all the ways someone else could gain access through physical, social, or evil methods.

---

### Post by EuclideanCoffee on 2020-09-18
I want to warn people considering Virtualbox VM extensions for professional solutions without a license from Oracle. This is actually illegal, and you can be sued. A lot of IT folks now are critical of Oracle and typically avoid Virtualbox for this reason. Many use other software like VMware and Xen instead. Another thing you could do with a computer out in the open is still encrypt it. Why? If you are worried about someone stealing the computer, the computer will still encrypt once it's shut off. Unless someone is very, very clever, they are likely not able to get out of the building with the server still powered and escape. Same principle, no illegal usage that could get your client sued. :)

---

### Post by TheFu on 2020-09-18
> **EuclideanCoffee said:**
> I want to warn people considering Virtualbox VM extensions for professional solutions without a license from Oracle. This is actually illegal, and you can be sued. A lot of IT folks now are critical of Oracle and typically avoid Virtualbox for this reason. Many use other software like VMware and Xen instead. Another thing you could do with a computer out in the open is still encrypt it. Why? If you are worried about someone stealing the computer, the computer will still encrypt once it's shut off. Unless someone is very, very clever, they are likely not able to get out of the building with the server still powered and escape. Same principle, no illegal usage that could get your client sued. :)

Most places use KVM. That's what Amazon and all the big cloudy companies use that aren't MSFT or VMware. 

Oracle has been known to track down businesses and bill them for violation of the license.  A guy in my LUG says his employer is removing all virtualbox capabilities from all their systems. You can find stories online.  It is just easier to use KVM and avoid anything connected to Oracle be that vbox, any SQL-DBMS, or anything else.  I've seen huge bills from Oracle in prior jobs. That wasn't just purchasing and annual "maintenance". It was for hundreds of "consultants" pushing more and more complex, expensive, products from Oracle corporate.

Law enforcement has portable power to keep computers running as they take equipment back to their labs for study.  Read a study about the FBI's child porn search and how they didn't let any of the systems believed to hold that content lose power. But law enforcement shouldn't worry us, right? [https://www.eff.org/press/releases/fbi-search-warrant-fueled-massive-government-hacking-was-unconstitutional-eff-tells](https://www.eff.org/press/releases/fbi-search-warrant-fueled-massive-government-hacking-was-unconstitutional-eff-tells)

---

### Post by EuclideanCoffee on 2020-09-18
TheFu, this is perhaps the most on-fire, controversial post on security support yet. lol. Not touching this today.

---

### Post by TheFu on 2020-09-18
> **EuclideanCoffee said:**
> TheFu, this is perhaps the most on-fire, controversial post on security support yet. lol. Not touching this today.

Just following your lead, my friend.
Someday, I'd love the freedom to say what I really think. ;)   Actually, that happens almost every Sunday.

---

### Post by scorp123 on 2020-09-18
> **EuclideanCoffee said:**
> I want to warn people considering Virtualbox VM extensions for professional solutions without a license from Oracle. This is actually illegal, and you can be sued. 

I was working for an Oracle partner at the time, so my ass was fully covered. I had unlimited licenses for everything ;)

You are absolutely right: Don't ever use unlicensed stuff. That can get pretty costly. 

If anything I hope my posting above gave OP an idea how they can replicate my setup from back then with an alternative solution (e.g. KVM and LUKS inside the VM?), it wasn't meant as endorsement of one corporation's products.  I don't work for them or their partner companies anymore, they don't pay for my salary anymore, and I didn't mean it like that at all.

If I had to do something like this today I'd probably go with e.g. ProxMox and LUKS inside the VMs.

---

### Post by Nightwalker07 on 2020-09-21
I appreciate everyones time, input and ideas on solutions.

I should probably clarify; this PC is litterally just in a shed / workshop of mine, its not a high value system but rather a Intel NUC which is a few years old (but much loved as it has served me well).

I understand that a lot of different encryption mechanisms can only be relied upon for their full protection when at rest / off, but in this scenario I am anticipating physical theft by a unsophisticated thief and assume it will be off when stolen. Considering the workshop is alarmed I'm not anticipating a burglar to be tampering, rebooting or working with the system whilst online, it's going to be a snatch and grab afair if anything happens.

It wont be storing any critical or highly sensitive information which may be attrative to sophistcated attackers, but rather I just wanted to limit damage from logged in browser sessions, keys or other credentials from being stolen if it were physically stolen from me.

I hadn't thought about running the system within a VM on it, which is crazy really considering as part of my work we run hundreds of servers many of which utilise different forms of virtualisation + and at home for personal use I use VirtualBox.

Whilst I do love virtual machines I have found the visual / graphical capabilities a little limiting at times and buggy, for a power use that uses a wide variety of applications. This system in the workshop will be using CNC/Laser software and working with graphics a lot. Still I could give virtualisation a go, it may be a good combo in this scenario.

I also love Raspberry Pi's so I thought the idea of using one of those as a out of band input device was cool. I also have access to a few Yubikeys and other 2FA possibilities so I really do appreciate all the ideas.

I'll have to see if my NUC has any inbuilt Intel out of band capabilities as well.

---

### Post by TheFu on 2020-09-21
Thanks for posting the location. That information would have been very useful a few days ago.  Seems the real issue is just having to walk 200 ft on a cold night.  If that is true, I'd just use normal LUKs whole-drive encryption with a challenge/response yukikey to access it and a 50+ random character passphrase as a backup. I don't have the details handy, but this:
[https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks](https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks) seems reasonable for a how-to.
There are 8 slots for authentication in LUKS. Pick which ever slots you like, just be certain they are different.

Current KVM+libvirt+spice protocols are amazing.  

Ran into a guy who used AutoCAD inside a Windows VM over Spice.  My recent testing of SPICE connections, local and remote, show it to be freakin' amazing compared to what we had 2+ yrs ago.  I think the KVM + Spice improvements were all backported to 16.04.

---

