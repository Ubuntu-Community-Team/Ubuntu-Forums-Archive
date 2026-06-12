---
title: "uninstall LAMP?"
date: 2009-11-15
forum: Server Platforms
---

### Post by aaronchall on 2009-11-15
I think LAMP is using too much memory on my new little server, and I want to uninstall it.  What is the command line code to do this?  (aptitude doesn't work for me, too low on memory I guess.) Or perhaps, how do I make it not come up by default when the box comes on?

Aaron

---

### Post by Vegan on 2009-11-15
How much RAM do you have?

---

### Post by aaronchall on 2009-11-15
> **Vegan said:**
> How much RAM do you have?

256 Megs...

---

### Post by Vegan on 2009-11-15
You can remove it with....

```
sudo tasksel
```

and unselect LAMP should do the job.

---

### Post by aaronchall on 2009-11-15
Well, I tried the tasksel, and thanks to my small memory (I think) the GUI messed up on the second down arrow I hit.  It gave me a "General error mounting filesystems. A Maintenance shell will now be started, CONTROL-D will terminate this shell and re-try."

So what now?  Is there a simple command to turn off the related applications, as opposed to uninstalling them?

---

### Post by Vegan on 2009-11-16
You may have to add more RAM, you are too far ahead of yourself due to impatience.

---

### Post by aaronchall on 2009-11-16
> **Vegan said:**
> You may have to add more RAM, you are too far ahead of yourself due to impatience.
 
One line responses that have little meaning to those inquiring tend to aggravate impatience.

---

### Post by aaronchall on 2009-11-16
> **aaronchall said:**
> So what now?  Is there a simple command to turn off the related applications, as opposed to uninstalling them?

So, yeah, I guess this is where I'm at.  I don't really think of this as a chat room with an hour plus lag, I think of it more as a BBS type forum.

So, what is the "kill" command, and how do I list the processes that are running to shut them down and see how much memory I reclaim.  

And if the error isn't related to memory, what is it?  The GUI appears frozen, so I opened another tty (terminal?) and free tells me I have 14/250K system memory free...

If I can't get this to work well, I'm going to try Damn Small Linux instead, because I might be able to use a GUI with it, plus Samba... or maybe just NASlite...

---

### Post by Goobie81 on 2009-11-16
What version is it? If tasksel isn't working too well for you try this:

You can stop and permanently "switch off" LAMP (well the AM* component) by running:

```

sudo invoke-rc.d mysql stop
sudo invoke-rc.d apache2 stop
sudo update-rc.d -f apache2 remove
sudo update-rc.d -f mysql remove

```

update-rc.d doesn't check if the links exist, so make sure each command has more than one line of output (you might assume that it worked as it says "Removing any system startup links for blah")

it should look like this :

```
                           
 Removing any system startup links for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2
   /etc/rc1.d/K09apache2
   /etc/rc2.d/S91apache2
   /etc/rc3.d/S91apache2
   /etc/rc4.d/S91apache2
   /etc/rc5.d/S91apache2
   /etc/rc6.d/K09apache2

 Removing any system startup links for /etc/init.d/mysql ...
   /etc/rc0.d/K21mysql
   /etc/rc1.d/K21mysql
   /etc/rc2.d/S19mysql
   /etc/rc3.d/S19mysql
   /etc/rc4.d/S19mysql
   /etc/rc5.d/S19mysql
   /etc/rc6.d/K21mysql

```

If you want to uninstall the AMP constituents :
```
sudo apt-get --purge remove mysql-common apache2* php5-common
```
You may need to run sudo apt-get autoremove after that to remove the unused packages (Just remember to carefully read what autoremove is suggesting be removed)

Alternatively, based on [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) you can try :
```

sudo apt-get --purge remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

```

This is a surgical removal, what i suggested was more of a carpet bomb. Either way should work fine

---

### Post by aaronchall on 2009-11-16
Thanks, a lot, really, that was helpful!  Really, all I suppose I need to do is stop them, at least for the time being.  But removal may be a good idea too, if they're going to keep starting up by default.  

I think the carpet bomb approach will be the best for removal, since I can't cut and paste, and bomb is equivalent in terms of results.

---

### Post by aaronchall on 2009-11-22
So I uninstalled using the simple line one, followed up with autoremove, thanks!

---

