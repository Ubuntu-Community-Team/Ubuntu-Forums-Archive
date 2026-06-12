---
title: "Hello and a few questions regarding my installation!"
date: 2019-01-16
forum: Ubuntu, Linux and OS Chat
---

### Post by stirlitzba on 2019-01-16
Hello there! 
First post on the forums, right after my first Ubuntu installation. I've been struggling with it for a day now but I finally managed to get it working just a few minutes ago. 

I still had some questions though, and was about to just add them to the original post and continue with posting it in the Installation forum but it was a subforum of Support, so I thought I'd copy and paste it here in the general discussion. 
I'm pasting my original post as-is as, apart from the Hello part, the rest of the post is new and relevant.

Post follows:

Hello, 
I'm relatively new to Linux. I originally started with Mint and really loved it, but I wanted to try Lubuntu, the Cinnamon version being too heavy for my laptop. I'll try to explain my predicament and all the steps that led me there, hoping that's enough, since I'm not well-versed in operating systems or much else regarding computers(yet).

===I solved it while writing this post, but I'd still like to post it because I still don't understand why it now works.===

I made a boot stick, booted on Lubuntu and clicked the install icon. During the partition phase, I was not given any option other than the manual one, so I made 3 partitions: 
a 200MB EFI FAT32 mounted on /boot/efi and flagged with boot and esp(I read that I needed much less space for that, but some ubuntu guide online suggested 200ish MB so I thought why not be safe?), 
a 26GB(most of my hdd) main partition, using an ext4 file system and mounted on / 
and a linuxswap partition with the 3 GB that's left(I have 2GB ram and thought having as much plus a little more for hibernation etc seemed like a good idea).
Then I put in my username and password and hit install.

When the installation was finished, I hit restart, and out of stupidity, pulled the USB so as to avoid booting from that, while the system was shutting down. I don't know if that affected it somehow, but afterwards my system wouldn't boot.

It would load the Bios(I had disabled Fast and secure boot beforehand, btw) and wouldn't allow me to select boot devices. I tried making a DBAN stick to wipe it clean, but it wouldn't boot either, nor did any other boot stick I tried. It boots normally though from the Lubuntu stick that I installed and  when I do so, I can see the installation on the hard drive, but I cannot make it boot from that OS.

I tried installing Mint again just in case it would reset it to my previous configuration hoping that I'd be able to make a better install afterwards, but I got the same kind of response: It would boot from the Mint flash drive, but after installing Mint and restarting it would only boot the OS that's in the flash drive and not the one on the HDD.

I tried resetting the laptop to it's factory defaults pressing the power button for 30 secs as Asus suggests, but it didn't work. 
I also tried installing Lubuntu using the OEM version from the Grub loader, but it felt just the same as installing it through the try version.

Another thing of note is that after I unplugged the flash drive while restarting, I started having a "dell_smbios unable to run on non-dell system" message pop up on the screen.

===Post Solution===
So while reading up on EFI, I thought I'd try to reinstall Lubuntu, but this time make the first partition be the EFI one, followed by the main partition with the swap one in the end. I thought that maybe on startup, when the disk starts reading it needs the information of where to look for the files, so the EFI part should be first. I hope my reasoning is correct, but  I would like some confirmation on that(and any other insight someone might wish to add).
If that's the case, why didn't it work when I installed Mint afterwards, which did not make an EFI partition but just installed the main partition and a swap? As far as I know, my previous Mint installation didn't have an EFI partition before either.
Also, what could have caused the dell-related message to appear?

I'd appreciate any input!
Thanks a lot for your time, 
Bill

---

