---
title: "Prevu and mythtv .20?"
date: 2006-10-25
forum: Repositories &amp; Backports
---

### Post by McQuaid on 2006-10-25
Referring to jdong's backport program for edgy to dapper
[http://ubuntuforums.org/showthread.php?t=268647](http://ubuntuforums.org/showthread.php?t=268647)
I'm wondering if mythtv .20 would be a good candidate for prevu.


I have a dapper box that for various reasons won't be upgrading to edgy for a bit but I'd like mythtv .20 on it.  I'm concerned if I'll run into issues with some of the dependences (mainly mysql stuff).  Will preview attempt to backport mysql etc as well?  Would it still if I install the dapper binary's of mysql first?  And would that even be recommended?

Just trying to pick the smoothest way to get mythtv .20 on dapper.

---

### Post by superm1 on 2006-10-26
I have been hosting a dapper repository with the same sources being released for edgy.  It also has the missing libraries that would normally fail through prevu, libraw1394, libavc1394.

```
#my myth repo
deb http://home.eng.iastate.edu/~superm1 dapper main
deb-src http://home.eng.iastate.edu/~superm1 dapper main
```

---

### Post by McQuaid on 2006-10-26
I'm gald to see this, I'm sure this will save a lot of headaches.  I searched for a dapper rep, but never came across yours.  There really should be an apt-get.org/search equiv for ubuntu.

But anyway ran into my first snag, got this at the end of the install:

E: mythtv-database: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured

but I'll continue with the configuring and see if it resolves it.

---

### Post by superm1 on 2006-10-26
There have been a number of issues with using mythtv-database.  Your original install, how was it done?  if its originally installed from source, update a file named /etc/mythtv/mysql.txt.  This needs to match the settings for where your mysql server is setup and the correct username and password for the database if it already exists.

---

### Post by McQuaid on 2006-10-26
I reinstalled mythth-database just to get a more detailed console output:

Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mythtv-database (0.20-0.2ubuntu1) ...
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu1); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv


Ok, so seeing your post and this, I'm sure it's a mysql issue.  When first installing it asked me the mysql database pass, which I haven't set up on this system and help said to most likely leave this blank.

I'll read up on the mysql part but if you have any info to get me started quickly or point me in the right direction it would be great.

Oh and regards to your question, I never had mysql nor mythtv on this box so I never touched the source of either.

---

### Post by superm1 on 2006-10-26
This may be a silly question, but Do you have mysql-server installed an running?  It's not installed by default because mysql-server doesn't have to be on the machine that mythtv-database is installed on.

---

### Post by McQuaid on 2006-10-26
And looking in /etc/mythtv/mysql.txt I see a db name and generated dbpass word.  The original install asked me for that, Could I just reinstall mythtv (not sure which particular pkg) and input the password or do I need to setup mysql manually at this point?  And I assume I have to create the user account mythtv, not sure if the install did that.

---

### Post by superm1 on 2006-10-26
The install creates the mythtv user account.  When you install mysql-server, you should be able to complete the install.

Be sure to run mythtv-setup as sudo however.  This will make sure that /etc/mythtv/mysql.txt is readable.

so in short:

```
sudo aptitude install mysql-server
```

If the install of mythtv-database doesn't finish from this step,

```
sudo apt-get -f install
```

And lastly, start the backend setup:
```
sudo mythtv-setup
```

---

### Post by McQuaid on 2006-10-26
Heh, not a silly question at all, nope it wasn't installed, I thought it was flagged for install during myth's install, but makes sense that mysql doesn't need to be on the same box.  

I've installed it now, and reinstalled database with no errors, thx a lot for the assistance.  

And now I noticed the mythtv user has been created, I'll continue on with the setup procedure and post back.

---

### Post by McQuaid on 2006-10-26
Hmm, I replied earlier but just noticed it didn't post.

Heh, no it's not too silly a question, I thought I had it flagged for install but I didn't.  I've installed it now and everything seems to be configured properly. Thanks again.

Now, on to actually configuring this beast.   The first thing I'd like to do is get my ati remote working with this.  I've seen some guides that use lirc, but for awhile now there has been an ati module which I already have loaded.  It has the basic keys configured, but never looked into how to configure this with all the buttons.  Too bad myth doesn't have a remote configuration utility.  

Next I want to set up a mythfrontend on another box to log into this one.  

One thing I haven't been able to figure out is when watching live tv, if I push up/down to see the text description of whats on other channels, it has the description, but in the top left of the popup it says 'adding cha'  (assuming adding channel).  During the guide setup I said sort by channel number and not by name, not sure if that gave it some issue.

Btw, I wanted to run through the setup just to check things over again, and it said the backend is already running.  I know I could just kill the process but is there a more graceful way of shutting it down?

And the mythtv user just launches gnome by default, once it's all configured I want it to automatically launch mythfrontend, or better yet have that as an option in gdm for the sessions, so I can launch the mythtv user in a normal (gnome/icewm etc) session if I need to troubleshoot stuff.

Right now I'm just launching icewm and from there launching the front end and just having icewm hide the panel.

---

### Post by superm1 on 2006-10-26
> **McQuaid said:**
> 
Now, on to actually configuring this beast.   The first thing I'd like to do is get my ati remote working with this.  I've seen some guides that use lirc, but for awhile now there has been an ati module which I already have loaded.  It has the basic keys configured, but never looked into how to configure this with all the buttons.  Too bad myth doesn't have a remote configuration utility.  


So you have an ATI Remote wonder?  If you want to configure it with lirc, you will have to blacklist the ATI remote wonder kernel driver.  I don't know what its called offhand, but you should be able to determine it from lsmod.  Add a line  in /etc/modprobe.d/blacklist to blacklist this module.


You should be able to configure lirc then as lirc is normally configured.  See the lirc wiki page, and let me know what information is missing from setting it up.

> **McQuaid said:**
> 
Next I want to set up a mythfrontend on another box to log into this one.  


If this is a fresh install, take a look at the MythTV wiki page for edgy [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

It should be able to get you up and running.  Again, if anything is missing (these pages just got put up the last few days and i'm sure i'm missing some content), ping me and let me know.

> **McQuaid said:**
> 
One thing I haven't been able to figure out is when watching live tv, if I push up/down to see the text description of whats on other channels, it has the description, but in the top left of the popup it says 'adding cha'  (assuming adding channel).  During the guide setup I said sort by channel number and not by name, not sure if that gave it some issue.


This i'm not too sure about.  I *never* use livetv at *all.  *I'd say query the mailing list :)

> **McQuaid said:**
> 
Btw, I wanted to run through the setup just to check things over again, and it said the backend is already running.  I know I could just kill the process but is there a more graceful way of shutting it down?
 

```
sudo /etc/init.d/mythtv-backend stop
```

> **McQuaid said:**
> 
And the mythtv user just launches gnome by default, once it's all configured I want it to automatically launch mythfrontend, or better yet have that as an option in gdm for the sessions, so I can launch the mythtv user in a normal (gnome/icewm etc) session if I need to troubleshoot stuff.

Right now I'm just launching icewm and from there launching the front end and just having icewm hide the panel.

See the wiki page again.  The description of a frontend only machine explains exactly how to do this.  I did it with openbox, but you should be able to adapt it to icewm as well.

---

### Post by McQuaid on 2006-10-26
Man I'm glad I found out about your rep, It saved me lots of time.

I've seen others mention using lirc, I thought it was kinda cool that there's a module ready to go for my ati, and was reading about setting up the keys using xmodmap.  If I do go the lirc route instead, does this ease the setup for myth?  Does myth have it's own config for ati remotes using lirc?


But regardless thanks for your help, and I'll read more info at the wiki's.

---

### Post by superm1 on 2006-10-26
> **McQuaid said:**
> Man I'm glad I found out about your rep, It saved me lots of time.

I've seen others mention using lirc, I thought it was kinda cool that there's a module ready to go for my ati, and was reading about setting up the keys using xmodmap.  If I do go the lirc route instead, does this ease the setup for myth?  Does myth have it's own config for ati remotes using lirc?


But regardless thanks for your help, and I'll read more info at the wiki's.

Lirc is nice because then you can have different buttons have different purposes in all your apps.  Say you want your skip right button to skip commercials in myth, but you want it to skip chapters in xine.  The keys aren't necessarily the same for both, and this way you don't need to modify the keymaps, but just the lirc configuration.

I'm sure that you can find some configs online that show how lircrc files for myth work with an ati remote to save yourself the trouble figuring out what buttons work well with what.

Whichever route you go, add a page to the wiki.  Once you get all the material in, let me know, and i'll link to it and clean it up to match the style for the other pages.

---

