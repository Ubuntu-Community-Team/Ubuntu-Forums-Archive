---
title: "Config help for a total *nix newbie, please..."
date: 2009-04-18
forum: Server Platforms
---

### Post by MaxxD on 2009-04-18
Hello everyone. I have been doing web development for quite some time now and have always had an in-house development server running php & MySQL on IIS. Well, that system finally died, so I bought a new box and decided to wipe out the default XP Home and install Ubuntu server on it. Now, I just want this for in-house testing (before clients see the pages) so it needs to be reasonably secure, but I need to be able to develop on my Windows box and ftp or file-share (preferably both) the files to the dev server so I can view it on my Windows box in one of my browsers.

I installed Ubuntu 8.1.0 server just fine (LAMP, OpenSSH, Samba, File and Printer Sharing installed), and immediately surfed to [http://box_name/](http://box_name/) web page - got the "It Worked!" page. I was happy. But then it occurred to me that I had no idea how to put pages on the system, so I started reading. I've now got ProFTPd installed and running and can connect to the Ubuntu dev server from my Windows box via ftp just fine. Problem being, I can't create or delete any directories or files through Filezilla on the Ubuntu dev server.

I also can no longer start the Apache2 service - I get a [ [COLOR="Red"]Fail[/COLOR] ] every time I try.

I haven't gotten to the point of even attempting to configure Samba yet, though I would happily take any advice about that. However, of more immediate concern is that I'm pulling out hair trying to configure ftp access for myself and to set up the web server. I'm using PuTTy to connect to the Ubuntu server from the Windows box, btw.

Most of the threads that I've seen about Ubuntu-Windows P2P networking seem to assume that you're using the Ubuntu box as your main box - I'm not. I don't have monitor, keyboard, or mouse attached to that box now and I'd like to keep it that way.

I've also always used someone else to host the sites I create because I know jack-all about *nix (a fact that is completely biting me in the butt right now) and it's just easier to use someone else to physically host the sites. I don't want the dev server to be available to the public, just me and the one other computer in the office. Most of the articles I've seen about setting up ProFTPd and Apache assume a level of knowledge about base-level server configuration that I'm really not sure I have at this point.

Anybody have any uber-newbie advice, tutorials, articles, or walk-throughs - anything really?

---

### Post by 123456789123456789123456 on 2009-04-18
as far as apachie, I don't know, the problem with the files could be permission related, but not sure, you said you don't have anything connected to the ubuntu machine, are you trying to delete the files, through ftp on the windows machine, or directly from the ubuntu machine.  If you are trying to use the windows machine, I would assume that ubuntu server has not given but only read permission to the windows machine, therfore you can transfer files to the ubuntu machine, but you can only read that the files are there, you would not have permission to delete or possibly move the files to different folders/directories.  I am not that apt with ubuntu server.  You may need to temporarily connect the keyboard and mouse to the ubuntu machine, log in, and add write permission to the windows computer access while it is accessing the ubutnu machine.  If it is a permission problem, that is the only thing I can think of.  You should not need to keep the keyboard and mouse on the ubuntu mahcine after that.

stay tooned however, someone else may know more.

---

### Post by MaxxD on 2009-04-18
1234(etc) -> Thanks, I'll be looking into permissions as well. Right now I'm just trying to get Apache to run at all. Erk.

Mods - sorry, I thought General Help would be a decent place to post this. Thanks for the move.

---

### Post by MaxxD on 2009-04-19
And now I've been trying to get Samba working to no avail for several hours. I can see my Ubuntu box in my Windows Network workgroup, but it's asking me for a username/password combo that I set up already and am entering correctly, though it's telling me I'm *not* entering it correctly.

lovin' this experience so far.

---

### Post by BkkBonanza on 2009-04-19
For your apache problem you'll want to look in the apache log to see what error it logs for the start failure. It may be clear right away or if not then post the message here and someone can help you with that.

---

### Post by Thirtysixway on 2009-04-19
Are you starting apache with sudo?  sudo /etc/init.d/apache2 start

---

