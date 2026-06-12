---
title: "Persistent livecd password reset - how?"
date: 2017-09-25
forum: Ubuntu/Debian BASED
---

### Post by fboecom on 2017-09-25
I've created a persistent livecd on a USB stick with Zorin 9 (trusty) and it runs great. One problem - I forgot the root password. 
All instructions to boot into single mode for an installed system fail with the persistent livecd boot. No shift key, no F10. It just boots. Editing the boot startup instructions is easy - but livecd doesnt allow (at that time) editing grub.
When the USB disk is mounted in a running Ubuntu (also Zorin) system, I can easily go into /media/<user>/casper-rw/upper and sudo nano the /etc/passwd file. And the shadow file. And the passwd- and shadow- files. Take out the 'x' and setting root:::: in shadow. Checking the edits - yes, the files have changed.
Not funny is when I boot the persistent USB livecd again, those changes are undone and the passwd and shadow files have their passwords back in.
I've searched and searched but cannot find where and why my edits aren't 'persistent' back from an installed Ubuntu editing session on a mounted USB stick. Is there a backup of casper-rw somewhere which is rolled back? Disappearing edits on a file system are unpleasant magic to me.

---

### Post by sudodus on 2017-09-26
I don't know about Zorin, but Ubuntu (and the official Ubuntu community flavours Kubuntu, Lubuntu ... Xubuntu) do not let you log in as root. Instead you should use sudo from your normal user ID, for example

```
sudo parted -ls
```

In Ubuntu (and the official Ubuntu community flavours Kubuntu, Lubuntu ... Xubuntu) live and persistent live systems, you need no password to run sudo, while you need your standard password for the normal user ID in installed systems to run sudo.

Have you tried with sudo in Zorin? What happens?

---

### Post by fboecom on 2017-09-27
OK thanks a lot for your answer. Afaik Zorin 9 Trusty - especially in this case - is behaving like Ubuntu 14.04.. 

I made one user in the persistent environment which was added to the root group. It logs in automatically, but any program requiring root privileges, like 'sudo parted' inflict the ```
[sudo] password for <user>:
```  response. I guess I also gave user 'root' that same password because if I try to login with ```
su - live
``` it also asks for a password. I cannot login with 'live' either.
This means that when you build a USB live cd with persistence, and then create one (persistent) user with root privileges, the standard allowed sudo operations from livecd aren't possible anymore. That's sort of scary or handy - depending on how you look at it.

I had several USB sticks made from the same procedure so I could test a little.
I tried to sudo on the stick with which I have been testing yesterday - and to my surprise after your response I could sudo there, but I was sure it had refused before. And too bad I dont remember exactly what I have done, but basically what I described below.

Trying to remember my steps, I started with another disk with an installed Zorin/Ubuntu I changed on the USB (/media/<user>/casper-rw/upper/etc) passwd and shadow. ALL steps requiring a reboot in between, all unsuccesful.
[LIST]
[*]I took out the 'x' from passwd and the ecrypted passwd from shadow for <my user>.
[*]changing not only passwd but also passwd- with 'x' removed.
[*]changing in shadow and shadow- <my user> to contain only ::::::::
[*]now removing x from both root and <my user> in passwd(-) as well as placing :::::::: for both root and <my user> in the shadow(-)
[*]now removing x for root, <my user>, live as well as making those users :::: in shadow
[*]changing the permission on all those files to o+rw
[*]changing the permission on casper-rw/work to 777
[*]reboot. sudo still asking for a password. the permissions of shadow- is still o+rw but for shadow that is removed. Same for passwd. All passwd and shadow files have been rewritten by the reboot as I can see from the datestamp.
[*]
[/LIST]

The sudo chroot /media/../casper-rw obviously also does not work on liveCD.
I am kinda stuck and puzzled. I do expect that the precise format of the shadow file might be the trick. And, although not crucial, I would say it could be in the community's interest to find out the how-to this niche corner of Ubuntu.

---

### Post by howefield on 2017-09-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by sudodus on 2017-09-27
@fboecom,

Thanks for this detailed description :-)

---

### Post by fboecom on 2017-09-27
I think I have found a solution - weird but it works. I'll spare you the description of the many attempts.
On the first USB drive, where I could sudo, and with a very similar install/usernames as on the second USB, I did set a new password for the <my_user>.
Using an installed Ubuntu version, as superuser and with both USB drives attached, I copied out the 2 lines for the users <live> and <my_user> from USB1../casper-rw/upper/etc/shadow and replaced the lines for the same users on USB2../casper-rw1/upper/etc/shadow. In both passwd files the <live> and <my_user> entries keep their 'x', so no change there.
Reboot to USB2.. success! This time my /etc/shadow edits survived over the reboot where with all previous attempts it did not. On the first USB I've probably been lucky with one edit session; as editing /etc/shadow is generally unrecommended and little documented I probably made mistakes on USB2.
But, as simple as it is, take an equally named user from one installation's shadow file, replace it in another's and surprise! you login with another password.
I agree I won't do this on an enterprise production Ubuntu installation, but in my USB project it will not hurt anyone.

If someone can contribute a better solution I'm happy to learn, but for now I've reached my goal.

Later edit of this post:
with some later findings of changing that password, the only thing that I probably should have changed is taking out the text between the first and second ':' for <my-user> in the shadow file, and leave anything else in that line intact. 
So some findings, contrary to what's stated in several google posts:
[LIST]
[*]editing a shadow file is not dangerous or a "DO NOT" action ... but is simple and effective (in this case)
[*]editing the passwd file to remove 'x' is useless
[*]passwd- and shadow- are backup files and editing those has no effect
[*]in the shadow file, taking 'everything' out to leave only :::: is forcing the live boot process to overwrite those changes
[/LIST]
With all text removed between the first : and : you'll effectively removed the password; the next reboot you'll be able to logon without a password and if that user belongs to the root group you'll have a password-free sudo. the first thing you'll do is change the password and now remember it

---

### Post by sudodus on 2017-09-28
The mark [SOLVED] might help other users to find your solution, so please click on
**Thread Tools** at the top of the page and mark this thread as SOLVED

---

