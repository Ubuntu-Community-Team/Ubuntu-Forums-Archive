---
title: "apparmor profile for sshd"
date: 2009-03-28
forum: Security
---

### Post by treymul on 2009-03-28
Hey guys, I have been trying to set up an apparmor profile for sshd.  I thought it was going fine, but I am having problems now. I keep getting these complaints and I don't know how to fix them.

```
Mar 28 18:14:25 XXXX-desktop kernel:  audit: type=1502 operation="file_mmap" requested_mask="::mr" denied_mask="::mr" name="/lib/libncurses.so.5.6" pid=6792 profile="null-complain-profile" namespace="default"
```

I am getting these for numerous files that I have already given sshd read rights to.  I think it has something to do with the pid or profile, but I don't know what.  

Any help would be appreciated.

---

### Post by bodhi.zazen on 2009-03-28
Those errors mean sshd wants to map those libs, in addition to read.

So, in your ssh profile, add (change) to :

```
/lib/libncurses.so.5.6 mr,
```

and on.

Then restart apparmor and restart sshd

You might also want to put the profile into enforce, it is working ?

If things are working the way I like I do not try to eliminate all the messages aa throws.

---

### Post by treymul on 2009-03-28
Thanks, that got it working.  Now I've just got some fine tuning left.

---

### Post by treymul on 2009-03-28
Now I am trying to get rid of this message when I ssh into that machine:

```
/usr/bin/X11/xauth:  timeout in locking authority file /home/xxxx/.Xauthority
```

---

### Post by bodhi.zazen on 2009-03-28
Probabably :

@{HOME}/* r,
@{HOME}/* r,

but you may wish to be more restrictive or deny access to some things in home :

@{HOME}/.Xauthority 

It will depend on your version of Ubuntu as the version and options for aa vary across versions of Ubuntu. 

It helps if you post the full message you are getting, as in your first example.

---

### Post by treymul on 2009-03-28
Here is the entire message, but keep in mind this is not logged by apparmor, this is the error i get on the machine that is logging into the one running apparmor:

```
To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
You have mail.
Last login: Sat Mar 28 21:37:57 2009 from 192.168.1.1
/usr/bin/X11/xauth:  timeout in locking authority file /home/XXX/.Xauthority
user@desktop:~$  
```

---

### Post by bodhi.zazen on 2009-03-28
Oh, I see.

Try 

@{HOME}/.Xauthority r,

or the more general 

@{HOME}/ r,
@{HOME}/** r,

or even more general, especially w/ home directories :

@{HOME}/ rw,
@{HOME}/** rw,

I find it helps to follow the log while debugging :

tail -F /var/log/messages

---

### Post by treymul on 2009-03-28
Well the @ gave me errors when I restarted apparmor, so I added:

```
/home/*/* rw,
/home/*/** rw,

```

but that didn't fix it either, I still get the error.  It doesn't seem to be affecting anything though, I can still do what I want, it's just irritating seeing the error.

---

### Post by bodhi.zazen on 2009-03-29
If it is not broken, don't fix it ;)

As an aside, now that you mention it, I do not think apparmor likes the . in .Xauthority

Try @{HOME}/.Xauthority r,

And what error are you getting with that in the apparmor profile for sshd ?

---

### Post by treymul on 2009-03-29
Yeah, I tried that, but didn't work.  Apparmor is not logging any complaints, just the error on the other machine.

---

