---
title: "stop openssh from - ever - running at start up??"
date: 2011-06-12
forum: Server Platforms
---

### Post by ClientAlive on 2011-06-12
Hi,

I'm running Ubuntu 10.04 LTS and I have installed openssh.

I need to find a way to configure it so that it never start up when I boot into my computer. The reason is: I haven't had the time yet to learn how to set it up and configure it correctly. Until that time comes I don't want it to run at all.

As of right now I have to go into the terminal and issue the command:

```

sudo /etc/init.d/ssh stop

```

Every single time I boot into the system and I have to do that first before I can even do what I really need to on the computer. It's annoying.

Does anyone know the best and least complicated way to just make it not run at all until I'm ready to set it up properly?

Thanks in advance for any help.
-------------------------------

Edit: Also how to check what is running on my system after I boot up so I can double check, after making the changes, that it worked right.

---

### Post by Lars Noodén on 2011-06-12
> **ClientAlive said:**
> ...I have installed openssh.

I need to find a way to configure it so that it never start up when I boot into my computer...


[update-rc.d](http://manpages.ubuntu.com/manpages/natty/en/man8/update-rc.d.8.html) will do that:

```

update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .

```

---

### Post by ClientAlive on 2011-06-12
> **Lars Noodén said:**
> [update-rc.d](http://manpages.ubuntu.com/manpages/natty/en/man8/update-rc.d.8.html) will do that:

```

update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .

```


Ok. I ran that and here's what I get back.

```

~$ update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .
update-rc.d: warning: ssh start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: ssh stop runlevel arguments (0 1 2 3 4 5 6 S) do not match LSB Default-Stop values (none)
 System start/stop links for /etc/init.d/ssh already exist.
Died at /usr/sbin/update-rc.d line 57.

```

I'm not very familiar with this particular software but that seems to be saying to me that it didn't work and telling me why it didn't.

What now?

Thanks Lars Nooden.

---

### Post by BkkBonanza on 2011-06-13
Try,
sudo update-rc.d -f ssh remove

That will disable the service for now. Later you can enable it again with,

sudo update-rc.d ssh defaults

---

### Post by Lars Noodén on 2011-06-13
> **BkkBonanza said:**
> Try,
sudo update-rc.d -f ssh remove

That will disable the service for now. Later you can enable it again with,

sudo update-rc.d ssh defaults

Thanks.  That's a better way.

---

### Post by ClientAlive on 2011-06-13
Thanks BkkBonanza. I did that and then ran:

```

ps ux

```

to see what is running. Maybe there's a better way to do that but I don't know of it.

When I ran ps ux here is one line I saw in there that I also saw before I ran the code you gave me. It is still there.

```

shine     1592  0.0  0.0   3284   356 ?        **Ss**   08:08   0:00 /usr/bin/ssh-ag

```

It is the only line is see that has "ssh" in it so I assume it's talking about that service. I'm not sure. (There is a comment/ question about "**Ss**" at the bottom of this post - please read on).

So then I looked at:

```

man update-rc.d

```

The following is a paragraph in that man page and is something I was wondering what it meant. I'll explain why after that content (at the bottom of the post).


> 
A  common  system  administration error is to delete the links with the
       thought that this will "disable" the service, i.e., that this will pre&#8208;
       vent  the  service from being started.  However, if all links have been
       deleted then the next time  the  package  is  upgraded,  the  package's
       postinst  script  will  run  update-rc.d  again and this will reinstall
       links at their factory default locations.  The correct way  to  disable
       services  is  to  configure  the service as stopped in all runlevels in
       which it is started by default.  In the System V init system this means
       renaming the service's symbolic links from S to K.


The reason I took notice of this paragraph in the man page is that it says:

> 
. . . is to delete the links . . .


Compare that with the output after I ran the code you gave:

```

~$ sudo update-rc.d -f ssh remove
 **Removing any system startup links for /etc/init.d/ssh ...**
   /etc/rc0.d/K20ssh
   /etc/rc1.d/K20ssh
   /etc/rc2.d/S20ssh
   /etc/rc3.d/S20ssh
   /etc/rc4.d/S20ssh
   /etc/rc5.d/S20ssh
   /etc/rc6.d/K20ssh

```

I don't know enough about it all to understand. Does that output compare with what is being said in the man page or am I totally off track? And what does the line from running ps ux mean? And what does the "**Ss**" in that line mean?

---

### Post by Lars Noodén on 2011-06-13
> **ClientAlive said:**
> 
```

~$ sudo update-rc.d -f ssh remove
 **Removing any system startup links for /etc/init.d/ssh ...**
   /etc/rc0.d/K20ssh
   /etc/rc1.d/K20ssh
   /etc/rc2.d/S20ssh
   /etc/rc3.d/S20ssh
   /etc/rc4.d/S20ssh
   /etc/rc5.d/S20ssh
   /etc/rc6.d/K20ssh

```


In the old days, the [runlevels](http://www.debian-administration.org/article/212/An_introduction_to_run-levels) were used to start and stop groups of services. K is stop (kill), S is start.  The two digit number is the order in which the service is started or stopped.  You can still use [telinit](http://manpages.ubuntu.com/manpages/natty/en/man8/telinit.8.html) to switch run levels.  People mostly start and stop individual services instead of using run levels.  [Runlevel](http://manpages.ubuntu.com/manpages/natty/en/man8/runlevel.8.html) 2 is the default.

---

### Post by BkkBonanza on 2011-06-13
It sounds like using remove may not be the best way if an ssh upgrade might later add the links again. I haven't seen that happen but would expect the man page knows best.

The line with ssh-ag I suspect is a cutoff output of ssh-agent. This is not the same as sshd - it is the agent daemon that knows how to provide keys for the ssh client when it does a remote login. You don't need to worry about that as far as ssh-server still running.

Off hand I think Ss means the process is in sleep state, ie. not actaully doing anything at the moment it was recorded by ps. For more detail you'd have to browse the ps man page as I don't know why it has both upper/lower case.

---

### Post by YesWeCan on 2011-06-13
> Does anyone know the best and least complicated way to just make it not run at all until I'm ready to set it up properly?You could uninstall ssh/openssh-server/openssh-client in Synaptic.

If you are concerned about unauthorized, external access:
You could block port 22 in your firewall
You could change /etc/ssh/sshd_conf to restrict users who can log in with an AllowUsers directive

---

### Post by ClientAlive on 2011-06-13
Right on. Thanks for all the great input everyone. I guess I did it again. Sometimes my eyes are bigger than my stomach. I think I've taken on 3 or 4 big projects now and openssh is just one of them. That on top of working and my plate is spilling over. Yeah, I guess uninstalling is an option but not one I would like to go with. My idea was I could install the thing and not let it run so it would be here for me to fiddle with whenever I can find the time. Eventually I'll learn enough about it and get it configured right, then, lastly, let it run again.

I sure appreciate everything you've shared with me.

Be Blessed.

Jake

---

### Post by ClientAlive on 2011-06-13
> **Lars Noodén said:**
> In the old days, the [runlevels](http://www.debian-administration.org/article/212/An_introduction_to_run-levels) were used to start and stop groups of services. K is stop (kill), S is start.  The two digit number is the order in which the service is started or stopped.  You can still use [telinit](http://manpages.ubuntu.com/manpages/natty/en/man8/telinit.8.html) to switch run levels.  People mostly start and stop individual services instead of using run levels.  [Runlevel](http://manpages.ubuntu.com/manpages/natty/en/man8/runlevel.8.html) 2 is the default.


Hey wait a minute! If K is kill (or to stop) and S is start, then all those lines at the bottom of your quote (your quote of me/ my system) mean those things are still starting? Is it like the last 4 lines?

Uhh . . .  Ok, so where am I at with this here guys? As it is, can someone find me on the net and start cracking my system? Heck, I don't even know how openssh is configured by default. Maybe there isn't even anything to crack. Just walk right on in eh?
-----------------

Edit: Looks like it's the lines with "rc3, rc3, rc4 and rc5" in them.

---

### Post by BkkBonanza on 2011-06-14
The remove command removes those links. The output msg was telling you which links it removed. You can do a simple directory listing to see if you still have the links present or not.

ls -ls /etc/rc2.d/

And see if a line with ssh is listed. I suspect that your links have been removed already anyway. 

If you really want to be sure and you aren't using ssh anyway then why not remove it until you need it. Not having the server installed is always going to be safer than having it disabled.

sudo apt-get remove openssh-server

It's so easy to install again if you need it.

sudo apt-get install openssh-server

In a default Ubuntu install the ability for someone to get in is mostly dependent on the difficulty of your login password. root is disabled anyway. If you don't go and misconfigure it by accident then it should be safe if you have a decent password. But I always believe if you don't need something then clean up and remove it.

---

### Post by ClientAlive on 2011-06-14
> **BkkBonanza said:**
> 
If you really want to be sure and you aren't using ssh anyway then why not remove it until you need it. Not having the server installed is always going to be safer than having it disabled.



Well, I know you're right about that. It's just that I can't work with ssh server to learn about it without it actually existing on my computer. I don't think this learning process is going to happen in one session messing with it so it's something I will have to go back to several times until I get the skills. By having it on the system at least I have it to mess with. I figured that, if done right, stopping it is as effective as removing it. It isn't other's who don't understand what "done right" is, it's me. That's what I meant by that commment. I meant that I'm smart enough to doubt myself with things I know I don't know (if that makes any sense).

---

### Post by BkkBonanza on 2011-06-14
You could leave it enabled and put, 

ListenAddress 127.0.0.1

in the /etc/ssh/sshd_config file. This tells it to listen only on the localhost interface. This allows connecting only from your own system which would allow you to test and learn about it. It's not very useful in real world use but it does prevent outside access.

After doing that, for your own edification you can use the netstat command to see what interface/port it is actually listening on,

sudo netstat -lntp

should show it bound to localhost and not "*" or your external IP.

---

### Post by Lars Noodén on 2011-06-14
> **ClientAlive said:**
> Hey wait a minute! If K is kill (or to stop) and S is start, then all those lines at the bottom of your quote (your quote of me/ my system) mean those things are still starting? Is it like the last 4 lines?

That was output from 
```

sudo update-rc.d -f ssh remove

```

---

### Post by ClientAlive on 2011-06-14
> **Lars Noodén said:**
> That was output from 
```

sudo update-rc.d -f ssh remove

```


Cool. I'll have to look at doing that. Thanks.

---

