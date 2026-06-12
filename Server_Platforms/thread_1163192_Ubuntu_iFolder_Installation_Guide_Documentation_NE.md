---
title: "Ubuntu iFolder Installation Guide? Documentation NEEDED"
date: 2009-05-18
forum: Server Platforms
---

### Post by wubrgamer on 2009-05-18
I need to install an iFolder ([Wikipedia http://en.wikipedia.org/wiki/Ifolder]("http://en.wikipedia.org/wiki/Ifolder"))server on my ubuntu 8.10 server at home.

I cannot find documentation for this specific task.

[Community Wiki https://help.ubuntu.com/community/iFolderEnterpriseServer]("https://help.ubuntu.com/community/iFolderEnterpriseServer") is outdated to ubuntu version 7.10

---

### Post by wubrgamer on 2009-05-19
Why is it that nobody responds to my requests for help anymore? I thought these were support forums?

Are there any other, more serious, support forums for ubuntu?

Honestly, I might switch distros over this. Not that I expect any of you to care, that isn't a threat, just a statement of where I stand.

I can never get the help I need for my systems anymore.

---

### Post by steev182 on 2009-05-19
Have you tried following the documentation given for 7.10? What differences are there between the installation procedure for 7.10 and 8.10?

iFolder's site only gives information for openSuSE, but apart from the rpm information, it should apply to ubuntu aswell.

Maybe the community part of iFolder's site could give some insight on how to install it on non openSuSE distributions.

---

### Post by lightnb on 2009-05-19
Have you considered using Samba?

---

### Post by wubrgamer on 2009-05-19
> **lightnb said:**
> Have you considered using Samba?

I currently use [Dropbox]("http://www.getdropbox.com/") and I'd like to have an unlimited dropbox solution in my own home.

Isn't that what iFolder is?

Basically?

It keeps folders synced automatically between machines.

Not just folder sharing, I can set up ftp/ssh/samba/whozitwhatitcalled shares all day, but it's the automatic/reliable syncing I'm after. (just with a larger limit than 2gb.)

---

### Post by scorp123 on 2009-05-19
> **wubrgamer said:**
> I need to install an iFolder ([Wikipedia http://en.wikipedia.org/wiki/Ifolder]("http://en.wikipedia.org/wiki/Ifolder"))server on my ubuntu 8.10 server at home. Please ask Rui Boon. He's got a PPA where he provides iFolder packages. But right now these are still the old versions. Maybe if you ask nicely he might build new packages?

[https://launchpad.net/~ruiboon/+archive/ppa](https://launchpad.net/~ruiboon/+archive/ppa)

Please also see this bug report:
"Needs packaging: iFolder"
[https://bugs.launchpad.net/ubuntu/+bug/87122](https://bugs.launchpad.net/ubuntu/+bug/87122)

Towards the end of that report several people suggest alternatives. Some are free + open source, some are free but closed source, some are commercial ...

I personally have settled with SpiderOak (closed source, but it "just works" with Linux and the first 2GB are free, and there is no limit on how many folders or how many PC's you can sync) and I'm quite happy with it.

[https://spideroak.com](https://spideroak.com)

---

### Post by Hopey on 2009-05-21
Some new information about this:

Mike Taylor  wrote on 2009-04-01:
> Hey everyone! Novell finally released their new version! Go see it at: [http://www.ifolder.com](http://www.ifolder.com) Also, people are actively talking about it on IRC on freenode, #ifolder.

Does this mean we could get Ubuntu packages for this anytime soon? Or is there some "political" reasons for Ubuntu people not to do it (Ubuntuone)?

---

### Post by wubrgamer on 2009-05-25
+1

---

### Post by albinootje on 2009-05-31
> **Hopey said:**
>  Does this mean we could get Ubuntu packages for this anytime soon? Or is there some "political" reasons for Ubuntu people not to do it (Ubuntuone)?

iFolder seems a little Novell/OpenSuse focused, but we can of course try to create working debs from the rpms using alien. :)

---

### Post by wubrgamer on 2009-06-01
Isn't linux software supposed to be distro-agnostic?

UGH, I'm getting so sick of *buntu.

Why can't things "just work" a little more?

Stop implementing features and just get the OS to work!

I got a mac and it's actually VERY feature-sparse, but VERY stable.

It doesn't even have full FTP client. But it's a stable OS which developers can focus entirely on their applications without any worry about the OS or it's internals.

Ubuntu needs to be a bit more like Apple. Provide the framework, encourage the devs.

[end-rant] 

Sorry for that...

I don't mean to flame, but really. "It works on another OS?" Not good enough. :(

---

### Post by albinootje on 2009-06-01
> **wubrgamer said:**
> Isn't linux software supposed to be distro-agnostic?

The iFolder project was dead, now it is back. 
Novell is a company that wants to promote itself, just like Apple wants more and more paying customers.

You can compile from source, or help with providing Ubuntu packages.

---

### Post by slurdge on 2009-06-02
Here are some instructions for installing iFolder on Ubuntu server. The process is quite straightforward, however there are some pitfalls that are best avoided. Hope that it helps.

[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)

---

### Post by TwiceOver on 2009-06-02
> **slurdge said:**
> Here are some instructions for installing iFolder on Ubuntu server. The process is quite straightforward, however there are some pitfalls that are best avoided. Hope that it helps.

[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)

Interesting...

---

### Post by wubrgamer on 2009-06-03
So...

this project, even though the source is open, is not "linux" software so much as it is Novell linux software. right?

---

### Post by slurdge on 2009-06-03
No. It is as much linux as everything else. However, since folks at Novell did develop it, it seems natural they first packaged it for Suse no ?
There is some guy that created .deb for 3.6.
The source is available as for any open source project. The fact they are no packages for Ubuntu does not signify this is a not 'linux'. Maybe it's not 'Ubuntu' yet, but it is certainly an open source project (with the server on linux).

---

### Post by wubrgamer on 2009-06-03
I understand that, but things like GNOME and Firefox are designed to be cross-platform and such.

I was merely trying to state that this felt as though iFolder is going "against the grain" in the open source world.

---

### Post by Hopey on 2009-06-08
> **slurdge said:**
> Here are some instructions for installing iFolder on Ubuntu server. The process is quite straightforward, however there are some pitfalls that are best avoided. Hope that it helps.

[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)


I tried this with Ubuntu server 8.04, but didn't get it to work. Problem was that it seems to be impossible to get mono and php both work together with apache.

I don't know if they have fixed this in 9.04, but I would rather use LTS releases with servers.

This surely haven't been made easy... I guess I just forget about it now and wait that someone fixes this apache/mono/php bug (that has been open for long time I guess) and/or makes some debian packages for ifolder.

---

### Post by wubrgamer on 2009-06-08
> **Hopey said:**
> I tried this with Ubuntu server 8.04, but didn't get it to work. Problem was that it seems to be impossible to get mono and php both work together with apache.

I don't know if they have fixed this in 9.04, but I would rather use LTS releases with servers.

This surely haven't been made easy... I guess I just forget about it now and wait that someone fixes this apache/mono/php bug (that has been open for long time I guess) and/or makes some debian packages for ifolder.

I would *_**LOVE**_* some packages for *buntu.  But again, I'm not a programmer, just a user.

Ugh, I hate it when developers make things intentionally "integrated" with THEIR systems rather than make them intentionally EASY TO INSTALL CROSS-PLATFORM/DISTRO

UGH

/end open-source gripes

---

### Post by whorider on 2009-07-23
[https://launchpad.net/~weboide/+archive/ifolder](https://launchpad.net/~weboide/+archive/ifolder)

.debs for juanty

---

### Post by wubrgamer on 2009-07-23
Thank you!

This is great work!

Do you think they will be placed into the standard universe repositories soon?

---

### Post by cariboo on 2009-07-23
Create a feature request bug on [Launchpad]("https://launchpad.net/")

---

### Post by Psycam on 2009-07-24
Wow I actually got this to work. Running 9.10 server edition fresh install, this is what I did:

(Assuming Apache is installed)
1. Setup certificate for SSL:
[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

2. Configure HTTPS for proper use:
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration](https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration)

3. Follow the instructions aforementioned on this page almost exactly (except you should change Simian admin password for security sake, it doesn't say that on the guide):
[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)

4. Followed step 9 of Debian (very similar) instructions to get rid of a minor error message:
[https://trac-git.assembla.com/unifolder/wiki/InstallingIFolderServerOnDebianLenny](https://trac-git.assembla.com/unifolder/wiki/InstallingIFolderServerOnDebianLenny)



Now I have a fully functioning iFolder server (tested with Mac client, going to try it on windows 7 soon). I also have a DropBox, but I'm using the precious 5gb for a shared group project right now, so having my own server space for syncing personal documents is pretty nice.

---

### Post by jars99 on 2009-09-29
Psycam:

When you say you got it working on 9.10 - are you talking about an alpha version?  Think it would work on 8.04, since it is the latest LTS?

Were you able to get a client installed in Ubuntu?

---

### Post by drejom on 2009-12-22
Any stories of success on 9.10 - preferably with documentation? (some of the links from psycam no longer work)

---

### Post by mdbarton on 2010-02-26
Just used the instructions at [http://www.x2b4.com/howto/how-to-ins...ubuntu-server/](http://www.x2b4.com/howto/how-to-ins...ubuntu-server/) to create the server on my karmic server box, will try installing the clients soon....

---

### Post by capscrew on 2010-02-26
> **mdbarton said:**
> Just used the instructions at [http://www.x2b4.com/howto/how-to-ins...ubuntu-server/](http://www.x2b4.com/howto/how-to-ins...ubuntu-server/) to create the server on my karmic server box, will try installing the clients soon....

Some how the above link doesn't work.  The following should work (at least it does for me).

[_**[COLOR="Navy"]http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/[/COLOR]**_]("http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/")

This is great news.

---

### Post by tatewaki on 2010-03-24
Now i have tried iFolder for about 1 week, and i think it looks a lot as subversion, or is it just me? You can sync folder to a central server and have version control on the folder. Is that not what subversion can do? You can even setup a webdav thing for subversion, like the webaccess iFolder is providing. The only diff. i can really see is that iFolder auto syncs every X min.

Is it just me?

---

### Post by tatewaki on 2010-03-25
Also for people that are looking for alternative to iFolder i have the following: [http://tonido.com]("http://tonido.com") or [http://www.teamdrive.com]("http://www.teamdrive.com")

---

### Post by sanjaya on 2010-04-01
I have working scripts to build iFolder clients that work on Ubuntu 9.10 and the Simias server builds on Ubuntu 9.04

Join the group:

[http://groups.google.com/group/ifolder-ubuntu-debian-dev](http://groups.google.com/group/ifolder-ubuntu-debian-dev)

Read them before using. You may need to additional packages, post your issues there in group (not here) and I can incorporate them into future versions of the script.

I need testers to contribute their bug reports and error so the Ubuntu community can help the iFolder and Simian developers helps us get solid debs for Ubuntu.

---

### Post by HermanAB on 2010-04-02
Sooooo, what do you really have a problem with?

If you want a Linux system where you can go click happy with wizards for everything like in Windows, then you should switch to Suse or Mandriva.  

Ubuntu is really aimed at people that are content to do some things themselves.  So in other words, if Ubuntu happens to have a wizard for something, cool, by all means use it.  If it doesn't, then you got to RTFM. 

Sorry, but that is just how it is - pick your poison and deal with it!

---

### Post by sanjaya on 2010-04-02
Not sure who HermansAB comment is aimed at. I for one am definitely a do it your-selfer and focused on weeding out problems so the whole world does not have to reinvent the wheel every time.

First feedback from someone who used the scripts is that they successfully compiled a working client.

[http://groups.google.com/group/ifolder-ubuntu-debian-dev/browse_thread/thread/00691f855f6b95e4?hl=en#](http://groups.google.com/group/ifolder-ubuntu-debian-dev/browse_thread/thread/00691f855f6b95e4?hl=en#)

---

### Post by JigglyWiggly_ on 2010-05-08
Help

[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)


Go to step 3

Get the simias source from sourceforge:
wget [http://downloads.sourceforge.net/project/flaim/stable/flaim/source/libflaim-4.9.845.tar.gz?use_mirror=freefr](http://downloads.sourceforge.net/project/flaim/stable/flaim/source/libflaim-4.9.845.tar.gz?use_mirror=freefr) -O - | tar -xzf -
cd simias-1.8.3.9328.1/

How do you cd into simias-1.8.whatever

There is no folder that was ever created for that!

---

### Post by JigglyWiggly_ on 2010-05-08
> **whorider said:**
> [https://launchpad.net/~weboide/+archive/ifolder](https://launchpad.net/~weboide/+archive/ifolder)

.debs for juanty

How do I access the admin page after installing it?

---

### Post by JigglyWiggly_ on 2010-05-08
How can none of you care about ifolder? It's like dropbox but on your own server.

---

### Post by CharlesA on 2010-05-08
There are better methods of doing it on a local LAN. Samba, NSF, etc.

If you extracted the tar, it should have created a directory. cd into that.

It still looks like a major pain in the **** to even get it running on an Ubuntu base. I'll stick with SMB.

---

### Post by JigglyWiggly_ on 2010-05-09
Thing about iFolder is, that all the clients keep the files themselves on their hard drive, and they sync.

It is a pain to configure, I even made an opensuse machine, and of course the package ruins into "unresovable dependencies"
Tried fixing it, only to see when I run simias-server-something script, it crashes connecting to the openldap server.

They have such a nice program, it just needs to be fixed up...
By that, I mean packaged for deb :P

---

