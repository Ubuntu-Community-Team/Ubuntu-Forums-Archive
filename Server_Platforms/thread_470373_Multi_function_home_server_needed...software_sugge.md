---
title: "Multi function home server needed...software suggestions?"
date: 2007-06-10
forum: Server Platforms
---

### Post by edbyford on 2007-06-10
I'm going to set up a linux server on a spare desktop I have. I want to share my photos, download torrent files and back up my files. I need software suggestions and also any tips you might have!

I have a spare box (think it's 1ghz, 256mb) and I would like to use Ubuntu server on it for all of this.

1) Now first off, I am a linux n00b, so I'm not really sure whether I'll need the LAMP stuff (is there a disadvantage to installing that if you're not going to need it?) but you guys should be able to tell me if I tell you what I need, right? :)

A couple of other things: my main computer runs windows, and I'm going to uni soon.

2) I would like to share my photos with Gallery2.

3) I would like to be able to backup my files onto the machine from uni (I'm guessing by FTP, but incrementally...should I use rsync?). I'll also need a good (read: open source) FTP backup program for my main computer if I'm going to do it by FTP.

4) The uni will probably block bitorrent ports, so I would like a bitorrent program, with a scheduler, so I can feed it addresses of torrent files and then it will download them. I can then pick them up later via FTP.

5) I would also like to be able to stream my music (if possible). I like the look of Jinzora. Are there any copyright issues I need to worry about?

6) It will also be behind a NAT, but I already have DynDNS Static IP set up. Will there be any security issues I need to worry about?

7) I obviously will want to remote administer this from uni, so will I need to telnet to do that?

So if you have any suggestions on good software, have noticed an area where I'm mistaken, or have done this before and have any advice to offer, it'd be very much appreciated.

---

### Post by 444 on 2007-06-10
Don't use telnet, unless you want your box hacked. Use ssh. I do some of things you talked about via vnc through a ssh tunnel, or just plain ssh depending on my mood...

---

### Post by conjur3r on 2007-06-10
1,2.  Yes you will need LAMP seeing that you wish to run Gallery2 (which is a web application). 

3. Stay away from FTP.  It is insecure and sends your username and password unencrypted over the internet.  If at all possible, I would recommend using sFTP (secure FTP).  All you need is to install the ssh daemon.  Unfortunately, whatever solution you decide to implement, make sure it works from your university as they have a habit of blocking alot of ports.

rsync is great.  Use it when you want to mirror things.  If it's just a handful of files that you want to copy across, simply use SSH (or SCP).  If you are on a linux client, open up your file browser and just type "ssh://username@serveraddress" and you've got a gui.

6. Nothing wrong with using dyndns.

7. Never use telnet.  Similar to ftp, it sends your username and password unencrypted.  Use SSH instead.

Because you will be offering many services over the internet, make sure you harden your box as much as possible!  You do not want to leave open a few things so that hackers/robots can get on and run a muck.  Add a firewall.  Make sure you use strong passwords.  Disable root logins.  Apply other best practice stuff.

---

### Post by 444 on 2007-06-10
And that's why I use ssh tunnels. Only one port open, only one spot to secure. Once the tunnel's open you can use ftp or whatever you want because the tunnel encrypts it.

---

### Post by conjur3r on 2007-06-11
I also meant to add:

4. Seeing that you will be running a LAMP, have a go at Torrentflux [http://www.torrentflux.com/](http://www.torrentflux.com/) which is a web based bt client.  It's quite good.

---

### Post by dfreer on 2007-06-11
Torrentflux is awesome, you will need apache, mysql, and php for it to work (so yeah, you'll need LAMP). It does support zipping up the files it downloads on the fly, download using your standard web browser. I dunno about a scheduler for it, but it does have queues. 

GNUMP3D works ok for streaming music, haven't tried anything else myself. It has some issues, but it serves it's purpose well.

You can use ssh to both admin the box and download files, either with rsync, scp, sftp, or various other means. Make sure to instal fail2ban to help weed out people brute-forcing SSH, and using private/public key auth along with changing the default port from 22 to something else will help alot.

From a windows machine, I would recommend ssh client from ssh.com ([http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html](http://www.ssh.com/support/downloads/secureshellwks/non-commercial.html) ), as it is IMO a lot eaiser to use than putty, when trying to upload/download files to the server, so no need for FTP really. 

Since you are behind a NAT, make sure to poke holes through your router in order for the various services to work, mainly whatever port you use for ssh (default = 22), 80 for apache, 8888 for gnump3d, and whatever ports you configure torrentflux with need to be open (important for bittorrent to work correctly).

---

### Post by briguy on 2007-06-20
If you have installed Feisty, Torrentflux should be in the repos.  apt-get install torrentflux will take care of everything.

---

### Post by airtonix on 2007-06-20
get rtorrent.....much better. works as nCurses gui so it is Screen compatiable.

also.....you can get xMing for windows so you can do thus from putty : 

> ssh [email]yourUserName@your.dyndnsdomain.org[/email]:withSensiblePortNumber -X [nautilus]


note : replace sqaure brakets and contents of with desired gnome program...

the example will load the nautilus desktop onver the top of your windows desktop...

how frekn awesome is that!!!

---

