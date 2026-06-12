---
title: "Firestarter on Dapper"
date: 2006-05-10
forum: Server Platforms
---

### Post by xXx 0wn3d xXx on 2006-05-10
Has anyone gotten firestarter to run on startup on dapper ? When I edit my sudoers file with the visudo command, it refuses to load at all (I can't even start it from the menu or "sudo firestarter." Has anyone suceeded with getting it to run at startup ?

---

### Post by Anduu on 2006-05-14
Same problem here.

When I try to launch it from a terminal I get;

(firestarter:8515): Gtk-WARNING **: cannot open display:

:-k

Update:

Found this 

[http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fid%3D39179&prev=/search%3Fq%3Dfirestarter%2Bdapper%26hl%3Den%26hs%3D8x7%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official_s%26sa%3DG](http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fid%3D39179&prev=/search%3Fq%3Dfirestarter%2Bdapper%26hl%3Den%26hs%3D8x7%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official_s%26sa%3DG)

But sorta afraid to try it in case something may have been lost in the translation.

Can anyone clarify this please?

---

### Post by cgjones on 2006-05-15
I followed [these](http://www.fs-security.com/docs/faq.php#trayicon) instructions and got it working.

---

### Post by Anduu on 2006-05-15
[QUOTE=cgjones]I followed [these](http://www.fs-security.com/docs/faq.php#trayicon) instructions and got it working.[/QUOTE]

Yes that is the way it is supposed to work but in my case it doesn't work with Dapper.

Worked fine with Breezy.

---

### Post by tagra123 on 2006-05-16
[I]Ubuntu 6.06, Dapper Drake!
Kernel : 2.6.15-22-386[/I]


Fixes the " Gtk-WARNING **: cannot open display: "  problem


Open a terminal:  MENU: Applications > Accessories > Terminal

Type in:
[b]
sudo visudo
[/b]
enter your password when prompted.

Move the cursor near the bottom of the screen.
Find these lines

[I]
Defaults       !lecture,tty_tickets,!fqdn

and replace with  
[b]
# Defaults
#Defaults       !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHORIZATION "
[/b]
[/I]
when finished editing press CTRL-X and it will ask to save and give a temp file name.  If you did everything right you will be back at the command prompt. If it says there is an error in the file just press "e" and try again.

When finished editing the file type
[b]
sudo firestarter 
[/b]
You will see some write errors if you completly removed and reinstalled firestarter and then the firestarter setting screen will display.

Once finished setting up firestarter, close the the terminal (this will also close the firestarter that was just ran)  


Now that firestarter works; synaptic and the other programs needing to start with gksu or sudo fail. 

Here's the step that gets everything working the way it did before the DAPPER update broke it.

Open a terminal:  MENU: Applications > Accessories > Terminal
[b]
sudo ln -fs /home/USERNAME/.Xauthority /root/.Xauthority
sudo chown USERNAME.root /home/USERNAME/.Xauthority

[/b]

USERNAME = your username


Now start firestarter using the menu : Applications > Internet > Firestarter

Synaptic and all of the other administrative applets should still prompt for a password.

Firestarter will run without a  sudo password.

---

### Post by Anduu on 2006-05-16
Cool that corrected problems starting Firestarter.....

However it still will not start on startup.Once ubuntu has fully loaded I can open terminal and type "sudo firestarter --start-hidden" and it wil go but not using that line in my startup list.

It was nice when you could set the order in Breezy as I suspect there is some kind of issue there.

:-k

---

### Post by tagra123 on 2006-05-17
[QUOTE=Anduu]Cool that corrected problems starting Firestarter.....

However it still will not start on startup.Once ubuntu has fully loaded I can open terminal and type "sudo firestarter --start-hidden" and it wil go but not using that line in my startup list.

It was nice when you could set the order in Breezy as I suspect there is some kind of issue there.

:-k[/QUOTE]

Anduu posted a better method below for starting firestarter -- post number 10


To get it to work at startup:

MENU: System > Preferences >Sessions

Click on the Startup Sessions Tab 

Edit or add the line for firestarter to read:

gksudo /usr/sbin/firestarter --start-hidden

ALSO  Make sure that permissions are set to allow this

Open a terminal:  MENU: Applications > Accessories > Terminal

Type in:
[B]
sudo visudo
[/B]
enter your password when prompted.

Move the cursor near the bottom of the screen.
Find these lines (below the Defaults section)
[I]
# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
[/I]
then

Add this line at the bottom

[I]
USERNAME ALL=NOPASSWD:/usr/sbin/firestarter
[/I]

when finished editing press CTRL-X and it will ask to save and give a temp file name.  If you did everything right you will be back at the command prompt. If it says there is an error in the file just press "e" and try again.

USERNAME = your username

---

### Post by Anduu on 2006-05-17
Yup yup did that.Except for using gksudo instead of sudo.Been told on many occasions not to run as root unless absolutely nescessary.....

I just made myself a little script and called that at startup and it works fine ;)

---

### Post by tagra123 on 2006-05-18
[QUOTE=Anduu]Yup yup did that.Except for using gksudo instead of sudo.Been told on many occasions not to run as root unless absolutely nescessary.....

I just made myself a little script and called that at startup and it works fine ;)[/QUOTE]


Please post the script you used.

---

### Post by Anduu on 2006-05-18
[QUOTE=tagra123]Please post the script you used.[/QUOTE]

Okeedokee...

```
#!/bin/bash
sleep 10
sudo firestarter --start-hidden
```

Put this in an empty document,save it somewhere and name it whatever you like.

Then just call it in your sessions startup list...

I put mine in my /home/bin folder so I call it like this:

/home/anduu/bin/myscript

---

### Post by Limulus on 2006-05-28
[QUOTE=tagra123]Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHORIZATION "
[...]
Now that firestarter works; synaptic and the other programs needing to start with gksu or sudo fail. [/QUOTE]
As per [http://forum.ubuntu-fr.org/viewtopic.php?id=39179](http://forum.ubuntu-fr.org/viewtopic.php?id=39179) if you use:

```
Defaults! reading, tty_tickets! FQDN, env_reset, env_keep+= " HOME LOGNAME PATH SHELL TERM DISPLAY XAUTHORITY XAUTHORIZATION LANG LANGUAGE LC_* TO USE "
```
you don't have to alter anything else to get the other sudo programs working (it seems to work for me too).

**Edit:** Hrumph; something about the change caused Synaptic to not work properly for some, but not all upgrades (something about the PATH not being right).  Thus I recommend NOT using this method :/  Changing it back seems to have corrected things though...

---

### Post by Anduu on 2006-05-28
Nah I think I can live without firestarter in the notification area...too much hassle and you never know what the hell else your going to break :mad:

---

### Post by cy218 on 2007-01-27
Sorry to resurrect this one, I couldn't find anywhere else to answer my questions!

I did all that was suggested in the above posts and was left with:

Firestarter ran on startup -Good

Sudo worked in terminal -Good

Menu applications that required a password would ask, I'd type my password in, the mousewheel turns and.... nothing happens! -Not so good

If I selected the same application (or another) again no password would be required but still no application.

I've since removed the 'Defaults' line from the sudoers file suggested in the post and I can now use Synaptic etc from the menu but I can't get Firestarter to run.

```
cy@laptop:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5605): Gtk-WARNING **: cannot open display:
cy@laptop:~$


```

My sudoers file now looks like:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

#Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHO$
# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

cy ALL=NOPASSWD:/usr/sbin/firestarter




```

I also did the linking thing as per this post and haven't undone that because a)I'm not sure how and b)I didn't want to further confuse the issue or myself!

Any ideas?

Any more output?

Help?

Thanks

---

