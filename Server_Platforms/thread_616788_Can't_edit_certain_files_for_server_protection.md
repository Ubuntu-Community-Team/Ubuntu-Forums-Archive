---
title: "Can't edit certain files for server protection"
date: 2007-11-18
forum: Server Platforms
---

### Post by bourne- on 2007-11-18
Hey there everyone
I recently installed openSSH and since then I have been trying to secure my machine to cut down on the chances of someone being able to break in. However I have running into some road blocks. I have been doing a lot of searching on how exactly to secure my machine while using SSH. One of the tutorials, directly from the ubuntu site, requires me to edit the "/etc/ssh/sshd_config" file. However when I used the following command:
```

sudo vim /etc/ssh/sshd_config

```
it will not open into vim allowing me to edit it. I can access it using vim as a regular user but I have no power to edit it. I checked the permissions and as a super user I should has access to edit the file. 

I have also noticed that there are other files that I cannot gain access to to allow me to help protect my machine. I read another tutorial that suggested I use the "/etc/hosts.allow" and "/etc/hosts.deny" to specify the hosts I want being able to access my machine however when I attempt to edit them I get the same thing happening as when I attempt to edit the "sshd_config" file. I was just wondering if anyone has run into this, and if they have is there away around it? Or are you not supposed to be able to edit this file?

thanks in advance
todd

---

### Post by conjur3r on 2007-11-18
The file probably has the read only attribute (and not write), but you can tell vi to force a save with the following:

:w!

So open it up like you did before, then just issue that command when you're happy.  The permanent solution is to apply read/write access to the file using chmod.

---

### Post by bourne- on 2007-11-18
> **conjur3r said:**
> The file probably has the read only attribute (and not write), but you can tell vi to force a save with the following:

:w!

So open it up like you did before, then just issue that command when you're happy.  The permanent solution is to apply read/write access to the file using chmod.

This didn't work.
And according to permissions on the file the root (sudo) user should be able to edit the file however I am unable to. I can't open the files AT ALL using:
```

sudo vim sshd_config

```
nothing happens when I issue this command

when I issue:
```

vim sshd_config

```
the file opens in vim but I can't make any permanent changes even when using the 'w!' as you suggested

thanks 
todd

---

### Post by bourne- on 2007-11-18
After doing some more digging i stumbled across a post on linuxquestions.org: [http://www.linuxquestions.org/questions/linux-server-73/cannot-edit-sshdconfig-as-root-510959/](http://www.linuxquestions.org/questions/linux-server-73/cannot-edit-sshdconfig-as-root-510959/)

However this doesn't work. I am unable to alter the flags. 

I am wondering. Is it possible that 'sudo' isn't configured properly?

thanks in advance
todd

---

### Post by bourne- on 2007-11-18
Ok really weird. I think it has to do with my 'sudo' functionality. It isn't working at all anymore. I can't even edit normal simple files that I have been able to edit before.
So I think that I might have somehow broken 'sudo'

even when trying to edit files under an account I created just for practice. I have been able to use 'sudo' to edit the files, however now sudo doesn't do anything. when I issue a command using sudo to edit a text file nothing happens, the file won't open

anyone know what might be wrong with sudo?

thank in advance
todd

---

### Post by conjur3r on 2007-11-19
What groups are you in?

# groups

Also, what is in your /etc/sudoers file?  It will probably be hard for you to view it if sudo isn't working so try su first.

---

### Post by bourne- on 2007-11-19
yeah I figured the problem out. What a stupid thing I can't believe I didn't see it before. I ended up reinstalling to ugh.
But yeah I took myself out of the sudo group by accident, super dumb!. What would be the command to add myself to multiple groups? like if I use "usermod" is there someway that I can tell "usermod" not to take me out of the other groups that I am apart of, but just to add me to another?

thanks
todd

---

### Post by sciurus on 2007-11-19
> **bourne- said:**
> yeah I figured the problem out. What a stupid thing I can't believe I didn't see it before. I ended up reinstalling to ugh.
But yeah I took myself out of the sudo group by accident, super dumb!. What would be the command to add myself to multiple groups? like if I use "usermod" is there someway that I can tell "usermod" not to take me out of the other groups that I am apart of, but just to add me to another?


The debian way is *useradd -G {group-name} username*. With usermod, the syntax is *usermod -a -G {group-name} username*.

---

### Post by conjur3r on 2007-11-20
No, when you do a usermod for groups, it doesn't append you to groups you are already in.  You need to specify all group memberships you would like to set for the specific user.

Take a look at the man page for usermod/useradd and search for two switches: -g and -G.  The -g (small g) is your main group, the -G (large g) is for any other group memberships separated by commas.

Alot of the time, I find myself editing /etc/group cause I can't be stuffed entering all the groups I'm already in if I just want to be added to one other group.  Take caution though cause a mistake here could lead you to other weirder problems...

---

### Post by wirelessmonkey on 2007-11-20
Blame vim... if you'd just use emacs.... sigh.   ;)))))

---

### Post by bourne- on 2007-11-21
Thanks for all the help guys
I managed to figure that out. I have noticed a few small weird things since I messed with that file. However for the most part it seems like everything is working good for right now.

Thanks for all the help guys

todd

---

