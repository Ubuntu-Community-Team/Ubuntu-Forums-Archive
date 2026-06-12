---
title: "firestarter everytime how ?"
date: 2005-12-20
forum: Server Platforms
---

### Post by rfruth on 2005-12-20
Just getting started with Breezy here, I can run FS manually no problem but would rather it start everytime Breezy boots so using the help file & the wiki I added FS to the systems > sessions > startup programs and you guessed it now I get the not enough privilege error message (whatever it is) how can I get around this ?

---

### Post by cactus on 2005-12-20
googled it.
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by rfruth on 2005-12-20
A simple web search did it, thanks ! (gedit ver 2.x reports access denied when I try to edit /etc/sudoers but I should be able to figure that out) #-o

---

### Post by cactus on 2005-12-20
edit sudoes with visudo. it is a command line utility (vi wrapper I think).

EDIT:
[http://www.courtesan.com/sudo/man/visudo.html](http://www.courtesan.com/sudo/man/visudo.html)

looks like you can use gedit too if you like.
$ export EDITOR=`which gedit`
$ sudo visudo --with-enveditor

that might work.

---

### Post by towsonu2003 on 2005-12-20
wasn't auto-starting FS on startup not trendy any more? [http://ubuntuforums.org/showthread.php?t=93974&highlight=firestarter+joke](http://ubuntuforums.org/showthread.php?t=93974&highlight=firestarter+joke) ;)

---

### Post by tokyovigilante on 2005-12-21
You don't need to start the Firestarter GUI at boot. Firestarter is not a firewall on its on, it is only an easy way to configure the kernel iptables rules, which control network activity and routing on a Linux machine with a 2.6 kernel. 

The GUI is only for modifying existing rules and for checking your log. Firestarter also has a constantly running daemon which adds the rules you have defined with the GUI at boot, hence not needing the GUI running all the time.

The reason running the GUI all the time isn't "trendy" is because it runs as root, and leaving it open all the time, and allowing it into the sudoers file, gives people with physical access to your machine carte blanche access to your firewall configuration, allowing for all sorts of port-opening shenanigans.

The firewall runs whether the GUI is active or not.

---

### Post by frodon on 2005-12-21
I agree, it's more secure to not use firestarter with the GUI always opened.
As tokyovigilante said firestarter is always running, type this command if you want to be sure : ```
sudo /etc/init.d/firestarter status
```However if you still want to launch the GUI on each startup even if it's lesss secure, look here : [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by rfruth on 2005-12-21
What a wealth of info this group is !:)

---

