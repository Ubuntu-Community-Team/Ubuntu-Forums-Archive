---
title: "Forgotten Server Password - Recovery Mode No Help"
date: 2007-05-10
forum: Server Platforms
---

### Post by Catsworth on 2007-05-10
Hey Guys,

I've got my server sitting in front of me (so have physical access to it), but I've forgotten the passwords to login to it (user passwords, root password, the lot).

I've tried going into recovery mode, but I don't get a root shell prompt.

First I get a message asking me to enter the root password 'for maintenance', or to press Control-D to continue.  I don't know the root password so I press Control-D - I then get a standard login prompt, which is no use (obviously) because I don't have the password.

I'd appreciate a little help in regaining access please.  I've searched,but the solutions all seem to point to recovery mode (which, as I've said, is no good....).

Thanks.

---

### Post by Catsworth on 2007-05-10
Bump.

Sorry for the early bump, but I'm in a bit of a pickle here and need to get this working tonight if I can - anybody able to help with this? :(

---

### Post by StarMonkee on 2007-05-10
I'm not sure exactly how ubuntu deals with a single user login, but try one of these (2 will definitely work)

1, At the grub menu, press esc to see the menu. Then press 'e' on the top line (to edit), then 'e' on the long line from the few which appear. Try adding the word 'single' without quotes and then press enter, and 'b' to boot. If that doesnt work, try using 'linux single' instead. That should boot straight as root, but I think that's what the recovery mode is supposed to do.

2, Boot from the installer cd, or any linux livecd (knoppix/dsl/puppy/gentoo/anything). Then mount your primary hard drive somewhere and edit /etc/shadow on the mount (/mnt/etc/shadow or wherever you mount it). Change the long garbled string next to either root or your normal user to blank and save - that should allow you to login without a password.

---

### Post by Catsworth on 2007-05-10
Ok, I can't open /etc/shadow (it has a red cross on it, and the icon appears empty anyway).  I've found an /etc/passwd.

If I delete the x next to my name will that have the same effect?

Thanks for your help with this.

---

### Post by StarMonkee on 2007-05-10
I don't think so, passwords aren't stored in /etc/passwd any more, it's all in /etc/shadow.

You should have access to edit that though - are you logged into whatever environment you're currently in as root?

One thing to make sure of is that you're editing the /etc/shadow on the drive you're trying to recover, and not the environment you're booted into. I'd do the following:

mkdir /mnt/recover
mount /dev/hda1 /mnt/recover

Then either:
vi /mnt/recover/etc/shadow
or
chroot /mnt/recover
vi /etc/shadow

I should point out that I've never actually done this myself, but it should easily be possible. It's the same as sticking the drive as a slave in another machine and editing the files on it.

---

### Post by Catsworth on 2007-05-10
Def logged in to this environment as root.

I'm going to reboot and try again.  The whole thing isn't helped by the fact that the live CD keeps crashing, and that the keyboard is playing games (I just typed sudo and it came out as ssssssssssssssuuuuuuuuuuuudddddddddddddddddddddddddddddoooooooooooooo).

I'll keep trying, but this is looking fairly hopeless :(

---

### Post by Catsworth on 2007-05-10
Ok, given up on the Ubuntu Live CD.  Gonna try a different CD and see if that helps.  Still can't get anywhere with this, mainly because the keyboard responses are screwed but also because the damn thing keeps crashing!

---

### Post by StarMonkee on 2007-05-10
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) is pretty good for this kind of situation.

good luck!

---

### Post by Catsworth on 2007-05-10
Ok, the trusty Knoppix STD disc saved the day and I've removed the passwords for the accounts I need access to.

So, I can access the files I need (which is good) - all I need to do now is restore access to the network shares that are on it and see if I can get it doing what it should be doing.

Thanks very much for your help with this, really appreciate it :)

---

### Post by StarMonkee on 2007-05-10
Glad I could help :D

---

### Post by Catsworth on 2007-05-10
:)

Just when I think I'm liking Ubuntu it all goes wrong again.

I *did* have webmin set up on this server, I could just double click on a folder on my desktop and access a shared folder on the server, the first time I try to access the files for a couple of weeks it all goes to sh*t!!

I can't access the webmin control panel, I can't access the share, I can't ssh into the server.  I can login remotely and get a root terminal but that's it.

Looks like it's a complete rebuild for this one, yet another thing to add to the list of tasks that I just don't have the time to do.

---

