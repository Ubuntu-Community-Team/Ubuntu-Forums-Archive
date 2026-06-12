---
title: "HOW-TO: non-root user shutdown"
date: 2006-02-22
forum: Tutorials
---

### Post by guano on 2006-02-22
Lots of people which use Ubuntu use GNOME or KDE, so they don't have any kind of problem to shutdown or restart the computer. But if you use other window manager, that might be an issue. 

Maybe you need to logoff, wait until GDM (or other) to restart and then choose reboot/shutdown. Or if you don't use  GDM and your machine starts from the console (and you use the good'ol "startx') you need to 'sudo shutdown -h now' or something like that, and give your password, just to turn off your own machine! 

I find that really annoying.

So, that's what motivate me on writing this little how-to (my first!)

This is based on: ```
http://www.ma.utexas.edu/users/stirling/computergeek/shutdown.html
```


There is a option of using /etc/shutdown.allow (look at 'man shutdown'). This file is a list with the logins (one per line) of users allowed to shutdown. But only from a terminal (out of X) and typing CTRL-ALT-DEL. Not very useful, in my opinion.

So, let's take a look in what we have in Spencer Stirling's page: 

```

sudo
The program sudo allows normal users to execute certain root-only commands. 
Which users are authorized to run which commands is specified in the /etc/sudoers file. 
This should only be edited with the command visudo.

For example, suppose I wanted to add a group of users who are allowed to shut down the machine. 
So I first want to add a group called "shutdown" (run these commands while root)

groupadd shutdown

Then I need to edit the /etc/group file to add users to the "shutdown" group. 
I just tack the usernames at the end of the shutdown line, separated by commas, e.g.

shutdown:x:407:user1,user2,...

Whatever users I put there will be able to shut down the computer (so choose wisely). 
Now I need to configure sudo to allow members of the "shutdown" group to actually 
invoke the assorted shutdown commands provided in linux. Run **visudo** and add 
the following lines

%shutdown ALL=(root) NOPASSWD: /sbin/reboot
%shutdown ALL=(root) NOPASSWD: /sbin/halt
%shutdown ALL=(root) NOPASSWD: /sbin/shutdown

This allows the "shutdown" group to run /sbin/reboot, /sbin/halt, and /sbin/shutdown 
AS IF THEY WERE ROOT. The only caveat is that the users must run the commands 
with the command sudo in front, e.g.

sudo /sbin/halt

This is always a bit of a pain (and users never remember), so I can create the 
following script called "/usr/bin/reboot" (and similar scripts for halt and shutdown)

#! /bin/sh
sudo /sbin/reboot $*

Remember to make these scripts executable! To make this slightly more secure, 
I might want to change the ownership of these scripts to the "shutdown" group

chgrp shutdown /usr/bin/reboot /usr/bin/halt /usr/bin/shutdown

and then make them executable only for the group "shutdown"

chmod g+x /usr/bin/reboot /usr/bin/halt /usr/bin/shutdown

```

Now that's interesting!

The thing is that he did a script to call shutdown, but you can just add an entry 
in the menu of the WM you use.

For example, I use OpenBox, so I edited the file
 ```
~/.config/openbox/menu.xml
```

and add this:

```
  <item label="Shutdown">
    <action name="Execute"><execute>sudo /sbin/shutdown -h now</execute></action>
  </item>
    <item label="Reboot">
    <action name="Execute"><execute>sudo /sbin/shutdown -r now</execute></action>
  </item>
```

in the end of the menu.

Voilá !!

Hope its usefull.

---

### Post by jchau on 2006-02-22
Oh, btw, there is a special section in the forum for howtos.  
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

You'd probably want to move this thread there

---

### Post by frühstück on 2006-07-23
> **guano said:**
> There is a option of using /etc/shutdown.allow (look at 'man shutdown'). This file is a list with the logins (one per line) of users allowed to shutdown. But only from a terminal (out of X) and typing CTRL-ALT-DEL. Not very useful, in my opinion.

Utterly retarded, in my opinion! Thanks for the HOWTO :)

---

### Post by wildemad on 2009-08-13
Thanks for the how-to. Very usefull. 

Best regards from spain.

---

### Post by chrisyco on 2011-05-23
The GUI shutdown actually uses two services, UPower and ConsoleKit, which let you shutdown the computer without having to be root, among other things. I've made a nifty shell script that lets you use these services: [https://gist.github.com/988104]("https://gist.github.com/988104")

---

### Post by sgz on 2011-11-21
> **chrisyco said:**
> The GUI shutdown actually uses two services, UPower and ConsoleKit, which let you shutdown the computer without having to be root, among other things. I've made a nifty shell script that lets you use these services: [https://gist.github.com/988104]("https://gist.github.com/988104")

Thanks, mate! Have to turn off the pc from my bed via radio keyboard, and this script really does it!

---

