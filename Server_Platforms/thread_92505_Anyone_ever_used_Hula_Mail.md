---
title: "Anyone ever used Hula Mail?"
date: 2005-11-19
forum: Server Platforms
---

### Post by s0c0 on 2005-11-19
My teacher has suggested I use something called hula-mail: [http://www.hula-project.org/Hula_Project](http://www.hula-project.org/Hula_Project) for my email server.  It looks pretty neat and has lots of exchange-like features, an all GUI, and web-based mail included.  No it's not in the apt repositories.  So has anyone used this before?  How hard is it to setup and how stable is it?

Also do you have other suggestions for me?  Bare in mind I've never tried setting it up.  I don't even think i have sendmail configured on my linux.

---

### Post by rsay on 2005-11-20
I tried the open-exchange server last week and it seemed pretty nice. The installation was no picnic but they had good howtos on their wiki.  The zimbra project looks very interesting but I haven't tried it yet. I looked at hula but I wasn't sure if they had a program that was ready for prime time. Has your teacher actually set up a hula server?

---

### Post by jimjawn on 2005-11-20
I'm using hula now and I've been running it, quite succesfully, for the last 6 months or so.  Its definitely not primetime yet but its getting pretty darn close.  I've been following it pretty closely and read the newsgroups about once a week or so.

Setup, literally, takes about 4 minutes.  Probably even faster if you've got broadband.  After you install, you're running IMAP/IMAPS, SMTP/SMTPS, POP/POPS HTTP/HTTPS, Integrated Antivirus and Spam Protection, ModWeb (A custom web server), A hack of the Novell eDirectory backend and hot monkey love.  The new calendaring interface is supposed to be sweet and the guys working on this project are pretty much linux rock stars.  A veritable who's who in the Gnome/SuSE/CalDAV/Mono world.  

Seriously, the install is pretty much turnkey.  There's a couple of fields you've got to fill out, but it runs, does what I tell it to and pretty much shuts up after install.  You can make it harder than it has be here:  [https://wiki.ubuntu.com/BuildingHula]("https://wiki.ubuntu.com/BuildingHula") or you can install the .deb files from here: [http://www.alcoholicsunanimous.com/hula/]("http://www.alcoholicsunanimous.com/hula/")  Seriously easy to install, seriously easy to remove.  I'm running it on a fedora core 3 box (that was the only package available at the time, but now its got your deb packages (see above...)  

Now for the bad/so/so news.  The UI as it stands now, isn't that impressive.  It will be someday from the screens on [nat.org and his kick ass CalDAV movie]("http://nat.org/demos/hula.html").  In fact, you can check out the alpha of that feature in one of the SVN trees.  There is a search feature and the CalDAV stuff, but the UI is flagrantly simple.  I can't do a lot of stuff with it that I can with say, squirrelmail or horde that I think MUST be included (like read reciepts and HTML format, etc.)  The coolest thing about this project though is the support you get from the IRC group and mailinglist.  These guys are for real.

I've also been playing around with [zimbra ]("http://zimbra.com/demo/")and am about to install it at a school site.  I must admit I'm so impressed with the quality of the project that I would make you eat turkey.  Its that good.  Oh and its HEAVY on the enterprise side and is much more developed and complicated than Hula is (in my opinion).  Easy to setup but overkill for a home server.

What I'd suggest is that if you have some time to kill and want to help a great project become even greater, check out hula, see how it goes and try to help fix it.  If you want to impress your friends and make ladies swoon with a cutting-edge AJAX app that is the first real exchange-killer contender for LINUX (IMHO) and you want to learn about web-services, check out ZImbra.  If you want to really, really learn most of the ins and outs of building and running your own email server from the ground up and find the most resources and frustrating hair pulling out times, [squirrelmail]("http://squirrelmail.org/").  Or even [roundcube]("http://roundcube.net/").  You will learn more about why people use linux than you'll ever care to.  Check out [howtoforge.com]("http://howtoforge.com") for hints.  

Personally, I'd suggest building your own squirrelmail box first, learning how it works, then checking out the alternatives.   If you want to check out hula, I can set you up with a simple demo account.  Let me know if your interested.  Good luck with this.  There are litterally hundreds of options and each have their own merits.

---

