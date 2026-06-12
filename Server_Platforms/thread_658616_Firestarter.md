---
title: "Firestarter"
date: 2008-01-04
forum: Server Platforms
---

### Post by Skivache on 2008-01-04
I am trying to get Firestarter to start when I log in by following [these instructions]("http://www.fs-security.com/docs/faq.php#trayicon") but i can't edit sudoers.  Is there any other way to get firestarter to start at logon or edit the file?

---

### Post by stump138 on 2008-01-04
try:
System->Preferences->Sessions->Start up programs

---

### Post by Skivache on 2008-01-04
I have already added ```
sudo firestarter --start hidden
``` the the startup programs

---

### Post by PeterJS on 2008-01-04
You need to have root privileges to edit the sudoers which defines who's allowed root privileges and for what applications. It wouldn't be very secure if you could edit the list who was allowed elevated privileges as an unprivileged user now would it?

Try using visudo to edit your sudoers file, visudo will let you edit your sudoers files with elevated privileges, and warn you if you're going break something because of bad syntax. You can forego the warnings if you want a graphical editor with:
```

sudo gedit /etc/sudoers

```

---

### Post by Skivache on 2008-01-04
Great, now i can edit the file! The instructions say to add ```
username ALL= NOPASSWD: /usr/sbin/firestarter
``` at the end of the file.  Do i replace the last line in the file with that or add that after the last line?

---

### Post by PeterJS on 2008-01-04
Add it, that last line (presumeably %admin ALL=(ALL) ALL) is kind of important because it defines that people in the admin group can use root privileges for any purpose. If you remove that you'll break the relationship between sudo and the admin group, and it's kind of a pain to fix, recovery mode and all that fun stuff.

EDIT:
and might I suggest using:
```

%admin ALL= NOPASSWD: /usr/sbin/firestarter

```instead so that all admins can run fire starter not just you're user. It'll make your life easier down the line if you ever add more admin users.

---

### Post by Skivache on 2008-01-04
Ok, I added the line at the end of the file but now i can't save it because i have read-only privileges. I will log in as root and see if i can save the file then.

---

### Post by Dr Small on 2008-01-04
Just remember, if you are using Gedit instead of Visudo, and have a syntax error, Gedit won't warn you and you'll be locked out of sudo!

---

### Post by Skivache on 2008-01-04
Even when I am logged in as root I have read-only privileges (even when opening the file using the sudo command).
And Dr Small, can you tell me more about Visudo?

---

### Post by Skivache on 2008-01-04
When logged in as root, I changed the settings to allow root to read and write.
I am rebooting now and will see how it turns out.  still wondering about Visudo...

---

### Post by eolson on 2008-01-04
from the terminal

man visudo

More info than you probably want.

---

### Post by Skivache on 2008-01-04
I changed the sudoers file and added firestarter to the startup programs list and it still doesn't start when i log on.  I may just load the program manually when i start.

---

### Post by Skivache on 2008-01-05
For some reason firestarter refuses to start. I have un-done all of the changes I made but nothing seems to work. Fortunately, I tried this in VMware before I did so on my Ubuntu partition......

---

### Post by bodhi.zazen on 2008-01-05
Well, to start firestarter type :

```
gksu firestarter
``` In a terminal.

Unlike some operating systems, firestarter is NOT you firewall. Your firewall is iptables.

Firestarter is a gui tool that allows you to write rules for IPtables.

The guide you are following is misleading, at best. Firestarter should DOES not need to be running for you firewall to be active. You should NOT launch firestarter at log in. 

You should launch firestarter, configure IPTables, then close firestarter. It is a security risk to be running firestarter constantly.

See this link : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

============

visudo is a means of editing you sudoers file in a sane, safe manner

> [noparse]visudo edits the sudoers file in a safe fashion, analogous to vipw(8). visudo locks the sudoers file against multiple simultaneous edits, provides basic sanity checks, and checks for parse errors. [/noparse]

[http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html)

---

### Post by Skivache on 2008-01-05
I knew that firestarter was just a front end GUI for the IPtables, but is running it constantly a security risk because it always runs with root privileges?

---

### Post by bodhi.zazen on 2008-01-05
> **Skivache said:**
> I knew that firestarter was just a front end GUI for the IPtables, but is running it constantly a security risk because it always runs with root privileges?

Yes, exactly

---

### Post by Skivache on 2008-01-06
Well I won't be needing to running it much one I get all the rules set.

---

### Post by casalino.luca on 2008-01-06
Help! I install Firestarter and click on the icon and the GUI doesn't show up at all to set up the rules. I tried to reinstall it at least twice and it doesn't work. I'm running ubuntu 7.10 and I can tell you that it doesn't work because if I run sudo iptables -L I see this kind of output:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
So I'm pretty sure that it doesn't work. 

How could I fix it?
In the past I tried to start firestarter without asking the password at boot. Just to make sure that you have all the information...
Thank you for your attention...Please be kind and tell me how to slve this problem...

---

### Post by bodhi.zazen on 2008-01-06
> **casalino.luca said:**
> Help! I install Firestarter and click on the icon and the GUI doesn't show up at all to set up the rules. I tried to reinstall it at least twice and it doesn't work. I'm running ubuntu 7.10 and I can tell you that it doesn't work because if I run sudo iptables -L I see this kind of output:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
So I'm pretty sure that it doesn't work. 

How could I fix it?
In the past I tried to start firestarter without asking the password at boot. Just to make sure that you have all the information...
Thank you for your attention...Please be kind and tell me how to slve this problem...

Firestarter must be run as root.

FYI I just installed firestarter in 7.10 and had no problem.

Try :```
gksu firestarter
``` in a terminal and post any error messages.

---

