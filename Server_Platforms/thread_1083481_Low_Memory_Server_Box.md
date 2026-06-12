---
title: "Low Memory Server Box"
date: 2009-03-01
forum: Server Platforms
---

### Post by lazman on 2009-03-01
I was given an old computer that has 500Mhz cpu with 88 meg of ram (after the 8meg shared for video) the hard drive had failed in it and I put in a 6gig hard drive I stashed away after upgrading my desktop. (with the distros I have tried so far I have had no problems with hardware not working)

What I would like to do with this box is use it as a web server for family to use. I'm thinking xampp would do the trick nicely. I know with this low specs it's not going to be a speed demon but I would like something that would be responsive. The problem is I can't seem to find a linux distro that fits this type of setup. My goal is to have this box sitting in the corner on my home network serving webpages on the net, running an ftp server for file transfers, MySQL for website database, and using vnc from my desktop to control it when necessary.

I have tried a look at Damn Small Linux (DSL), DSL-N, and PCfluxboxOS, fluxbox simply will not run with any speed at all. DSL has speed but I can't seem to even download xampp from their webpage with it. When the browser starts it shoots the memory usage from about 20% to about 80% and becomes non-respondent when I click the download link. 

I was looking at slampp but the system requirements calls for 128meg (low I know, but sadly I just don't have it here). Then I was looking at Debian which would be nice because that is what Ubuntu is based on. I can't seem to find any system requirements for Debian. From what I gather about Debian is you can install the bare bones of the OS then simply add what software you need. If this is the case, is it possible to do this and only add xampp, vnc, perhaps a file browser of some sort, editing package for configuring the software files, and a light windows manager like fluxbox just to save the fingers with?

I understand I will have to configure at least the vnc server to start when the system starts. Auto starting xampp would be nice too, but I can figure that out after I get it up and running. 

My main thing is I have never installed Debian and I don't know if it's possible to select only the packages that I need at the time of install, I don't know if it will even work on this system to begin with, I'm not real sure what all the packages I would need other than the ones I have mentioned to be able to maintain a setup like this, and are there any "gotcha" things that I should be aware of with an install of this type? Has anyone ever setup a server like this? If so what distro did you use? What software did you put on it?

I have tried to figure this all out on my own, because that is the way to learn things. But this coaster making adventure it starting to become really time consuming as I have been trying to get this setup for two solid days now and have only learned what isn't working, which is at least something. Any help or advice would be GREATLY appreciated!

---

### Post by handy on 2009-03-01
You'd do much better in the Server Platforms sub-forum.

I've asked the mod's to move the thread for you.

---

### Post by Xiong Chiamiov on 2009-03-01
If it's an i686 processor (Pentium II and above, I believe), I'd strongly recommend taking a look at [Arch](http://archlinux.org).  Any of the systems in [this list](http://ubuntuforums.org/showthread.php?t=575456) should be good, too.

I'm not going to give you a full rundown of what you want to do, but here are a few points:
1) XAMPP is not meant to be used for anything besides development.  It's horribly insecure for actual usage.
2) Apache is a bit of a resource hog.  Use lighttpd or nginx instead.
3) MySQL also takes a bit of memory.  Depending on what you're doing, you can probably use SQLite instead.
4) Running a VNC server is wasteful.  For that matter, running X at all is wasteful.  Run ssh and do everything by the terminal.  If you *really* need to do some web browsing, use elinks, w3m or the like.  Things will be significantly snappier.

I'll be watching this thread, if you need more information than this.

---

### Post by handy on 2009-03-01
I'm an enthusiastic Arch user, but I wouldn't use Arch for a server.  I see no need for a server to be running cutting edge software.

There is an Arch based server distro in the works, you may be interested in looking at their site:

*_[http://arch-stable.wholebean.info/default.html](http://arch-stable.wholebean.info/default.html)_*

---

### Post by bapoumba on 2009-03-01
Moved to Servers, thanks Handy :)

---

### Post by lazman on 2009-03-01
bapoumba,

Thank you for moving this to the correct forum. This wasn't really a question about ubuntu, this is why I posted it in the general section.

I was not sure if the processor was i686 or i586, so I done some research and found that the processor in there is a AMD K6 3D and it is a i586. I also booted up DSL and it's also reporting it's a i586. The L1 and L2 are 32k each. I have no idea what the front side bus speed is, but the max for that chip is 100mhz. It's definitely not a quick processor compared to the Ghz that are around today. This computer was made in 1998 and I suspect the amount of ram that it was shipped with is only 64meg. The two memory chips are different sizes both in amount of ram and physical size.

Xiong Chiamiov,

Fist off, thank you for your reply! The processor being only i586 bumped me out of Arch, as it appears only a i686 disro is being supplied on their site. However, you have made a valid point of using lighter server software, and no gui. The reason I was looking at xampp is I have no experience configureing a production server in linux and was under the impression it could be secured with little effort. As far as the gui, I also have limited experience with the terminal and have never used ssh. However, I am here to learn! I am willing to give this a go, because I know you are right about the performance boost to a setup like this. But, as I would like for this to be a live server I also would like for it to be secure. I have not looked near as much into a guide to make a secure web server as I have a disro that would work on this system.

I was thinking about tying out previous releases of some of the distros (from around the year 2000). I think this might get a decent speed on this computer as it was shipped in 98. However, I think that approach will have some issues with bugs, security, finding the correct packages, and an overall bad idea. 

Now that Arch is out of the question, I think leaning toward Debian might be the best choice as I have read post about people getting it to run well on 300Mhz cpu with only 64meg of ram. I'm going to research more and see if the packages you suggested are also available for Debian. I'm still not sure if Debian will be the best choice, but it does look like it will be at least one option.

I'm really concerned about the low amount of ram this pc has in it. Tomorrow, if I don't get something going today, I am going to call the local computer store and see if they might have some of this old ram laying around and try to get at least up to 256 or 128. I think that would help the situation a lot. This system shipped with windows 98 on it. I'm thinking if it will run windows 98, it should be able to run a light load linux server as it is, but I could just simply be wrong on that assumption.

---

### Post by bapoumba on 2009-03-01
> **lazman said:**
> bapoumba,

Thank you for moving this to the correct forum. This wasn't really a question about ubuntu, this is why I posted it in the general section.


You are welcome. I'll add the [other_os] prefix to the thread.

---

### Post by linux_tech on 2009-03-01
check here for swap memory setup 
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Thirtysixway on 2009-03-01
You may be able to use DamnSmallLinux.  I've never configured it to use as a server but you could try.

---

### Post by lazman on 2009-03-01
I tried DamnSmallLinux. I was unable to get anywhere with it. I am currently trying a Debian install. I think it's about finished installing as I type this. I just hope it will run smoothly, and I will be able to figure out how to set it all up from the command line. If all fails, I can always start over.

That is one nice thing about having a computer I don't have to duel boot or anything like that. It's easy enough to just format and start again if I mess it up. I installed windows 95 about 50 times because I kept messing with it until I broke it and had no idea how to fix it. However, with that learning experience I was able to learn all about the OS, what it would and would not do, and how to fix things when someone started messing with stuff they shouldn't ;P. It made me "the computer guy" in a short amount of time.

Thanks for the suggestion.

---

### Post by cariboo on 2009-03-01
With only 88Mb ram you should be able to serve static web pages, buts that about all. Have a look at the [mini.iso]("http://help.ubuntu.com/community/Installation/MinimalCD") and only install what you need.

I would suggest installing a cli sytem, then install what you need.

Jim

---

### Post by albinootje on 2009-03-01
> **lazman said:**
> 
My main thing is I have never installed Debian and I don't know if it's possible to select only the packages that I need at the time of install, I don't know if it will even work on this system to begin with

With Debian you can easily do a very minimal installation. 
And grab your chance now, the shiny Debian Lenny is just out! :)

After installation you can go for the MySQL installation (apt-get install mysql-server) and for example lighttpd instead of apache2, although you might have to read some documentation because in some setups lighttpd has different requirements than apache.

Here's a link about tweaking MySQL : [http://www.joomlaperformance.com/articles/server_related/tweaking_mysql_server_23_16.html](http://www.joomlaperformance.com/articles/server_related/tweaking_mysql_server_23_16.html)

Install also rcconf, and make sure that only the mysql init script is started and not the other mysql related init scripts (which are for clustering afair).

---

### Post by kerry_s on 2009-03-01
> **lazman said:**
> I was given an old computer that has 500Mhz cpu with 88 meg of ram (after the 8meg shared for video) the hard drive had failed in it and I put in a 6gig hard drive I stashed away after upgrading my desktop. (with the distros I have tried so far I have had no problems with hardware not working)

What I would like to do with this box is use it as a web server for family to use. I'm thinking xampp would do the trick nicely. I know with this low specs it's not going to be a speed demon but I would like something that would be responsive. The problem is I can't seem to find a linux distro that fits this type of setup. My goal is to have this box sitting in the corner on my home network serving webpages on the net, running an ftp server for file transfers, MySQL for website database, and using vnc from my desktop to control it when necessary.

I have tried a look at Damn Small Linux (DSL), DSL-N, and PCfluxboxOS, fluxbox simply will not run with any speed at all. DSL has speed but I can't seem to even download xampp from their webpage with it. When the browser starts it shoots the memory usage from about 20% to about 80% and becomes non-respondent when I click the download link. 

I was looking at slampp but the system requirements calls for 128meg (low I know, but sadly I just don't have it here). Then I was looking at Debian which would be nice because that is what Ubuntu is based on. I can't seem to find any system requirements for Debian. From what I gather about Debian is you can install the bare bones of the OS then simply add what software you need. If this is the case, is it possible to do this and only add xampp, vnc, perhaps a file browser of some sort, editing package for configuring the software files, and a light windows manager like fluxbox just to save the fingers with?

I understand I will have to configure at least the vnc server to start when the system starts. Auto starting xampp would be nice too, but I can figure that out after I get it up and running. 

My main thing is I have never installed Debian and I don't know if it's possible to select only the packages that I need at the time of install, I don't know if it will even work on this system to begin with, I'm not real sure what all the packages I would need other than the ones I have mentioned to be able to maintain a setup like this, and are there any "gotcha" things that I should be aware of with an install of this type? Has anyone ever setup a server like this? If so what distro did you use? What software did you put on it?

I have tried to figure this all out on my own, because that is the way to learn things. But this coaster making adventure it starting to become really time consuming as I have been trying to get this setup for two solid days now and have only learned what isn't working, which is at least something. Any help or advice would be GREATLY appreciated!

don't use a gui and you'll be fine, anything with a gui is going to tear that puppy up. it can all be setup from the command line.
all you need is a server or base install from what ever distro you prefer.

---

### Post by Xiong Chiamiov on 2009-03-01
Debian is a good choice, and very similar to Ubuntu in many aspects.  The reason I put forth Arch was for it's customizability, rather than it's cutting-edge aspects.  Since you probably don't want to use a source-based distro on that processor, that rules out Gentoo and the BSDs.  If you're feeling adventurous, you might try Slackware.  Debian's good, though, don't get me wrong.

Oh, and you shouldn't really use older versions of Linux for older machines.  Newer ones are generally more efficient, as well as having security and bug fixes.

---

### Post by albinootje on 2009-03-01
> **Xiong Chiamiov said:**
> Since you probably don't want to use a source-based distro on that processor, that rules out Gentoo and the BSDs.

You can actually install a whole lot from packages with FreeBSD, and FreeBSD might be pretty nice concerning memory on such on old machine, although Debian or Ubuntu are propably much easier for the OP to install, configure and maintain.
> 
Oh, and you shouldn't really use older versions of Linux for older machines.  Newer ones are generally more efficient, as well as having security and bug fixes.
That's true when it comes to security and updates, but, very generally speaking, the older the Linux distribution the less memory it needs, and since the OP wanted to install a family file server, I don't think that computer security is a big issue there.

---

### Post by lazman on 2009-03-01
Well, I have a server up and running! YAY! I used Debian with only the base system installed (used about 20meg of ram), then installed nano for editing config files, lighttpd-php5 for webserver, sqlite-php5 for database, ssh server, for remote access. After all that was installed it's all running in only 76meg of ram! free -m is reporting I still have 7 meg to play with.

I setup a 219 meg swap, so if things get out of hand it should still work just will most likely slow down. However, I'm getting a quick response from it with just phpinfo().

I still need a good way to move files to it. There is no ftp server running. From what I understand I can move files with ssh. But It would take a really long time to move a few hundred files having to type them all out with the path. Is there a tool that I could use on my desktop that would use ssh in the background and do all the typing for me? Or, am I going abut this all wrong?

---

### Post by albinootje on 2009-03-01
> **lazman said:**
> Well, I have a server up and running! YAY! I used Debian with only the base system installed (used about 20meg of ram), then installed nano for editing config files, lighttpd-php5 for webserver, sqlite-php5 for database, ssh server, for remote access. After all that was installed it's all running in only 76meg of ram! free -m is reporting I still have 7 meg to play with.

Congrats, well done! :)
> 
I still need a good way to move files to it. There is no ftp server running. From what I understand I can move files with ssh. 
Install the openssh-server (apt-get install ssh) on your server, and then use scp/sftp clients like WinSCP on MS-Windows, gftp or FileZilla on Linux, or CyberDuck on MacOSX for your client machine(s).

And scp on the command line in Linux is also not so difficult, for example, secure copy the directory /data to your home directory on your server :
```

scp -r /data your_user_name@server_ip_address:

```
That's all.

With a GUI scp/sftp client you will get probably more transfer details and more "eye candy".

---

### Post by lazman on 2009-03-01
> **albinootje said:**
> That's true when it comes to security and updates, but, very generally speaking, the older the Linux distribution the less memory it needs, and since the OP wanted to install a family file server, I don't think that computer security is a big issue there.

Actually it is, I'm not talking about a LAN server. I want to put this on the internet for friends and family to view also. The only requirements I really need for the server is http with php, and a database for website login scripts using php. I could save myself a lot of effort and just pay godaddy to host my site for me (which is what I'm going now) but then what fun is that? I have been having a blast trying to get this up and running. And, I'm learning alot! It's a win-win. And it as the added benefit of not paying godaddy to host my site anymore :)

You guys have been really helpful! I would have not got anything going without all the suggestions. Thank you!

---

### Post by lazman on 2009-03-01
> **albinootje said:**
> Congrats, well done! :)

Thank you!

> **albinootje said:**
> Install the openssh-server (apt-get install ssh) on your server, and then use scp/sftp clients like WinSCP on MS-Windows, gftp or FileZilla on Linux, or CyberDuck on MacOSX for your client machine(s).

And scp on the command line in Linux is also not so difficult, for example, secure copy the directory /data to your home directory on your server :
```

scp -r /data your_user_name@server_ip_address:

```
That's all.

With a GUI scp/sftp client you will get probably more transfer details and more "eye candy".

This is just the type of thing I was thinking of. I do believe the default where the pages are loaded are not in the home directory. I still have to figure out how to setup the config for it all. But, at least it's up and running. And now I know how to move files to it. After I get it configured I think it will be ready for a port forward from the router. 

Thank you for all your help!
All of you!

---

### Post by Xiong Chiamiov on 2009-03-02
The default directory that web pages are served up from in Ubuntu is /var/www, at least for Apache (I've never run lighttpd on Ubuntu), although you can change that in the server config.

If you want to scp to a different directory, it'd be something like
```

scp -r /data user@server:/var/www/

```

I recently set up vsftp on a server, and put symlinks to the directories I wanted accessible in users' home directories, then chroot-ed them into their home, so they can't access anything I don't want them to.  I don't know if you'll need to do anything like that, if you're the only one ftp-ing, but if you do, you'll need to know [this](http://www.usenet-forums.com/linux-general/92992-vsftp-chroot-outside-home.html).

---

