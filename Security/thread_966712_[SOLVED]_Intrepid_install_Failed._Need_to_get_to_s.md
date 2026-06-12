---
title: "[SOLVED] Intrepid install Failed. Need to get to single user root mode"
date: 2008-11-01
forum: Security
---

### Post by davidkahn on 2008-11-01
I have set up Grub to require a password to select recovery alternative modes. However, in the past when I selected a "Recovery Mode" version of a kernel, it went directly to a command prompt logged in as root. Now with Intrepid I come to a new menu that has an entry "Drop to root shell prompt", which I can't use because it then asks for the root password, and in Ubuntu you don't know root's password because the root account is locked.

I don't have earlier versions of Linux on the disk that I perhaps would go directly to the command prompt logged in as root.
 
When I enter "e" to edit the grub commands before booting I see:
[INDENT]lock
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/md0 ro single
initrd /boot/initrd.image-2.6.27-7-generic
[/INDENT]Is there something I can add to the kernel command line to have it go directly to the single user cammand prompt as root?
 
Can I reinstall Hardy over this disk without losing all of my personal data?

What else could I do?

Please help.

David

---

### Post by davidkahn on 2008-11-01
I don't know if anyone is going to read this, since there were no replies to my question.  But since I solved it, I wanted to post my solution for other people.  Moreover, if requiring a password to get to the single user prompt logged in as root was intended to improve security, I just found a security hole.  This hole might not apply to my computer because I setup /boot/grub/menu.lst to cause grub to require a password to edit the grub boot parameters.  But since many people don't, this procedure is a security hole for them.
 
I used grub to perform a one-time edit of the boot line:
[INDENT]kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/md0 ro single
[/INDENT]and made it:
[INDENT]kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/md0 rw init=/bin/bash
[/INDENT]Booting then brought me to a command prompt as root, with the file system being read-write.  I then used the passwd program to set root's password to a known value, and now I can select menu item that has an entry "Drop to root shell prompt", and enter root's password.
 
However, having a (presumably) crackable root password seems so un-Ubuntu.  So I am wondering if anyone else has a more elegant solution.

---

### Post by Dave_Connor on 2008-11-02
This is with physical access to your machine. Linux is more prevent online attacks but there are measures against people you don't trust accesssing your machine physically.

---

### Post by bodhi.zazen on 2008-11-03
First of all, the default behavior in Ubuntu when you boot to recovery mode is to boot to a root shell without asking a password.

The only time you will be asked a password is if you change the default behavior or set a root password.

Second, in a nut shell you are asking about how to secure a box from someone who has physical access, and the short answer to that is you can not. BIOS passwords, grub passwords, root passwords, all that is easily defeated.

The only "protection" you have is encryption. Encryption will protect sensitive data, but beyond that physical access == game over :lolflag:

---

### Post by davidkahn on 2008-11-03
I had to set the root password to install a modem/fax driver, and wanted to unset it to get back to Ubuntu's standard security model.  My understanding was that the way to do this was to run:
[INDENT] sudo passwd --lock root
[/INDENT]This certainly makes it very difficult to log in as root.

However, after I did that, grub still asked for root's password, but I no longer knew its value, and couldn't boot into recovery mode.

What's the correct process to lock root and restore grub's default behavior. 

Thanks.

David

---

### Post by bodhi.zazen on 2008-11-03
> **davidkahn said:**
> I had to set the root password to install a modem/fax driver, and wanted to unset it to get back to Ubuntu's standard security model.  My understanding was that the way to do this was to run:
[INDENT] sudo passwd --lock root
[/INDENT]This certainly makes it very difficult to log in as root.

However, after I did that, grub still asked for root's password, but I no longer knew its value, and couldn't boot into recovery mode.

What's the correct process to lock root and restore grub's default behavior. 

Thanks.

David

You are asking two questions.

First, how to remove the grub password.

With any editor (gksu gedit /boot/grub/menu.lst) edit /boot/grub/menu.lst

Remove the line with "password" in it:

> password --md5 xxxyyyzzz

To lock the root (or any account) use :

```
sudo usermod --lock root
```

[https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755)

=============

Last, to get a root shell, rather then setting a root password, use sudo :

```
sudo -i
```

:twisted:

---

### Post by davidkahn on 2008-11-03
I intentionally added  the password --md5 $1$BIWmD$dA8Bbs4WZ7... line to /boot/grub/menu.lst to require a password to select one of the recovery mode boot choices.  But I didn't know about usermod. Thanks for the help.

---

### Post by davidkahn on 2008-11-04
I tried going to single user recovery mode, and it's still asking for root's password.  So as far as I can tell 'sudo usermod --lock root' may do exactly the same thing as 'sudo passwd --lock root', though the man page for passwd doesn't explain how it disables the password.

To be completely clear, I am not talking about the grub password to allow running locked boot options.  The problem occurs after the menu that was introduced in Hardy that allows choices like fixing xorg.conf, updating packages.  When one selects "Drop to root shell prompt", before it gets to the command prompt, it asks for root's password, even though the usermod command has made entering a valid password impossible.

Is there any way to restore the "normal" state with a password isn't needed?

---

### Post by bodhi.zazen on 2008-11-04
You will need to manually edit /etc/shadow and possibly /etc/passwd

/etc/passwd 

[noparse]root:x:0:0:root:/root:/bin/bash

/etc/shadow

root:!:14182:0:99999:7:::[/noparse]

Notice the ! in the second column in /etc/shadow for root, that is probably the edit you need.

---

### Post by davidkahn on 2008-11-04
bodhi,

Editing /etc/shadow and making the password equal "!" rather than simply inserting a "!" in front of the password, which is what usermod does, worked perfectly.  /etc/passwd did not require an edit.

Thanks for following through.

David

---

### Post by bodhi.zazen on 2008-11-04
You are most welcome.

---

### Post by brightsmile on 2008-11-06
I had changed my user password to something I couldn't remember later.. and this procedure worked perfectly. :)

Thank you very much, bodhi!  ( How does one thank a person? Is there a link somewhere? )

Just one question: can I leave the "!" in that "shadow" file?  What do I lose regarding security?


BTW, I meditate too, with Holosync from Centerpointe -- wonderful technology:
[http://www.centerpointe.com/](http://www.centerpointe.com/)


Once more, thank you very much bodhi!

---

### Post by bodhi.zazen on 2008-11-06
> **brightsmile said:**
> I had changed my user password to something I couldn't remember later.. and this procedure worked perfectly. :)

Thank you very much, bodhi!

You are most welcome.

> ( How does one thank a person? Is there a link somewhere? )There is a small icon in the lower right of the post you wish to thank.

> Just one question: can I leave the "!" in that "shadow" file?  What do I lose regarding security?A ! disables a log in to the account, in this case root.

If I may elaborate, the password is not stored a plain text, but rather it is encrypted or a hash. If you have an invalid symbol, it invalidates the hash.

So a ! = Inactive.
A !xxxyyyzzz = inactive, but the user's password hash remains. To reactivate the account and restore the old password, just delete the !.

All of this is "old school" and in general we do not directly edit these files (well, some of the geeks still do). We use tools such as adduser, deluser, passwd, etc. Some people go as far as to use GUI tools :twisted:

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

[http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html](http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html)

[http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.html](http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.html)

> BTW, I meditate too, with Holosync from Centerpointe -- wonderful technology:
[http://www.centerpointe.com/](http://www.centerpointe.com/)

Once more, thank you very much bodhi!Sweet, thank you for the link. Always nice to see the tradition is alive and well.

---

### Post by Cosimix on 2008-11-12
Hi everybody... I hope this is the right thread for my issue. 

Problem Description:
Regardless of whether the password is locked or not when I "init 1" from X I get the nasty password prompt which I wish to disable. 

"Give root password for maintenance or press CTRL+D to continue"

This might have occurred _since I upgraded to Intrepid_ with the "do-release-upgrade" utility from CLI and happened in the past when I moved from Ubuntu 7.10 to 8.04 as well.  

I will let you know if I can find anything. Any help much appreciated.
Cosimo

---

### Post by davidkahn on 2008-11-12
Try this recommendation from [[COLOR=#d40000]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"):
[INDENT]"You will need to manually edit /etc/shadow and possibly /etc/passwd

/etc/passwd 

[noparse]root:x:0:0:root:/root:/bin/bash[/noparse]

/etc/shadow

[noparse]root:!:14182:0:99999:7:::[/noparse]

Notice the ! in the second column in /etc/shadow for root, that is probably the edit you need."

Edit bodhi.zazen: disabled smiles in code :twisted:
[/INDENT]

---

### Post by Cosimix on 2008-11-12
[COLOR="Red"]"Notice the ! in the second column in /etc/shadow for root, that is probably the edit you need."[/COLOR]

That worked indeed... God bless you guys !!

Cheers
Cosimo

---

