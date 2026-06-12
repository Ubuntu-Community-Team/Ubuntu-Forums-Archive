---
title: "OpenSSH server says no such file"
date: 2010-01-09
forum: Server Platforms
---

### Post by Tsquad on 2010-01-09
Im using ubuntu 8.10 desktop version and im trying to set up OpenSSH and after installing i enter "/etc/init.d/sshd restart" in terminal to restart but it says no such file or directory. 

Now from the guide im following here, [http://www.brennan.id.au/16-Secure_Shell.html](http://www.brennan.id.au/16-Secure_Shell.html), that command should be a good test to see if it is working or not. From the no suc file etc. that comes up it seems like it is not installed right.

I have un installed and re in stalled the client and server many times with the same result. The first time i tryd i even had edited the /etc/ssh/sshd_config file as supposed to in the guide. Im pretty new to all this so i have no idea why this would be happening. 

Any ideas?

---

### Post by BkkBonanza on 2010-01-09
Make sure you use sudo when doing this. That tutorial was written for Red Hat based distros and they don't use sudo so much because they login as root. That's why the prompt in the tutorial is # (indicating root access). In Ubuntu you must use sudo for root access. Without root you may get permission or file missing errors.

sudo /etc/init.d/sshd restart

Also Ubuntu has a different init process using upstart. It still has compatibility with the /etc/init.d type control mechanisms but is moving towards service management where it uses start, stop and restart directly as in,

sudo restart sshd

Either way should work now.

---

### Post by Iowan on 2010-01-09
Dunno about 8.10, but on my Hardy server, there is no */etc/init.d/sshd* file - it's just ssh, so restart would be ```
sudo /etc/init.d/ssh restart
```

---

### Post by BkkBonanza on 2010-01-09
Heck, ya. Getting the filename right also helps :)

---

### Post by Tsquad on 2010-01-10
> **BkkBonaza said:**
> Make sure you use sudo when doing this. That tutorial was written for Red Hat based distros and they don't use sudo so much because they login as root. That's why the prompt in the tutorial is # (indicating root access). In Ubuntu you must use sudo for root access. Without root you may get permission or file missing errors.

sudo /etc/init.d/sshd restart

Also Ubuntu has a different init process using upstart. It still has compatibility with the /etc/init.d type control mechanisms but is moving towards service management where it uses start, stop and restart directly as in,

sudo restart sshd

Either way should work now.


ohh great thanks. I didnt know what was for red hat, you happen to know of one for ubuntu?


EDIT: I got it all working now thanks. one quick question tho, off subject kinda. 

Im trying to delete a folder in my ftpuser's home dir. Im trying to do this from the terminal. my problem is the dir is iTunes Music. it thinks im trying to del a dir named iTunes and one named Music. how can i get over this issue of having a space in the dir name??

---

### Post by BkkBonanza on 2010-01-11
Either put " quotes around the name or use the escape \ symbol in front of the space. It should work then,

rmdir "iTunes Music"
rmdir iTunes\ Music

It won't remove a directory with files still in it. 
If you are sure you want to nuke the whole thing you can use,

rm -rfd "iTunes Music"

to delete and remove the directory and everything below that. Be careful with those command options, they can do major damage if you give it the wrong directory.

---

