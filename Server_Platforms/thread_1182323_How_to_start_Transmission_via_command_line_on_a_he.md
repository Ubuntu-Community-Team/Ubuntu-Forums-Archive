---
title: "How to start Transmission via command line on a headless server?"
date: 2009-06-08
forum: Server Platforms
---

### Post by davidmigl on 2009-06-08
I am trying to start the transmission bittorent client from a command line on a headless server. I set up transmission (via the gui when I still had a monitor connected) to have the web interface enabled and successfully accessed transmission via the web. Now in headless mode, I have installed transmission-cli and started transmission-daemon. However, I can't access my box via the web interface. I can ssh in just fine.

I've searched around on google and found plenty of things on advanced transmission command line settings and scripts but nothing on just how to start it. There were no posts that had "transmission command line" in the title on these forums.

Thanks in advance for your help!!

David

---

### Post by Charles Kerr on 2009-06-28
Run "transmission-daemon" on the headless server to start a gui-less session there.

There are lots of ways to control this session:

[LIST=1]
[*] point your web browser at port 9091 of the headless server and use the Web UI
[*]  ssh into the server and use "transmission-remote" to query the daemon from the terminal
[*]  Use Transmission's beta Qt GUI to connect
[*]  There are other third-party clients available, such as [this curses one]("http://github.com/fagga/transmission-remote-cli/tree/master") and [this Windows GUI]("http://code.google.com/p/transmission-remote-dotnet").  Most of these third-party clients are listed [here]("http://www.transmissionbt.com/links.php").
[/LIST]

---

### Post by wightman.p on 2010-01-09
Perhaps you have already sorted this out, but here goes anyway:

Open up the Transmission Client GUI, Edit | Preferences | Web

Mine only has 127.0.0.1 as an allowed address, perhaps you'd need to add the IP Address of the viewing box?

---

### Post by xcurtisx on 2011-01-25
Found this thread via google - same issues.
Have a headless Transmission server.
Need to start transmission at boot time and then access via web.
I can do it manually with the monitor hooked up but not auto or from CLI.

Advise?

---

### Post by James78 on 2011-01-25
There's another torrent client you can use that's meant for command line if you want to check it out. It's rtorrent. My friend uses it, and absolutely loves it. It sounds like you want a webgui as well. rtorrent has one as well, although you will have to find it as I forgot the name. As for starting it up automatically, there's many ways of doing this. One easy way is to edit rc.local.
```
sudo nano /etc/rc.local
* add your startup command to it *
sudo chmod +x rc.local
```

---

### Post by xcurtisx on 2011-01-25
hmm I dont see a web ui so looks like it wont really work for me.
Plus seems you should be able to start it (transmission) at boot time

---

### Post by Bucky Ball on 2011-01-25
I just opened a terminal and typed in 'transmission' and up she popped.

---

### Post by James78 on 2011-01-25
> **xcurtisx said:**
> hmm I dont see a web ui so looks like it wont really work for me.
Plus seems you should be able to start it (transmission) at boot time
A well crafted Google search yields tons of results. Also, my friend was talking about wtorrent I believe when he wanted a web interface, fyi. You can also configure rtorrent to watch a folder so if you drop a .torrent in there it'll start downloading/seeding.
[rtorrent web interface](http://www.google.com/search?client=ubuntu&channel=fs&q=rtorrent+web+gui&ie=utf-8&oe=utf-8#hl=en&sugexp=ldymls&xhr=t&q=rtorrent+web+interface&cp=16&qe=cnRvcnJlbnQgd2ViIGludA&qesig=5ilOD1BEODacHM-Cis5V4w&pkc=AFgZ2tnozskHkijaX-A1gYuyPehljAvsjMQbNo-qG5EjfDeOKrnzW0UDO5DJMUNmRtzrIg-G9oYT30U07OlPjXQ5JeVI-ft8PA&pf=p&sclient=psy&source=hp&aq=0&aqi=&aql=&oq=rtorrent+web+int&pbx=1&fp=241062ed1d424d73)

And for starting it at boot time, I gave you a solution on how to do that.

---

### Post by xcurtisx on 2011-01-25
> **Bucky Ball said:**
> I just opened a terminal and typed in 'transmission' and up she popped.

Yea I got that to work as well but it seems to loose its configuration settings - AKA it starts not not the WebUI that I have enabled already.

---

### Post by sr20ve on 2011-06-02
I have an occasional need to ssh to my remote box and start a torrent download. I just use :

transmissioncli filename.torrent

---

### Post by chika.tambun on 2011-12-09
> **sr20ve said:**
> I have an occasional need to ssh to my remote box and start a torrent download. I just use :

transmissioncli filename.torrent

when it starting to SEEDING only, where i can get the torrent file have downloaded?

---

### Post by Bucky Ball on 2011-12-09
? You pick where to download the file to when you first add the torrent. You can right click the seeding torrent and 'open containing folder' or something like that from memory. ;)

---

### Post by Jose Catre-Vandis on 2012-01-28
> **chika.tambun said:**
> when it starting to SEEDING only, where i can get the torrent file have downloaded?

By default it goes to your ~/Downloads directory

---

### Post by codmate on 2012-01-28
Personally I use Deluge, which seems to be more set up for this sort of thing (headless server; web interface).

I used to love rTorrent, but a recent version had a bug that meant torrents never completed, so I abandoned that.

---

