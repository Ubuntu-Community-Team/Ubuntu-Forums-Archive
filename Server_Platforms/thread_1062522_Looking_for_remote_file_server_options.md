---
title: "Looking for remote file server options"
date: 2009-02-07
forum: Server Platforms
---

### Post by falconed7 on 2009-02-07
Hey everyone.

I have set up my Ubuntu home server and it has been running for over a month. With Uni drawing near once again I would like to have access to my university documents anywhere I am using a web browser. I am not sure of how many options there are but I do know of a few:
- Apache web server
- FTP
- SFTP

I am looking for the most secure option with a decent web gui I can access through firefox, ie, etc. I already have ddclient up and running, constantly updating my IP address.

Which would be my best option and would I have to harden my server before I open up any ports?

Any help would be great!
Cheers.

---

### Post by falconed7 on 2009-02-07
Anyone have any input at all?

---

### Post by michaelzap on 2009-02-07
Personally I don't like opening up my machine for access from the outside world. I prefer to use a remote server of some sort to store shared files. I've done this all sorts of ways (FTP to a web server, Gmail drive, Dropbox, JungleDisk/Amazon S3), and you might want to try one of those before setting up a server on your machine.

But if you want to set up your machine to serve files over the net, you should be able to do this with an (S)FTP server or WebDav. WebDav would give you a browser-based GUI, so that's probably what I'd try first. You probably will need to make sure that the right ports are open (on your computer, router, and ISP's network), but I'm sure it wouldn't be all that difficult to make work.

Long ago I used to setup an FTP server on Windows to share files with coworkers, but I haven't messed with WebDav on Linux so if you're interested in that I suggest you Google a guide and give it a shot.

---

### Post by hyper_ch on 2009-02-08
(1) install openssh-server
[(2) install denyhosts or fail2ban]
(3) connect to it using sftp or sshfs or some other means. In Dolphin and Konqueror I can just enter:  fish://user@HOME and I'll be prompted for the password. No clue how to do it in nautilus. with sshfs you can mount for exam your home folder on the home server in any place on your local machine that you want.

---

### Post by jimv on 2009-02-08
You could use a program like DropBox.  It gives you 2 gigs of storage space on their server, and you install their little program on your machine that gives you quick access to your files.  You can also access your files through their website.

[http://www.getdropbox.com/](http://www.getdropbox.com/)

---

### Post by bigbearomaha on 2009-02-08
If you setup a LAMP server, you can use a webapp called "AjaXplorer"  it is a web app to manage file access.

it does have a feature to make use of SSL and be a https site for secure access.

then , all you do is associate a directory with your user and you have remote access anywhere you go.  

notice, if you don't have business ISP service, you might likely have to use a DynDNS solution or similar to be able to reach the server from the web.

Big Bear

Of course, you don't really need a server at all.

You can use Dropbox as has been suggested or even open up a Google user acct and save all your documents google docs.  or set up a google site, which is free which allows you to create a group or pages that specifically function as a file management site for file upload or download.  again, those are free so cost is minimal.

---

### Post by HermanAB on 2009-02-08
The easiest to set up is probably SSH Server and Webmin.

Cheers,

Herman

---

### Post by falconed7 on 2009-02-08
> **bigbearomaha said:**
> You can use Dropbox as has been suggested or even open up a Google user acct and save all your documents google docs.  or set up a google site, which is free which allows you to create a group or pages that specifically function as a file management site for file upload or download.  again, those are free so cost is minimal.

Dropbox looks quite good, but is it possible to install it on a headless server?

---

### Post by BlakeM on 2009-02-08
Hey,

I'll be going to uni next year as well. What I intend to do is use SFTP and rsync (or unison) to synchronise a folder on a laptop and a server.

Dropbox is probably the easiest option though. I chose to build my own server as a learning experience.

---

### Post by bigbearomaha on 2009-02-09
I don't think dropbox software is available.  they are a hosted service only as far as i know.

to do your own server, if that's important for you, I would look into AjaXplorer.

Big Bear

---

### Post by Thirtysixway on 2009-02-09
I use ssh or ftp to access my server remotely.  Just change default ports and setup fail2ban and you should be secure.

---

### Post by hyper_ch on 2009-02-09
why should the change of ports make you secure?

---

### Post by jimv on 2009-02-09
> **falconed7 said:**
> Dropbox looks quite good, but is it possible to install it on a headless server?

In fact there is:

[http://turin.nss.udel.edu/programming/dropbox2/](http://turin.nss.udel.edu/programming/dropbox2/)

I'm going to try it when I get home :D

---

### Post by jimv on 2009-02-09
> **hyper_ch said:**
> why should the change of ports make you secure?

If you're a hacker running a port scanner, are you going to try to brute force port 51231 or port 22 for SSH?

I used to get login attempts all the time on my SSH server until I changed the port to a random high number.  I haven't had one since.

---

### Post by bigbearomaha on 2009-02-09
nope
that is not what I was thinking of myself.  I meant dropboks.  spelled that way.


Big Bear

---

### Post by hyper_ch on 2009-02-10
> **jimv said:**
> If you're a hacker running a port scanner, are you going to try to brute force port 51231 or port 22 for SSH?

I used to get login attempts all the time on my SSH server until I changed the port to a random high number.  I haven't had one since. 
And still, why do you think changing ports makes it any more secure? You said yourself fail2ban/denyhosts. So after x unsuccessfull attempts the IP is banned...

---

### Post by jimv on 2009-02-10
> **hyper_ch said:**
> And still, why do you think changing ports makes it any more secure? You said yourself fail2ban/denyhosts. So after x unsuccessfull attempts the IP is banned...

Actually, I didn't mention f2b....but I imagine that's a good method.  But security through obscurity is a valid layer of protection.

---

### Post by hyper_ch on 2009-02-10
there is no such thing as "security through obscurity".

---

### Post by jimv on 2009-02-10
For someone with as many posts as you have, one would think that you would at least check before you make an assertion.

[http://en.wikipedia.org/wiki/Security_through_obscurity](http://en.wikipedia.org/wiki/Security_through_obscurity)

---

### Post by hyper_ch on 2009-02-10
> **jimv said:**
> [http://en.wikipedia.org/wiki/Security_through_obscurity](http://en.wikipedia.org/wiki/Security_through_obscurity)
That's why the list of arguments against is so much longer...
Besides changing port to non-standard ports will not help against those attacks you should really worry about ;)

---

### Post by jimv on 2009-02-10
> **hyper_ch said:**
> That's why the list of arguments against is so much longer...

Irrelevant.  You said it wasn't a security method and it actually was.  Whether or not it's effective is a different debate.

> Besides changing port to non-standard ports will not help against those attacks you should really worry about ;)

Those kind of attacks are not going to be directed at Joe User's home network.  The small time hackers who would be attempting to break in to a small network aren't going to spend their time checking every port to see what's there.  They're going to be looking for easy targets on common ports.

You're simply wrong, so drop it.

---

### Post by hyper_ch on 2009-02-10
> **jimv said:**
> Whether or not it's effective is a different debate.
Ineffective security == no security ;)

> **jimv said:**
> Those kind of attacks are not going to be directed at Joe User's home network.  The small time hackers who would be attempting to break in to a small network aren't going to spend their time checking every port to see what's there.  They're going to be looking for easy targets on common ports.

You're simply wrong, so drop it.
Script kiddies will just use default ports and that's what you don't have to worry about. And scanning every port is quite simple. So those that are dangerous will know what port you run on anyway.

You're simply worng, so drop it.

---

### Post by dtach on 2012-08-06
Honestly, I've been looking to do the exact same thing, and actually came across a WAY better solution, at least for me. It's FreeNas, which is based on FreeBSD. It runs off of a USB drive rather than your computer itself, so even if you only have one HDD you can still have a remote server. Also, the thing that I really like about it is that it can operate under just about every network protocol imaginable, so it works with Macs seamlessly, allowing you to use it as a network time machine, while still being available to all the linux and windows PC's on your network. 

I don't know, seriously, I've been looking into this for a while, and I think this is really the easiest and most viable option for someone like me, who is just wanting to turn an old computer into something usable again, without having to spend any money.

---

### Post by LHammonds on 2012-08-06
One other option available depending on what you are looking to accomplish is [ownCloud]("http://owncloud.org").

LHammonds

---

### Post by michaelzap on 2012-08-06
FreeNAS is a great option, but I chose to run a full Debian system instead for the following reasons:
[LIST]
[*]file system encryption - this is essential to me, since if someone breaks in and steals my server I don't want them to also have all of my files
[*]offsite backup - I use JungleDisk to backup all of my files to the cloud, and with Debian I can leave that running and know that everything on the server will also be online
[*]other perks of running a full system - burning DVDs of files on the server without having to copy them over the network to another machine, for example. I've also recently done some batch renaming and mp3 tagging. And every once in a while I set up a video compression batch on the server so that I can use my main machine for other things.
[/LIST]
I'm really happy with my Debian server setup, but if I didn't feel that file system encryption were essential I might try FreeNAS and work around (or do without) the other points.

---

### Post by a2j on 2012-08-06
owncloud is what we use and lovin'it  :)

---

### Post by cejack on 2012-08-20
Using both OwnCloud on my remote on-line provider (not running it locally on my own server) and running AjaxPlorer.  

Ajax is really slick and can also provide repositories to other remote servers it is hooked up to.  File sharing and granularity is pretty awesome with Ajaxplorer.  Wasn't too hard to get rolling once you get LAMP set up.  

If you feel comfy running LAMP and you know how to direct and secure stuff on your network, then go for it.  

Owncloud looks pretty slick too but I haven't tried it on my own server yet.

---

