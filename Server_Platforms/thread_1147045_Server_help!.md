---
title: "Server help!"
date: 2009-05-03
forum: Server Platforms
---

### Post by V1ru586 on 2009-05-03
Hello:
I've been using Ubuntu for quite a while and i must say i love it!!! It's the most amazing OS in the planet!!!...now put that aside..here what i wanna do and i hope you guys can help me:P
I've been trying to set up a home server to host my files such as movies, games, music, and other stuff. i've been reading about windows server, freeNAS, they all sounds good but since i love ubuntu i wonder if i can use it as a server, am new to the features of ubuntu, i know it can do wonders. but can i make it into a home server?? thanks in advance!!!! and I LOVE UBUNTU!!!!

---

### Post by Iowan on 2009-05-03
Sure - Ubuntu can do that... In fact, there's a server version of Ubuntu (but comes without GUI). Most of the "server" programs can be added to a desktop version of Ubuntu.  [Here]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is a help page to get you started. Another good place is [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu"). There is usually a "perfect server" setup for the current version of Ubuntu.

---

### Post by V1ru586 on 2009-05-04
i forgot to mention that most of my computers connected to the network are going to be windows...would that change anything?

---

### Post by wouterke on 2009-05-04
You might want to lookin into setting up a Samba share then (i assume the windows machines will want to use "shared folders") 
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")


if you want to be able to reach the server from the outside you can forward the necesary ports on your router and install ddclient 
a how to for that can be found here ; [http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html]("http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html")

---

### Post by V1ru586 on 2009-05-05
thats seems like a very good option, i've been reading about freeNAS and it seems more simpler to set up than ubuntu. what do u guys think?

---

### Post by ugm6hr on 2009-05-06
> **V1ru586 said:**
> thats seems like a very good option, i've been reading about freeNAS and it seems more simpler to set up than ubuntu. what do u guys think?

I'm an equally big Ubuntu fan, using it on my main computer and netbook.

However, after a short period of experimentation with Ubuntu server for my home server, I went with FreeNAS for its simplicity.

The only reasons not to use FreeNAS: you want to learn more about Linux / Ubuntu; you need a print server; you need a database server.

For simple file server / sharing, FreeNAS is perfect, and includes Fuppes for uPNP if you have a PS3 etc.  It will also run from a USB stick, and allow easy backup / restore of settings.  Running it from a USB stick means that if the server computer breaks, it is easy enough to retrieve the data and server by simply replacing the HD and USB into a new networked computer.

Check out the link below for further details.

---

### Post by V1ru586 on 2009-05-06
> **ugm6hr said:**
> I'm an equally big Ubuntu fan, using it on my main computer and netbook.

However, after a short period of experimentation with Ubuntu server for my home server, I went with FreeNAS for its simplicity.

The only reasons not to use FreeNAS: you want to learn more about Linux / Ubuntu; you need a print server; you need a database server.

For simple file server / sharing, FreeNAS is perfect, and includes Fuppes for uPNP if you have a PS3 etc.  It will also run from a USB stick, and allow easy backup / restore of settings.  Running it from a USB stick means that if the server computer breaks, it is easy enough to retrieve the data and server by simply replacing the HD and USB into a new networked computer.

Check out the link below for further details.

wow ur link helped me out a lot thanks!!!!!

---

### Post by V1ru586 on 2009-05-09
Okay now that i have set up my searver ( which is working really good so far), i wanna be able to access it outside my network.. i've tried certain websites such as no-ip but i cannot get it to work.. any help will be greatly appreciate it! thanks!

---

### Post by ugm6hr on 2009-05-09
I believe you now have a functioning FreeNAS server.

In order to access the FreeNAS settings page from outside your LAN, you need:

1. A no-ip / DynDNS account (I use DynDNS)
2. The FreeNAS settings page port forwarded on your router (default 80)

In order to give more detailed advice, you will have to provide:

1. Your FreeNAS ip address
2. Your router make / model

Remember, it is impossible to check whether your no-ip address forwards correctly from within your LAN.  You need to check it from somewhere else.

Also, I am not a security expert, and don't personally allow internet access to the settings page (only my webserver).

---

### Post by Vegan on 2009-05-09
I have an old WRT54G and I have ports setup for the usual cast of characters. I use Samba which is simple to do behind the firewall. I was up in minutes with a simplistic setup.

All I did was make an unsecured share of the web server folders so I could use Windows tools. Works fine for me.

My Linux sever runs my web sites. On the LAN Samba allows me to see the machine from XP to Windows 7 no problem.

---

### Post by V1ru586 on 2009-05-11
okay my freeNAS address is 192.168.1.250
router model is a WRT54GS

okay i was able to get it to work via DynDNS.com
i can acces my freeNas Server page. now can i actually access my files doing the same way?? aswell as my bittorrent service??

---

### Post by ugm6hr on 2009-05-11
> **V1ru586 said:**
> i can acces my freeNas Server page. now can i actually access my files doing the same way?? aswell as my bittorrent service??

I think that the File Manager works on the same port as the Admin page, so should work from the link on the Admin page.

To access the Transmission page, you will need to forward that port too (it tells you which port on the Torrent settings page).

---

### Post by V1ru586 on 2009-05-11
well all i can see is my freeNas page. i cannot access my files

---

### Post by Wiebelhaus on 2009-05-11
This is very very simple , if your just looking to set up a file server then [here's a how to that will spare me having to explain it]("http://www.howtoforge.com/ubuntu-home-fileserver") , the information there is old but this is a fundamental core ability of any linux system more or less so the information hasn't changed that much. 

Once you start setting it up jump on the boards for advice and we can simply walk you through it.

Cheers!

---

### Post by ugm6hr on 2009-05-11
> **V1ru586 said:**
> well all i can see is my freeNas page. i cannot access my files

From within the LAN, try [http://192.168.1.250/quixplorer/](http://192.168.1.250/quixplorer/)

Or Advanced -> File Manager

---

### Post by V1ru586 on 2009-05-11
> **ugm6hr said:**
> From within the LAN, try [http://192.168.1.250/quixplorer/](http://192.168.1.250/quixplorer/)

Or Advanced -> File Manager
within my network i can access the files without a problem, my problem is accessing them remotely for example from a  friends house?? i've been using filezilla to download and upload files to any computer. but i was just wondering if i can use something else such as the browser to download and upload files to my network? once again i can browse my files within my network without a problem!

---

### Post by ugm6hr on 2009-05-12
If you want to use FTP (FileZilla), forwarding port 21 from your router to the FreeNAS ip should do it.  Then just use your DynDNS url to connect.

Quixplorer allows downloads but not uploads, which should be available at [http://your_dyn_dns_url/quixplorer](http://your_dyn_dns_url/quixplorer)

---

