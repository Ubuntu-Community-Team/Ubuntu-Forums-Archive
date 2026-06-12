---
title: "MacOSX (as guest) on Mac hardware with Ubuntu host"
date: 2009-02-14
forum: Virtualisation
---

### Post by MarkHarrison on 2009-02-14
This may seem an odd request, but I want to know if anyone has got OSX running as a guest OS _ON MAC HARDWARE_ with Ubuntu as the host?

For various reasons too long and complex to go into, I want to be able to run Ubuntu and MacOS at the same time on my Mac hardware.

I've a fair bit of experience with VirtualBox as the Virtualisation manager on MacOS, and frankly it's a bit flakey. Yes, the GUI is nice, but I'm old enough to remember the days when command lines were the only option, and therefore not scared of them.

I've a reasonable bit of experience installing qemu/kvm on generic hardware, and have Ubuntu running as both hosts and guests a fair bit :-)

Hence I was wondering whether I could install Ubuntu as the HOST OS on my Mac, and put OSX as the guest on top of it. As far as I can make out, this is permitted by the Apple software licence, since I have a single licence to run OSX on Apple Branded hardware, and the EULA says nothing about not running a hypervisor underneath it.

So, anyone got this to work? Or am I better off persevering with OSX as the host???

---

### Post by Dies on 2009-02-14
You should be able to use the boot-132 method to install OS X on VMWare. I say VMWare because I know OS X can be run on it. I have no experience with Virtual Box or qemu/kvm and whether OS X will even be able boot on those, though the availability of the Voodoo kernel and the upcoming Chameleon bootloader should make it a whole lot easier. 

Google OSX86 or see this thread

[http://www.infinitemac.com/f19/howto-efi-partition-booting-zero-modification-installs-on-t1609/](http://www.infinitemac.com/f19/howto-efi-partition-booting-zero-modification-installs-on-t1609/)

Then try to get it running and running well before you go formatting your drive to install Ubuntu. ;-)

Quite frankly though with VMWare Fusion and Parallels available I just don't see the sense in it ? Then there's also the fact that all this could have been accomplished on cheaper, generic hardware...  :-p

But hey, I would never try to discourage someone from doing something like this, even if it's for no other reason than to see if they could.

---

### Post by freakalad on 2009-05-06
I have a similar need.

I've done a fresh install of OS X & Jaunty on my MBP SR 3.1, with KVM (ala libvirt) as my VM solution. KVM is pretty stable, and I can still boot into my OS X, and the HFS+ partition is accessible from Ubuntu.

Under the new virt-manager I've managed to lod the OS X part as a block device & assign it to a VM.

So far so good.

Unfortunately I am unable to boot it though (boot flag is set, btw).
Mac does not make use of BIOS any more, but EFI. I don't know what effect/requirement this would have on the client's config.

My understanding (and correct me if I'm wrong) is that with "paravirtualization" the virt runs at a lower level (kernel or sub-kernel), providing better performance, but requires a modified kernel.
With "full virtualization", virt is a tweak to the kernel (KVM is provided as a kernel module), and although there is a bit of a performance/latency sacrifice, stability & compatibility is better, because you can run unmodified clients.
Hence simply hooking into my existing OS X block device

---

### Post by NJLash on 2009-06-04
I have a similar need.
I came upon this site.
[http://d4wiki.goddamm.it/index.php?title=Howto:_Mac_OSX_on_KVM](http://d4wiki.goddamm.it/index.php?title=Howto:_Mac_OSX_on_KVM)
I'm pretty sure this would work.
However, unlike you two, I'm not very experienced with the command line.  I've pretty much resorted to copy/paste, but I'm learning a lot.  I have a MB 2,1 and I just switched over last week...
I went through the instructions with the patch, qemu, etc.
This is one of the first times i built something. HAHA.
i got lost right at the end: How do you boot OS X from a partition?  My OSX installation is in the first partition.  I have no idea what the code is for that.  How do you run the getkey script I tried saving the getkey script as getkey.sh and running it, but it pulled up an error. And what is human-readable ASCII string of 64 chars in -osk parameter?
if anyone can figure this out and help me through it, that would be most excellent.

---

### Post by freakalad on 2009-06-04
Thanks for that post; looks pretty promising.

Unfortunately, I'm officially lost there.
That set of instructions is intended for SuSE, and makes reference to RPM (which is RedHat), and though I've sure I could slog through it, it does my head in at the moment.

There are 2 fundamental differences between your "typical" PC a.k.a. "IBM-clone" (haven't use THAT turn of phrase in a while) & the modern MacTel:
* BIOS has been deprecated in favor of EFI, a "boot-OS", not dissimilar to [SplashTop]("http://en.wikipedia.org/wiki/Splashtop") (termed different names under different vendors)
* FS is now based on [GUID Partition Table (GPT)]("http://en.wikipedia.org/wiki/GUID_Partition_Table"), as opposed to the regular MBR

These issues are not insurmountable, but since it's pretty new(ish) tech, it does make it tricky. (I REALLY do prefer apt-get to building. Maybe I'm just lazy)

Standard KVM is well-supported under the old-school methods, and the EFI/GPT support & integration is gaining traction (see GRUB-2)

Currently my system's pretty stable (Jaunty), more so than it's been in a very long time, so at the moment I'm a bit loathe to rock the boat too much. Sorry

2 guys that are pretty clued-up on those subjects are [bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054") (VM guru) & [cyberdork33]("http://ubuntuforums.org/member.php?u=34295") (the Mac-daddy)

If you manage to get something cooking, please let us know.

With regard your disk query; that pretty tricky. You're assuming that your OS/X if your very first partition, but if you've installed the rEFIt, as per instructions, odd are that your 1st partition may very-well be an EFI partition, and only then would your mac follow.
To check this, make sure you have the FS-compatibility drivers installed (hfsplus, ntfs-3g, etc), and then run:
`sudo fdisk -l` 
(but now that I come to think of it, I can't quite remember if fdisk is all that happy with GPT's. Try it anyway; may give you come insight regradless)

In KVM, you're able to load disk as "block devices". This means that you're able to create VM that make PHYSICAL use of a PHYSICAL partition, as opposed to using a monolithic image file(s). 
This means, in theory, that you can take an existing disk or partition, attach/map it to a configured VM, fire it up, & you should be good to go.
You may have to re-install a couple of drivers, but data-wise, it should be sweet.
Very few other VM platforms can do this out of the box.

For WYSIWYG/click&drag/GUI VM admin, you can make use of virt-manager (which uses the libvirt).
[KVM from CLI]("https://help.ubuntu.com/community/KVM/Directly") is not too bad, and sometimes necessary, once you get a bit more used to it. 

- J

---

### Post by NJLash on 2009-06-04
I feel like I could be very close, but who knows...
freakalad, dev/sda2 would be the OS X partition. 
I tried using the virt-manager, but I cannot boot OSX.  I think its because it needs the hardware key
I'm at the last step, and I'm having trouble figuring it out.  It seems like I could be almost done.  If I do figure this out, I'm definitely posting a more straight-forward how-to.

Here's the last bit
qemu-system-x86_64 -M mac -kernel ~/kvm-osx-bootloader/boot \
-usb -usbdevice mouse -usbdevice keyboard -hda /dev/sda2 \
-cdrom /dev/cdrom -m 512 -osk $HARDWARE_KEY -serial stdio

So, I need the hardware key "as a human-readable ASCII string of 64 chars in -osk parameter."
I think the key is

OSK0 [ch8*] (bytes 6f 75 72 68 61 72 64 77 6f 72 6b 62 79 74 68 65 73 65 77 6f 
72 64 73 67 75 61 72 64 65 64 70 6c)
OSK1 [ch8*] (bytes 65 61 73 65 64 6f 6e 74 73 74 65 61 6c 28 63 29 41 70 70 6c 
65 43 6f 6d 70 75 74 65 72 49 6e 63)

How do I get that into the right format?

---

### Post by NJLash on 2009-06-04
I'm getting so close, I just need the Hardware Key.
For now i'm giving up on the partition stuff,
I created a virtual disk (stupid_file)
And then I put in all of this
qemu-system-x86_64 -M mac -kernel ~/kvm-osx-bootloader/boot \
-usb -usbdevice mouse -usbdevice keyboard -hda stupid_file \
-cdrom /dev/cdrom -m 512 -osk $HARDWARE_KEY -serial stdio

It began to start up! However, I still need the hardware key!
We're almost here!

---

### Post by freakalad on 2009-06-04
Well, your progress is looking pretty promising so far.
Nice work!

What makes you think it's a key issue?
I was also able to get an initial boot going on my vm, but I assumed that it failed due to the fact that the KVM/Qemu provides a BIOS & not an EFI firmware emulation.

I've [located some Qemu EFI drivers]("http://www.nongnu.org/qemu/download.html"), but I've not had the inkling to build & load them. From what I can tell, it's an either-or BIOS/EFI situation, and presently I'm running various other OS clients, so it's not been a pressing priority for me, yet.

BTW. Thus far I've found very little relating the 3D hardware-acceleration from the VM's. There was a the [VMGL]("http://vmgl.sourceforge.net/") project, but that has since kinda run dead (last build was more about a year ago). Another project that looks promising is a 3D VNC; [VirtualGL]("http://www.virtualgl.org/")

Keep up the good work.

---

### Post by NJLash on 2009-06-04
I've been using the patched kvm from the above link, I followed all of the instructions.

OK, I found something else online and I'm sure I know the answer

I need to Concatenate OSK0 and OSK2 together (each one is 32 bytes of ASCII text).

How do I do this?

If someone can concatenate them, I will have found it, I think!

As a sidenote: [http://www.twuug.org/pipermail/twuug/2008-May/059692.html](http://www.twuug.org/pipermail/twuug/2008-May/059692.html)
That's why I need the key!:KS

---

### Post by Chronon on 2009-06-05
You could concatenate them by simply inserting the contents of the second file at the end of the first file.  Concatenation is just connecting the strings end-to-end.

---

### Post by lpsantil on 2009-06-30
Was this ever resolved?

---

### Post by freakalad on 2009-06-30
> **lpsantil said:**
> Was this ever resolved?

Not that I know of.

I run Jaunty-64 9.04 quite happily on my MBP SR 3,1, in a rEFIt dual-boot config. Ubuntu being my primary (& for all ends & purposes, only) OS.

Since this hardware is VT-capable, I'm running KVM (& occasionally switch to VirtualBox), & I've tried to hook the Mac HFS partition as a block device into KVM as a client. I still suspect it's a EFI vs BIOS issue (though I've little to back this suspicion up at this time)

Unfortunately, I have bigger fish to fry @ the moment, so I'll have to revisit this again at a later stage.

I'd suggest approaching bodhi.zazen & cyberdork33 , as those are to guys I've found to be VERY clued-up on these subjects

---

### Post by freakalad on 2009-06-30
don't know if this got a mention before:
[Howto: Mac OSX on KVM]("http://d4wiki.goddamm.it/index.php?title=Howto:_Mac_OSX_on_KVM")

RPM-based, but the basics should be the same

---

### Post by marioruiz on 2009-07-03
So I had an interesting time finding key.  First I used the keys from earlier in the post.  Those keys are UTF-8 encoded and we need normal ASCII characters.

So what I did is found an online converter tool at [http://rishida.net/scripts/uniview/conversion.php](http://rishida.net/scripts/uniview/conversion.php) and I input the OSK values in the UTF-8 section (just what was inside the parentheses and not including the body).

It then decodes into a very humorous little line from apple.  If the result is not funny and readable, then you are doing it wrong.

So now my machine starts up without the appleSMC errors, but I now get the following error:
```
System config file '/Library/Preferences/SystemConfiguration/com.apple.Boot.plist' not found
```What next?

---

### Post by lpsantil on 2009-07-18
I'm stuck here too.  Using a 10.5.4 disc.

> **marioruiz said:**
> So I had an interesting time finding key.  First I used the keys from earlier in the post.  Those keys are UTF-8 encoded and we need normal ASCII characters.

So what I did is found an online converter tool at [http://rishida.net/scripts/uniview/conversion.php](http://rishida.net/scripts/uniview/conversion.php) and I input the OSK values in the UTF-8 section (just what was inside the parentheses and not including the body).

It then decodes into a very humorous little line from apple.  If the result is not funny and readable, then you are doing it wrong.

So now my machine starts up without the appleSMC errors, but I now get the following error:
```
System config file '/Library/Preferences/SystemConfiguration/com.apple.Boot.plist' not found
```What next?

---

### Post by lpsantil on 2009-07-18
To get around the plist issue, hit F12 as qemu boots, choose 3 (cdrom), and quickly hit a key (you have 2 seconds to do that), then type e0 and hit enter (select e0 partition).  This gets you around the multiboot issue of the OSX DVDs.  However, at this point, I get the apple logo followed by a kernel panic.   I'm not sure what is causing that.

---

### Post by quorr on 2009-07-20
I got the same problem. Here is a log of what happened:
[http://pastebin.com/f16c770bf](http://pastebin.com/f16c770bf)

Is this a CPU problem? The log shows that OSX does not correctly recognize the cpu. I have a Intel P8600 ...

---

### Post by jaqrah on 2009-07-20
Here is an interesting thread from the VirtualBox.Org forum:

[http://forums.virtualbox.org/viewtopic.php?f=4&t=2076&sid=894a2c0beefe6e4ee9c4146b2663108a](http://forums.virtualbox.org/viewtopic.php?f=4&t=2076&sid=894a2c0beefe6e4ee9c4146b2663108a)

I have been reading endlessly about this topic the last two days.  The thread meanders in many directions but it is definitely worth reading. The thread itself has many links that are worth tracking down as well.

Hope it helps in some small informational way.

---

### Post by freakalad on 2009-07-22
SWEET! Thanks for the info

I think that'll clear the major hurdle: [The emulated EFI boot-loader for Qemu]("http://alex.csgraf.de/self/?qemu/").

Since I'll be running a legal copy of OS/X (from the original block device/partition, btw), I'm not too concerned by the legalities of the matter.
I really liked this last bit: "makes everything run fast" :D

Now, if only we could get the 3D Hardware acceleration on the KVM client going...or maybe remote-abstracting single apps, like [SeamlessRDP]("http://www.cendio.com/seamlessrdp/"),or even [NX]("https://help.ubuntu.com/community/FreeNX")

---

### Post by freakalad on 2009-07-22
KVM-OS/X wiki guide [here]("http://d4wiki.goddamm.it/index.php?title=Howto:_Mac_OSX_on_KVM")

Could be simpler to get hold of a x86-hacked OS/X, but I've heard rumors that there are a couple of nasties (trojans, bot-backdoors) on those, so I'd be loathe to try that out, personally

---

