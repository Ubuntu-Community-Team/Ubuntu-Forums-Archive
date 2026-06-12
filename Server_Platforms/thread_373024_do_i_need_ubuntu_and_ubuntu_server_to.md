---
title: "do i need ubuntu and ubuntu server to"
date: 2007-02-27
forum: Server Platforms
---

### Post by devious1 on 2007-02-27
I have a couple of websites that I am paying for (shared hosting plans I believe).
I am completely new to linux. I hate windows! Anyway, I don't want to have to worry about running out of space so,I have an old pentium II that I am going to use as my main website and link the others 2 it if this is possible. but the main thing is I want to be able to host my own files(flash,mpg,mp3,etc....) I installed ubuntu and I don't know how to exit out of edit scrrens following the guide perfect setup I also want to make this a flash server if that is possible with ubuntu. I've been reading, trying to learn fast but it is too time consuming at this point. I can't get the other stuff I need to do, done.

I had to issues installing

I named the server deviousmindspro. When I used the comman hostname and hostname -f
they did not match.I kept going, now after installing mysql (following perfect guide) I got the error

mysqladmin: connect to server at 'deviousmindspro.com' failed
error: 'unknown mysql server host 'deviousmindspro.com' (1)

big job for little person.

any help would be greatly appreciated!!!

---

### Post by Brunellus on 2007-02-27
I'm moving this to server talk, with a request for more specific information, please.

---

### Post by devious1 on 2007-02-28
get my server up? I am trying to host my files for my other websites on my own server.

---

### Post by devious1 on 2007-02-28
run ubuntu server?

---

### Post by researchsci on 2007-02-28
Yes, the server is a just a different install than the gui'ed client version.

---

### Post by Quillz on 2007-02-28
Ubuntu Server Edition is just one take on using the Linux kernel as a server. Almost every major Linux distro has a server configuration of some sort.

---

### Post by Maestro23 on 2007-02-28
This community is one of the best for any distro I have been a part of.

Is this the kind of info you are looking for?

Ubuntu Server Guide: [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

---

### Post by ~LoKe on 2007-02-28
Just install in server mode? o_O

LAMP?

---

### Post by devious1 on 2007-02-28
Ok, in previous post I stated that I wanted to use my server to host my files(flash,video,music,video chat,communities, the abilities for my users to make there own web pages on mysite. I have already looked into cms like joomla,xxops and a few others.I also want to learn linux, I rrreeaallly don't like microsoft. I have 2 websites that I pay for. do I have to pay for a domain name or can i just switch to server or can i just link my larg files to my webpages live feeds and streams. I have alot of content that's just waiting to be uploaded. I've been in the house for months trying to figure this stuff out. All help is greatly appreciated!

---

### Post by llamakc on 2007-02-28
> **devious1 said:**
> Ok, in previous post I stated that I wanted to use my server to host my files(flash,video,music,video chat,communities, the abilities for my users to make there own web pages on mysite. I have already looked into cms like joomla,xxops and a few others.I also want to learn linux, I rrreeaallly don't like microsoft. I have 2 websites that I pay for. do I have to pay for a domain name or can i just switch to server or can i just link my larg files to my webpages live feeds and streams. I have alot of content that's just waiting to be uploaded. I've been in the house for months trying to figure this stuff out. All help is greatly appreciated!

For starters you have multiple questions with multiple answers. You'll help yourself by separating the issues.


1. Yes, you need to pay for a domain name unless you want people to access your data by IP only.

2. You don't switch to 'server'. You install the appropriate packages. You determine which packages are appropriate by telling the forum precisely what you want to serve to your users. One would serve web pages by installing a web server (software package). An example would be "apache2". 

3. Serving streams and live feeds are dependent on #2 above. 

You can not hold this community at fault for your inability to ask clear questions, or a misunderstanding of what you need. The onus is on you to learn. People here are very, very willing to help and show you how.

---

### Post by Praill on 2007-02-28
I think he wants to create his own web server instead of paying for one.
That is more of a hardware issue. You can run a webserver on ubuntu, but do you have the bandwidth and hardware to support it? Not to mention a static IP and a domain name?

Its almost always more cost effective for a individual to just pay for hosting than purchase all those items seperately and have to worry about keeping it on 24/7 and maintenance after that.

---

### Post by frup on 2007-03-01
I'm no expert on this but i'll try help

Check out ubuntuguide.org for some really good info.

install Apache MySQL and PHP. Thats creates the LAMP mentioned before which allows your computer or operate as the webserver... you need to allow port 80 traffic in apache and on your router (port forwarding)

I'm guessing you might want FTP set up if your users are having their own webpages or is it more like a myspace thing (yuck).

Once the Apache server is configured (first try [http://computername](http://computername) or [http://computersnetworkip](http://computersnetworkip) from the network) you should get the apache default pages. then get outside the network and try it with the domain or your home IP if you have set all that up... then any file inside /var/www should be able to accessed the same way as linking to any other file on the web.

I hope that helps, i know its not technical but ubuntuguide.org can help with that side of it :)

Search these forums for MYSQL APACHE and PHP too... you can use perl and python too etc. etc.

---

### Post by devious1 on 2007-03-01
thank you all for your replies.

I have to domain names that I am currently paying for monthly. I really think that what I actually need is to be able to host my files for my websites that I currently own. As far as keeping the server on 24/7 that is not a problem. All of my computers are on 24/7
I have windows xp pro on main computer AMD 64 3000 2 gig mem 600 gig hard drive space nvidia sx5400 or something like that with 3 other computers running windows 2000 pro and now ubuntu on old pentimum II 500 mhz 256 m ram 230 gigs hard drive space this is the one I want to use for server. I don't want to pay for more webspace for the files. I have a lot of swf files that I want to embed into my webpges some of these are large files FLV files are definitely big. The other sites all have joomla at current for cms I plan on going far beyond myspace. I am also putting together another pentium II to run ubuntu on so that I can use the above in full server mode. Sorry if I don't talk the same lingo I do music and video production. I also do tons of other things. I have always loved working on computers since the ti/994a. I'm trying to learn, it's just that unfortunately I'm tring to do the work of a team by myself. So I admit that in some cases I'm trying to take a few short cuts. I have no life I'm in front of these computers all day working on fraphics, commercials, skits, models, dance groups, pics, live recordings, and so on. not trying to bore everyone I just tried to be to the point with what I was trying to do.
thank you for the responses that you gave me.

---

### Post by devious1 on 2007-03-01
For some of you big time programmers out there, Here's an idea

Make a program that can be used by producers all over the world to work on each others video and audio through a web page preferably in flash. Live online studio! I believe I saw a linux program that boast the equivalent to digidesign protools.  I myself am a living network. you could make alot of money!

---

### Post by Brazen on 2007-03-01
> **llamakc said:**
> For starters you have multiple questions with multiple answers. You'll help yourself by separating the issues.


1. Yes, you need to pay for a domain name unless you want people to access your data by IP only.

2. You don't switch to 'server'. You install the appropriate packages. You determine which packages are appropriate by telling the forum precisely what you want to serve to your users. One would serve web pages by installing a web server (software package). An example would be "apache2". 

3. Serving streams and live feeds are dependent on #2 above. 

You can not hold this community at fault for your inability to ask clear questions, or a misunderstanding of what you need. The onus is on you to learn. People here are very, very willing to help and show you how.

If you want users to be able to make their own pages, you might want to consider using a hosting control panel like zPanel or VHCS.

---

