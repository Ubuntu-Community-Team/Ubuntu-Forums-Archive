---
title: "Server security - hide /etc?"
date: 2007-03-14
forum: Server Platforms
---

### Post by Steve Smith on 2007-03-14
I'm about to give remote access to my webserver over ssh.  Would it be good practise to somehow hide /etc (and possible some other directories) from those users?  I know that anything critical will be chmoded 600 anyway, but I can't help but think it'd be better to hide the lot.

I've thought about changing the group of /etc, but would that give read problems for some programs?

---

### Post by Frosty Cold Drink on 2007-03-14
> **Steve Smith said:**
> I'm about to give remote access to my webserver over ssh.  Would it be good practise to somehow hide /etc (and possible some other directories) from those users?  I know that anything critical will be chmoded 600 anyway, but I can't help but think it'd be better to hide the lot.

I've thought about changing the group of /etc, but would that give read problems for some programs?

Do not attempt to hide /etc or change the group. Everything that is really sensitive should have already been stripped of world read permissions as you mention. If you are worried about giving someone SSH access, you can always set up a chroot enviornment for them, if its practical.

The web hosting control panel I use does this quiet effectively.

---

### Post by Steve Smith on 2007-03-14
chroot won't catch SFTP, will it?  As in, sign in with an FTP program which doesn't result in a command line.

What about a file mask, like samba's "veto files = "?  I can't find anything like that for SSH, but is there?

---

### Post by Frosty Cold Drink on 2007-03-14
> **Steve Smith said:**
> chroot won't catch SFTP, will it?  As in, sign in with an FTP program which doesn't result in a command line.

What about a file mask, like samba's "veto files = "?  I can't find anything like that for SSH, but is there?

It will work for SFTP and SCP too.

What SSH does start a regular command shell on the serving machine, and attaches that to the remote client. Trying to protect things that happen over a SSH connection would actualy involve messing with the shell, be it bash or whatever.

---

### Post by Steve Smith on 2007-03-24
Thanks, I'll look into chroot then!  Though in hindsight I'd prefer a solution that will work at the machine as well as via SSH.

---

### Post by Mr. C. on 2007-03-24
Steve,

Unless you really understand the security implications of chroot, I would advise against this approach.  You gain very little, and your efforts are better suited at understanding basic Unix/Linux security.

Before embarking on implementing a security mechanism, it is important to identify what you want to allow, and what you don't.   Do you have a set of defined programs or access you want to allow? You are giving access to people - but for what purpose?

Perhaps you can clarify a bit more.

MrC

---

### Post by Steve Smith on 2007-03-24
Thanks for the advice!

I've set up a web and email server, and have begun to host friends' websites on there.  Although I know I can trust them not to deliberately cause any harm, I can't control their password habits.  So I'm working on assuming that a stranger could gain ssh access using one of their passwords, and if that happens I don't want to give away any files/information that would aid them in hacking the server.

I realise this is possibly over cautious, but I thought it would be a good opportunity to learn a thing or two about security!

---

### Post by Mr. C. on 2007-03-24
I applaud your desire to be secure and safe.

Consider giving your friends a restricted shell such as rbash.  This will allow you to control what they can do.  Beware that chroot or rshell can still be circumvented with the proper techniques, so it is important to know how to minimize risk.  If its inadvertent screw-ups you are concerned about most, a restricted shell where you manage the user's environment should be sufficient.  Check the bash man page, searching for rbash to learn more about its limitations and controls.

MrC

---

### Post by Steve Smith on 2007-03-24
rbash sounds worth remembering about, though I can't find anything in the bash man page that suggests it'll restrict file access.  I can't disable cd completely.  Any thoughts?

---

### Post by Frosty Cold Drink on 2007-03-24
> **Mr. C. said:**
> ... Beware that chroot or rshell can still be circumvented with the proper techniques, so it is important to know how to minimize risk...

So long as root isn't around, there isn't too much to worry about. Well, root or suid root binaries, but having those lying around is just silly anyway (except for the regular few)

---

### Post by Mr. C. on 2007-03-25
What do mean "there's no root around".  In chroot environments improperly configured, one can create their own mini-environment, defeating the system accounts.

MrC

---

### Post by Frosty Cold Drink on 2007-03-25
> **Mr. C. said:**
> What do mean "there's no root around".  In chroot environments improperly configured, one can create their own mini-environment, defeating the system accounts.

MrC

Improperly configured is improperly configured, and there is always going to be something that goes wrong. But so long as no one can wield the power of root inside teh chroot enviornment, they can't get out. And if they can't get out, any damage is contained. Isnt that the point of chroot in the first place?

---

### Post by elst on 2007-03-25
> **Steve Smith said:**
> So I'm working on assuming that a stranger could gain ssh access using one of their passwords, and if that happens I don't want to give away any files/information that would aid them in hacking the server.


If possible, require key-based authentication for SSH, and don't allow access by password. SSH services running on the standard port are *really* heavily targetted these days. 

I haven't played with it yet, but Edgy has a package for "scponly", which claims to provide a restricted shell, so that you can allow users to manage files over SSH without having full login access:

[http://sublimation.org/scponly/wiki/index.php/Main_Page](http://sublimation.org/scponly/wiki/index.php/Main_Page)

One of the biggest risks with Web servers is actually the Web sites themselves. PHP is notorious, partly because it's easy to write PHP code that has security flaws. If the users are going to upload ready-made Web applications like blogs or image galleries  then it's a good idea to investigate the security history of the software, and either recommend good-quality products, or even install them yourself, to avoid configuration errors.

---

### Post by Steve Smith on 2007-03-25
> **elst said:**
> If possible, require key-based authentication for SSH, and don't allow access by password. SSH services running on the standard port are *really* heavily targetted these days.

Hmmm, I've thought about that but I'd rather not.

> **elst said:**
> I haven't played with it yet, but Edgy has a package for "scponly"

That sounds quite good, but "This would mean users with this shell can neither login interactively or execute commands remotely. They can however, scp files in and out, governed by the usual unix file permissions." - and I want them to have a propper command line and have access to all the (non-root) utilities on the server (eg nano, whois).

> **elst said:**
> 
One of the biggest risks with Web servers is actually the Web sites themselves.


Mmm, thanks for the warning, definitely something to watch out for.

---

### Post by elst on 2007-03-25
> I want them to have a propper command line and have access to all the (non-root) utilities on the server (eg nano, whois).

The standard file permissions are pretty good, but you could easily tighten things up even more by doing a minimal install into a virtual machine, and then just removing packages until you have a really small tailored system that you are happy with. You can then clone the original VM, and split accounts between VMs if you wish.

AIDE monitors system files and directories for alterations, so is particularly useful for small systems that don't change much.

---

