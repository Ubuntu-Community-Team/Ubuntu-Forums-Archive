---
title: "Problem Dual-Booting Windows 10 and Ubuntu 16.04"
date: 2016-12-16
forum: Windows
---

### Post by Ukemi on 2016-12-16
I'm attempting to install Ubuntu 16.04 alongside Windows 10; when I set Ubuntu as first in my BIOS boot order, I'm greeted by a blank screen with a single blinking cursor ( _ ). If I set Windows to boot first I can successfully boot into Windows with no problems.

I tried boot-repair (running from the same Ubuntu live USB that I used for installation) using the recommended repairs, but saw no change. I have re-run boot-repair and generated a report here:

[http://paste2.org/5f8MfshW](http://paste2.org/5f8MfshW)

Note that the "Suggested repair" contains the same message that it did the first time I ran this tool, which exited successfully but had no observed impact.

I'm not sure how to proceed here... any advice would be greatly appreciated.

---

### Post by oldfred on 2016-12-17
Usually somewhere in script is what video you are using. I did not see it?
What brand/model system and what video card/chip?

It looks like you installed grub to MBR for BIOS boot. That will not be used, but never boot in BIOS/CSM/Legacy mode as it will start to use that grub and just give grub error.

You also left Windows fast start up on which is always on hibernation. You need to turn that off in Windows to dual boot. But that is for later to let you use grub to boot Windows.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by Ukemi on 2016-12-17
The motherboard is Gigabyte Z170N-Gaming 5
[http://www.gigabyte.com/products/product-page.aspx?pid=5529#ov](http://www.gigabyte.com/products/product-page.aspx?pid=5529#ov)

Video card is an Nvidia GTX 1080

---

### Post by oldfred on 2016-12-17
I have a Gigabyte Z170 and it has worked well. But I have no video card, just use the Intel video.

You probably need nomodeset to get low quality video.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

And you will need the very newest nVidia driver after you have installed. Do not download from nVidia, but use the ppa.
       
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 

One user with video issues, use the Intel video to install and first boot. Then he manually installed the nVidia driver and rebooted & switched to nVidia connection.

       Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
Go to the BIOS, Peripherals > "Initial Display Output": set it to IGFX (basically, this tells your computer to use your motherboard to display graphics)
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648)

---

### Post by Ukemi on 2016-12-17
Thanks for taking the time to respond.
I did the following:
- switched to using internal graphics in BIOS
- moved HDMI cable from gfx card to motherboard HDMI port
- re-ran boot-repair tool with option to add "nomodeset"

I'm still greeted with a black screen with blinking cursor. I never get to the grub menu at all.

Second boot-repair output is here:
[http://paste2.org/FmW72Fwp](http://paste2.org/FmW72Fwp)

I should note that I was able to install ubuntu once (by itself) on this machine with no problems. I followed a procedure similar to the one you've suggested - installed using internal graphics, then added drivers for the Nvidia card. Never had any problems with grub.

I decided that I wanted a copy of windows as well, so I wiped the hard drive and installed windows 10 first, then tried installing ubuntu using the "install alongside windows" option. That's basically how I got to this point. 

Perhaps I should wipe the ubuntu side and start again, using internal gfx the whole time? Or could this be a grub/EFI/BIOS issue unrelated to the graphics card?

I'm fairly Linux-savvy in some ways but don't know much about the boot process. Are there good resources for learning about this stuff? I.E. legacy BIOS vs EFI/UEFI, the MBR, grub, how Linux and Windows differ in how they manage the boot process, and what people have done to get them to work well together.

---

### Post by oldfred on 2016-12-17
The link in my signature has lots of links to more info on UEFI.
With UEFI there are now three ways to boot.
UEFI with secure boot.
Standard UEFI
CSM or legacy/BIOS

Both Windows & Ubuntu use same ESP - efi system partition. And how you boot install media is then how it installs.

You are showing Windows is hibernated which causes issues. But no screen is still usually graphics related.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by Ukemi on 2016-12-18
I forgot to mention, but I did also disable fast boot before my last post (in addition to switching from the Nvidia card to the motherboard's integrated gpu). 

Notice that there were ~6 messages with "The NTFS partition is in an unsafe state." in the "Additional Information" section of the first boot-repair message I posted. In the second one, from after I disabled fast boot, one of them remains.

I tried disabling hibernate as well, which is distinct from fast boot.
[https://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](https://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

That alone didn't get rid of that message. I followed boot-repair's instructions and ran:
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4

Then I re-ran boot-repair again (info-only mode) and verified that I get none of those messages.

I went ahead and ran the recommended repairs again and got the same "boot was fixed" message, but I still see the same black screen with blinking underscore when I boot.

Latest output here:
[http://paste2.org/2kXmKKp2](http://paste2.org/2kXmKKp2)

So I *think* I've implemented both suggestions fully (switched to integrated graphics, disabled fast boot) but the problem remains. Anything else it could be? And/or, is there something else I should check (aside from the boot-repair tool's output) to verify that I have indeed ruled these things out?

---

### Post by oldfred on 2016-12-18
I am not seeing much else.
Is nVidia driver installed? Not sure if that then would interfere with Intel video?
My system just has Intel, so never installed nVidia driver.

Do not remember what UEFI settings I may have changed, with my other Asus motherboard I changed a lot of settings and may have just done some of the same. 
I did update to newest UEFI from Gigabyte. But every reinstall of a new UEFI, requires resetting most of the changes you make to UEFI settings.

---

### Post by Ukemi on 2016-12-27
Since there wasn't any clear course of action, and this was basically a fresh install, I just wiped the whole system and re-installed both operating systems from scratch.
What I paid closer attention to this time, which may have helped, was the following:
- Made sure to always mount my USB media in UEFI mode
- Performed the entire installation process using internal graphics, then installed the NVidia drivers once everything was working properly

Thanks for the help. Sorry for the perhaps-not-so-helpful conclusion.
Is it appropriate to mark this thread as [SOLVED] in this case, or just end it?

---

### Post by oldfred on 2016-12-27
You can change to solved as you did solve it, even though the brute force reinstall.

We like to try to fix things, so we understand issue. But sometimes fixing them takes longer than a reinstall.
And with many users they do not have good backups or new install so repairs become more vital.

---

