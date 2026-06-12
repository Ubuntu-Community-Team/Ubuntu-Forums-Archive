---
title: "Cant edit server files"
date: 2006-09-27
forum: Server Platforms
---

### Post by dthreap on 2006-09-27
Im currently setting up a server on my computer with ubuntu and i added a mysql, but I want to make it accessable to people outside my network(myself at another computer) but when I type in gksudo gedit /ect/mysql/my.cnf

I get "GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed." as my error and gedit open but its blank.

Help would be greatly appericated.

---

### Post by mitch.c on 2006-09-27
> **dthreap said:**
> Im currently setting up a server on my computer with ubuntu and i added a mysql, but I want to make it accessable to people outside my network(myself at another computer) but when I type in gksudo gedit /ect/mysql/my.cnf

I get "GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed." as my error and gedit open but its blank.

Help would be greatly appericated.

There's a bug filed on this:
[https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917)

But it's only a nuisance, so the priority is low. It happens on my machine too, but the file opens properly, and I can edit.

In your case, the problem is (assuming that's not a typo in your post) that there is no /ect/mysql/my.cnf; it should  be /etc/mysql/my.cnf.

---

### Post by dthreap on 2006-09-27
Well, is there any other way I can edit the file?

---

### Post by mitch.c on 2006-09-27
> **dthreap said:**
> Well, is there any other way I can edit the file?
Sure. Take your pick.
```
sudo nano -w /etc/mysql/my.cnf
sudo vim /etc/mysql/my.cnf
```
But again. Watch the typos on your file name.

---

### Post by dthreap on 2006-09-27
Hmm... The first one I use and none of the commands in it work. And the second one creates a new file...

---

### Post by mitch.c on 2006-09-27
> **dthreap said:**
> Hmm... The first one I use and none of the commands in it work. And the second one creates a new file...

This shouldn't be that hard. Are you sure /etc/mysql/my.cnf exists? The fact that gedit and vim both open blank files leads me to believe it does not exist, or it's empty.

What happens when you:
```
cat /etc/mysql/my.cnf
```

What is the output of:
```
ls -l /etc/mysql/my.cnf
```

---

### Post by dthreap on 2006-09-28
When I type in cat /ect/mysql/my.cnf I get : no such file or directory...

Though I can see the file file myself by going there.

---

### Post by mitch.c on 2006-09-28
> **dthreap said:**
> When I type in cat /ect/mysql/my.cnf I get : no such file or directory...

Though I can see the file file myself by going there.
Alright, I don't know how I can make this any clearer. LOOK at what you typed in the post... there is not directory called /ect !!! It's called /etc !!! I've pointed this out to you in previous posts. If this is what you are typing, you'll always get a blank file... there is no such path!! ](*,)

---

### Post by dthreap on 2006-09-28
Dude... I feel like the slowest person in the world... Wow... Thanks alot man for helping me :)

you got an msn or gtalk or any kind of messenger that we could chat on sometime?

---

### Post by chrisfay on 2006-09-28
> Alright, I don't know how I can make this any clearer. LOOK at what you typed in the post... there is not directory called /ect !!! It's called /etc !!! I've pointed this out to you in previous posts. If this is what you are typing, you'll always get a blank file... there is no such path!! 

...lol

I've seen this happen so many times....

---

