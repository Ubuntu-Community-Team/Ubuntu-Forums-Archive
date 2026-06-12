---
title: "Installing rtorrent gives me an error"
date: 2010-06-07
forum: Server Platforms
---

### Post by imjakes on 2010-06-07
Hi,

I have followed this HOW-TO [http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/](http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/)
 on how to install rtorrent.

Now i get the following error : cannot find readable session directory  from config /home/rt/.rtorrent.rc. check permissions
when i try to start the rtorrent by using :
sudo /etc/init.d/rtorrent start

The file /home/rt/.rtorrent.rc looks like this :
> scgi_port = localhost:5000
min_peers = 40
max_peers = 100
min_peers_seed = 10
max_peers_seed = 50
max_uploads = 15
#upload_rate = 50
directory = /home/rt/torrents/doing
session = /home/rt/sessions
schedule = watch_directory,5,5,load_start=/home/rt/torrents/watch/*.torrent
schedule = tied_directory,5,5,start_tied=
schedule = untied_directory,5,5,close_untied=
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/rt/torrents/$
on_start    = link1,"create_link=tied,,.started"
on_stop     = link1,"delete_link=tied,,.started"
on_finished = link1,"create_link=tied,,.finished"
on_erase    = link1,"delete_link=tied,,.finished"
schedule = low_diskspace,5,60,close_low_diskspace=100M
#schedule = ratio,60,60,"stop_on_ratio=120,200M,2000"
port_range = 63963-63981
port_random = no
check_hash = yes
use_udp_trackers = yes
encryption = allow_incoming,try_outgoing,enable_retry
dht = auto
dht_port = 63982

The directory /home/rt/sessions does exists and i have run the following to give me permisson to that directory :
 sudo chmod 777 /home/rt -R

What am i missing?

Regards,
Jacob

---

### Post by retry32 on 2010-06-07
Use nTorrent its rTorrent but then with a gui and Java based

[http://code.google.com/p/ntorrent/](http://code.google.com/p/ntorrent/)

Greets RetRy

---

### Post by imjakes on 2010-06-07
Perhaps i should tell im using Ubuntu - commandline server 10.04

---

### Post by konsole on 2010-06-07
> **imjakes said:**
> 
The directory /home/rt/sessions does exists and i have run the following to give me permisson to that directory :
 sudo chmod 777 /home/rt -R

What am i missing?

Regards,
Jacob
You've just created your system's first security hole. Don't make folders world readable or writable unless absolutely necessary. Only the rtorrent user needs write access to this folder. chmod it 744 

If the problem is not permissions then it is ownership.

```
man chown
```

---

### Post by imjakes on 2010-06-07
> **konsole said:**
> You've just created your system's first security hole. Don't make folders world readable or writable unless absolutely necessary. Only the rtorrent user needs write access to this folder. chmod it 744 

If the problem is not permissions then it is ownership.

```
man chown
```

Thanks for the warning have changed it to 744

Tryed following : sudo chown jakes:jakes /home/rt -R
(my user is jakes)

And it changes nothing still the same error?

---

### Post by konsole on 2010-06-07
> **imjakes said:**
> Thanks for the warning have changed it to 744

Tryed following : sudo chown jakes:jakes /home/rt -R
(my user is jakes)

And it changes nothing still the same error?

Start rtorrent from the console and note any error messages. Your startup script may be borked.

```
shellprompt#/usr/local/bin/rtorrent
```or wherever rtorrent is installed.

good luck.

---

### Post by imjakes on 2010-06-08
> **konsole said:**
> Start rtorrent from the console and note any error messages. Your startup script may be borked.

```
shellprompt#/usr/local/bin/rtorrent
```or wherever rtorrent is installed.

good luck.

Im sorry but i do not understand what you mean?

---

### Post by arrrghhh on 2010-06-08
> **imjakes said:**
> Im sorry but i do not understand what you mean?

He wants you to run it by hand as the same user that you run rtorrent in your script...

So kick off rtorrent yourself and give us the output.



Oh, and it looks like your rtorrent user is rt, not jake.  /home/rt gave it away - perhaps chown everything in that folder to rt:rt instead.

---

### Post by BobVila on 2010-06-08
Are you starting the rtorrent process as jakes, or as rt?
Might want to su to rt and try that as well while you're working on the permissions soup you've created.

---

