---
title: "Opengroupware.org"
date: 2006-03-30
forum: Server Platforms
---

### Post by stabface on 2006-03-30
Hi, I could use a lot of help. I tried to find this on the opengroupware forum but there is no help there. 

I work for a small record label and I was asked to install Opengroupware.org for the company. 

I don't know a lot about this, I have an inhouse server running microsoft server 2003, it is set up with ftp and is for mostly file sharing. Then i have a old pc turned into ubuntu file sharing server. 

then we have our remote linux based webserver with the works holding all of our  databases SQL, webpage, email etc. I was wondering if i could get some more helpful info on to how to go about installing something like this.

---

### Post by LKRaider on 2006-03-30
The [opengroupware.org]("http://opengroupware.org/en/install/index.html") site seems to have great documentation about it.

The easiest seems to be [Instant OGo CD]("http://opengroupware.org/en/instantogo/index.html")

There is a [Windows Install]("http://opengroupware.org/en/install/windows/index.html") avaiable (under Cygwin or VMware - or even MinGW).

On Ubuntu, you could try using the [gnustep-make-ogo]("http://packages.ubuntu.com/dapper/libs/gnustep-make-ogo") package, or use compiled [Debian Sarge packages]("http://opengroupware.org/en/install/debian/index.html").

---

### Post by stabface on 2006-03-30
thanks for getting back to me 
so i ran that make ogo and then i added the deb for opengroupware to my sources.list  

and ran apt-get install opengroupware and it seemed to install. but now i am lost on what to do any ideas?

---

### Post by LKRaider on 2006-03-30
Hm, sorry, never used it myself, so I can't be of much help.

You may have luck at their [forums or IRC]("http://opengroupware.org/en/users/support/index.html") tho.

---

### Post by BoneKracker on 2006-06-08
Did you get it installed?  

It looks like they've got it pretty well packaged for Debian, but not Ubuntu per se.

I'm interested in running this, but would like to avoid the configuration hassles of compiling it.  Did the deb work?

---

