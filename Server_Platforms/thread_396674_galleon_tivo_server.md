---
title: "galleon tivo server"
date: 2007-03-29
forum: Server Platforms
---

### Post by bmenge on 2007-03-29
I posted this on the tivo forum with no answers and was hoping that maybe someone where might be able to help

Running galleon in linux terminal with ubuntu 6.10 this had been working earlier but now will not start.

brian@brian-desktop:/usr/share/galleon/bin$ sudo ./run.sh
Password:
Galleon 2.3.0 is starting...


I have tried this a number of times and it will hang here indefinitely

any ideas?

I try to find the galleon apps on the tivo and there is nothing there.

---

### Post by bmenge on 2007-04-12
ok so I got rid of my galleon folder and started fresh.  I reconfigured galleon and no get galleon is ready but when I run the ./gui.sh command it won't connect to the server.  someone here has to know about the galleon server.

---

### Post by jdalegonzalez on 2008-05-20
I've got it installed and mostly working.  For me, when the gui couldn't connect to the server, it was because the server was running as root - which created a log file - and the client was run as a normal user that couldn't write to the log file.

If I were you I would:

1) Get the latest version.  I think it's 2.5.1
2) Remove whatever your current version is.  You can back up configure.xml if you care.
3) unzip the galleon file.
4) One of the shell scripts (galleon itself maybe?) has a reference to etc.d/functions.  Comment this out.
5) The make file references chkconfig.  That call is going to fail.  I've seen a couple of threads claiming to give instructions on how to get chkconfig working on unbuntu, but I could never get it going with Gutsy.  So, I just ignored the chkinstall failure and ran galleon by hand from the shell.
6) run sudo make install.  I don't know if it REALLY has to be run as root but I didn't feel like dealing with permissions errors.
7) cd to /usr/share/galleon/bin
8) run sudo ./galleon.  Again, not sure if this has to be done as root.
9) run sudo ./gui.sh.  

Hopefully, you'll be mostly good to go.  I can't get the galleon as a service bit (which is what they're using chkconfig for) working and right now my tivo can't see the HME apps but pulling from the tivo is working fine.

---

