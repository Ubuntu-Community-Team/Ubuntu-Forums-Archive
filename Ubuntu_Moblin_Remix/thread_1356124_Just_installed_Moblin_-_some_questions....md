---
title: "Just installed Moblin - some questions..."
date: 2009-12-15
forum: Ubuntu Moblin Remix
---

### Post by fourjays on 2009-12-15
Hey,
Got a Samsung N130 netbook today and installed Ubuntu Moblin Remix on it straight away. I've dabbled with Linux on multiple occasions on a desktop PC but this is my first time with any kind of mobile computer so I have a couple of questions.

1) How can I improve the battery life? I know the Windows install comes with all kinds of things for this, but what is there that can be done in UMR?
2)I had the "official" Moblin installed first which booted very fast. Unfortunately getting ndiswrapper for wifi on it was near impossible so I gave up and used UMR which was much easier to get working. Is there any way to improve UMR's boot time though? Not hugely important but if it can be quicker then I'd like it to be. ;)
3) How do I edit the grub menu? I'd like to give the entries more logical names, set it to auto-boot quickly unless I press a key to bring the menu up, and display a prettier menu if possible. Last time I used Linux it was done by the "menu.lst" file... now it's all changed. :/ I've done some quick searches for information but am getting a lot of results for the old methods I know. Can anyone point me towards some solid, easy to understand explanations on how to achieve what I want to achieve?
4) A weird error... *sometimes* when it boots I get the terminal up after a little while. It says "fsck" followed by the drive "id" (/dev/sda2) and some numbers referring to "cleared" files and blocks. Shortly after this it pops-up "stopping ntp server ntpd" then "starting ntp server ntpd", before repeating them both again and going no further. Have to force the computer off and boot it again, at which point it boots fine. How do I stop this issue?

Thanks in advance for any help you can give :)

---

### Post by tux821 on 2009-12-16
Note: 
* You need some Linux / Ubuntu experience for this ;)
and it's experimental, so only if you like to experiment with your netbook.

This weekend I did some experimenting with Moblin 2.1 on my Acer Aspire One A110 netbook this weekend, here are some ideas:

2)Speeding up boot time, using the Moblin 2.1 kernel in Ubuntu netbook remix 9.10

* You must have installed your Ubuntu Netbook remix 9.10 on a ext3 partition (not the default ext4).

I extract the Moblin 2.1 kernel plus kernel modules, did copy those into my Ubuntu 9.10 netbook install and added this kernel to my grub menu.
The netbook booted significant faster into the feature rich Ubuntu remix 9.10 because the Moblin 2.1 does not use a initrd.. For me everything worked, you may have figure out problems with your wifi ;)

3) How do I edit the grub menu? I'd like to give the entries more logical names, set it to auto-boot quickly unless I press a key to bring the menu up, and display a prettier menu if possible. Last time I used Linux it was done by the "menu.lst" file... now it's all changed. :/ I've done some quick searches for information but am getting a lot of results for the old methods I know. Can anyone point me towards some solid, easy to understand explanations on how to achieve what I want to achieve?

Yep, Ubuntu kernel upgrades re-generate the grub menu automagically ;)
Because I experiment with different Linux setups I keep a backup grub menu.lst (or now the grub.cfg) and after every kernel upgrade I manually check and adjust my grub configuration.

4) A weird error... sometimes when it boots I get the terminal up after a little while. It says "fsck" followed by the drive "id" (/dev/sda2) and some numbers referring to "cleared" files and blocks. Shortly after this it pops-up "stopping ntp server ntpd" then "starting ntp server ntpd", before repeating them both again and going no further. Have to force the computer off and boot it again, at which point it boots fine. How do I stop this issue?

Hmm.. Not good if fsck (file system check) keeps complaining.
I should perform a full fsck on your /dev/sda2 partition and correct any errors.
Further, do not know if you do so, but use the normal shutdown from the Ubuntu menu to power down your netbook.

---

### Post by fourjays on 2009-12-16
> Further, do not know if you do so, but use the normal shutdown from the Ubuntu menu to power down your netbook.
Moblin remix has no shut down button though? Have to use the netbooks off button at which point it seems to shut down normally (displays the black/white Ubuntu splash then a command line briefly before turning off).

---

### Post by tux821 on 2009-12-16
> **fourjays said:**
> Moblin remix has no shut down button though? Have to use the netbooks off button at which point it seems to shut down normally (displays the black/white Ubuntu splash then a command line briefly before turning off).Yep I did search a while for the 'shutdown' symbol. Just pressing the power button triggers the shutdown pop-uo window. This also works in Ubuntu remix.
I was just wondering why you might have file system errors. Hmm the only time I had those where from a harddisk breaking down..

I never had problems with the network time protocol so best guess is first check your disk using a live iso on USB stick.
You can use the System / Disk Utility from a Ubuntu 9.10 live iso for this.

---

### Post by fourjays on 2009-12-16
It didn't seem to say there are errors. It's almost like the process was interrupted - it said fsck then had "files" with two numbers indicating a processed amount (eg: 12345/123456), then repeated it for "blocks" (obviously with different numbers). Then immediately after this line it said "stopping ntp" then "starting ntp", etc. There was nothing to indicate it had completed scanning the files, or that it had found any errors.

Will do a disk check from the ISO.

---

### Post by fourjays on 2009-12-16
I can't find the System/Disk Utility on the Ubuntu Moblin Live ISO. Is it not included? Is there a way to do it via the terminal using the ISO?

---

### Post by fourjays on 2009-12-16
Just downloaded the Netbook Remix to give it a go and found the "Disk Utility" on that. Ran the "Check file system" option (running from USB) on the partition with the Moblin Remix currently installed and it says "File system is clean".

---

### Post by tux821 on 2009-12-17
Ok your file system seems ok.

> **fourjays said:**
> 
Will do a disk check from the ISO.

Did you check the md5 sum of the iso?

Maybe a re-install or try the Ubuntu netbook remix 9.10?

Hmm where did you get that Ubuntu Moblin iso from, when I try to download I get:

"The requested URL /ubuntu-moblin-remix/daily-live/current/karmic-moblin-remix-i386.iso was not found on this server." 

I don't understand, the new Moblin 2.1 is based on Fedora, is Ubuntu still trying to build a Ubuntu based Moblin release?

(Sorry If I go a bit off-topic here)

---

### Post by fourjays on 2009-12-17
I didn't check the md5 - I rarely do when I probably should. I found that it was "not found" when going to the linked url too, but browsed through it up to /ubuntu-moblin-remix/ and found the it also under another directory there. Was "karmic-koala" or something. I figured it to just be a slightly older version of 9.10, rather than the latest up-to-date one.

Anyway, I've installed the netbook remix now and have not had the same issue yet. Much prefer it too as it seems a little less buggy (especially with the wireless).

Only thing I'm struggling with at the moment is user accounts. I set-up one for my mother earlier and it works fine. However, I tried to create one for my sister and thought it had worked ok, but it refuses the password! I've checked and double-checked that I'm entering it correctly and it still refuses it. I get the impression it isn't being set in the first place as when I go to properties there are the blank password fields, whereas if I go to one that works it has a "change password" button instead of the two input boxes.

I've also tried to delete the account from my own. It disappears and I log out, but then it is there on the login screen... I logged into my mothers account, tried to delete it from there and it disappeared. Logged out and it is still there. :S

Any ideas?

---

### Post by tux821 on 2009-12-17
> **fourjays said:**
> I didn't check the md5 - I rarely do when I probably should. I found that it was "not found" when going to the linked url too, but browsed through it up to /ubuntu-moblin-remix/ and found the it also under another directory there. Was "karmic-koala" or something. I figured it to just be a slightly older version of 9.10, rather than the latest up-to-date one.

Anyway, I've installed the netbook remix now and have not had the same issue yet. Much prefer it too as it seems a little less buggy (especially with the wireless).

Well, .. as you will discover the Ubuntu netbook remix 9.10 is a solid, feature rich platform with many more easy installable applications.
Moblin is targeted for fast, easy on line, performance. For me it did feel more like a mobile phone / PDA platform. I liked the fast boot and easy user interface (for that reason I installed it in a tiny second 2.5 MB partition on my 8 GB SSD :P
> **fourjays said:**
> 
Only thing I'm struggling with at the moment is user accounts. I set-up one for my mother earlier and it works fine. However, I tried to create one for my sister and thought it had worked ok, but it refuses the password! I've checked and double-checked that I'm entering it correctly and it still refuses it. I get the impression it isn't being set in the first place as when I go to properties there are the blank password fields, whereas if I go to one that works it has a "change password" button instead of the two input boxes.

I've also tried to delete the account from my own. It disappears and I log out, but then it is there on the login screen... I logged into my mothers account, tried to delete it from there and it disappeared. Logged out and it is still there. :S

Any ideas?
I guess you used: System / User and Groups 
Probally not a good idea to delete your own account because it will have the sudo / Administrator rights..
Best you can do is google for user management in Ubuntu and search if there are specific problems found, like:

[http://www.ghacks.net/2009/12/17/user-and-group-administration-in-ubuntu-9-10/](http://www.ghacks.net/2009/12/17/user-and-group-administration-in-ubuntu-9-10/)
[http://ubuntuforums.org/showthread.php?p=8508206](http://ubuntuforums.org/showthread.php?p=8508206)

However be sure you keep an Administrator account to perform sudo (super user / root actions because some times you need those higher permissions).
Good luck with your Ubuntu discovery ;)

---

### Post by fourjays on 2009-12-18
I wasn't trying to delete my Admin account, but one of the others. Fortunately managed it by using the deluser command. Then re-added the user and their password worked correctly.

All the user systems have changed (for the better) since I last used Ubuntu. All seems to be working well now though. Thanks for your help. :)

---

### Post by tux821 on 2009-12-19
Enjoy the Ubuntu netbook remix ;)

Just for your first question, another idea to speed up things when your netbook has a slow SSD like mine:

[http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One](http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One)

I now run Ubuntu from a fast SD Disk (Scandisk Ultra II / 8 GB), beside the great Ubuntu desktop, I now have some pretty performance on my old Aspire One 110.

Ah and don't forget this one for maximum media support on your netbook:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

(just click the here to install link on that page for easy install)

and for those sites using the MS Flash .. :

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

(I prefer Flash, but ok nice to see there is some competition here ;)

---

