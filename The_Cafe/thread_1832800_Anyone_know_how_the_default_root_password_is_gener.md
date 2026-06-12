---
title: "Anyone know how the default root password is generated in Ubuntu?"
date: 2011-08-25
forum: The Cafe
---

### Post by ninjaaron on 2011-08-25
I've been using Ubuntu for a few years, happily typing sudo or gksu for any of my administrative tasks, never thinking much about my root profile.

I've recently installed Arch and Gentoo a few times and discovered the convenience of logging into a root shell for doing heavy, maintenance-related activities.  I fully understand the risks involved and don't do this regularly, and I normally only have it in a terminal or a TTY (since messing with the contents of your home folder with root privilages creates a permissions nightmare when you log back into your profile).

So, I was creating a new partition table and directory structure in Ubuntu, and I thought, "Hey, this would be much better with a root shell."  I attempted to login as root using my password, and discovered that this was not the root password.  I used... some commands that are not allowed to passed along on the Ubuntu message board (seriously.  I almost got bant from the #ubuntu IRC channel because I was going to tell a guy)... and I changed the root password, logged in as root, did my business, etc, etc, /etc/fstab, and all is well.

This got me wondering, where does the default root password in Ubuntu come from.  I guess it must be randomly generated at install or something, being that having a set default would be a major security problem, but I haven't a clue what goes into that.  It kinda bugs me that a Linux system, based on the ideology of empowering the user, doesn't allow you to set the root password durring the install, but I guess it makes sense, given the target audience.

So what's up?

---

### Post by SeijiSensei on 2011-08-25
Root has no password at all in Ubuntu; that's the essence of using sudo for everything.  If you look (as root) at /etc/shadow on a default installation, you'll see there is no password entry for the root user.

---

### Post by gutterslob on 2011-08-25
[Edited]

Nevermind.

---

### Post by sisco311 on 2011-08-25
The root account password is locked by default: [uhelp]community/RootSudo[/uhelp]

More precisely the encrypted password is: !

See: **man passwd** and **man 5 shadow**.

---

### Post by F.G. on 2011-08-25
hey, i've found that if you start-up into repair mode. and then go down to 'start with root command prompt' then use startx you can start into root without entering any password at all. i don't know if this is a security hole or a design feature.

---

### Post by sisco311 on 2011-08-25
> **F.G. said:**
> i don't know if this is a security hole or a design feature.

This has been discussed many many times.

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue_Mode](https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue_Mode)

[thread=11161668]Physical access is root access[/thread]

---

### Post by Aquix on 2011-08-25
You can always change the sudo timeout in visudo..

---

### Post by haqking on 2011-08-25
> **F.G. said:**
> hey, i've found that if you start-up into repair mode. and then go down to 'start with root command prompt' then use startx you can start into root without entering any password at all. i don't know if this is a security hole or a design feature.


Supposed to be that way.

Physical access is root access.

Use least privilege at all times and dont let anyone have access to your machine if you are security conscious.

Security 101 ;-)

---

### Post by snowpine on 2011-08-25
This command will give you a "root shell" for system maintenance:

```
sudo -i
```

It's equivalent to using "su -" in a distro with a root password.

---

### Post by ninjaaron on 2011-08-25
> **F.G. said:**
> hey, i've found that if you start-up into repair mode. and then go down to 'start with root command prompt' then use startx you can start into root without entering any password at all. i don't know if this is a security hole or a design feature.Yeah, like everyone has already been hinting, anyone with a USB stick and physical access can pretty much do whatever they want to anyone's machine.  That's why a Live media of Ubuntu is so popular for fixing windows and Mac; it gives access to areas of the system that are normally sealed away. 

> **snowpine said:**
> This command will give you a "root shell" for system maintenance:

```
sudo -i
```

It's equivalent to using "su -" in a distro with a root password.

I just learned that recently, after I had changed my root password, but it is good to know.  I'll probably use that in the next install.

---

### Post by cgroza on 2011-08-25
I always use:
```

sudo su

```
to get a root shell.

---

### Post by ninjaaron on 2011-08-25
> **cgroza said:**
> I always use:
```

sudo su

```
to get a root shell.

That's how I changed the password.  I recently learned that you are theoretically not supposed to do this because it doesn't properly load the environment variables and makes some sort of mish-mash work environment.

"sudo -i" is the preferred way if you want to load the full root environment.  "sudo -s" is the way if you want to load a root shell but keep the normal variables of your user session.

Course, after changing the password, I can just use "su" strait up.

---

### Post by Thewhistlingwind on 2011-08-25
> **ninjaaron said:**
> 
Course, after changing the password, I can just use "su" strait up.

I always just used sudo -s.

(I forgot to use sudo when setting up fedora, so until my next install I'll just go ahead and use su.)

---

### Post by apollothethird on 2011-08-25
> **ninjaaron said:**
> That's how I changed the password.  I recently learned that you are theoretically not supposed to do this because it doesn't properly load the environment variables and makes some sort of mish-mash work environment.

"sudo -i" is the preferred way if you want to load the full root environment.  "sudo -s" is the way if you want to load a root shell but keep the normal variables of your user session.

Course, after changing the password, I can just use "su" strait up.

I don't think "su" straight up changes the environment to root.  I believe you have to use, "su -" to get to the root level with the root's environment.

On rare occasions I use "sudo su -".  But that's rare occasions.  I find the "sudo command" to suffice for making root changes to the whole system.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by ninjaaron on 2011-08-25
> **apollothethird said:**
> I don't think "su" straight up changes the environment to root.  I believe you have to use, "su -" to get to the root level with the root's environment.

On rare occasions I use "sudo su -".  But that's rare occasions.  I find the "sudo command" to suffice for making root changes to the whole system.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Could be.  I'm a newb at su.

---

### Post by snowpine on 2011-08-25
If you are a "newb at su" then why not just use 'sudo'? The main advantage to 'sudo,' of course, is that all of the Ubuntu help documentation and wiki is written with 'sudo' in mind. 

Nothing wrong with enabling a root password and using 'su' in my opinion, but you will be on your own in terms of help documentation and support on these forums.

---

### Post by ninjaaron on 2011-08-25
> **snowpine said:**
> If you are a "newb at su" then why not just use 'sudo'? The main advantage to 'sudo,' of course, is that all of the Ubuntu help documentation and wiki is written with 'sudo' in mind. 

Nothing wrong with enabling a root password and using 'su' in my opinion, but you will be on your own in terms of help documentation and support on these forums.

I didn't really think about it at the time.  I was doing a lot of admin, I tried to login to a root shell.  I couldn't.  The 'hacker instinct' of I'm-not-supposed-to-be-able-to-do-this-so-I-have-to-find-a-way kicked in, so I tried a couple of commands. They worked.

In the future, I will probably just use sudo -i, now that I know about it.  I'm sort of at this point in my "discovering console" where I'm just figuring what bash can really do, so I'm always challenging myself to see what I can get out of it with a new command or script, regardless of whether that goal is worthwhile or not.

Don't worry though. I have my most important files backed up on two computers and on the cloud, all other data backed up on an external hard-drive, my home folder on a separate partition, post-install scripts and logs for setup, and always a few live USB's handy.  

I've wrecked my system once or twice messing around, but at this point it's a matter of an hour or so to get everything back the way I like it.  Safety first.:lolflag:

---

