---
title: "Lock user in home folder"
date: 2008-02-16
forum: Security Discussions
---

### Post by Dissident85 on 2008-02-16
Hi all, i wanted to know if it were possible to lock a "guest" user in their home folder???

basically what is happening i have my laptop and occasionally my house mates use it. i have created a guest account for them and from this guest account they can view everything. i wanted to know if it were possible to lock them in their home folder so that that is all that is all they can see/access is their home folder?

---

### Post by ajgreeny on 2008-02-16
As long as they don't have admin permissions, ie they can't use sudo, you can make sure they can only see their own files in /home/guest by making your own user files unreadable to them.  As far as I'm aware you can do it by opening nautilus and navigating to /home/yourusername and in the permissions setting access to you only, thereby locking all others out of your files; they will not even be readable by other users.

You can also do it with the chmod command, but I'm afraid I've never quite got to grips with the numerical intricacies of that;  I must look into it a bit deeper, I think.

If they have sudo permissions, of course, there is nothing you can do to stop them if they really want to look at your files, so make sure they are not in the admin group.

---

### Post by kevdog on 2008-02-16
You either need to modify the file permissions system wide so the user you specifiy belongs in a group that can not read the system files (so for example rather than 644 permissions on most of the files, it would be 640, or you need to place your user in a jail.  Ive used the utility called jailkit before.  Its not 100% lock down secure, meaning its possible for the user to break out of the jail, and then they would be back to their normal permissions as if no jail existed (they dont suddenly have root priviledges or anything).  Jailkit can be found here:
[http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

---

### Post by Dissident85 on 2008-02-16
> **ajgreeny said:**
> As long as they don't have admin permissions, ie they can't use sudo, you can make sure they can only see their own files in /home/guest by making your own user files unreadable to them.  As far as I'm aware you can do it by opening nautilus and navigating to /home/yourusername and in the permissions setting access to you only, thereby locking all others out of your files; they will not even be readable by other users.

You can also do it with the chmod command, but I'm afraid I've never quite got to grips with the numerical intricacies of that;  I must look into it a bit deeper, I think.

If they have sudo permissions, of course, there is nothing you can do to stop them if they really want to look at your files, so make sure they are not in the admin group.

cheers that sounds like it could work... but i also came across "chroot" ??? not to sure exactly what it dose but it sounds like it could be what i need??? any one got some info on that?

---

### Post by ajgreeny on 2008-02-16
Don't think chroot is of use, and the manual (man chroot) is no help at all.

---

### Post by mojoman on 2008-02-17
> **ajgreeny said:**
> Don't think chroot is of use, and the manual (man chroot) is no help at all.

Correct, a chroot environment will not do the trick. It is used to produce an isolated environment, for example to test applications in or secure the rest of the Os under various testing. A lot of people who run 64-bit OS have a 32-bit chroot environment to launch pure 32-bit applications (wine, browsers etc) but it doesn't contain users the way a jail does.

---

### Post by HermanAB on 2008-02-17
There is also another more fun Rube Goldberg way:
Install a Virtual machine with a full copy of Ubuntu (or whatever you fancy) in that, then give guests accounts in the VM only.

---

### Post by Dissident85 on 2008-02-17
Thanks every one, changing the permissions seems to be the best way to go about it… minimal hassle,  and it dose the job well.. 

Cheers

---

### Post by bodhi.zazen on 2008-02-18
I suggest you look at a restricted shell, like say iron Bars (although there are others).

> Iron Bars Shell is a restricted Unix shell. **The user can not step out of, nor access files outside the home directory.** It is written in C for Linux. No libraries used. It is small, fast, secure. Two ascii configuration files for more control.

[http://sourceforge.net/projects/ibsh/](http://sourceforge.net/projects/ibsh/)

[http://www.cryptolife.org/2008/02/17/how-to-secure-login-with-linux-restricted-shell/](http://www.cryptolife.org/2008/02/17/how-to-secure-login-with-linux-restricted-shell/)

---

### Post by cryptolife on 2008-02-19
Thanks very much for the link to my post. I guess that there's some other way to restrict the user in is own dir, but this is very intuitive and straight forward.

Regards,

phillip

---

