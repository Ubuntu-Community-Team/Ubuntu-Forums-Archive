---
title: "server freezes"
date: 2006-07-09
forum: Server Platforms
---

### Post by Isoss on 2006-07-09
I have an ubuntu-server and I work on it using ssh from my laptop. I can see the localhost of the server by entering the server's ip in the browser of my laptop " [http://192.168.0.1](http://192.168.0.1) " and I can edit the files of /var/www using ssh with bluefish and it works just fine. But the server sometimes freezes ... I can say it's the browser of the laptop that freezes when trying to connect to  [http://192.168.0.1](http://192.168.0.1) in two situations:
1. When I hit refresh more than twice very fast!
2. When I try to insert a big sql file into phpmyadmin. 
Please remember that I am using my laptop on the network and all the work is done on the ubuntu-server PC.

Also I have a problem transfering big files using SSH with remote places. sometimes the PC that is recieving (sometimes when sending) data freezes and requires a restart. sometimes I can just terminate (or force end) but the SSH would never work again unless I restart.

Why is that? and what is the solution?

Thanks in advance.

Isos

---

### Post by atoponce on 2006-07-09
Sounds to me like lack of decent hardware specs.  Whether insufficient RAM or a slow HDD.  On your server, are you running a gui?

---

### Post by Isoss on 2006-07-09
Well .. I believe my RAMs are sufficient! I have 512 for the server and 768 in my laptop. both processors are fast ... and I don't know what is a gui .. I think I have perfect machines so why it's so slow?

Thanks

---

### Post by lamego on 2006-07-09
A Gui is a graphical interface like Gnome or KDE, if you do have GNOME or KDE running on the server with 512 MB its not really that much.
Login to the server and learn to use the commands "top" to watch for cpu usage, and "vmstat" for memory usage.

---

### Post by verbatim210 on 2006-07-10
> **Isoss said:**
> I can say it's the browser of the laptop that freezes 

so what is actually freezing, the server or the **browser of the laptop?**

how can you use ssh to transfer remote files, you need scp.

---

### Post by Isoss on 2006-07-10
[quote=lamego]A Gui is a graphical interface like Gnome or KDE, if you do have GNOME or KDE running on the server with 512 MB its not really that much.[/quote]
I am using KDE for my laptop and Gnome for the server. would it be better if I don't use a desktop environment for ubuntu-server at all? What DE do u think is the best for ubuntu-server?
[quote=lamego]Login to the server and learn to use the commands "top" to watch for cpu usage, and "vmstat" for memory usage.[/quote]
I am not sure how to do that. as I mentioned, I connect to the server using a lotta ways. 1st to view my websites (/var/www) which are located on the server I use the browser from my laptop: [http://192.168.0.1](http://192.168.0.1) (which is the server's IP on the network). I use gftp using ssh2 sometimes so I can transfere files from and to the server. I also use remote places using ssh client by creating a SSH folder of /var/www and here it freezes a lot. I use PuTTy sometimes to run some commands like chmod and cp and rm, apache2 and mysql stop, start, restart and configure some stuff for the network. Here it never freezes. So, I hope you'd explain more on that you mentioned ... I dunno what is top or vmstat! I am not a linux expert so I am still learning here for I've only been using linux for 4 months.

---

### Post by Isoss on 2006-07-10
[quote=verbatim210]so what is actually freezing, the server or the browser of the laptop?

how can you use ssh to transfer remote files, you need scp.[/quote]

Sorry I think it's the server but I ment like it's the port 80 which connects me to the localhost of the server. I am not really sure, not an expert, so forgive me and correct me when I explain or name things wrong. 

What makes me feel it's the server is that when it freezes at the transfere with SSH folders I can't do anything else with the PC ... sometimes applications work but they freeze after countering problems with the transfer. and when it freezes when hitting refresh manytimes too fast or upload a heavey DB to phpmyadmin it feels like it's only the "browser" that can't connect no more to /var/www at the server.

When I first wanted to do my programming work using my laptop and everything is saved on the server I asked here at the server talk (in fact I posted more than 3 times on the topic) and many have suggested SSH. But I'd appriciate it if you'd recommend a better and faster way! I dunno what is scp! is it something like ftp or ssh? ... because sometimes I need to transfer big stuff like media files but that seems impossible. And what if I needed to backup my files to another ubuntu machine? ppl suggested SSH ... is there a better and stronger method?

Thank you all guys.

---

### Post by verbatim210 on 2006-07-10
i think something is incompatible and your hardware drivers maybe outdated or not present at all.

faulty ram perhaps?

to solve this problem you'll need to experiment, try another machine or different hardware.

too many possibilities to come to a realistic conclusion at this moment.

---

### Post by Isoss on 2006-07-11
Thanks. I'll try to check where the problem is and will report the results.

---

