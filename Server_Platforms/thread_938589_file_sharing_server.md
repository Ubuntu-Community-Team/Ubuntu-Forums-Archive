---
title: "file sharing server"
date: 2008-10-05
forum: Server Platforms
---

### Post by miesnerd on 2008-10-05
Im a little out of my league here, so I'm looking for a little help.
What I'd like to do is set up a LAMP server but instead of using it like I have before for storing my files so I can access them anywhere, I want it to be setup so many people can do this from an easy to access, uncomplicated web interface. I'd also like these different users to be able to send a file (pdf) from one user to another. 

So to try to explain this a different way (so that maybe it'll help) I'll probably want approximately 20 users to be able to login and basically use their files like they would with a file manager, except send files from their folder to either a public folder or to another specific user's folder.
Of these 20 people all of them are academic types who have no knowledge of linux so it needs to not look like linux or be complicated. They're point and clickers. If it can be made to work "like email" or "copying and pasting just like in windows" that'd be wonderful as I wont get as many "support" emails.

Thanks

Miesnerd

---

### Post by miesnerd on 2008-10-05
also, not to be completely greedy, Im curious about another feature.
I'd love to know if there's anyway to use the database features that are tied inot a lamp server (the M in lamp) to use some sort of tags. IE- let's say Im looking on that server for an pdf on topic X. Can I build in a search and if my friend has tagged a paper as being relevant to topic X into a public folder, have it find it?

probably impossible, but it'd be amazing for us.

Thanks again,
Miesnerd

---

### Post by Iowan on 2008-10-05
The "P" in LAMP is for PHP.  I'm still reading books, trying to get acquainted with it, but it seems to be a great way to interface between a database or file server and a web page.  The tags would work if built into a database, but getting them there would be non-trivial (nothing truly useful ever is).  There are good articles on [howtoforge.com]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") for building "perfect servers" including one based on Hardy.

---

### Post by miesnerd on 2008-10-05
I was reading up on Samba shares. Can I make a samba file server that is accessible from outside the LAN? IE-- can people go off campus and then access the server?

---

### Post by Iowan on 2008-10-05
Sure... or mostly sure.  Primarily, you'd need to have the internet-accessible router port-forward to your Samba server (and maybe change some firewall rules to permit Samba access.)  The limiting factor is whether you have access to the router (and firewall).

---

### Post by miesnerd on 2008-10-05
> **Iowan said:**
> Sure... or mostly sure.  Primarily, you'd need to have the internet-accessible router port-forward to your Samba server (and maybe change some firewall rules to permit Samba access.)  The limiting factor is whether you have access to the router (and firewall).

yeah, that is going to be a problem. I was planning on setting up a server and plugging it in @ the department on campus. As it is within a large university, im sure they would not be so keen on me accessing anything to do with their firewall, etc., and hence, I will need to go back to the route of using some sort of web interface. I hated webmin and i dont know PhP so if there's another route, Im ready to explore that...

---

### Post by lykwydchykyn on 2008-10-05
SAMBA is not generally used over the internet, I'd probably choose ssh instead and have people connect using SFTP.  

Pretty much all the functionality you're asking about is possible with LAMP, but the issue is that you've either got to design it yourself or find a web app that someone has created for this purpose.  I don't know of any such app, though if you take a bit of time to get some PHP skills you can certainly put something like this together.

---

### Post by miesnerd on 2008-10-05
that's kinda central to the issue.. I was really looking for a "quick install" type of thing. I dont have time to learn PhP- - maybe over christmas if i choose not to work on my dissertation? I guess what I was looking for was a cookie-cutter web app that I could install and tweak and just add users to. So if anyone knows about anything like that or even where to start to look for something like that, I'd love to know.

---

### Post by lykwydchykyn on 2008-10-05
Well, what's wrong with just installing FTP?  You don't get your tags and so forth, but people can connect through a browser and download files.

---

### Post by miesnerd on 2008-10-06
a few things are wrong with that. I dont know that the workstations include a ftp client. I dont think you can upload to a FTP thru a web browser, and they cant share files as well. Maybe I'll just have to learn PHP?  I honestly thought something like what Im looking for would exist... or at least a framework for doing it.

---

### Post by miesnerd on 2008-10-06
im back, and I found a demo of what Im looking for.
Unfortunately, its not cheap. But now at least people can see what Im getting at and maybe offer some additional guidance or a trick based on seeing it from a different angle.

[http://demo.afian.com/](http://demo.afian.com/)

Thanks again for all your help and suggestions.

---

### Post by miesnerd on 2008-10-06
i just discovered webdav. Will that work for what Im talking about?
If so, any advice before I dive in?

---

### Post by oavicena on 2008-10-06
Try [eyeos]("http://eyeos.com"), I have been using it for a while and I think It might be what you are looking for.
Good luck,
Borja

---

### Post by lykwydchykyn on 2008-10-06
Ah ok, sorry for being thick-headed.  There are lots of those kinds of things.  I think a wiki might also do what you're looking for, though it would not be optimized (but it's searchable and you can upload files).  

But check out [this sourceforge search]("http://sourceforge.net/search/?words=file+sharing+web+php&type_of_search=soft&pmode=0&words=document+management+web+php&Search=Search") for some options.

---

### Post by bunnynuts on 2008-10-07
First, I agree with lykwydchykyn in that Samba is not usually used beyond sharing on a lan...however, in a university atmosphere it may not be the worst thing. This depends on the type of documents you are sharing. If they contain any sensitive information I would not use a Samba share. Your university likely has a vpn that can be accessed by those who are affiliated with the university. By setting up a samba share, restricting access to it to university IPs (or specific user IPs if you are able)it may work. When off campus the users will need to connect to the VPN before connecting to the share. Just don't plan on it being the most secure way to do this. The PHP/SQL thing will truly be a better choice...but that does nothing to help with your dissertation. Good Luck!

---

### Post by bcn17 on 2008-10-11
Keep in mind if the server is to be plugged into the universities network that no matter what kind of server is installed you will need to have the router forward a certain port to that pc. Even if it is webaccess when someone enters the universities external ip they have a router that forwards port 80 to a certain server. Unless they give you webspace, or access to a server you might have to plug it into your own connection.

---

### Post by R.Bucky on 2008-10-12
I utilize Nexus File manager. [http://nexus.iwonderdesigns.com/](http://nexus.iwonderdesigns.com/) It has .pdf plugins and is fairly simple to operate and even easier to install.

---

