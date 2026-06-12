---
title: "name of home and user folder."
date: 2012-05-14
forum: The Cafe
---

### Post by spiritech on 2012-05-14
should the home folder in the file system be renamed user or users.
then be given a choice to name your "home" as home or your user name. just thought it would help with eliminating having a path called /home/home/

that way it would become /user/home/ or /user/"your user name"/

spiritech

---

### Post by carl4926 on 2012-05-14
I think you may be a little confused
Try pressing Ctrl+L and look at the path again

---

### Post by Copper Bezel on 2012-05-14
No, he's not talking about the way it's presently arranged. He's saying that "user" or "users" would be a more accurate description than "home." OSX actually uses something like "users" for the same folder, doesn't it?

---

### Post by aysiu on 2012-05-14
The way Windows 7 does it is *C:\Users* is where the users are and then *C:\Documents and Settings* is a symlink (or shortcut) to *C:\Users*.

Ubuntu could make it so that */users* is where the users are and then */home* is a symlink to */users*.

---

### Post by carl4926 on 2012-05-14
> **Copper Bezel said:**
> No, he's not talking about the way it's presently arranged. He's saying that "user" or "users" would be a more accurate description than "home." OSX actually uses something like "users" for the same folder, doesn't it?

OK
I was a little unsure
I though maybe he meant
[[IMG]http://thumbnails73.imagebam.com/19014/74faf4190133099.jpg[/IMG]](http://www.imagebam.com/image/74faf4190133099)

---

### Post by carl4926 on 2012-05-14
> **aysiu said:**
> The way Windows 7 does it is *C:\Users* is where the users are and then *C:\Documents and Settings* is a symlink (or shortcut) to *C:\Users*.

Ubuntu could make it so that */users* is where the users are and then */home* is a symlink to */users*.
Yuck and more yuck
Windows file system is a complete mess IMO

---

### Post by zombifier25 on 2012-05-14
> **carl4926 said:**
> Yuck and more yuck
Windows file system is a complete mess IMO

Agree. On Windows I don't know what folders do backup because software configs is thrown randomly everywhere. On Linux, backup the home folder and bam! you're good.
And this is only one example.

---

### Post by mcduck on 2012-05-14
> **spiritech said:**
> should the home folder in the file system be renamed user or users.
then be given a choice to name your "home" as home or your user name. just thought it would help with eliminating having a path called /home/home/

that way it would become /user/home/ or /user/"your user name"/

spiritech

Wouldn't that break pretty badly if you actually have more than one user? ;) Only one of them would have the option to call his home directory "home" while all the others would still have to use their actual usernames instead...

---

### Post by Bandit on 2012-05-14
> **carl4926 said:**
> Yuck and more yuck
Windows file system is a complete mess IMO

I hate windows file system.

Linux FS is fine the way it is. It may not be perfect, but dear god at least I can find what I am looking for.

---

### Post by spiritech on 2012-05-16
> **carl4926 said:**
> OK
I was a little unsure
I though maybe he meant
[[IMG]http://thumbnails73.imagebam.com/19014/74faf4190133099.jpg[/IMG]]("http://www.imagebam.com/image/74faf4190133099")

this is exactly what i was talking about.

---

### Post by spiritech on 2012-05-16
> **mcduck said:**
> Wouldn't that break pretty badly if you actually have more than one user? ;) Only one of them would have the option to call his home directory "home" while all the others would still have to use their actual usernames instead...

i am sure people could navigate to a folder named by there user name instead of home.

---

### Post by forrestcupp on 2012-05-16
First of all, it would be confusing, because we already have a /usr folder.

> **aysiu said:**
> The way Windows 7 does it is *C:\Users* is where the users are and then *C:\Documents and Settings* is a symlink (or shortcut) to *C:\Users*.

Ubuntu could make it so that */users* is where the users are and then */home* is a symlink to */users*.That's actually not a bad idea to help Windows converts. But I think it would be more compliant with standards to make /users link to /home. I think it's probably better for people to learn about how Linux is different, though.

> **spiritech said:**
> this is exactly what i was talking about.
If that's what you're talking about, then you're just confused by how Nautilus shows things. The directory is not actually /home/home. The first "home" that Nautilus shows is the actual /home folder. The next "Home" that Nautilus shows is just what Nautilus chooses to display as your current user's /home folder, and the actual folder name is your username. It's kind of confusing that it does that, but no matter what your username is, it would show up as "Home" right there in Nautilus. So it's a Nautilus problem, not a Linux filesystem problem.

---

### Post by zombifier25 on 2012-05-16
Actually, IMO it will not help Windows convert. Linux's file system structure is very different from Windows and trying to change it wouldn't narrow the differences down, it only makes the current situation more difficult. (usr and user. Seriously?)
If they want to use Linux, they have to learn Linux first. Linux's goal is not to be a Windows' replacement, and we have to accept that.

---

### Post by llua+ on 2012-05-16
> **carl4926 said:**
> Yuck and more yuck
Windows file system is a complete mess IMO
Sloppy? Yep. but ensures backwards compatible with programs that expect the folder. Very similar to the /usr merge thats going on in linux at this very moment in [fedora]("http://fedoraproject.org/wiki/Features/UsrMove"), [opensuse]("http://en.opensuse.org/openSUSE:Usr_merge") etc. symlinks and all.

---

### Post by SlackerD on 2012-05-16
> **Bandit said:**
> I hate windows file system.

Linux FS is fine the way it is. It may not be perfect, but dear god at least I can find what I am looking for.

Which fileystem?

---

### Post by carl4926 on 2012-05-16
> **llua+ said:**
> Sloppy? Yep. but ensures backwards compatible with programs that expect the folder. Very similar to the /usr merge thats going on in linux at this very moment in [fedora]("http://fedoraproject.org/wiki/Features/UsrMove"), [opensuse]("http://en.opensuse.org/openSUSE:Usr_merge") etc. symlinks and all.
Yes I know about this.

I'm not a windows user, but my visits there have proved frustrating, as much on the user side as the system
Eg; finding the equivalent of .mozilla
Got there in the end :D

---

### Post by Copper Bezel on 2012-05-16
Blah. If we're talking about user data, there's still the half of Linux apps that store things in .config/whatever and .local/share/whatever instead of .whatever. Or do both, so that you think you've cleared or backed up your user data but haven't really.

---

### Post by spiritech on 2012-05-16
> **forrestcupp said:**
> First of all, it would be confusing, because we already have a /usr folder.

yes that would be confusing i did not realize there was already a /usr. folder.


> **forrestcupp said:**
> If that's what you're talking about, then you're just confused by how Nautilus shows things. The directory is not actually /home/home. The first "home" that Nautilus shows is the actual /home folder. The next "Home" that Nautilus shows is just what Nautilus chooses to display as your current user's /home folder, and the actual folder name is your username. It's kind of confusing that it does that, but no matter what your username is, it would show up as "Home" right there in Nautilus. So it's a Nautilus problem, not a Linux filesystem problem.

thats probably the point i was trying to make. it would be nice if nautilus would call your "home" folder your user name, or  at least, thats my preference anyway. i dont find it confusing, just a little annoying. maybe there is a way of changing in the gconf or dconf without editing the source. i think i will have a poke around a bit and find out.

---

### Post by smellyman on 2012-05-16
lesson one:

"/home   This is where users keep their personal files. Every user has their own directory under /home"

"ok, understood"



it's really not daunting or confusing to anybody.  If it is, then good luck teaching them anything else about OS's and applications.....it will be a very bumpy ride.

---

### Post by aysiu on 2012-05-16
I'm partial to the way OS X does it. I don't like everything OS X does, but the file/folder structure is pretty good.

Basically, /Applications stores the applications, /Users has the users, /Volumes has all the drives (CD-ROMs, USB sticks, external hard drives), and /Library has most of the application libraries. The rest of the folders are hidden (but still accessible). If you know what you're doing, you can still access /etc, /bin, /usr... you just won't stumble on those directories accidentally.

---

### Post by szymon_g on 2012-05-16
hm... one of the first things I do after installing linux, is changing /etc/default/adduser to change default $HOME directory: from /home/$USERNAME to /home/users/$USERNAME
I also create /home/services (for ftp, www etc) and /home/shared (for things shared between users on the same computer.
Reason? /home is usually on different partition, so keeping "big" things out of / is useful when I'm not willing to use LVM. also, it can be kept on different disk/disks array.

---

