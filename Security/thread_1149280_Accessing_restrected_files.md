---
title: "Accessing restrected files"
date: 2009-05-05
forum: Security
---

### Post by triunenature on 2009-05-05
So, some background.

I created a second user and named it guest.  gave it no password by doing a little trick i read about.

Anyway... that all went dandy, however out of courisoity, i was trying to see what i could do in the guest account.

So i restrected access to /home/guest via the guest account (right clicked the file and made it where only guest could access it)

Then i went to my main account, and was trying to see how to use my admistrative abilitys

I went to the file and double clicked it... access restrected. (ok... well at least this will be fun)

Terminal ->
```

CD /home/guest
Permission denied.

```
Ok... well i know how to fix that

```
sudo cd /home/guest
sudo: cd: command not found

```

Well now im stuck...  How does the administrator access restrected files?  (I mean i could always log back into guest and unrestrect them, but thats no fun)

---

### Post by Masuran on 2009-05-05
The command 'sudo cd /home/guest' won't work because 'cd' isn't a command, it's a builtin command of Bash, the shell. 

To get around to this you should do 'sudo -i' to become root and then 'cd /home/guest'. Just don't forget to do 'exit' after you are done doing whatever you do to become a regular user again.

If you don't want to become root you always do 'sudo ls /home/guest' to take a peek inside the directory.

---

### Post by bodhi.zazen on 2009-05-05
use ```
sudo bash -c "builtin cd /"
```Note this will not do much of anything as bash will cd , then exit.

You can see it works if you execute a command

[quote]~$ sudo bash -c  "builtin cd / ; ls "
bin    dev   initrd.img      lib32       media  proc  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lib64       mnt    root  srv      usr  vmlinuz.old
cdrom  home  lib             lost+found  opt    sbin  sys      var

~$[/code]

Which of course can be accomplished with 

```
sudo ls /
```Most likely you so not need to sudo cd ...

---

