---
title: "Amanda 2.6 and Glib 2.2"
date: 2008-07-16
forum: Server Platforms
---

### Post by matthewboh on 2008-07-16
I'm trying to install Amanda 2.6 - it allows you to backup to Amazon S3 - and I get this error message

checking for GLIB - version >= 2.2.0... no

I know the repositories are a bit old, so I'm trying to figure out the easiest / best way to install it.  Should I install gtk+ or just the glib libraries?  Do I have to uninstall anything?

Thanks,

---

### Post by windependence on 2008-07-16
If you just get this on the configure script, that doesn't mean it won't install. You should go ahead and do your make and install and see if it completes. Why aren't you intsalling Amanda from packages?

-Tim

---

### Post by matthewboh on 2008-07-16
I'm not using the packages because it's Amanda 2.5.2 and the capability for Amazon S3 wasn't introduced until version 2.6

I'll give it a try to keep going and see what happens.  Thanks for the incredibly quick response

Oops - won't let me run make - says no makefile found

---

### Post by windependence on 2008-07-16
You must be in the source directory and then do:

```
sudo ./configure
```

After that is finished you can do:

```
sudo make && make install && clean
```

-Tim

---

### Post by matthewboh on 2008-07-16
No go - got

```
sudo make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by windependence on 2008-07-16
what is the output of:

```
pwd

```

-Tim

---

### Post by matthewboh on 2008-07-16
I created the directory 

/opt/amanda

It's the root of the amanda download

Wahoo!

I needed to install libglib2.0-dev

---

### Post by windependence on 2008-07-16
Yes, but you also have to be in the source code directory to compile it. I guess you figured that one out :)

BTW what is Amazon S3?

-Tim

---

### Post by matthewboh on 2008-07-16
It's Amazon's Simple Storage Service - let's you store as much as you want on Amazon's servers - [http://www.amazon.com/gp/browse.html?node=16427261](http://www.amazon.com/gp/browse.html?node=16427261)

---

### Post by Ximbiot on 2008-08-19
Yep, that's what I did to get Amanda 2.6 to compile.  May have had to install a few other packages and specify --user=backup --group=backup or something like that too.  I also set Amanda up to use public key encryption before sending anything over the network and hid my private key on an encrypted USB key drive off the network.  Have had things backing up successfully to Amazon S3 for a month or two now from a small dapper drake production system which only backs up a couple of gigabytes in a level 0.

I also set up an almost identical install under Hardy recently.  It seems to be working except that for some reason my system is rebooting every morning at 7:30am, but I'll bring that up in another thread.

---

### Post by hmdicowii on 2009-01-09
You seem to have successfully installed Amanda. I have been attempting to do so with 2.5.2p1-1 for the last week but am obviously not familiar enough with Linux or Ubuntu 8.04 to accomplish this. Do you know of any step-by-step instructions, instructions that don't assume the reader knows very much, for downloading, configuring, installing, and using Amanda? If so, I'd appreciate a link or something to them so that I can begin using what appears to be the answer to my company's backup dream.

Thank you for your attention.

Peter
The Default IT Guy
BERRY ARCHITECTS, P.C.

---

### Post by matthewboh on 2009-01-09
The easiest way to install amanda is using apt-get or the package manager.  If you have a GUI running, just select "System | Administration | Synaptic Package Manager" and search for amanda

Or you can do it from the command line

```
sudo apt-get install amanda-server amanda-client
```

I "think" that will also pull in amanda-common - it will complain if it doesn't.

That package is for 2.5.2p1 from Amanda.  If you need S3 support, you will have to install from the packages from Amanda.

They currently have packages available here - [http://www.zmanda.com/download-amanda.php](http://www.zmanda.com/download-amanda.php) 

If you already have it installed - the best way to deal with it is:

Amanda uses directories under /etc/amanda (in the Ubuntu apt-get install version - may be different if you installed from source).  Each directory will represent a backup definition for you.  There's really three files that are important.  The disklist file will contain your list of files that you want backed up and the type of backup you will want.  Check out the Amanda wiki at [http://wiki.zmanda.com/index.php/Main_Page](http://wiki.zmanda.com/index.php/Main_Page)

The second file is the amanda.conf file - it tells Amanda about the backups, where to put the holding files, what your tape drive looks like, etc.  

The third file is the changer.conf - you shouldn't need to touch that.

Best place to start is the wiki - and there's a quick start guide.  I suggest that you read it - don't skim over it.  Amanda is really pretty simple once you get it up and running - it's just that most people that have used it are seasoned Linux folks.

---

### Post by encrytionguru on 2009-04-07
If you are looking to encrypt the data using Amanda backup software, have a look at Indra Networks website and their products.  It mention about integration with Amanda, and a very easy adn secure key management along with std Glib/Zlip compression thru dedicated hardware.  

Have a look at the following link it is informative.

[http://indranetworks.com/SSamanda.html](http://indranetworks.com/SSamanda.html)

Thanks,

---

