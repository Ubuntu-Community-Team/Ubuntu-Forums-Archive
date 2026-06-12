---
title: "Update-Less Repos?"
date: 2008-09-14
forum: The Cafe
---

### Post by kevin11951 on 2008-09-14
Lets say you have a repo that has tons of software that you love, but it also has a new version of compiz that breaks on your computer.  Wouldn't it be great if you could just use the repo for installing software, but not allow it to update anything already on your system?

In the sources.list it would be great if you could do something like this:

deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free **update=false** #Skype 

and then when you update the list, it will see the packages in the repos, but would not update from them.

EDIT: Although I wonder if there is already something like this?

---

### Post by LaRoza on 2008-09-14
Anything after the # is a comment, so that wouldn't work.

Also, updating the sources list doesn't upgrade the packages. So I don't see what the problem is.

---

### Post by howefield on 2008-09-14
you don't need to update anything you don't want to. I stand to be corrected :)

---

### Post by mister_pink on 2008-09-14
If there's just one package you don't want to update its easy - just find it in synaptic and select force version from the menu.

---

### Post by kevin11951 on 2008-09-14
> **LaRoza said:**
> Anything after the **# is a comment**, so that wouldn't work.

Also, updating the sources list doesn't upgrade the packages. So I don't see what the problem is.

fixed

---

### Post by kevin11951 on 2008-09-14
> **howefield said:**
> you don't need to update anything you don't want to. I stand to be corrected :)

what about if ubuntu releases a security fix to the same program, then i cant tell the difference...

---

### Post by kevin11951 on 2008-09-14
> **mister_pink said:**
> If there's just one package you don't want to update its easy - just find it in synaptic and select force version from the menu.

but then what happens if ubuntu releases a security fix to the same program?

---

### Post by tdrusk on 2008-09-14
I noticed in Debian my /etc/apt/sources.list looks like
```
 
deb http://ftp.us.debian.org/debian/ lenny main contrib non-free
deb-src http://ftp.us.debian.org/debian/ lenny main contrib non-free

deb http://security.debian.org/ lenny/updates main contrib non-free
deb-src http://security.debian.org/ lenny/updates main contrib non-free

deb http://www.debian-multimedia.org lenny main

```

Noice how the 2 in the middle are /updates. So I suppose I can do what you are talking about...

It should be possible in Ubuntu if it works in Debian.

---

### Post by The Keeper on 2008-09-15
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Untick all five repository sources that are shown in this image:
[https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=Updates1.png](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=Updates1.png)

The only official Ubuntu repository that isn't selectable is the security repository, which I believe means that it is always enabled unless disabled from sources.list.

Then the only updates you would receive are security updates.

---

### Post by FuturePilot on 2008-09-15
There is a way :)
[https://help.ubuntu.com/community/UbuntuBackports#Use%20pinning%20to%20limit%20the%20backports%20repository]("https://help.ubuntu.com/community/UbuntuBackports#Use%20pinning%20to%20limit%20the%20backports%20repository")

Should work with any repository

---

