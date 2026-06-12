---
title: "Bind9 Setup Via Webmin Issue"
date: 2014-08-13
forum: Server Platforms
---

### Post by wayne19 on 2014-08-13
Hello and thank you for any help in advance , I have set up a server, now i really want bind9 to work and can't understand why its not working,

can i for the life of me get this thing to work, I suspect its a setting in a conf file somewhere or something but maybe someone with more experience can help me a bit.

i am on a vps which is ubuntu server 14.04 i have followed tutorials till i am blue in the teeth, this is a last resort to try and get this sorted before i turn green :) 

so i have apache 2 installed 

php

phpmyadmin 

nano 

bind9

msmtp

webmin 

every tutorial i have followed basically resides around this [Setting Up DNS Using Webmin - ServerPronto]("http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&ved=0CDQQFjAC&url=http%3A%2F%2Fwww.serverpronto.com%2Fkb%2Fpage.php%3Fid%3DSetting%2BUp%2BDNS%2BUsing%2BWebmin&ei=rPXqU_s-jp7sBvyHgJAM&usg=AFQjCNHryS-J-TmLgp4mzjwVud7ZjbQ1FA&bvm=bv.72938740,d.ZGU")  really not sure what to do now, my friend is on the same server and he got this method to work so clearly he has forgot to tell me how to edit apache conf file or some sort of file any help would be great i am quite new to this but can use command line if required.

oh yes getting SERVFAIL error on nslook up

[FONT=Menlo];; Got SERVFAIL reply from 8.8.8.8, trying next server[/FONT]
[FONT=Menlo];; Got SERVFAIL reply from 8.8.8.8, trying next server[/FONT]
[FONT=Menlo]Server:		8.8.4.4[/FONT]
[FONT=Menlo]Address:	8.8.4.4#53[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]** server can't find testtest.tk: SERVFAIL[/FONT]

---

### Post by Doug S on 2014-08-13
Hi and welcome to Ubuntu forums,

You are using the google name servers. Try forcing the use of your own name server. Example:```
doug@doug-64:~$ [COLOR=#ff0000]nslookup carrie.smythies.com - 8.8.4.4[/COLOR]
Server:         8.8.4.4
Address:        8.8.4.4#53

** server can't find carrie.smythies.com: NXDOMAIN

doug@doug-64:~$ [COLOR=#ff0000]nslookup carrie.smythies.com - 127.0.0.1[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   carrie.smythies.com
Address: 192.168.111.106
```

---

### Post by wayne19 on 2014-08-13
Where do you edit this file ?? Nano /etc/resolv.conf ?? Not sure thanks in advance

---

### Post by SeijiSensei on 2014-08-13
If you are using static IP addressing, which is the norm for servers, then you can add this line to the stanza for eth0:
```
dns-nameservers 8.8.8.8 8.8.4.4
```
For more details: [https://help.ubuntu.com/14.04/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/14.04/serverguide/network-configuration.html#name-resolution)

---

### Post by wayne19 on 2014-08-13
Its a paid for unmanaged ubuntu 14.04 server what is the stanza ?? New to all this .

---

### Post by wayne19 on 2014-08-13
Bit confused now so do i edit 2 files ??

---

### Post by nerdtron on 2014-08-13
DNS servers is defined in the /etc/network/interfaces file along with the static IP address of the server. Or you can also add them to the /etc/resolv.conf

How do you edit files? There's nano and there's vim. Both are command line editing tools.

Users come here and setup server and even install webmin and they don't know how to edit files? I don't want to sound a bit harsh but to be a system admin, you should first practice on the basics of the command line and system administration before going all out an installing your own bind9 dns server, etc.

---

### Post by wayne19 on 2014-08-13
I have setup lots of servers, I am familiar with command line just never have been able to get bind 9 working as always it will be something silly but can i find it :) no so this is why i am here to find out why i shall go in and edit these files now then reboot the server to see if it works.

---

