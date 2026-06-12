---
title: "Seed torrents from server?"
date: 2010-01-03
forum: Server Platforms
---

### Post by Jonasu on 2010-01-03
I'm just wondering if there's a way to seed torrents from ubuntu server 9.10, I have tried to google it, but I couldn't find the answer. But if it is possible, I would like to know if there is a way to start seeding a file with a php script.

Thanks in advance. :)

---

### Post by Lars Noodén on 2010-01-03
P2P means peer-to-peer, so each 'client' is also a 'server'.  That's the long way of saying, "yes, you can"

Install a torrent utility of some kind and let it roll.  Here are some for a server, but there are more if you look:

[btpd](http://www.murmeldjur.se/btpd/) is very simple

[transmissioncli](http://linux.die.net/man/1/transmissioncli) is actually web-based

---

### Post by Jonasu on 2010-01-03
> **Lars Noodén said:**
> P2P means peer-to-peer, so each 'client' is also a 'server'.  That's the long way of saying, "yes, you can"

Install a torrent utility of some kind and let it roll.  Here are some for a server, but there are more if you look:

[btpd](http://www.murmeldjur.se/btpd/) is very simple

[transmissioncli](http://linux.die.net/man/1/transmissioncli) is actually web-based

Thanks. But from what I've tried before, it looks like I've already have installed btpd on my server, but the problem is, when I type btpd --help, is says nothing about how to start seeding a file, witch is what I want. So if you could provide me a command to do this it would be really helpful!

---

### Post by HighCommander540 on 2010-01-03
> **Jonasu said:**
> Thanks. But from what I've tried before, it looks like I've already have installed btpd on my server, but the problem is, when I type btpd --help, is says nothing about how to start seeding a file, witch is what I want. So if you could provide me a command to do this it would be really helpful!

Bro, do you not understand BitTorrent? To seed just use the torrent file for the torrent, when it is done downloading the files it will start seeding it.

And if you mean you want to create a torrent from files you have and seed it. Just create the torrent and you are done.

---

### Post by BkkBonanza on 2010-01-03
I think the command you want is given in the help/readme,

btcli add -d foo.torrent.d foo.torrent

I'm not sure if that creates a new torrent from source files though. I didn't see a command for that but transmission has a create (-c) command.

---

### Post by Lars Noodén on 2010-01-04
Here's approximately how I launch **btpd** with the user **torrent**

```

# start btpd
HOME=/var/torrents sudo -u torrent \
       /usr/local/bin/btpd -d /var/torrents/.btpd \
        -p *XXXX* --bw-out *YYY* --max-peers *ZZZ* \
        --logfile /var/log/btpd/bt.log &

```

Here's approximately how I launch a new torrent:

```

# add a new torrent
HOME=/var/torrents /usr/bin/sudo -u torrent \
       /usr/local/bin/btcli -d /var/torrents/.btpd \
          add -d /var/torrents/ *kubuntu-9.10-alternate-amd64.iso.torrent*;

```

One point of confusion is that **-d** is used in two different contexts.  Before the command **add** it means the directory where btpd stores its working files.  After, it means the directory where the torrents shall be found.  

Neither of the above code snippets will work as-is without the proper directories, users and permissions, but should nonetheless serve as a model.

Once **btcli** can show a list of torrents, you can start or stop them by number.

I've been sticking with btpd because it works purely in a shell environment.  Maybe I'm missing something about transsmissioncli, but despite the name, it doesn't seem to be able to do that and the built-in web server it uses seems dependent on javascript.

---

### Post by BkkBonanza on 2010-01-04
That's interesting. From the readme it looked like you had to provide a torrent file for the add command. From your example it appears you can provide a "data file" that will be the source for a torrent. So I take it that it work either way. Provide a torrent to download from or a datafile to create a torrent to seed? 

I'm just curious because I actually use Deluge here. Someday I may want to run a cmd line torrent and btpd seems like it would be a nice lightweight way to do it.

---

### Post by K.J. on 2010-01-04
I highly recommend rtorrent. Although, it lacks a daemon feature, so you'll need to run it with the screen command to keep it going in the background. There are also a number of web UI for it. I use ruTorrent which emulates the uTorrent GUI.

---

### Post by Lars Noodén on 2010-01-04
> **BkkBonaza said:**
> ...Provide a torrent to download from or a datafile to create a torrent to seed? .

Sorry.  Mouse bounce truncated the filename.  Yes, like with other torrents, you have to have the torrent file and add that.  I usually grab them with **wget**.

---

### Post by BkkBonanza on 2010-01-04
Ah, I see now. So does btpd have any way to create a new one? Sometimes called "super-seed", where it acts as the originating seed. It probably doesn't as that appears to be more complicated, involving trackers. I see in Deluge I can do that but I have never tried it.

---

### Post by Lars Noodén on 2010-01-05
btpd doesn't seem to have anything to create fresh torrents ... yet. 

I got curious enough to look around and torrent files contain [specific metadata](http://www.bittorrent.org/beps/bep_0003.html) bout the torrent, all packed up as [bencode](http://effbot.org/zone/bencode.htm).  There appears to be a [bencode library](http://packages.ubuntu.com/karmic/libbtutil0) for ubuntu in the universe repository, but it's not clear from just looking at the web page if it can actually *encode* a torrent file.  

So, it is "just" a matter of getting the metadata and processing it.


[http://www.bittorrent.org/beps/bep_0000.html](http://www.bittorrent.org/beps/bep_0000.html)

---

### Post by BkkBonanza on 2010-01-05
I know Deluge has a create torrent function. It is written in Python so presumably there is a Python library that has this function and the source could always be browsed. Seems like something to add someday. The thing I'm not too sure about is the "tracker". I suppose if you start a new torrent and then add it to a torrent site then they manage the trackers for it. But when you want to just share privately can it be done without a tracker? Somehow it has to know which IPs to contact.

I use torrents often enough but I have never seeded a new one like this, so I was just curious about it. I guess I should just try it sometime to see.

---

### Post by Adina on 2010-01-05
When you create a new torrent file you need to specify which trackers you want to use for that torrent. If you try to seed a torrent without a tracker then you will not know who else is sharing that same file. A tracker announces who is currently sharing the torrent to peers. If you want to share a file privatly you could just make your own tracker with opentracker and have it run on your server, It's really simple.

---

### Post by BkkBonanza on 2010-01-05
Thanks Adina. Good to know about that part of it.

---

### Post by nerr on 2010-01-05
> **K.J. said:**
> I highly recommend rtorrent. Although, it lacks a daemon feature, so you'll need to run it with the screen command to keep it going in the background. There are also a number of web UI for it. I use ruTorrent which emulates the uTorrent GUI.

rtorrent is most definitely the way to go.  I've been running it for six months 24/7 and have had no issues with it.

[http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html](http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html)

[http://libtorrent.rakshasa.no/downloads/libtorrent-0.12.6.tar.gz](http://libtorrent.rakshasa.no/downloads/libtorrent-0.12.6.tar.gz)
[http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.6.tar.gz](http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.6.tar.gz)

The newest versions are libtorrent 0.12.6 and rtorrent 0.8.6.  You can install older versions of libtorrent/rtorrent from repositories, but compiling from source is painless and will give you the latest and most stable version.  Just replace the old download links given in the tutorial with these up-to-date ones and you should be all set.  rtorrent is very light on resources and can be used very easily over SSH, both of which I find key for operating in a server environment.

---

### Post by Jonasu on 2010-01-05
Oh! Sorry for not responding, I totally forgot this topic.. Anyway, thanks for all response, I do know how to do this now.

A possible way I was thinking of doing it was to allow my friends to upload files to my server through a web app, then create a php script using **[this]("http://w-shadow.com/blog/2008/11/11/parse-edit-and-create-torrent-files-with-php/")** to create a torrent file. After that I'll make the php script run a shell command to add the new torrent file for seeding using my own tracker.

I don't know if it is possible to create a bash script to add the torrentfile for seeding using the +s bit to run it as sudo? I don't know if you can add the s bit on scripts ether.. If someone is familiar with it, I would appreciate some feedback.

Thanks.

---

### Post by Lars Noodén on 2010-01-07
> **Jonasu said:**
> 
I don't know if it is possible to create a bash script to add the torrentfile for seeding using the +s bit to run it as sudo? .


The SUID option would be a big security risk:  If the SUID file gets re-written then it will still run whatever it contains as that user.  Or if there is a way for the file to run another file, same problem.  

sudo by itself will run it as another user.  The following snippet in /etc/sudoers would allow btpd to be run as user 'btorrent' by any account that is a member of the group 'torrenters', but only with the options exactly as provided

```

# allow btpd
%torrenters   ALL=(btorrent) NOPASSWD: \
     /usr/local/bin/btpd -d /var/torrents/.btpd \
        -p 24556 --bw-out 100 --max-peers 10 \
        --logfile /var/log/btpd/bt.log 

# allow adding torrents, hopefully only from a single directory
%torrenters   ALL=(btorrent) NOPASSWD: \
     /usr/local/bin/btcli -d /var/torrents/.btpd \
          add -d /var/torrents/ [a-zA-Z0-9.]*,   \
     /usr/local/bin/btcli -d /var/torrents/.btpd \
          add -d /var/torrents/ !  *..*;

```

Triple check the regex or globbing in sudoers, it doesn't always work the way it looks like it might.  The btcli example should allow any user in the group 'torrenters' to add a torrent from the directory /var/torrents

---

### Post by Vegan on 2010-01-07
Install the desktop, it includes a torrent client. It is that simple.

:guitar:

---

### Post by Lars Noodén on 2010-01-08
> **Vegan said:**
> Install the desktop, it includes a torrent client. It is that simple.


As above, there are many ways to install a torrent.  

Adding a whole desktop meta package to a server is a Bad Idea(tm) to try, as it violates the [K.I.S.S. principle](http://catb.org/jargon/html/K/KISS-Principle.html) in a very big way by installing hundreds of unrelated, unneeded and undesirable (in the context of a server) packages.

---

