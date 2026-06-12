---
title: "Warning!!! *buntu can be run as root! (False alarm)"
date: 2007-11-17
forum: The Cafe
---

### Post by integr8e on 2007-11-17
*BINGO!!!  ALPHA!  BRAVO!  CHARLIE!  MAYDAY! MAYDAY!  HOUSTON, I THINK WE HAVE A PROBLEM!!!*

OK, I believe I have your attention now . . . I have found a bug that ***does allow*** users to run *buntu as root.  It is definitely a security issue and shortly after posting this thread I will create a bug report.

To run as root, all you have to do is exit KDM and run the following command from the terminal:
```
sudo startx
```

Be forewarned, this is ***NOT*** a good thing, as it allows any and all processes to run as root and do whatever they want to your system.  Not to mention that once you log out (or reboot) and log back in as a normal user, the permissions for most of your apps will have been changed to root only, rendering them useless to you unless you either run them as root (very bad idea) or manually change the permissions for hundreds of directories and files located in your /home directory (trust me, I know . . .).

---

### Post by zhaozhou on 2007-11-17
X will probably always be able to run as root, most people wont do it unless they know what they are doing.

Application settings will almost always be in users home directory, which is /root for root.

I don't think this will change, it will be hard for some people to run failsafe if the ubuntucommunity comes up with a script to replace the startx-binary.


Edit:
Most people thinking about running a server wont run X anyway, since its hazardous.

---

### Post by OoooMatron on 2007-11-17
> **integr8e said:**
> *BINGO!!!  ALPHA!  BRAVO!  CHARLIE!  MAYDAY! MAYDAY!  HOUSTON, I THINK WE HAVE A PROBLEM!!!*

OK, I believe I have your attention now . . . I have found a bug that ***does allow*** users to run *buntu as root.  It is definitely a security issue and shortly after posting this thread I will create a bug report.

To run as root, all you have to do is exit KDM and run the following command from the terminal:
```
sudo startx
```

Be forewarned, this is ***NOT*** a good thing, as it allows any and all processes to run as root and do whatever they want to your system.  Not to mention that once you log out (or reboot) and log back in as a normal user, the permissions for most of your apps will have been changed to root only, rendering them useless to you unless you either run them as root (very bad idea) or manually change the permissions for hundreds of directories and files located in your /home directory (trust me, I know . . .).

I don't get the problem. Firstly, a user has to be made a sudo user to run sudo, and as far as i know only the installation user is on the sudo list.

secondly, you have to enter a password for the sudo, so even if it was run on the sudo user account you'd need their password.

---

### Post by ToniVC1963 on 2007-11-17
> **OoooMatron said:**
> I don't get the problem.

Me neither... :confused: If you are able to run commands as root (that is you are a sudo user and know your parsword) you can do ANYTHING. You even could format your entire disk! Is this a bug?

---

### Post by OoooMatron on 2007-11-17
> **ToniVC1963 said:**
> Me neither... :confused: If you are able to run commands as root (that is you are a sudo user and know your parsword) you can do ANYTHING. You even could format your entire disk! Is this a bug?


yes i think the poster is trying to insinuate that ANYONE can kill X and type sudo startx to have a machine running purely as root. It's not true.

---

### Post by LowSky on 2007-11-17
Oh My God....... I'M SO FRIGHTENED!!!!



but seriously... this isn't a big deal! Most (99.9999%) users wouldn't try to run as Root anyway.

---

### Post by aysiu on 2007-11-17
How is this a security problem?

If someone wants to run as root on your system, all she has to do is boot into recovery mode.

---

### Post by jdong on 2007-11-17
This is not a problem:
(1) You must have sudo (root) access to perform this procedure
(2) Or you must have access to a physical recovery console.

Either way, the user effectively has root rights to begin with. Yes, you can do dangerous things on the system as root. Is that a vulnerability in the OS or the user?

---

### Post by Mr. Picklesworth on 2007-11-17
> or manually change the permissions for hundreds of directories and files located in your /home directory (trust me, I know . . .).

Hah, that's a fun experience! Just happened to me, actually. Something really needs to be done about logging in problems -- bullet-proof GNOME or something. It should not give up so easily with trivial little permissions issues, but rather offer to fix them. Especially with .dmrc, since GDM explicitly tells the user exactly what he should do. Why not just do it?!

---

### Post by aysiu on 2007-11-17
I've retitled the thread to include the phrase *false alarm*, because it is.

I don't want new users freaking out when they see this thread title.

There have been legitimate security problems in the past (like Breezy storing the admin password in a plain text file). This is not one of them.

---

### Post by init1 on 2007-11-17
I don't think that's really an issue. An easier way to login as root is
```

sudo passwd root

```
and then just login with root as the username and the password that you set. I do realize that it's far more dangerous than logging in as a normal user, but I do it anyway since it's more convient and I don't have to worry about permissions, or running apps in the wrong user.

---

### Post by jdong on 2007-11-17
Please DO NOT suggest running the entire system as root, or even setting passwords on the root account. This behavior is extremely dangerous and openly invites your system to be hacked and used as a zombie over your web browser or any other networking application you use that has had a history of security exploits. Worse people are probably running Java and Flashplayer, both of which grant anonymous virtual machine like access to run any code they want in your browser without even a prompt, and there are bound to be vulnerabilities in their sandboxes.

---

### Post by undine on 2007-11-17
This isn't news to me. When I introduced my uncle, who is a Linux user from way-back and quite accustomed to running everything as root (he knows that it's wrong, but it's what he's used to), it took him about 2 minutes to run Ubuntu as root.

---

### Post by p_quarles on 2007-11-17
> **jdong said:**
> Please DO NOT suggest running the entire system as root, or even setting passwords on the root account.
While running the system, or even just the web browser, as root is dangerous (and completely pointless), setting a root password is no more dangerous than having an account with root privileges via sudo. They're both as secure as the password is good.

---

### Post by n3tfury on 2007-11-17
hey, where'd the OP disappear to

---

### Post by jdong on 2007-11-17
> **p_quarles said:**
> While running the system, or even just the web browser, is dangerous (and completely pointless), setting a root password is no more dangerous than having an account with root privileges via sudo. They're both as secure as the password is good.

The fundamental assumption though is that the password is good. And from what I've seen I honestly don't think 90% of people have the capacity to maintain one good password, much less two.

Also, setting a root password typically suggests the user is going to be overusing root privs.

---

### Post by Linuxratty on 2007-11-17
> **ToniVC1963 said:**
> Me neither... :confused: If you are able to run commands as root (that is you are a sudo user and know your parsword) you can do ANYTHING. You even could format your entire disk! Is this a bug?

 Peter van der Linden wrote:
"The "don't run as root" mantra dates from the days of
timesharing servers. When you run on a single user PC, your
most valuable resource is your data, not the integrity of
the system.

If your system is compromised, the attacker can do all the
things he wants to do in your user account, equally well as
a root account (store files, send spam, run zombie
software). Being or not being root doesn't hinder him at
all.

On a server it is bad to be root all the time because a
mistake by you could affect many other people. On a single
user PC behind a firewall there is no compelling reason not
to run as root."

---

### Post by p_quarles on 2007-11-17
First of all, there are many things a non-root user cannot do. Altering the startup sequence and modifying log files being two of the more significant ones. So, yes, you could make a shell script run once, and send a few spams. You couldn't get it to boot with the computer, though, and you couldn't cover your tracks. 

Beyond that, the real point is that running all apps as the root user (particularly apps that communicate with any potentially hostile URL) makes it much more likely that your system will be compromised in the first place. Don't do it.

---

### Post by integr8e on 2007-11-17
> Please DO NOT suggest running the entire system as root, or even setting passwords on the root account. This behavior is extremely dangerous and openly invites your system to be hacked and used as a zombie over your web browser or any other networking application you use that has had a history of security exploits. Worse people are probably running Java and Flashplayer, both of which grant anonymous virtual machine like access to run any code they want in your browser without even a prompt, and there are bound to be vulnerabilities in their sandboxes.

This is exactly my incentive as to why I posted this; this *is* a security issue from that perspective, but not from the aspect that *anybody* can login as root.

---

### Post by p_quarles on 2007-11-17
> **integr8e said:**
> This is exactly my incentive as to why I posted this; this *is* a security issue from that perspective, but not from the aspect that *anybody* can login as root.
It's not a security issue. You just don't type "sudo startx" and you're fine. Calling this a "bug" is like calling a kitchen knife a weapon.

---

### Post by integr8e on 2007-11-17
> Calling this a "bug" is like calling a kitchen knife a weapon.

Almost everything is conditional, it all depends on how it's used . . .

---

### Post by arvevans on 2007-11-17
The sky is falling!  The sky is falling!  and  Warning!!! *buntu can be run as root!

I noticed that the initiator of this "alarm" stayed out of the discussion for quite a while while she lurked in the background,  probably laughing at all the comments that her posting elicited. ** You have been had!**
_._

---

### Post by jrusso2 on 2007-11-17
> **jdong said:**
> Please DO NOT suggest running the entire system as root, or even setting passwords on the root account. This behavior is extremely dangerous and openly invites your system to be hacked and used as a zombie over your web browser or any other networking application you use that has had a history of security exploits. Worse people are probably running Java and Flashplayer, both of which grant anonymous virtual machine like access to run any code they want in your browser without even a prompt, and there are bound to be vulnerabilities in their sandboxes.

When I stared using Linux it had a root account.  I always make a root account on Ubuntu.

I don't log into it often but I like to have it there if I need it.

I have not had any problems doing this.  All this root nonsense is hysteria.. If people are dumb enough to screw something up they can certainly do it with sudo.

Its their computer and if they want to do something as root whats the issue?

---

### Post by p_quarles on 2007-11-17
Absolutely, and that's my point. A kitchen knife *can *be used as a weapon. That's not a valid reason to replace them with safety scissors. 

There are numerous ways in Linux to gain a root shell, run applications as the root user, or run the entire system as the root user. That's not a bug -- it's just something you shouldn't do unless you know what you're doing and have a specific reason for it.

---

### Post by integr8e on 2007-11-17
> I noticed that the initiator of this "alarm" stayed out of the discussion for quite a while while she lurked in the background, probably laughing at all the comments that her posting elicited.  You have been had!

Actually, I just got up-and-running again shortly before replying to this thread because this experiment (I used an external hdd I had and installed Kubuntu on it) somehow fragged my GRUB entry on my main /boot partition (even though it wasn't mounted during the operation).  I have not had any good experiences with this command.

> Absolutely, and that's my point. A kitchen knife can be used as a weapon. That's not a valid reason to replace them with safety scissors. 

No, but the danger and grave potential is there to do harm.

> There are numerous ways in Linux to gain a root shell, run applications as the root user, or run the entire system as the root user. That's not a bug -- it's just something you shouldn't do unless you know what you're doing and have a specific reason for it.

I agree, this method is just a little *too* easy to perform.  I learned this the hard way after repairing my video driver from the terminal; I had been using "sudo" a lot and absent-mindedly entered "sudo startx", which was very problematic and resulted in me just reinstalling the whole thing.

---

### Post by arvevans on 2007-11-17
Sudo is there so that the system administrator (usually you) does have the option of fixing things that go wrong.  There is, or should be,  the assumption that the Sudo password will be limited to the knowledgeable person who manages that particular computer.

If you have system users who are not safe to have Sudo permissions, then you simply build them their own ID and password, and do not give them Sudo capability by not telling them the Sudo password.

Sometimes we forget that Linux, UNIX, and all the other - - IX's out there are industrial strength computing platforms, with capability for multi-user support, distributed networking, remote administration, and security management for a truly  multi-user environment.  If you are the System Administrator, then you do have access to powerful commands, including Sudo.
_._

---

### Post by integr8e on 2007-11-17
True, but it's not the computer's ***normal*** users I'm worried about . . .

If you manage to accidentally login to root mode (like me), you are setting yourself up for some potentially debilitating consequences (not just with your hardware, but financially and otherwise).

---

### Post by jdong on 2007-11-17
> **jrusso2 said:**
> 
I have not had any problems doing this.  All this root nonsense is hysteria.. If people are dumb enough to screw something up they can certainly do it with sudo.

Its their computer and if they want to do something as root whats the issue?

It's two fold. First of all, sudo puts you into a mentality of "I am doing this with escalated access" every time you access it.

Secondly, sudo logs all the actions being performed, who performed it, and what time it was performed, for easy auditing later on.

I used to do some work at a *nix support firm and one of the basic policies in the support contract was that there's additional support charges if the client bypassed sudo in any way (no, we didn't use Ubuntu, we specifically set up all our *nix setups with sudo), because it made our work so much harder to diagnose exactly what they broke.


There is definitely, even on a single user system, clear differences to what one can do as root and what one can do as a regular user. A tainted user account is **trivially** simple for an experienced adminstratrator to identify. There are only a few places that something can hide. However, if there is a chance root access could've been gained, now you've got a serious problem on your hands...  Were any binaries replaced with rootkitted versions? How about kernel modules inserted? Could paravirtualization or a kernel-level rootkit be disguising everything you see on the system?

Bottom line is even under a single-user system, doing everything as root is still a bad idea. Is doing anything and everything under a limited user account safe? of course not! As noted, you can seriously damage your own data, and that could be just as disastrous as your entire system being compromised.

---

### Post by mojoman on 2007-11-18
> **integr8e said:**
> Not to mention that once you log out (or reboot) and log back in as a normal user, the permissions for most of your apps will have been changed to root only, rendering them useless to you unless you either run them as root (very bad idea) or manually change the permissions for hundreds of directories and files located in your /home directory (trust me, I know . . .).

Why on earth would this happen? I have a root account that I fire up using startx every now and then (or through slim when I used that), especially if I had a lot of settings to do, and **NEVER** has this changed **ANY** permissions under Ubuntu or Debian.

---

### Post by red_Marvin on 2007-11-18
> **integr8e said:**
> True, but it's not the computer's ***normal*** users I'm worried about . . .

If you manage to accidentally login to root mode (like me), you are setting yourself up for some potentially debilitating consequences (not just with your hardware, but financially and otherwise).

***Normal*** users do not have sudo access (and cannot log into root mode), only the admin does, and the admin is supposed to know what [s]he does, before running anything with sudo.

---

### Post by n3tfury on 2007-11-18
> **integr8e said:**
> True, but it's not the computer's ***normal*** users I'm worried about . . .

If you manage to accidentally login to root mode (like me), you are setting yourself up for some potentially debilitating consequences (not just with your hardware, but financially and otherwise).

wth

---

### Post by init1 on 2007-11-18
Am I just ignorant or is logging in as root not that big of a deal? If I login as the user, I'm constantly doing
```

mount /dev/something /mnt

```
and then correcting myself with
```

sudo mount /dev/something /mnt

```
It gets very annoying. Plus, if I do a 
```

su

```
just to make things easier, I'm bound to run an app and then have to close it, go back to user, and run it again so that I have the settings of the user account. If it really is such a serious issue, I may decide to cope with the inconvenience

---

### Post by PriceChild on 2007-11-18
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) is the official Ubuntu stance on root and sudo.

I do not believe that it is appropriate for the minority to be advocating the potentially very dangerous use of continual root in such a public forum.

You are free to make your own decision, and use root constantly, but don't come crying back here for support when you break something because you "didn't mean to press that" or "thought it'd give me a confirmation".

---

