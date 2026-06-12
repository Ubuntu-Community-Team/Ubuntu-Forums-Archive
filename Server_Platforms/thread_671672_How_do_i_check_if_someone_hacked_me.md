---
title: "How do i check if someone hacked me ?"
date: 2008-01-18
forum: Server Platforms
---

### Post by ShAd0w14 on 2008-01-18
so... everything was working fine... but the other day my X restarted (a week or so ago..) and now it does that every ?second? day if i remember well... more than just once... i have no ports open (only 80) i don't run ftp,ssh or someting like that... my password has 18 characters and i checked my sistem with rkhunter and it's clean (it says of 3 hidden files in /dev i deleted two of them but the one won't delete... it says it can't be deleted because  Device or resource is busy)...and 5 days ago i find my 'Music' map in trash... not only once... but more then just once o_0... so now i want to know what would YOU do ?... oh if you think it's a driver error because of the X reboot... i'm using the same drivers when i got gutsy... so i don't think so :s...

---

### Post by Vinno on 2008-01-18
Take rkhunter lightly, just because it says few files in your /dev is hidden, doesnt mean you have to delete it. Only delete what you know, google what the file is, might be an important file.

Also what do you mean by music map?

---

### Post by HermanAB on 2008-01-19
Some basic checks:
Check /var/log/messages for logins.
Run 'who' to see if anyone else is logged in.
Examine /etc/passwd to see if a new user was added that you don't know about.

BTW, usually, people break into servers in order to install a spam engine.  So if your machine slows down unexpectedly, then run 'top' and 'tcpdump' to see what is going on.

Cheers,

Herman

---

### Post by ShAd0w14 on 2008-01-19
Delete This One Please.

---

### Post by ShAd0w14 on 2008-01-19
thank you all for help...
@Vinno: i have a map called 'Music' on the desktop and i found it in trash several times... (this hasn't happened to me now for about 3 days but stil..) oh and does someone know why firestarter always crashes when it runs ? this is the output from terminal
marko@shadow:~$ sudo firestarter
iptables v1.3.6: host/network `kornbluth.freenode.net' not found
Try `iptables -h' or 'iptables --help' for more information.
Firewall started
Segmentation fault (core dumped)
marko@shadow:~$

and then it crashes

---

### Post by HermanAB on 2008-01-19
Don't worry about Firestarter.  It always crashes.  That is normal behaviour.

Note that the part that crashes doesn't affect the real firewall, so the crashing doesn't matter, which is probably why no-one bothered to fix it.

---

### Post by x3roconf on 2008-01-20
> **ShAd0w14 said:**
> so... everything was working fine... but the other day my X restarted (a week or so ago..) and now it does that every ?second? day if i remember well... more than just once... i have no ports open (only 80) i don't run ftp,ssh or someting like that... my password has 18 characters and i checked my sistem with rkhunter and it's clean (it says of 3 hidden files in /dev i deleted two of them but the one won't delete... it says it can't be deleted because  Device or resource is busy)...and 5 days ago i find my 'Music' map in trash... not only once... but more then just once o_0... so now i want to know what would YOU do ?... oh if you think it's a driver error because of the X reboot... i'm using the same drivers when i got gutsy... so i don't think so :s...

What php scrips (like phpbb) you are running? (if any) Attackers usually leave some kind of phpshell if they decide to compromise trough apache..

---

### Post by tjk on 2008-01-20
> **ShAd0w14 said:**
> thank you all for help...
@Vinno: i have a map called 'Music' on the desktop and i found it in trash several times... (this hasn't happened to me now for about 3 days but stil..) oh and does someone know why firestarter always crashes when it runs ? this is the output from terminal
marko@shadow:~$ sudo firestarter
iptables v1.3.6: host/network `kornbluth.freenode.net' not found
Try `iptables -h' or 'iptables --help' for more information.
Firewall started
Segmentation fault (core dumped)
marko@shadow:~$

and then it crashes

Just finished trying it again and it still is crashing for me too.  I wish they'd fix it. It's my favorite firewall frontend.  I've been trying Firestarter on and off for the past couple years.  Seems to me that it ran well on Drapper, but it hasn't been happy with both Feisty and Gutsy.  I guess I could add my bit to the bug list...

---

### Post by ShAd0w14 on 2008-01-20
@x3roconf: i don't run any php scripts... this is just a normall desktop computer...

---

### Post by AlexShd on 2008-01-22
Try 
sudo nmap -v <your IP address>
if you see some strange or not used ports close them or remove the program that uses them. 
netwatch - nice program from command line to see network activity

---

