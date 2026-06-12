---
title: "root PW problem"
date: 2005-02-18
forum: Server Platforms
---

### Post by wglamm on 2005-02-18
Help.... I want to start by saying thank you to all the hard working coders that have brought Linux to this point.. that being Ubuntu... I am not a programer,  I have been building my own PCs for fun for years but I get lost in the programing and up till Ubuntu I was too easily lost in Linux...  Blah Blah Blah

I am having trouble with getting into firestarter and network tools device config thru the GUI it dosent like my password??  I have not set any other passwords on the system other then my sons login but it was doing this before he set up a login... Thanks in advance

---

### Post by rufius on 2005-02-18
[QUOTE=wglamm]Help.... I want to start by saying thank you to all the hard working coders that have brought Linux to this point.. that being Ubuntu... I am not a programer,  I have been building my own PCs for fun for years but I get lost in the programing and up till Ubuntu I was too easily lost in Linux...  Blah Blah Blah

I am having trouble with getting into firestarter and network tools device config thru the GUI it dosent like my password??  I have not set any other passwords on the system other then my sons login but it was doing this before he set up a login... Thanks in advance[/QUOTE]
 You should be able to use 'sudo <whatever>' and then sudo should prompt you for a password which the one you will use is your own username's password. There is no root passwd for security reasons.

---

### Post by wglamm on 2005-02-18
[QUOTE=rufius]You should be able to use 'sudo <whatever>' and then sudo should prompt you for a password which the one you will use is your own username's password. There is no root passwd for security reasons.[/QUOTE]


the use of 'sudo <whatever>' is in a terminal window? correct? 

I am being prompted for a password in a window in gnome.  I tried 'sudo <mypw>' I tried with caps, with out caps, all caps.. If some of these GUI interfaces are not ready for Ubuntus sudo password thang and I need to do it all in terminal that is ok.. its just a learning curve I was hoping to delay till after I got my firewall up

 ](*,)

---

### Post by wapowell on 2005-02-18
Yes, that's correct... sudo is a terminal command.

To find the correct syntax you can type in a terminal window: ```
sudo -h
``` 
To see the explanations for the various switches you can type in a terminal window: ```
man sudo
```

One wouldn't type sudo <password>.  The correct usage would be sudo <command>.  This will then prompt you for your password.  Assuming you type the password correctly, all should be well as long as the account that you are logged in as is in the sudoers file (/etc/sudoers).

As an example, you mentioned that you have an account and your son has an account.  If you were in the sudoers file but your son wasn't then he would not be able to use sudo to elevate his rights, however you would.

By default, the sudo session is valid for 15 minutes.  So, if you started a root terminal, or synaptic you would be prompted for your password.  If you enter it and you get in fine, then that sudo session will be valid for 15 minutes for any other apps which may require it.  Example, if your firewall gui is really asking you to enter your password for sudo, then if you started synaptic and entered your password... you could then close synaptic and your sudo session would still be valid.  Then if you started the firewall gui within 15 minutes of having entered your password for synaptic it should go through fine.

If you have any other problems I would think you would need to either:
[list=a]
[*]troubleshoot sudo.  You would know if you need to do that option if you can't even sudo for synaptic or a root terminal.
[*]troubleshoot the firewall gui specifically.
[/list]

I am not familiar with the firewall gui you mentioned, but I'm sure someone else here is.

Hope this helps you, or at least helps explain sudo a little.

-Bill

---

### Post by wglamm on 2005-02-18
[QUOTE=wapowell]Yes, that's correct... sudo is a terminal command.

By default, the sudo session is valid for 15 minutes.  So, if you started a root terminal, or synaptic you would be prompted for your password.  If you enter it and you get in fine, then that sudo session will be valid for 15 minutes for any other apps which may require it.  Example, if your firewall gui is really asking you to enter your password for sudo, then if you started synaptic and entered your password... you could then close synaptic and your sudo session would still be valid.  Then if you started the firewall gui within 15 minutes of having entered your password for synaptic it should go through fine.

If you have any other problems I would think you would need to either:
[list=a]
[*]troubleshoot sudo.  You would know if you need to do that option if you can't even sudo for synaptic or a root terminal.
[*]troubleshoot the firewall gui specifically.
[/list]

I am not familiar with the firewall gui you mentioned, but I'm sure someone else here is.

Hope this helps you, or at least helps explain sudo a little.

-Bill[/QUOTE]


That didnt work... I went to Synaptic and gave my password when prompted, then whent to firestarter and it wanted a password, it didnt like my PW nor did it like no PW...  :???: 

Thanks though.. still pluggin at it  :)

---

### Post by wapowell on 2005-02-18
Ok, I just installed it and had the same problem you did.

One note:  It prompts for the root password.  This is quite different than what synaptic prompts for.  Synaptic prompts for your password (aka sudo).  The difference is that by default root has no pw and thus is disabled.

The commands used in the shortcuts are:
For the Synaptic shortcut:
```
gksudo /usr/sbin/synaptic
```
For Firestarter (by default):
```
gksu /usr/sbin/firestarter
```

BIG difference, one calls gksudo (which wants your pasword), one calls gksu (which wants root's password).

Before you click on that firestarter shortcut, right click and choose properties.  Change the gksu to gksudo.  Then close the dialog box and start up firestarter.

I tried it on my system and changing the gksu to gksudo works like a champ.

I think this will do the trick for you too.   :-D 
Either way, please let me know what the outcome was.

-Bill

---

### Post by hndrcks on 2005-02-18
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

Give root a real password.

---

### Post by wglamm on 2005-02-18
[QUOTE=wapowell]
One note:  It prompts for the root password.  This is quite different than what synaptic prompts for.  Synaptic prompts for your password (aka sudo).  The difference is that by default root has no pw and thus is disabled.

The commands used in the shortcuts are:
For the Synaptic shortcut:
```
gksudo /usr/sbin/synaptic
```
For Firestarter (by default):
```
gksu /usr/sbin/firestarter
```

Before you click on that firestarter shortcut, right click and choose properties.  Change the gksu to gksudo.  Then close the dialog box and start up firestarter.

Either way, please let me know what the outcome was.

-Bill[/QUOTE]

Thank you.. thank you.. that did work.

It probably dos'nt fix my network device config issue but the next post says give root a password.  If I give root a password and <su> is requesting it is it still only temporary like sudo?? or would this be opening me up to to many security issues?

Thanks

---

### Post by wapowell on 2005-02-18
You're quite welcome.   :-) 

As far as the sudo vs root question, every now and again this debate gets sparked.  There is a wiki page that talks about sudo:
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

You'll find both ends of the spectrum on this topic.  I've seen "I'm a grown up..." blah blah blah postings airing that person's contempt for having the root account disabled by default.  On the other hand, others are focused more on the appreciation for security.

I can only offer you my perspective and experiences.  Personally, I have never had the need for "root" access per se.  I use sudo for everything.  From mounting drives (fat, ntfs, etc), installing or configuring apps, ssh into my Ubuntu box, etc... the combination of sudo and proper group memberships has worked just fine for me.

One thing that I really like about sudo is that it logs commands in  /var/log/auth.log - which makes it nice if you ever wonder what the heck you just did that messed something up  :wink:. (no offense, I think we've all done something like that at one time...or many times.  lol)

A friend if mine enables the root account when he needs to do extended maintenance, but then promptly locks the root account when he is done.  This is just to avoid the possibility that one can log in, and stay logged in as root for any extended period of time without intentionally enabling the root account (which would require sudo access).

Though, I can't promise that there would never be an occassion where root access itself would be necessary.  I'm just saying that I have never needed it.

As far as su timing out you can configure that.  However, you should remember that once root is enabled, su can be used to execute a full login or you can just login as root at the welcome screen, either of which would process etc/profile - this means that the ".bashrc" file is not processed.  The difference is being that when one "su"'s without a full login the ".bashrc" file is executed which is where you would configure the su timeout.

You mentioned a networking problem.  Is your networking problem posted in the forums?

-Bill

---

### Post by wglamm on 2005-02-18
[QUOTE=wapowell]You're quite welcome.   :-) 

You mentioned a networking problem.  Is your networking problem posted in the forums?

-Bill[/QUOTE]

Not yet, thats next... 

the password issue is a show stopper now I can try and trouble shoot the second NIC that dosent seem to want to play with my switch.

I need to snoop around in networking a little more before I become too much of a bother  :-)

---

