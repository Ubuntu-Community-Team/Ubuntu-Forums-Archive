---
title: "Access Secure Files with Live CD"
date: 2008-03-30
forum: Security Discussions
---

### Post by DonCoryon on 2008-03-30
Hello everyone, first post here.

I am brand spanking new to Ubuntu, but so far so good.  I ran into a problem earlier with a blank boot screen and a 5 min boot.  Thank you all in the forums for helping me.  I was able to find the info I needed without even having to post.

One thing I noticed was that in order to access menu.lst I had to go through the terminal and type:

sudo gedit /boot/grub/menu.lst

Then I typed in my password.  Secure I guess.

Something happened, I must have messed up, and the system crashed and I wasn't able to start the system.  I loaded up the computer with the live CD, opened up the menu.lst by typing in:

sudo gedit /media/disk/boot/grub/menu.lst

Found my mistake and corrected it.  

What I wanted to point out was I skipped the step about a password because Ubuntu never required it.

This doesn't seem secure if all you have to do is get a live cd to override passwords.

---

### Post by DonCoryon on 2008-03-30
Not a bump, just set my options to subscribe when I post or reply, so I need to post something.

---

### Post by Oldsoldier2003 on 2008-03-30
> **DonCoryon said:**
> Hello everyone, first post here.

I am brand spanking new to Ubuntu, but so far so good.  I ran into a problem earlier with a blank boot screen and a 5 min boot.  Thank you all in the forums for helping me.  I was able to find the info I needed without even having to post.

One thing I noticed was that in order to access menu.lst I had to go through the terminal and type:

sudo gedit /boot/grub/menu.lst

Then I typed in my password.  Secure I guess.

Something happened, I must have messed up, and the system crashed and I wasn't able to start the system.  I loaded up the computer with the live CD, opened up the menu.lst by typing in:

sudo gedit /media/disk/boot/grub/menu.lst

Found my mistake and corrected it.  

What I wanted to point out was I skipped the step about a password because Ubuntu never required it.

This doesn't seem secure if all you have to do is get a live cd to override passwords.

The fact remains even if you password your BIOS and your grub menu anyone with physical access to your machine will be able to get in it in moments if they have the skills and the commonly available (read googled and downloaded) tools.

---

### Post by hyper_ch on 2008-03-31
(1) take the hardisk out

(2) put it in another computer as secondary device

(3) mount it

--> that's all that's need for circumvention of bios and grub password...

If you want to secure files, use (full) disk encryption

---

