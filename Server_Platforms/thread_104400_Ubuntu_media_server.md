---
title: "Ubuntu media server"
date: 2005-12-16
forum: Server Platforms
---

### Post by Connollyir on 2005-12-16
I threw together a new pc from spare parts I had lying around the house and I intend to use it for storage and streaming media over a LAN to my main pc and a few friends. I want to use Ubuntu as the operating system for the server but I am not sure how I should configure the system or what to install with Ubuntu. I am confused about what programs to use as the server base (LAMP, Apache, ect.) and I wanted to see what the community had to say about it.

I'm just looking for something that I can upload to (I will be using two ultra-ata 80 gb drives, non-raid arrays, as space for storage and the operating system) and will be able to download from and or stream media from. I would also like to include some security like SSH so that I could have the option to share my files securely over a network to other users who could access the files if they had the password I set.

If anyone could give the steps to accomplish this, point me to the right wiki or tutorial, or give me any information on what I need to be doing that would be great.

Thanks

-Ian

---

### Post by LoclynGrey on 2005-12-16
I use Xampp for my linux server.
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by Connollyir on 2005-12-16
I now believe I posted in the wrong section, sorry for the inconvinience.

However, I cannot seem to find the Ubuntu HOWTO forum or a particular HOWTO that applies to my situation so a freindly shove in the right direction would be wonderfly appreciated.

Thanks

-Ian

---

### Post by diebels on 2005-12-16
Install Ubuntu(server).
 
Install 'openssh-server', 'samba' for windows clients and 'nfs-kernel-server' for linux clients.

Come back here asking how to configure it.

---

### Post by Ahriman on 2005-12-18
I installed mod_musicindex for Apache via Synaptic, it works well for what I need (browsing my music dir via webpage, and creating a playlist to download and stream). Unsure if it works for any other server other than Apache, though ...

---

### Post by majikstreet on 2005-12-18
You could try MPD for music streaming... and if you wanted to have it be like a jukebox, you could hook up some speakers to it then use phpmp2 with apache and php, and be able to control it from your web browser.

---

### Post by Connollyir on 2005-12-19
[QUOTE=Ahriman]I installed mod_musicindex for Apache via Synaptic, it works well for what I need (browsing my music dir via webpage, and creating a playlist to download and stream). Unsure if it works for any other server other than Apache, though ...[/QUOTE]

Sounds good... actually thats exactly the advice I was looking for. I wanted to use Apache anyway but I wasn't sure what programs would stream it for me. How is the sound quality and what are the features that come with the program? Does it work with video, and if so large video files - say over 3 gb? Acessing the directory through the webpage is neat, but when you say download and stream you mean you download the playlist and stream the music accoring to whats on the pl right? Basically I want to make sure its a streaming.

---

### Post by Ahriman on 2005-12-19
I don't think it works with video ... in the description field of synaptic it says:

> mod_musicindex is aimed at being a C implementation of the Perl module
Apache::MP3 ([http://search.cpan.org/dist/Apache-MP3/)](http://search.cpan.org/dist/Apache-MP3/)).
It allows nice displaying of directories containing MP3 or Ogg Vorbis and
FLAC files, including sorting them on various fields, streaming/downloading
them, constructing playlists and searching.

So you can set it to either stream or to download, too. I think the sound quality will be based on the encoding of the track and the soundcard/speaker setup of the playing system. I used to use it to listen to my music when I was at work, and it did that pretty well.
Style-wise it uses CSS, so if you know it at all, you can change it alot. If not, it still looks pretty decent.

---

### Post by ewtesterman@cox.net on 2005-12-24
[QUOTE=LoclynGrey]I use Xampp for my linux server.
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)[/QUOTE]

This looks interesting. I am a little lost in the text world, how would I download this from a fresh base install? Also can you upload files directly to this server?

---

### Post by ewtesterman@cox.net on 2005-12-25
[QUOTE=diebels]Install Ubuntu(server).
 
Install 'openssh-server', 'samba' for windows clients and 'nfs-kernel-server' for linux clients.

Come back here asking how to configure it.[/QUOTE]

I would like to know how to configure it. I have apache2 php4 mysql mod_musid index and the above listed still cannot access my shares.

---

### Post by Almighty on 2006-01-19
I know this thread has been long since dead but I too would like to stream media from my desktop. I have downloaded the openssh-server and would like to know how to configure it.

---

### Post by ewtesterman@cox.net on 2006-01-20
[QUOTE=Almighty]I know this thread has been long since dead but I too would like to stream media from my desktop. I have downloaded the openssh-server and would like to know how to configure it.[/QUOTE]

I am no expert, but openssh has little to do with being able to stream. If you installed openssh through synaptic or apt you do not need to configure it. The machine you want to use to connect to it needs to have putty installed (putty exists on both linux, and windows). If you are connecting through a LAN you just tell putty the LAN address of the machine you want to connect to. If you want to connect to it from a machine that is not on the same network and you have a router between your host and the internet then you will have to do some port forwarding (ssh uses port 22). In this last instance you would have to enter your gateways ip address not the LAN ip address. To find your gateway ip address simply go to this address [http://www.whatismyip.com/](http://www.whatismyip.com/) from one of the machines on your network.

---

### Post by Almighty on 2006-01-20
Wow I love this forum. Well I have read  brief tutorial on the use of  Putty to set up the server. I dont have a router but plan to in the future. So after I install Putty what do I do as far as configuration is concerned? Im sorry I am a complete newbie when it comes to this kind of stuff.

---

### Post by Almighty on 2006-01-21
any more input on this?

---

