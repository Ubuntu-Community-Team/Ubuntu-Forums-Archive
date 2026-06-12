---
title: "torrent on server with cron"
date: 2009-12-19
forum: Server Platforms
---

### Post by lmicu on 2009-12-19
I am looking to set up a torrent (to download only legal items that are NOT copyrighted ..... ) on my server. I do not want GUI and I would like to cron it so it only runs at night.

Right now I am using rTorrent and the .watch directory is amazing. I connect via ssh to my server and I mounted the watch directory on my laptop, so when I want to download something I look it up on  y laptop and place it in the watch directory and tomorrow morning ... voila. It is here.

Problem:

rTorrent seems to slow, the " next morning" is like couple od days away, when I know if I would be to use Transmission GUI it would be much faster, much much faster.

I got Transmission CLI but I cant set it up. I am new in Linux so small problems for you means big ones for me.

I would like a torrent client with the ".watch" feature if possible.

PS: When I start transmission I get 

Cannot connect to homeserver:9091: Name or service not known

---

### Post by shawn.abdushakur on 2010-05-12
i'm not sure if i'm having the same problem as you, but i'll describe it and we'll see as it sounds similiar. i have rtorrent installed on ubuntu lucid server. rtorrent runs fine. the problem is that when i let rtorrent run i lose the ability to ssh into or mount my server. it just hangs. if i restart the networking daemon at the server, everything returns to normal. i actually had the same problem on 8.04 with transmission-cli, but it wasn't this bad. previously, if i just let it hang for a while it would eventually ssh in, but not now.

any help would be greatly appreciated. i'm not sure where to look to start diagnosing this. thanks in advance.

shawn

---

### Post by gobbledigook on 2010-05-12
hi there!

You will need to use look at the transmission config file in your home directory:

     ~/.config/transmission

to set it to scan a folder to pick up .torrent files and where to put them etc... may even be a schedule option in here i havn't seen! check out the descriptions of the options [here](http://trac.transmissionbt.com/wiki/ConfigurationParameters)

then its just a matter of adding this to cron, see the [cron wiki](en.wikipedia.org/wiki/Cron) page, it's very informative :)

this is a basic set-up... i personally really like utorrent, so i run it under wine in a minimal xsession using fluxbox, this gives access to a great webui, and all the features of utorrent, ie the schedular etc... you can connect directly to the xsession by setting up a vnc server and using a vnc client...

@ shawn.abdushakur

check the number of open connections for your bandwidth and also that you have enough RAM

---

### Post by Boondoklife on 2010-12-19
[]("http://ubuntuforums.org/member.php?u=695343")@lmicu If you want a scheduler, you can use one I wrote for my WD MyBook.

[[LINK]("http://dl.dropbox.com/u/4804818/scripts/checktransmission")]

I am working on an RSS script too that will supliment it. As of now you can just add the links to the text file and it queues them in one after the other. It also polices to make sure seeds get removed at the set ratio as well as resuming paused torrents once the torrent queue is empty.

Set it in a cron job and you have a great queue manager.

---

