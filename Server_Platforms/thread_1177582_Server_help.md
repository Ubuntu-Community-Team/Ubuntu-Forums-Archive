---
title: "Server help"
date: 2009-06-03
forum: Server Platforms
---

### Post by Pur30wnage on 2009-06-03
I am currently making a server for Sourceforts and I am have trouble starting it. I am up to the last command using your guide, [http://www.sourcefortsmod.com/index.php?p=site_info_linux](http://www.sourcefortsmod.com/index.php?p=site_info_linux). I am using Ubuntu Server (linux). When i enter in the command ./srcds_run -console -game sourceforts +map sf_magma +maxplayers 16 +ip 67.255.255.255 (of course with my own information) in the /usr/home/steam directory it says, -bash: ./srchs_run: No such file or directory, could you tell me what I am doing wrong?

---

### Post by alastair on 2009-06-03
Well ... is there a "srchs_run" in the current directory ./ ?

If you do :

ls -l

Does a file called "srchs_run" exist?

Has it execute permission, so you can run it?

---

### Post by Pur30wnage on 2009-06-03
bin            mapcycle.txt  media       resource              sourceforts.fgd
cfg            maplist.txt   models      scripts               voice_ban.dt
CHANGELOG.txt  maps          motd.txt    SF1941-Server.tar.gz
gameinfo.txt   materials     README.txt  sound

That is all that is in there

---

### Post by v3xtra on 2009-06-03
I think it would be in bin.....?

---

### Post by Pur30wnage on 2009-06-06
client.dll  server.dll  server_i486.so

that is all in bin.

---

### Post by Serangan on 2009-06-07
Have you run ```
./steam -command update -game "hl2mp" -dir .
``` ?

I've had a css server running on my ubuntu box.

---

