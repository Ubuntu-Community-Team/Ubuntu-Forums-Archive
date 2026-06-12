---
title: "Torrent client and video converting"
date: 2010-05-11
forum: Server Platforms
---

### Post by Jonasu on 2010-05-11
Hello! 
Currently me and some friends of mine are creating a website for our new organization.
One of the main function on this site is to be able to share you're own created music, movies, pictures and so on. For this we need a media-player on the site and a torrent function for sharing.

The problem for the media-player is that most of them are created with flash and can only play flv type videformats. Since we do not want to force people to convert they're videos before uploading it, we need a converter that is server-sided and can do the job when the file is uploaded to the server. I've tried transcode, witch I believe should work, but it is just to advanced for me to understand with a man file on over a 1000 lines.. So basically I need someone to help me understand it, or point me to a easier converter.

For the torrent part I only need a torrent client that have a easy command to start seeding a file (maybe a way to create a torrent file, then start seeding). I've tried transmission, but I didn't get the transmission-remote to work (couldn't connect to the server at localhost or something..). So I need someone to point me to a better torrent client or help me with transmission!

Thanks in advance!

---

### Post by qjmoss on 2010-05-11
As for a torrent client.

Check out rtorrent.

---

### Post by Jonasu on 2010-05-11
> **qjmoss said:**
> As for a torrent client.

Check out rtorrent.

Tried already, it's always showing a strange "gui", i don't want that. Maybe there is way to not use that gui thing?...

---

### Post by Grenage on 2010-05-11
rtorrent doesn't have a GUI.

---

### Post by gobbledigook on 2010-05-11
rtorrent uses ncursers to give you limited control through the CLI. But Transmission seems to give more control through arguments.

how are you trying to connect to your transmission? have you already started transmission or the transmission-daemon first? because when you use transmission-remote if you are not starting it from the same machine as you have run the transmission-daemon then you will need to specify the host

transmission also has a CLI: transmissioncli - check out the [man](http://trac.transmissionbt.com/wiki/man) page for more info on all elements of transmission.

I know you want to get your site up and runnin asap! BUT you will need to be patient and read all the information relevent to the software you want to use... otherwise it may work for a week then break, and you won't know how to fix it !!

For a transcoder - i would use [VLC](www.videolan.org/vlc/) - this is a personal preference, and it even has a basic web interface which allows you to load a playlist and transcode it to FLV on the fly :) Alternatively you could write a script to scan a folder - your upload folder - and any new files are converted using vlc, to flv and can be moved to a playlist folder.

it all depends on how pretty you want it to look..... and how much "automation" you want

---

