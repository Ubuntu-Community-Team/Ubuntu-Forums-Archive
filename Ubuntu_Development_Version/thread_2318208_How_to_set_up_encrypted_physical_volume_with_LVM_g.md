---
title: "How to set up encrypted physical volume with LVM group?"
date: 2016-03-23
forum: Ubuntu Development Version
---

### Post by sanssadness on 2016-03-23
I found a guide from years ago that helped me set up an encrypted Ubuntu installation in a unique way. The guide is here: [http://techblog.mastbroek.com/all-articles/dualboot-encrypted-windows-and-ubuntu/5/](http://techblog.mastbroek.com/all-articles/dualboot-encrypted-windows-and-ubuntu/5/)

Allow me to summarize what I'm trying to do:

1. Create an unencrypted boot partition
2. Create a physical volume for encryption
3. Within the physical volume for encryption, create an LVM group
4. Create a logical volume for swap within the LVM group
5. Create a logical volume for root within the LVM group

To see a picture of what this setup looks like, visit the link to the guide and ctrl + f the word "complicated." The screenshot showing the structure of the drive is right above the word "complicated."

Here's what the setup would look like in Gparted:

/dev/sda1: Windows partition (don't worry about this part; I've got it set up already)
/dev/sda2: /boot partition for Ubuntu. Not encrypted.
/dev/sda3: Extended partition
     /dev/sda4: crypt-luks

The setup works perfectly on Ubuntu 12.04. It even upgrades well to 14.04, but it won't upgrade to 15.10 properly; I get some weird boot error that I can't fix, so I have to set up 16.04 manually. I tried using the live disc, but I can't seem to create a LVM group inside the physical volume for encryption. I think at least part of this has to be done using a third-party program like Gparted, unless I've missed a feature on the live disc's manual partitioning option, which is very possible given my lack of experience. If anyone could help me out here, I'd be very grateful.

---

### Post by mikodo on 2016-03-24
Well, I've never dual-booted with Windows. I have never used full-system encryption. I have never had UEFI BIOS with an ESP partition. You get the picture. I am not one to be able to offer advice.

I was too tired to read the guide to understand it. And I need to get up in 5 hours for work but, I did see the word TrueCrypt in it.

Somethings came to mind though that I will throw  out to you until, someone who can really help you chimes in:

1. I'm not sure TrueCrypt is still supported.
2. I'm pretty sure that Ubiquity insists on booting the first part of the drive.
3. Have you looked else where to try another way around this? Like here:
[https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system)

Specifically here with lvm on Luks:
[https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS)

---

### Post by sanssadness on 2016-03-24
TrueCrypt isn't supported anymore, but it still works. The latest security audit didn't find any significant vulnerabilities with it. I have gotten a multiboot scenario working with it and the encrypted Windows partition was the first boot loader, so no problems there. I knew mentioning TrueCrypt would open a whole can of worms, but the situation is not much different whether you have Bitlocker or even some unencrypted Windows installation at sda1. All that matters is that whatever you have can chainload grub on the /boot partition. If you can make that happen, then the only problem left is how to set up LVM/LUKS, which is why this thread focuses on that problem.

I'm looking through the guide you posted, but isn't it for Arch Linux? Assuming it works for Ubuntu as well, where's the step where the operating system gets installed? The "LUKS on LVM" section ends without really getting into that, unless I missed something.

---

### Post by mikodo on 2016-03-24
Hi,

1.* Incorrect information.* [s]Upgrading from 14.04 > 15.10 isn't supported. 14.04 > 16.04 will be supported. (14.04 && 16.04 are both LTS releases and upgrading is supported). Is that an option for you still?[/s]

2. Correct, you cannot set up LVM with Ubiquity. Could you do this to set up the LVM group: [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

&&

3. Use this guide to set up the encryption. Or, use this guide to do the encryption and the LVM: [https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity](https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity)

4. This to me, looks the most helpful for your question:  [http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows/470667#470667](http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows/470667#470667)

I hope this is helpful.

---

### Post by deadflowr on 2016-03-24
> [COLOR=#000000]1. Upgrading from 14.04 > 15.10 isn't supported.[/COLOR]
It is supported.

After the change of non-lts support was dropped from 18 months to 9, they decided that since support for the next release after the lts was so short they would open up the upgrade channel to the next release after the first non-lts release went EOL, and then when that release goes dark, they would open up the release to the channel after that, and so on until the next lts is available.

---

### Post by sanssadness on 2016-03-24
Technical upgrading from 14.04 to 16.04 is still an option, yes. I just need to get it to work. Once I do, I'll have until the end of 16.04's life cycle to figure out how to set up the encryption.

The reason I haven't gotten it to work is because I ran into a problem upgrading from 14.04 to 15.10. In the middle of the upgrading process my monitor went dark. I wasn't around my computer to see what happened, but I couldn't make it respond, so I force rebooted. Upon starting up 15.10 (that's what the splash screen said; I don't know if the upgrade actually finished), I got nothing but a purple screen with a blinking red cursor. Can I upgrade from 12.04 straight to 16.04, or must I go through every version in the middle? I know I went from 12.04 to 14.04 without problems.

---

### Post by mikodo on 2016-03-24
> **deadflowr said:**
> It is supported.

After the change of non-lts support was dropped from 18 months to 9, they decided that since support for the next release after the lts was so short they would open up the upgrade channel to the next release after the first non-lts release went EOL, and then when that release goes dark, they would open up the release to the channel after that, and so on until the next lts is available.

Thank you. I didn't know that. I'll amend what I said in the earlier post.

---

### Post by deadflowr on 2016-03-24
> **mikodo said:**
> Thank you. I didn't know that. I'll amend what I said in the earlier post.

It's relatively new.
The devs mulled doing something like that when they made the support change, but only recently implemented it.
Here's a screenie of the updater for 14.04 if you have the notify of any new release enabled.
(14.04 defaults to notify of long-term-releases only, so you would have to change that to get this:

Off topic.

Being more on topic, you can use the server edition to do what the alternative cd did.
Or the netboot image.

---

### Post by sanssadness on 2016-03-24
I took a closer look at the 2 guides you mentioned earlier. I think I may have seen this one before: [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

The only problem with that guide is that although it shows how to set up LVM, it doesn't also include LUKS. In other words, no encryption.

This one, however, is very promising: [https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity](https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity)

The only problem I'm having with it is that it doesn't mention where you actually install Ubuntu. I've seen similar guides on how to set up the partitions and LVM, including with a passphrase. But the guides tend to get a bit fuzzy on how you actually install Ubuntu on the encrypted partitions. When do you do it, and does the installer prompt you to unlock the encrypted physical volume or partition?

And regarding the supported upgrade from 14.04 to 15.10 can I just skip 14.04 and 15.10 altogether? A 12.04 to 16.04 upgrade would be nice. Or at least a 14.04 to 16.04. Going to 15.10 gives me that purple screen/red cursor of death.

---

### Post by mikodo on 2016-03-24
> **sanssadness said:**
> Technical upgrading from 14.04 to 16.04 is still an option, yes. I just need to get it to work. Once I do, I'll have until the end of 16.04's life cycle to figure out how to set up the encryption.

The reason I haven't gotten it to work is because I ran into a problem upgrading from 14.04 to 15.10. In the middle of the upgrading process my monitor went dark. I wasn't around my computer to see what happened, but I couldn't make it respond, so I force rebooted. Upon starting up 15.10 (that's what the splash screen said; I don't know if the upgrade actually finished), I got nothing but a purple screen with a blinking red cursor. Can I upgrade from 12.04 straight to 16.04, or must I go through every version in the middle? I know I went from 12.04 to 14.04 without problems.
Well, I hope you saw deadflowr's response above. Technically, you should be able to upgrade from 12.04 > 14.04 > 16.04 as they are all supported LTS. Except that 16.04 is not officially released until next month so, it might be too early for this yet. Keeping in mind though, that release-upgrade's have not always succeeded differing on people's experience.

Addendum: Yesterday on the Xubuntu-devel mailing list there was a report(s), of some of the _testing_ release-upgrades from 14.04 > 16.04 having recently failed while tested with using the update-manager. FYI. So, I guess wait and see for that.

I hope you saw my addendum to my post #4.  Number 4 answers your OP question quite simply, I believe.

---

### Post by mikodo on 2016-03-24
> **sanssadness said:**
> 
The only problem I'm having with it is that it doesn't mention where you actually install Ubuntu. I've seen similar guides on how to set up the partitions and LVM, including with a passphrase. But the guides tend to get a bit fuzzy on how you actually install Ubuntu on the encrypted partitions. When do you do it, and does the installer prompt you to unlock the encrypted physical volume or partition?
There does seem to be a sparsity of information on the internet for one to read and understand. I do find the Arch Wiki has  very good information on the concepts of dm-crypt/Device encryption with and without LUKS. Maybe, spend sometime there to see if it can provide the direction you need for, your use of encrypted volumes in Ubuntu on new installs:

[https://wiki.archlinux.org/index.php/Dm-crypt](https://wiki.archlinux.org/index.php/Dm-crypt)

Or even better, if I shut up possibly, someone that knows this well will chime in and quickly give you the answers you need.

:)

---

### Post by sanssadness on 2016-03-24
[QUOTE=mikodo]There does seem to be a sparsity of information on the internet for one to read and understand. I do find the Arch Wiki has  very good information on the concepts of dm-crypt/Device encryption with and without LUKS. Maybe, spend sometime there to see if it can provide the direction you need for, your use of encrypted volumes in Ubuntu on new installs:

[https://wiki.archlinux.org/index.php/Dm-crypt](https://wiki.archlinux.org/index.php/Dm-crypt)

Or even better, if I shut up possibly, someone that knows this well will chime in and quickly give you the answers you need.

:)[/QUOTE]

Don't shut up...ever. There's a lot of reading in this thread. Even though it might not seem like it, I'm going through every post and trying out things I haven't already done. I just realized why the Arch Wiki article doesn't mention installation. The wiki says this:

"Afterwards continue with the installation procedure up to the mkinitcpio step."

It was driving me crazy that I couldn't find the installation procedure. Then I did some digging around and found this: [https://wiki.archlinux.org/index.php/Installation_guide](https://wiki.archlinux.org/index.php/Installation_guide)

I think that's the guide it was referring to. If so, and if I can find a disc that boots properly and lets me enter the terminal while in the installer, my problems could be killed right here. The Arch wiki is so detailed and organized. If only someone had created a link for the words "installation procedure" that led back to the guide I just found. It would have saved lots of time. The Arch wiki is the first time I've seen all the major types of LUKS setups described in broad strokes and compared side by side. Simply amazing!

Are the steps in Arch all applicable to Ubuntu as well?

---

### Post by mikodo on 2016-03-24
> **sanssadness said:**
> Don't shut up...ever.

Well, there are a few people here at times that I can think of that would answer your questions as fast as I can type. I worry that if any of them do fly by and see the amount of responses in your thread they, may not think they need to add to it.

> Are the steps in Arch all applicable to Ubuntu as well?

> Afterwards continue with the installation procedure up to the mkinitcpio step.

Unfortunately, No. After posting what I was the solution initially for you, ([this link]("https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS")) I found by reading about mkinicpio that it appears to be only a library that is used in Arch, attending to initramfs. When I read the response/explanation of initramfs [here]("http://unix.stackexchange.com/questions/120198/how-to-fix-boot-into-initramfs-prompt-and-mount-cant-read-etc-fstab-no-su") I knew I was waaaaay over my head to try to find how to do that in Ubuntu. I did read how on one site for Debian/Ubuntu but, thought there must and easier way to deal with the the issue of LUKS on top of LVM in Ubuntu than messing with that file. I think a couple of the other non-Arch links I posted can hopefully attend to your needs with the knowledge you gain from the Arch Wiki.

I still remain hopeful that, some skilled people will respond quickly for you.

---

### Post by sanssadness on 2016-03-25
Well, the Arch article was still helpful. It gives you the overall picture of what is being done. I still need to find the commands for Ubuntu, but it's a step in the right direction. At least I know what to look for and will know it when I see it.

---

