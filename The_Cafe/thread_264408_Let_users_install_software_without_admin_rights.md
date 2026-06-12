---
title: "Let users install software without admin rights"
date: 2006-09-24
forum: The Cafe
---

### Post by saracen on 2006-09-24
It makes sense on a multi-user system for individual users to be able to install software that does not require root priveleges to run, like an FTP program or a new game.  But with the current apt-get/deb system any software needs admin rights to install since the software gets put into the main filesystem.

Ubuntu should have some mechanism out-of-the-box that allows individual users to install software into their home directories.  And not by having to download the source and extract/compile it, but by double-clicking (like with debs).  And yes I do know about [Klik]("http://klik.atekon.de/").  I'm not sure if that is the right tool for the job, it may be.  In any case, I think we should propose this for Edgy+1, unless it's already been proposed somewhere?

---

### Post by prizrak on 2006-09-24
> **saracen said:**
> It makes sense on a multi-user system for individual users to be able to install software that does not require root priveleges to run, like an FTP program or a new game.  But with the current apt-get/deb system any software needs admin rights to install since the software gets put into the main filesystem.

Ubuntu should have some mechanism out-of-the-box that allows individual users to install software into their home directories.  And not by having to download the source and extract/compile it, but by double-clicking (like with debs).  And yes I do know about [Klik]("http://klik.atekon.de/").  I'm not sure if that is the right tool for the job, it may be.  In any case, I think we should propose this for Edgy+1, unless it's already been proposed somewhere?
Horrible idea. In a multiuser system the admin has to be the one who controls what users install on their system. As someone who been in a multiuser environment where people are allowed to install crap locally, I can tell you that those machines were screwed up. In a home user environment the admin is the "geek" of the house and is easily bugged to install something.

---

### Post by maniacmusician on 2006-09-24
Also, you can just set the sudo password to something that everyone will know, at least in a home environment, if most of the users are educated enough to not install random crap (which is harder to do on linux anyways). in a work or school environment, users shouldn't be able to install stuff, period.

---

### Post by aysiu on 2006-09-24
I agree with Prizrak.

If you think users should have the right to install software, add them to *admin* group. If you don't want to add them to the *admin* group, you obviously don't trust them to install software.

---

### Post by Kannisto on 2006-09-24
> **prizrak said:**
> Horrible idea. In a multiuser system the admin has to be the one who controls what users install on their system. As someone who been in a multiuser environment where people are allowed to install crap locally, I can tell you that those machines were screwed up. In a home user environment the admin is the "geek" of the house and is easily bugged to install something.

You can already just untar stuff in your home folder and run it from there. It's not so different with package management, just simpler for users (makes also uninstalling easier).

---

### Post by aysiu on 2006-09-24
But if you untar stuff in your home folder, it won't affect any of the other users--that's fine.

And there's no additional functionality that needs to be added for that. Just double-click the .tar.gz and it'll open with File-Roller or Ark and unzip.

Isn't there a way you can allow (through *sudo*) users to have access to Synaptic Package Manager and nothing else administrative?

---

### Post by mostwanted on 2006-09-24
I think it's an interesting concept.

Many Linux programs are modeled after the traditional UNIX concept of favouring absolute filepaths, they can't just be untared into you home directory. The program expects certain files to be in certain folders.

The solution would be to be able to install it in a hidden folder inside your home directory so that it looks like a "virtual" filesystem resembling / (like Klik does it). Not that I'd know how to think up or program something like that, but it's a concept at least.

---

### Post by prizrak on 2006-09-24
> **aysiu said:**
> But if you untar stuff in your home folder, it won't affect any of the other users--that's fine.

And there's no additional functionality that needs to be added for that. Just double-click the .tar.gz and it'll open with File-Roller or Ark and unzip.

Isn't there a way you can allow (through *sudo*) users to have access to Synaptic Package Manager and nothing else administrative?
Ubuntu has a nice little GUI for setting up certain permissions for users. Can't remember if it allows you something as granular as allowing to use a package manager. This being Linux however it's not all that difficult to work out sudoing permission for just one program. Not too sure if there is much of a point to doing that but it's possible.

---

### Post by Kannisto on 2006-09-24
> **aysiu said:**
> But if you untar stuff in your home folder, it won't affect any of the other users--that's fine.

And there's no additional functionality that needs to be added for that. Just double-click the .tar.gz and it'll open with File-Roller or Ark and unzip.

Isn't there a way you can allow (through *sudo*) users to have access to Synaptic Package Manager and nothing else administrative?

You can do it with visudo, but it's not very wise to let users mess with the systemwide software configuration.

I thought that OP meant users installing stuff into their home directory not into root. Package management would make things a lot easier, depedency handling, icons added into panel menus and binaries in ~/bin/ so that you could start them by typing their name. "user-get" should also have option to either allow software only from strict repositories or be freely configurable by the user.

---

### Post by xhaan on 2006-09-24
> **aysiu said:**
> Isn't there a way you can allow (through *sudo*) users to have access to Synaptic Package Manager and nothing else administrative?

I believe so.
I'm not an expert at setting up sudo but I think you set in the sudoers file a Cmnd_Alias with the path of synapitc, then allow the user to use that alias..

I think it would be something like..

Cmnd_Alias SYNAPTIC = /path/to/synaptic

and then this:

username    ALL = SYNAPTIC

(or "hostname = SYNAPTIC" or "hostalias = SYNAPTIC" where hostname/hostalias are their respective values)

---

### Post by jISh on 2006-09-24
Some programs install shared libraries and things to your root filesystem as well, so root authority is generally needed unless the program comes with all it's dependancies in it's own folder.

---

### Post by IYY on 2006-09-24
It's not a bad idea. This won't be a security risk, since the program will be installed locally, and won't be able to damage anything in the system (can only access the user's home folder). In fact, many games and closed source apps like Google Earth already allow this.

---

### Post by aysiu on 2006-09-24
I don't know if we have a common understanding about what is or isn't a "bad" idea.

There are several options:

1. Make these users administrators because you trust them to install/uninstall programs systemwide... and you trust them in general.

2. Find a way to allow them (through the /etc/sudoers file) to only install programs systemwide and not do other administrative tasks.

3. Allow them to install programs locally if they can figure out how to do so (working binaries like Firefox or Google Earth)--no point in discussing that possibility, since this is already the case in Ubuntu by default.

4. Create a localized *apt* where people can do package management of programs for themselves... uh, who's going to write that program?

The only thing I thought was a bad idea was giving administrative privileges to people you don't trust. You either trust them (give them the privileges) or you don't (don't give them the privileges).

---

### Post by TravisNewman on 2006-09-24
I think what the OP is saying, is give them rights to install software in their home directory through apt (or something else that's easy) that won't screw with the system. Like, say there's a public system without Firefox installed, and Joe wants to install Firefox. He can download a deb, and it will ask if he wants to install it per user or per system. Per system will ask for a password, per user will not. Firefox won't muck with anything system-wide unless you have admin access.

IMO, great idea.

---

### Post by saracen on 2006-09-24
I don't want to make users administrators because I don't want them to be able to mess with the system or install any software that could potentially damage the system.  However I do want them to be able to install things into their home directory.  Right now there is no "double-click" easy install mechanism for them to do this.  Sure you can download a tar.gz file if there are pre-compiled binaries (such as firefox), but this method is not really "installing" a program because you have to manually create the shortcut to it if you want it to appear in your menus.

What is envisioned here is a double-click method (like with gdebi) that allows you install pre-packaged programs.  In many cases the program's dependencies will already be installed system-wide and if that is the case, then it shouldn't be a problem.  The program can just extract itself in the user's home dir and create the appropriate user-specific menu shortcuts.  If it is the case that the program requires additional libraries, which would then require admin priveleges to install, then the user would need to get the administrator to agree to the install and install them.  Or it could pull down the dependencies (just like gdebi does) and install them locally in the user's home directory.  It's my understanding that you can modify the library load path with the LD_LIBRARY_PATH environment variable.

---

### Post by saracen on 2006-09-24
> **panickedthumb said:**
> I think what the OP is saying, is give them rights to install software in their home directory through apt (or something else that's easy) that won't screw with the system. Like, say there's a public system without Firefox installed, and Joe wants to install Firefox. He can download a deb, and it will ask if he wants to install it per user or per system. Per system will ask for a password, per user will not. Firefox won't muck with anything system-wide unless you have admin access.


That is exactly what I mean.

---

### Post by TravisNewman on 2006-09-24
klik does in fact work like that, however, I still haven't gotten it to work properly.

---

### Post by prizrak on 2006-09-24
> **panickedthumb said:**
> I think what the OP is saying, is give them rights to install software in their home directory through apt (or something else that's easy) that won't screw with the system. Like, say there's a public system without Firefox installed, and Joe wants to install Firefox. He can download a deb, and it will ask if he wants to install it per user or per system. Per system will ask for a password, per user will not. Firefox won't muck with anything system-wide unless you have admin access.

IMO, great idea.

Won't work under the current paradigm of software design for Linux. Linux programs take advantage of system wide shared libraries and it would be a huge pain in the *** to implement both the ability to read those libraries and link to them AND install into the home directory instead of /bin or /usr/bin. Also alot of programs use absolute paths so installing them into ~ would screw with the way they work. If programs are to use the Windows model where all of the dependencies come with the program itself (although with .Net being very popular that is changing) then you could install them into each users ~

---

### Post by Kannisto on 2006-09-25
> **prizrak said:**
> Won't work under the current paradigm of software design for Linux. Linux programs take advantage of system wide shared libraries and it would be a huge pain in the *** to implement both the ability to read those libraries and link to them AND install into the home directory instead of /bin or /usr/bin. Also alot of programs use absolute paths so installing them into ~ would screw with the way they work. If programs are to use the Windows model where all of the dependencies come with the program itself (although with .Net being very popular that is changing) then you could install them into each users ~

If that's the case we should definetely get rid of absolute paths and substitute them with $VARIABLE/path/names. Nothing is more annoying than having to deal with absolute paths when migrating / porting some system to different environment.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=5](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=5)

chroot would be one solution to this problem, but it isn't the very pretty.

---

