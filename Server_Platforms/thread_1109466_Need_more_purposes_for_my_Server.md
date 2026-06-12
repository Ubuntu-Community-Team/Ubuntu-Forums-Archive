---
title: "Need more purposes for my Server"
date: 2009-03-28
forum: Server Platforms
---

### Post by Deathray on 2009-03-28
I just turned my old desktop into a headless ftp/ssh (on port 443 to bypass firewalls)/torrentflux server. Any other idea's I could add to my server.. It's going to be on 24/7 so I might as well use it for something else. Ive been thinking of webcam monitoring and an irc bouncer.. What else could be fun? :)

---

### Post by Dr Small on 2009-03-28
Oh, if you're into web development, throw in Apache, MySQL, and Php5. You could also run an Email server with Postfix with curiour-imap and SquirrelMail; oh, and a Jabber server. :)

---

### Post by ad_267 on 2009-03-28
Subversion or Git for version control. Maybe some kind of media server.

---

### Post by metallicamaster3 on 2009-03-29
My server does quite a bit of different things. 

- DHCP server (for distribution of IP addresses)
- DNS server (so that you don't always have to type out whole IP addresses all the time)
- Apache/PHP/MySQL server (for hosting webspace)
- Storage array -- I have all my storage in this behemoth, rather than in individual machines (because I have quite a few, it's better to have everything in one big center). Using Samba (SMB) to share it all throughout my whole network.
- Webcam -- you can throw a webcam into a password-protected HTTP page you know, using .htaccess files. Very handy!


There's just a handful! Got questions? You can always PM me if you like what you see :P

---

### Post by hyper_ch on 2009-03-29
you could make it a streaming audio server so you can listen to your collection at work or something...

---

### Post by tuskenraider on 2009-03-29
just be safe if you do a email server... i had one at one point in time... and it was always under attack from A$$holes in taiwan trying to telnet in and send spam...  jerks. :lolflag:


tusken

p.s i also use my server for media center stuff.. gotta love recording tv. no more commercials.

---

### Post by hyper_ch on 2009-03-29
well, you don't have a telnet daemon installed on a server, right?

---

### Post by MrWES on 2009-03-29
> **hyper_ch said:**
> well, you don't have a telnet daemon installed on a server, right?

I would hope not!  :)

---

### Post by Bachstelze on 2009-03-29
Also you can consider joining the [NTP pool]("http://www.pool.ntp.org/").

---

### Post by Dr Small on 2009-03-29
> **metallicamaster3 said:**
> 
- Webcam -- you can throw a webcam into a password-protected HTTP page you know, using .htaccess files. Very handy!

That's something I would like to do, but alas, I have no webcam!

---

### Post by gregor171 on 2009-03-29
Instead of email server think about using googleapps and avoid spammers ;-)

---

### Post by MrWES on 2009-03-29
> **hyper_ch said:**
> you could make it a streaming audio server so you can listen to your collection at work or something...

That's what I did with mine; I shared my music library across my home network with mt-daapd. Rhythmbox and Songbird in Ubuntu support daap, and iTunes in Windows/Mac support it.

Bill

---

### Post by BkkBonanza on 2009-03-29
Well, I think you said before you would have a big screen attached for movies. So do like B.Gates and run a slideshow program that plays scenes on your screen when not being used.

---

### Post by doogy2004 on 2009-03-29
jabber server (need openfire) (openfire is easy to configure and use, IMO)
use forwarded X sessions to run programs on the server but have the program displayed on a remote computer (need ssh with x-forwarding (included with ssh by default) and xauth, then just install any program you want to use remotely on your server)

---

