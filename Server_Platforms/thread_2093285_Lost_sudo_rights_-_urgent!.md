---
title: "Lost sudo rights - urgent!"
date: 2012-12-10
forum: Server Platforms
---

### Post by dreamspy on 2012-12-10
Hi there!


I'll get straight to the problem, which is quite urgent, so I hope someone here will be able to help me :)  

I'm administrating a big Ubuntu 12.04 server, and my user recently lost sudo rights to this server.  I was the only admin on this server, and don't have physical access to the server, so I can't use recovery mode to fix the problem.  

So what happened is this:

I was adding a new user to the server, called newuser from now on.

I wanted to give the user sudo rights, and noticed that the only user/group that was listed in the sudoers file was the root user.  I noticed however that the current sudo user (called olduser from now on) was in the admin group.  So I added newuser to the admin group, by editing the /etc/group file, and adding :newuser to the end of the admin line, which now looks something like this:

[noparse]admin:x:111:olduser:newuser[/noparse]

I didn't put a : at the end, don't think that's a problem though...?

After doing that olduser lost his sudo rights, and I'm completely locked out of the server. I can ssh into it, but I get this message "olduser is not in the sudoers file." whever I try to sudo. 

So somehow by adding newuser to the admin group, disabled the sudo rights of old user.  I don't understand how, and don't understand how olduser had sudo rights in the first place??

So I'm hoping someone has an ace up their sleeve, anyone know a trick to get me sudo rights back?  I don't think it's possible, without some major hacking acrobatics ;)  but I wanted to check here before I go into the drastic measure of reinstalling the server. 

Really hope someone here can help me out!


regards
Frímann

---

### Post by 1clue on 2012-12-10
Does newuser work as a sudoer?

Yes, all the punctuation matters, as does the uniqueness of the numbers.

If you find a way to get in, make the admin line look EXACTLY like the others, and I believe the list of users should be comma separated.

---

### Post by 1clue on 2012-12-10
Don't have access to an ubuntu box right now, but here's a similar line from a RHEL box I have access to:

[noparse]wheel:x:10:root,ken,joshua,joanna[/noparse]

No punctuation at the end, just a comma separated list of users.  No spaces.

---

### Post by steeldriver on 2012-12-10
For future reference, it really isn't necessary to edit the groups file directly (and now you know why)

```
gpasswd --add newuser sudo
```would have done it SAFELY

Also note that the default group for granting sudo permission is actually called 'sudo' (not 'admin' - although iirc that's retained for backward compatibility)

---

### Post by dannyboy79 on 2012-12-10
were you changing the file with sudo visudo? if not, i bet you buggered the file up. I would think to fix this, you'll have to have physical access to the machine and chroot it so you can properly fix the sudoers file. Good luck

---

### Post by dreamspy on 2012-12-10
The new user does not have sudo rights.  

And yes, the problem seems to be the : between the users, should have been a comma! I used nano to edit the file. Never again!

We'll see how this goes, I suppose I'll just have to reinstall \\:D/

Thanks allot for your quick answers guys'n'girls.


Regards
Frímann

---

### Post by koenn on 2012-12-10
> **dreamspy said:**
> 
And yes, the problem seems to be the : between the users, should have been a comma! I used nano to edit the file. Never again!

We'll see how this goes, I suppose I'll just have to reinstall \\:D/


Since you screwed up by editing that groups file, you can probably fix it by editing it again. So nano once more. 

To get to the file you probably need to work around the OS of the server, by booting a live CD or so. If you can then mount the disk and fix the file, you're in the clear. Faster than a full recovery, and you have nothing to lose anyway.

From then on, no more nano for editing sudoers and the likes, although  technically, you can. 

Tip: the ":" in password, groups, shadow, ... files is a field separator. If you know that, you'd probably have guessed that adding a 2nd user with ':' was a bad idea.
The format is  actually
```
groupname:password:group-ID:(comma-separated) list of usernames
```

config files like these are usually also documented in the man pages (chapter 5)

```
man 5 group
```

---

### Post by dreamspy on 2012-12-10
> **koenn said:**
> To get to the file you probably need to work around the OS of the server, by booting a live CD or so. If you can then mount the disk and fix the file, you're in the clear. Faster than a full recovery, and you have nothing to lose anyway.


The big problem is that I don't have a physical access to the server... so a reinstall is probably the only way 2 go for me.

---

### Post by koenn on 2012-12-10
how are you going to reinstall without physical access ?

---

### Post by 1clue on 2012-12-10
> **koenn said:**
> how are you going to reinstall without physical access ?

You beat me to it.

If you have physical access then you don't need to reinstall, but if you can reinstall then you must have physical access right?

---

