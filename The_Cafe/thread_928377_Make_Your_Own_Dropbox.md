---
title: "Make Your Own Dropbox?"
date: 2008-09-23
forum: The Cafe
---

### Post by solarwind on 2008-09-23
Dropbox is a very useful tool which allows you to have a central "folder" which is synchronized between all of your computer. They say data is encrypted as it goes in and out but here are some disadvantages:

Disadvantages of Dropbox:
* You want to sync personal files, but you don't want to trust any third party to manage encryption for you. This is the biggest issue.
* Costs a lot of money and there are restrictions on disk usage. You don't get much space.

My idea is - turn any web/ftp server into your own "dropbox" with a free/open source encrypted synchronization system.

Advantages of my system:
* More space and bandwidth for very little cost. You can get a webserver for almost nothing these days. Or, use your own computer as an FTP server to keep your laptop and desktop in sync, for example.
* Peace of mind - none of your data goes in and out of your computer without first being encrypted.
* Use your own webserver or any other server with FTP access. It's as fast as you want it, safe as you want it.
* Free/open source. No restriction on use, no one controls how much space and bandwidth you have except for limitations on your webhosting account, for example. This does not apply if you use your own computer as the FTP server.

Here is a diagram illustrating my idea:

[[IMG]http://img524.imageshack.us/img524/329/diagramju2.th.png[/IMG]](http://img524.imageshack.us/my.php?image=diagramju2.png)[[IMG]http://img524.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Please take a look at the diagram, it illustrates the entire concept.

What do you guys think? Is this project doable? I know it's worth it. Please discuss. I want to get this off the ground. I can write the program once I clear up a few things with the design.

---

### Post by kevin11951 on 2008-09-23
someone HAS to do this!

---

### Post by solarwind on 2008-09-23
> **kevin11951 said:**
> someone HAS to do this!
I will, once I get this encryption confusion sorted out.

---

### Post by dixon on 2008-09-24
Use sftp connection. I think, it's really not so hard to implement - I'm just in the middle of my diploma project now :(

---

### Post by MaxIBoy on 2008-09-24
I could do it with bash scripts for the client-side and server-side code, provided there's some kind of command-line encryption utility out there. Just have the script connect to an IP and use wget. Of course, I'd need to pull some crap with command-line email clients or something in order for the server to know what the client's IP address is.

On the other hand, in your scheme, something encrypted on your laptop needs to be readable on your computer at home. That means all clients must have the same encryption hash somehow. How is this done? A rand() call seeded with the current time and multiplied by the value of the fifth pixel from the left in the twelfth row of a Game of Life fractal which has been seeded with the MD5 sum of a sound file of "Stepping Stone" by Jimmi Hendrix? Something secure yet reproduce-able.

---

### Post by Tomosaur on 2008-09-24
Yeah  - I don't really understand your problem. Are you talking about writing an entirely new encryption system from scratch? There are *plenty* of encryption systems freely available, and GPL too, so you can just use the bits you want for your own software. Is there something I'm missing?

---

### Post by TwiceOver on 2008-09-24
I guess if you really need your documents "on the go".  Right now I just mount a share on my home server via CIFS and then use conduit to syncronize.  Obviously internally there is no encryption needed.

Would be kinda neat for on the go, but depending on connection could be really slow.  Might want to look into rsync for both ends as it will transfer only the needed changes to documents rather than the entire document.

---

### Post by solarwind on 2008-09-24
Ok. I'll write it without worrying about encryption on the server's disk. Let's see how far this gets.

---

### Post by dng000 on 2008-09-24
I have been discussing something similar to this with a friend of mine. I think this is a terrific idea for enabling secure offsite replication between two "trusted" parties.

An interesting use case would be combining multimedia libraries with a friend and making the entire library redundant and available on both ends. When one person adds to the library it automatically syncs with the other person.

In other words, a Dropbox without the third party server in the middle.

---

### Post by solarwind on 2008-09-24
> **dng000 said:**
> I have been discussing something similar to this with a friend of mine. I think this is a terrific idea for enabling secure offsite replication between two "trusted" parties.

An interesting use case would be combining multimedia libraries with a friend and making the entire library redundant and available on both ends. When one person adds to the library it automatically syncs with the other person.

In other words, a Dropbox without the third party server in the middle.

Without a server in the ***middle***. Either way there has to be a server *somewhere*, wheather it be on your machine or your friends'. Either way someone's computer has to be exposed on the internet with server privileges.

I can make a dropbox system right now if I wanted to that makes use of any FTP server. However, encryption is the biggest problem. What if someone at my webserver steals the hard drive? What if someone hacks into the webserver? What I'm saying is that the data that goes into the webserver must already be encrypted. The server can no way see the encrypted data.

Maybe something like public/private key encryption might work. Anyone can encrypt anything for you using your *public key*, but only **you** can **decrypt** your stuff with your *private* key.

The trouble is, how do we make it so that the data is already encrypted before it gets to the server? Once it's on the server, no one should be able to see your data, even if they have physical access to the hard drive.

---

### Post by dng000 on 2008-09-24
I should add that the added benefit is not having to keep a mirror of the data locally. You are basically amortizing the storage costs across both sites.

---

### Post by solarwind on 2008-09-24
I think I have another idea!

How about a filesystem-on-image? You would have an encrypted filesystem as an image on your FTP server and the system would mount it to a temporary directory on your hard drive through SFTP. It would then synchronize your "dropbox" folder and the remote mounted encrypted filesystem image. I think this would be the easiest method. I know it's possible to mount filesystem over FTP, but I don't know about encrypted filesystem images over SFTP. Is it possible?

---

### Post by dng000 on 2008-09-24
So I guess we are talking about different use cases. I agree with you regarding the server(s). I envisioned both ends being servers and both ends being clients if you will.

For my use case, I think that as long as the encryption occurs over the transmission (the internet) that would be sufficient. I am thinking that a VPN would work.





> **solarwind said:**
> Without a server in the ***middle***. Either way there has to be a server *somewhere*, wheather it be on your machine or your friends'. Either way someone's computer has to be exposed on the internet with server privileges.

I can make a dropbox system right now if I wanted to that makes use of any FTP server. However, encryption is the biggest problem. What if someone at my webserver steals the hard drive? What if someone hacks into the webserver? What I'm saying is that the data that goes into the webserver must already be encrypted. The server can no way see the encrypted data.

Maybe something like public/private key encryption might work. Anyone can encrypt anything for you using your *public key*, but only **you** can **decrypt** your stuff with your *private* key.

The trouble is, how do we make it so that the data is already encrypted before it gets to the server? Once it's on the server, no one should be able to see your data, even if they have physical access to the hard drive.

---

### Post by dng000 on 2008-09-24
I am not technically competent enough to answer that. Hopefully someone out there will address this. I would really like to see something like this get off the ground.

---

### Post by solarwind on 2008-09-24
I found these two:
[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)
[http://shfs.sourceforge.net/](http://shfs.sourceforge.net/)

Now the only problem is making it so no one at the server can see your files (for example, server admins).

---

### Post by dng000 on 2008-09-24
Have you seen [www.wua.la?](www.wua.la?)

I think they are doing something similar to what is being proposed except they are "sharing" the storage across many clients in an encrypted manner.

---

### Post by versvs on 2008-11-18
I don't think wua.la is exactly the same thing that's been proposed here. Wua.la looks a lot like dropbox. third-party handled storage and third-party handled encryption.

I'm not technically competent to help coding this soft, but I would be a beta tester from the beginning.

Is there any project already open at SF.net, or somewhere else, that i can join?

---

### Post by solarwind on 2008-11-18
> **versvs said:**
> I don't think wua.la is exactly the same thing that's been proposed here. Wua.la looks a lot like dropbox. third-party handled storage and third-party handled encryption.

I'm not technically competent to help coding this soft, but I would be a beta tester from the beginning.

Is there any project already open at SF.net, or somewhere else, that i can join?

Unfortunately, no. I'm only 17 years old and in high school last year. I have the competence and coding ability to start this project, but just don't have the time. If someone would like to help though, that's a different story.

---

### Post by MunkyJunky on 2008-11-21
This is something I'd love to have. I'm only 18, and studying in university, but I get long (4 day) weekends, so I may be able to help code it, depending what language you use. I don't mind learning a new language to help out either. If you want a hand, send me a message! :D

---

### Post by solarwind on 2008-11-21
> **MunkyJunky said:**
> This is something I'd love to have. I'm only 18, and studying in university, but I get long (4 day) weekends, so I may be able to help code it, depending what language you use. I don't mind learning a new language to help out either. If you want a hand, send me a message! :D

What are you good with? I'm thinking of a combination of C++ and Python.

---

### Post by ssam on 2008-11-21
maybe this could be part of [conduit]("http://www.conduit-project.org/"). also have a look at [duplicity]("http://duplicity.nongnu.org/").

---

### Post by castrojo on 2008-11-21
Novell's ifolder was doing this years ago (other than the encryption on disk), unfortunately it was abandoned. I have the mirrors of the SVN repositories here though it's bitrotted and probably doesn't build:

[https://edge.launchpad.net/simias](https://edge.launchpad.net/simias)
[https://edge.launchpad.net/ifolder](https://edge.launchpad.net/ifolder)

They have the server piece, the client for windows, linux, and OSX, it was quite cool at the time. You might want to check it out and if you're interested in taking over a rejuvenation effort let me know. :)

---

### Post by mbirth on 2008-12-03
There's [Tango Dropbox]("http://etonica.com/dropbox/"), which maps a folder to a FTP account. Everything you "drop" into that folder will be uploaded to the specified FTP server.

But what I'd like to have is something like the [Dropbox]("http://getdropbox.com")-Service for my own server - something which can also handle deltas (i.e. transfers only the changed bytes instead of whole files).

Cheers,
  -mARKUS

---

### Post by bruce89 on 2008-12-03
> **mbirth said:**
> But what I'd like to have is something like the [Dropbox]("http://getdropbox.com")-Service for my own server - something which can also handle deltas (i.e. transfers only the changed bytes instead of whole files).

Cheers,
  -mARKUS

It's called git (or any other DVCS).

---

### Post by mbirth on 2008-12-07
> **bruce89 said:**
> It's called git (or any other DVCS).

Yeah, but git doesn't watch a folder and automagically updates everything ... but anyways, it's worth a try. Didn't think of this possibility... thanks!

**EDIT:** After thinking about it, using *incron* (if something local changes, update TO repo) and *crontab* (update FROM repo periodically) ... this should be possible.


Cheers,
  -mARKUS

---

### Post by Mebus on 2008-12-21
Maybe this is useful:

[http://freshmeat.net/projects/kfsmd/](http://freshmeat.net/projects/kfsmd/)
[http://en.wikipedia.org/wiki/Inotify](http://en.wikipedia.org/wiki/Inotify)

[http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html?ca=drs-](http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html?ca=drs-)

Mebus

---

### Post by magmon on 2008-12-21
Adrive.com has a free online storage service where you get 50 gb. Is this kinda like your idea? There are other plans available too, but they are quite alot more costly.

---

### Post by Mebus on 2008-12-22
Nope, I think we need the Open Source Client Software and then will use our own ftp-Server.

:popcorn:

Mebus

---

### Post by borobudur on 2008-12-25
Hey, but why to synchronize over the web. If you have laptops and you regularly come back to your home network, your data is synchronized enough. 
Advantage:
- no third party storage
- bandwidth is good enough for large data
- no encryption necessary

Is there something like dropbox but for your local intra net which works with nautilus? 

I'd love to have something like dropbox just in my own network, so I could have all the same (synchronized) data on each machine and nicely visualized in nautilus.

---

### Post by borobudur on 2008-12-29
> **whiprush said:**
> Novell's ifolder was doing this years ago (other than the encryption on disk), unfortunately it was abandoned. I have the mirrors of the SVN repositories here though it's bitrotted and probably doesn't build:

[https://edge.launchpad.net/simias](https://edge.launchpad.net/simias)
[https://edge.launchpad.net/ifolder](https://edge.launchpad.net/ifolder)

They have the server piece, the client for windows, linux, and OSX, it was quite cool at the time. You might want to check it out and if you're interested in taking over a rejuvenation effort let me know. :)

whiprush: can you tell us why nobody continues with the iFolder project? It looks like a really cool feature to have in your own LAN. 

Did I understand it correct that iFolder is acctualy the same like dropbox? You have on each machine a synchronized version of your data?

---

### Post by castrojo on 2008-12-29
> **borobudur said:**
> whiprush: can you tell us why nobody continues with the iFolder project? It looks like a really cool feature to have in your own LAN. 

I agree it is cool. Novell for some reason just stopped committing stuff in the public repositories. I /think/ that they still have a commercial version that they sell to their customers.

I don't think anyone forked it or picked it up because people don't immediately get what it's for, which is why you have people saying "what's wrong with ftp/webdav?" or "use git". It wasn't until dropbox became popular that people started asking for a private version.

At the minimum you'd need someone who knows C#/Mono/GTK to look at both simias and ifolder and determine what needs to be done to fork it and get it to build. (The code is imported into launchpad so it's in bzr ready to go) I've had a few C#-smart friends look at it and tell me it's not trivial to get it working at this state though.

> Did I understand it correct that iFolder is acctualy the same like dropbox? You have on each machine a synchronized version of your data?

Yep, nautilus integration and everthing.

---

### Post by castrojo on 2008-12-29
Looks like this guy might have gotten it to work: [https://launchpad.net/~ruiboon/+archive](https://launchpad.net/~ruiboon/+archive)

You might want to contact him.

---

### Post by cb951303 on 2008-12-29
I don't see the problem with encrypting the data? Encrypt anything that goes out of your computer with your public key and than decrypt all data coming to your computer using your private key.
What exactly is the problem? 

BTW, nice project! It would be really good to have a dropbox like application that uses ordinary ftp servers.

---

### Post by MunkyJunky on 2009-01-18
Just a thought regarding the front-end. Nautilus-dropbox (the nautilus plugin thing for dropbox) is GPL'd, so you could always pick that up and just change the notification area logo to something of your own. It would save you having to write your own, but I haven't looked into it much, so I don't know how easy this would be to do.

---

### Post by kevindontenville on 2009-07-03
Just to update did everyone see this:

[http://www.novell.com/news/press/ifolder-project-releases-latest-source-code-and-packages-for-linux-mac-os-x-and-windows/](http://www.novell.com/news/press/ifolder-project-releases-latest-source-code-and-packages-for-linux-mac-os-x-and-windows/)

Thought it might help those looking like I was for progress information!

K

---

### Post by EarthMind on 2009-07-03
> **solarwind said:**
> Disadvantages of Dropbox:
* You want to sync personal files, but you don't want to trust any third party to manage encryption for you. This is the biggest issue.


I put my personal files in encrypted 7z archives and then upload 'em

---

### Post by gardara on 2009-08-13
No news on this?

Is everyone just going to use dropbox/ubuntuone?

I would love to use one of my servers instead of the dropbox servers

---

### Post by aysiu on 2009-08-13
How about SpiderOak?
[https://spideroak.com/](https://spideroak.com/)

It seems to be pretty good on the privacy/encryption front.

---

### Post by gardara on 2009-08-13
> **aysiu said:**
> How about SpiderOak?
[https://spideroak.com/](https://spideroak.com/)

It seems to be pretty good on the privacy/encryption front.

Can you run it on your own server?

---

### Post by borobudur on 2009-08-14
> **gardara said:**
> No news on this?

Is everyone just going to use dropbox/ubuntuone?

I would love to use one of my servers instead of the dropbox servers
Did you try iFolder? Looks like *THE* solution to me.

---

### Post by kevindontenville on 2009-08-14
For those interested in iFolder I found this howto which looks current and workable!

[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)

I havent built one with this yet but I will be trying it over the next week.

---

### Post by Thirtysixway on 2009-08-15
> **MaxIBoy said:**
> A rand() call seeded with the current time and multiplied by the value of the fifth pixel from the left in the twelfth row of a Game of Life fractal which has been seeded with the MD5 sum of a sound file of "Stepping Stone" by Jimmi Hendrix? Something secure yet reproduce-able.
:grin:

---

### Post by fak3r on 2009-09-21
while iFolder looks interesting, I've 'rolled my own' on a post I've called: 
[HOWTO build your own open source Dropbox clone]("http://fak3r.com/2009/09/14/howto-build-your-own-open-source-dropbox-clone/")

Built using Lsyncd, it watches a directory, then runs rsync against anytime it hears of a change (via inotify) it to sync to/from the server.  For now it's all commandline configuration, but I would like to develop this further, and plan on putting it into a production environment, so I appreciate all feedback to that post.

Thanks

---

### Post by LookTJ on 2009-09-21
You should look into truecrypt and see if it fits your needs :)

---

### Post by insane_alien on 2009-09-21
you can use truecrypt on dropbox.

or ecryptfs.

there are a number of solutions to the 'i don't trust dropbox'

i use truecrypt as i can mount it on windows too.

as for a homemade solution, ssh and scp work fine.

---

### Post by gjtoth on 2009-09-23
My webhost gives me unlimited storage.  How can incorporate some of the ideas here using my webhost?

---

### Post by Rohan on 2009-10-30
Does anyone know what exactly Dropbox runs on their backend? It might be easier to just setup whatever they do on their server and change their server address in your hosts file to your own server address.

---

### Post by Fl0ris on 2009-11-10
You can try Wuala, [http://www.wuala.com/](http://www.wuala.com/). It's a free application with 1GB online space for free when you sign up. But you can get more by referring friends, trading local disk space (install Java and Wuala on your server or desktop computer and trade the disk space) and of course you can buy it on their website.
You can access your files via your file explorer (if you've turned on filesystem integration) and via the Wuala Java web and standalone application.

Check out their blog + another blog for more information:
[http://www.wuala.com/blog/2009/03/effective-usage-running-wuala-on-debian.html](http://www.wuala.com/blog/2009/03/effective-usage-running-wuala-on-debian.html) (you could try it with other Linux distro's as well)
[http://pascal.nextrem.ch/2009/10/20/wuala-init-d-script/](http://pascal.nextrem.ch/2009/10/20/wuala-init-d-script/)

Gigatribe isn't a solution yet, its next version will work on Linux machines: [http://www.gigatribe.com](http://www.gigatribe.com)

Another solution already mentioned here is iFolder:
[http://www.ifolder.com/](http://www.ifolder.com/)

---

### Post by dr.phees on 2010-01-15
I am using Unison for that. ([http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/))
It is available for Mac, Linux and Windows, someone even compiled it for a NAS (!!)

There are basically two ways to sync from outside your own LAN:

1. Let Unison run in socket mode on your server, open a tunnel (i.e. with Putty) and let the client connect to it.

2. Use it with ssh. It opens an ssh connection to my server, starts a Unison session and starts to synch.

I use it mainly with a batch script under windows in a loop, to keep my Thumbdrive with portableapps on it synched. The server is running linux.

I put the basic package on my http server, so I can always create a fresh version of the drive where ever I am.
You can even use it to synch more than just one client with the same server path.

Unison would be a perfect application to build an open source DropBox on. If there are coders available, I would gladly support the project where I can. Please let me know!

---

### Post by hessiess on 2010-01-15
I already do something simmaler to this with Subversion, plus get the added advantage of having the complete history of everything, partial check outs and the ability to synchronise an unlimited number of comps.

---

### Post by pvledoux on 2010-06-14
Did you saw this project?

[http://www.sparkleshare.org/](http://www.sparkleshare.org/)

Still in alpha but seems promising.

I'm searching that kind of solution because we have terabytes of data to sync/share between users, but we would like to have some versioning and annotation too.

---

### Post by xc1024 on 2010-06-15
It's great but Mono? Bleh, I've had enough of torturing myself with this Novell/MS hybrid crapware. And any other hybrid crapware from the abovementioned for that matter. *cough* moonlight *cough*

---

### Post by pi3ch on 2011-05-22
I recently create a post on **how to create your own Dropbox using shared host**. with encryption and auto sync. it also talks about how to encrypt your files efficiently. have look at it here. [http://bit.ly/owndropbox](http://bit.ly/owndropbox)

---

### Post by ssam on 2011-05-22
for LWN subscribers this article might be interesting
DVCS-autosync
[http://lwn.net/Articles/442841/](http://lwn.net/Articles/442841/)

talks about DVCS-autosync and SparkleShare. more things mentioned in comments.

for nonsubscribers, you can read it after thursday. or PM me for a link (LWN lets subscribers give friends links).

---

### Post by dwhite on 2011-05-22
> **aysiu said:**
> how about spideroak?
[https://spideroak.com/](https://spideroak.com/)

it seems to be pretty good on the privacy/encryption front.

+1

---

### Post by handy on 2011-05-22
> **pi3ch said:**
> I recently create a post on **how to create your own Dropbox using shared host**. with encryption and auto sync. it also talks about how to encrypt your files efficiently. have look at it here. [http://bit.ly/owndropbox](http://bit.ly/owndropbox)

I just had a read of your how-to, & checked out Unison:

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

To see if it was open-source & was happy to see that it is.

I think that the solution that you have provided the walk through for should suit many people.

Thanks. :)

---

### Post by spupy on 2011-05-22
My programming workspace turned too big to be synced with dropbox between 2 PCs and 3 linux installs. So I wrote a 10 line script that uses rsync to sync my workspace with a remote folder on my server. SSH's security + rsync's effective algorithm.
It's not automatic so I need to remember to run the script when I start and finish working.

---

### Post by tapczan on 2011-07-08
Try [http://sparkleshare.org/](http://sparkleshare.org/) - dropbox like soft with own storage server.

---

### Post by ssam on 2011-07-08
also SyncAny has just shown up
[http://www.syncany.org/](http://www.syncany.org/)

---

