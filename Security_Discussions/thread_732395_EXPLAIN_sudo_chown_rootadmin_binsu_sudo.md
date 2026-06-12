---
title: "EXPLAIN: sudo chown root:admin /bin/su sudo"
date: 2008-03-22
forum: Security Discussions
---

### Post by MountainX on 2008-03-22
Please explain to me the security benefits of this command:
```

sudo chown root:admin /bin/su sudo
```

is recommended several places, including here:
[http://www.itsecurity.com/features/u...tall-resource/](http://www.itsecurity.com/features/u...tall-resource/)

right now it looks like /bin/su has owner and group of root root

how will changing group to admin help? Is that what the above command actually does?

And what is the "sudo" token on the end of the command for?

Thanks

---

### Post by kevdog on 2008-03-22
What are your crediantials on the sudo command?

---

### Post by MountainX on 2008-03-22
kevdog - not sure. How do I find out?

BTW, I like your avatar image. That's something I might know more about than Ubuntu at the moment.

---

### Post by kevdog on 2008-03-22
That's a very generic om.  Hard to find good om avatars.

do this
sudo updatedb <----wait for what seems like ever
locate sudo

Then when it gives you the location
lsmod -la /........./sudo    <----..... means fill this part in

---

### Post by MountainX on 2008-03-22
> **kevdog said:**
> 
do this
sudo updatedb <----wait for what seems like ever
locate sudo

Done
I got a long list, but the line I think I need says:
/usr/lib/sudo

> **kevdog said:**
> 

Then when it gives you the location
lsmod -la /........./sudo    <----..... means fill this part in

lsmod -la /usr/lib/sudo gives this:
Usage: lsmod

It acts like it doesn't take parameters or arguments

---

### Post by kevdog on 2008-03-23
sorry, its not lsmod, simply ls

I dont think its going to be in /usr/lib but rather /usr/bin

---

### Post by Dr Small on 2008-03-23
```
drsmall@darkghost:~$ whereis sudo
sudo: **/usr/bin/sudo** /usr/lib/sudo /usr/X11R6/bin/sudo /usr/bin/X11/sudo /usr/share/man/man8/sudo.8.gz

```

And then:
```
drsmall@darkghost:~$ ls -la /usr/bin/sudo
-rwsr-xr-x 1 root root 91508 2006-10-09 07:37 /usr/bin/sudo
```

Also, speaking of avatars.... :D

---

### Post by kevdog on 2008-03-23
DS

what happened to your PI avatar?  Or what did they call them back in the 50's -- dics?? short for detective in case anyone wants to report me!

---

### Post by MountainX on 2008-03-23
> **kevdog said:**
> What are your crediantials on the sudo command?

-rwsr-xr-x 2 root root 107776 ...

---

### Post by MountainX on 2008-03-23
The full command is:
```
sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su
```

Is that actually this, if whitespace is fixed?
```
sudo chown root:admin /bin/su 
```
```
sudo chmod 04750 /bin/su
```

I got this from the following security guide I've been using:
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

When the command is broken up into two lines it seems to make more sense. 
Sudo is given an owner of root and a group of admin. 
Then the permissions are root=read, admin=rwx, and others=rx

I'm not sure why the permissions aren't 04700. Why do others need any permissions? (And I'm not sure why the last 0 is needed.) 

I have also been reading:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by kevdog on 2008-03-23
Why did you want to do this in the first place?

---

### Post by Dr Small on 2008-03-23
> **kevdog said:**
> DS

what happened to your PI avatar?  Or what did they call them back in the 50's -- dics?? short for detective in case anyone wants to report me!
I hate changing avatars, but I thought that one would suit me better, since it is me ;)

---

### Post by MountainX on 2008-03-23
> **kevdog said:**
> Why did you want to do this in the first place?

I wanted to do it because it was recommended in the security article (link posted above). However, I don't want to do it until I understand the effect, which I still don't.

---

### Post by kevdog on 2008-03-23
Im a little confused my self to tell you the truth.  This is the first time Ive heard about this strategy.

---

