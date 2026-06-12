---
title: "Running as root ;)"
date: 2006-09-05
forum: The Cafe
---

### Post by nirax on 2006-09-05
Hi all,

---

### Post by nirax on 2006-09-05
Hi all,

im sure everyone of you heard and read countless times that running
everything as root is one of the worst idea security wise which you can do
on a linux - well on every system.

neverless as IT professionals/home users/whatever how do you really
treat this suggestion ?

actually it is kind of hard to run all ubuntu installation as plain root. the normal install way implies the usage of a user  and sudo for administrative purposes. neverless there seem still to be ppl that go ways around just to run  root.

so whats your story about ?
and how do you run your system ?

---

### Post by DoctorMO on 2006-09-05
Not in root, never in root. root is a freek and we don't want him here!

---

### Post by aysiu on 2006-09-05
I use sudo, gksudo, and kdesu. I've never needed to enable a root account. I found logging in as root to be slow and useless.

---

### Post by nirax on 2006-09-05
thanks for your both input. aysiu, how do you mean "slow" ?

---

### Post by aysiu on 2006-09-05
Well, I like to permissions multi-task--have one program running as user and another running as root.

For example, I would like to have Firefox open as user while I have Nautilus open as root to edit a system file.

If I enabled and used a root account, I would have to start up a new login window and log in as root. Launch up Nautilus and make those changes, then log out again to use Firefox. The whole time I was in root Nautilus making those changes, I would not be able to do any user functions.

With *gksudo*, I can operate a root Nautilus window at the same time that I have a Firefox user window open. Likewise, with *sudo*, I can mix and match user and root commands without having one terminal session as root and another as user.

---

### Post by nirax on 2006-09-05
I see now, thanks for the explaination !

---

### Post by nu2this on 2006-09-05
Thanks,I just found the hard way what Aysiu wrote about. I did this because I thought it was necessary. So just to be sure is having a simultaneous root & usr profile necessary for Mr. Average Joe Enduser?

---

### Post by aysiu on 2006-09-05
> **nu2this said:**
> Thanks,I just found the hard way what Aysiu wrote about. I did this because I thought it was necessary. So just to be sure is having a simultaneous root & usr profile necessary for Mr. Average Joe Enduser?
I think a better question is--is having to put all your regular activities on hold to log into root graphically (where *everything* you do will be executed with root privileges) necessary for Mr. Average Joe End User?

A nice little ```
gksudo nautilus
``` launcher is far more convenient. Click it, enter your password, do what you have to do, and then close the window.

---

### Post by nu2this on 2006-09-05
Aysiu, for this end usr probably not. Before this I did everything from the original username & password I put in at install. If I've read this thread right that was secure enough for most end users,it's just me here not a big corp.
So then would it be safe to just do as I did before with usr &pswrd from install?
If yes then how is total deletion done of a usr account done? When I select the delete on Users & groups it says it'll take out the access but not the
usr home.
And that code listed still applicable should I go back to the way  I was doing it?

---

### Post by aysiu on 2006-09-05
I'm not really sure I understand what you're asking.

Both the root/user and sudo/user models are safe provided you're not stupid and you have a strong (hard-to-guess) password.

I'm not sure I understand why you want to delete users...

---

### Post by SoundMachine on 2006-09-06
> **nu2this said:**
> Aysiu, for this end usr probably not. Before this I did everything from the original username & password I put in at install. If I've read this thread right that was secure enough for most end users,it's just me here not a big corp.
So then would it be safe to just do as I did before with usr &pswrd from install?
If yes then how is total deletion done of a usr account done? When I select the delete on Users & groups it says it'll take out the access but not the
usr home.
And that code listed still applicable should I go back to the way  I was doing it?

The username and password you put in when you install the system is a normal user, normally if you are the only user on that computer, that is what you use, doesn't get any more secure than that. :)

To delete a user completely including his home directory, open up a terminal and type "sudo deluser --remove-home [username]" without the quotes and brackets, to remove all files on your system owned by the user you are deleting (which includes his home directory) use "sudo deluser --remove-all-files [username]" instead, for more info about deluser, open up a terminal and type "man deluser" up and down arrows to scroll, q to quit.

---

### Post by nu2this on 2006-09-06
> **aysiu said:**
> I'm not really sure I understand what you're asking.

Both the root/user and sudo/user models are safe provided you're not stupid and you have a strong (hard-to-guess) password.

I'm not sure I understand why you want to delete users...
I had a paranoid and/or stupid moment & made an extra user both are me if I don't need 2 ,which I don't, then I only need one user so one needs to go.
That's why I want to delete a user, because it's a 2nd me.One of me is bad enough no matter where or what it is,PC,Forum,or OS.

---

### Post by aysiu on 2006-09-06
You can always delete the /home/second_user directory manually with *gksudo nautilus*

If you don't mind using the command-line, you can always do ```
sudo deluser --remove-home second_user
```

---

### Post by nu2this on 2006-09-06
Thank you everybody I'll do just what was said. Maybe next time I'll ask before I do stupid things.;)

---

### Post by curuxz on 2006-09-06
I have a root account switched on al my pc's

Maybe its because im a bit 'old skool' when I come to my users management but Root is perfectly safe in my mind so long as you dont act like a spaz while logged in as root:

Strong password.
Only use it for admin not for running things
Local logins only
good firewall
antivirus.....lmao only kidding who needs antivirus in linux, fun to write it tho ;)

---

### Post by SoundMachine on 2006-09-06
> **curuxz said:**
> I have a root account switched on al my pc's

Maybe its because im a bit 'old skool' when I come to my users management but Root is perfectly safe in my mind so long as you dont act like a spaz while logged in as root:

Strong password.
Only use it for admin not for running things
Local logins only
good firewall
antivirus.....lmao only kidding who needs antivirus in linux, fun to write it tho ;)

Yes, root is perfectly safe if you don't use if you don't use it for tasks such as surfing the web, opening unknown files, installing or running unverified applications.

The firewall is IP-Tables, it's the ruleset that can be less or more secure.

ClamAV is optional but since it's a good AV i don't really see any benefit of not having it, especially if you share anything with any Windows box, ever burn things that will be distributed to Windows boxes or dualboot.

---

