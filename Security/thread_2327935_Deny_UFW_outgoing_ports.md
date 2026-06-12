---
title: "Deny UFW outgoing ports"
date: 2016-06-15
forum: Security
---

### Post by cooloutac on 2016-06-15
[http://ubuntuforums.org/showthread.php?t=1893751](http://ubuntuforums.org/showthread.php?t=1893751)    

Wanted to reopen the above thread cause its a great tutorial for UFW.  But just wanted to add that instead of step1,  to default block all ports just do:  

ufw default deny outgoing  

And rules go top to bottom,  so for the deny rules in step 4,  they have to go above the allow rules.  You can edit /lib/ufw/user.rules   and move them up.  

Also a gui to make things easier is gufw.  

cheers.

---

### Post by danbosse1 on 2016-07-03
[SIZE=3][FONT=arial]I want the thread open as well. [/FONT][/SIZE]

The listed below allows 53(dns) 80(http) 443 (https) 123(time) 8080(alt. http)

[LEFT][SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo ufw default deny incoming  [/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo ufw default deny outgoing  [/FONT][/COLOR][/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3][COLOR=#000000][I]internet  
  [/I][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo ufw allow out 53  [/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo ufw allow out http  [/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo ufw allow out https  [/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo ufw allow out 123/udp  [/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo ufw allow out 8080  [/FONT][/COLOR][/SIZE][/LEFT]
[SIZE=3]   
I have default deny incoming and outgoing and prefer to learn about the system by **allowing** things to happen!  
It seems that disabling ICMP also disables my ability to Ping from the Command Line.  

Anyone else having this problem or others from a very controlled firewall setting?[/SIZE]

---

### Post by jeremy31 on 2016-07-03
I see no reason to reopen a 5 year old thread when this one is active

---

