---
title: "building 3proxy from source (FTP with ToR)"
date: 2007-05-27
forum: Server Platforms
---

### Post by malrost on 2007-05-27
This may be more appropriate in another forum, but since it's ultimately ToR-related, so security it is! I've been able to properly configure ToR so far, except for FTP. The  ToR FAQ recommends the use of 3proxy to do so, and that's where I'm stuck.

 The gist of it is that i'm stuck trying to configure 3proxy [http://3proxy.ru/download/]("http://3proxy.ru/download/")) as recommended on the helpful how-to ToR page ([http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO]("http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO"))

I've attached the errors. I'm following the 3proxy instructions for compiling using GCC under Unix/Linux ([http://3proxy.ru/howtoe.asp#GCCUNIX]("http://3proxy.ru/howtoe.asp#GCCUNIX"))

(Please note it appears THOSE instructions mistakenly first point to a non-existent Makefile.Linux, but the second mention is of the existing Makefile.unix.)

I'm a little rusty on compiling from source, so if you have a suggestion please be explicit with the proper commands.

I'm not married to 3proxy either; if there are any other suggestions for anonymous FTP.

Thanks!

---

### Post by malrost on 2007-05-27
Hm. Thought I'd attached the error text, but either I didn't or I lost them when previewing my post... anyway here it is.

---

### Post by Klein Moebius on 2007-06-04
First off, get the development sources from 3proxy: That'll be 3proxy-0.6-devel.tgz

Problems with overflow attacks against 3proxy are fixed in that one.

In your home directory, do:

mkdir 3proxy

then put the tarball in it.

cd 3proxy

tar xzf 3proxy-0.6-devel.tgz

cd 3proxy*

Make sure you've got a c compiler onboard:

sudo apt-get install gcc

Now, the Makefile.Linux blows for a Debian based distro,  so get rid of it.

I've attached a new Makefile.Linux.txt for this install:  it will place the binaries in /usr/bin and the manpages in /usr/share/man, and it will create /etc/3proxy

Place the new Makefile.Linux.txt as Makefile.Linux in ~/userwhatever/3proxy/3proxy-devel-0.6/

cd /home/userwhatever/3proxy//3proxy-devel-0.6/

sudo make -f Makefile.Linux

sudo make -f Makefile.Linux install

You will have to make a config file IAW the Tor site, and place it somewhere (/etc/3proxy/)

Then start 3proxy like this:

sudo 3proxy /etc/3proxy/configfile

I'm putting together a package for it at the moment, but I don't know how long it will take to get into the Debian repositories, thence the world...

Hope this helps...

---

### Post by Klein Moebius on 2007-06-05
I've attached a very rough .deb and sources for 3proxy - use at your own risk.  I haven't done anything fancy, such as boottime startup, etc, but it will install and uninstall cleanly with all docs so you can play around...  enjoy!

install the deb with this:

sudo dpkg -i 3proxy_0.6-devel-1_i386.deb

I do NOT have time to maintain this at the moment.  If someone wants to pick it up, feel very free,  and please consider contacting upstream about port maintenance.

UPDATE:  I'm deleting these files as it was pointed out to me that they don't work in Ubuntu.  Sorry.

I've attached a revised .deb to a message further along in this thread...

---

### Post by bslaveboy on 2007-07-28
> **Klein Moebius said:**
> First off, get the development sources from 3proxy: That'll be 3proxy-0.6-devel.tgz

Problems with overflow attacks against 3proxy are fixed in that one.

In your home directory, do:

mkdir 3proxy

then put the tarball in it.

cd 3proxy

tar xzf 3proxy-0.6-devel.tgz

cd 3proxy*

Make sure you've got a c compiler onboard:

sudo apt-get install gcc

Now, the Makefile.Linux blows for a Debian based distro,  so get rid of it.

I've attached a new Makefile.Linux.txt for this install:  it will place the binaries in /usr/bin and the manpages in /usr/share/man, and it will create /etc/3proxy

Place the new Makefile.Linux.txt as Makefile.Linux in ~/userwhatever/3proxy/3proxy-devel-0.6/

cd /home/userwhatever/3proxy//3proxy-devel-0.6/

sudo make -f Makefile.Linux


Hi, I got to this point, and then I got very similar errors to the poster above, here are the last couple of lines:

> 
3proxy.c:1808: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘struct commands’
3proxy.c:1813: warning: implicit declaration of function ‘pthread_mutex_init’
3proxy.c:1813: error: ‘bandlim_mutex’ undeclared (first use in this function)
3proxy.c:1814: error: ‘hash_mutex’ undeclared (first use in this function)
3proxy.c:1815: error: ‘tc_mutex’ undeclared (first use in this function)
3proxy.c:1816: error: ‘pwl_mutex’ undeclared (first use in this function)
3proxy.c:1824: error: ‘writable’ undeclared (first use in this function)
3proxy.c:1842: warning: implicit declaration of function ‘signal’
3proxy.c:1842: error: ‘SIGCONT’ undeclared (first use in this function)
3proxy.c:1843: error: ‘SIGTERM’ undeclared (first use in this function)
3proxy.c:1844: error: ‘SIGUSR1’ undeclared (first use in this function)
3proxy.c:1845: error: ‘SIGPIPE’ undeclared (first use in this function)
3proxy.c:1845: error: ‘SIG_IGN’ undeclared (first use in this function)
make[1]: *** [3proxy.o] Error 1
make: *** [all] Error 2


Any idea what's wrong?

---

### Post by Klein Moebius on 2007-07-29
Hmm.  The development version off 3proxy's site may have gone thru a minor upgrade since I posted this.  I'll take a look.

Have you attempted to install the .deb I attached?

---

### Post by bslaveboy on 2007-07-30
> **Klein Moebius said:**
> Hmm.  The development version off 3proxy's site may have gone thru a minor upgrade since I posted this.  I'll take a look.

Have you attempted to install the .deb I attached?

Yeah, I get this error with the package:

> 
sudo dpkg -i 3proxy_0.6-devel-1_i386.deb 
Password:
Selecting previously deselected package 3proxy.
(Reading database ... 89202 files and directories currently installed.)
Unpacking 3proxy (from 3proxy_0.6-devel-1_i386.deb) ...
dpkg: dependency problems prevent configuration of 3proxy:
 3proxy depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
dpkg: error processing 3proxy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 3proxy


Then I try:

> 
sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  3proxy: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Should I try install it with -f? If so, then do I type in "sudo dpkg -fi 3proxy_0.6-devel-1_i386.deb"?

---

### Post by Klein Moebius on 2007-07-30
Doh!

I built that one on my Debian Sid system.  I'll modify the Dependencies and repost tomorrow.

Sorry...

---

### Post by bslaveboy on 2007-07-30
Don't apologise!

I really appreciate you taking the time to help n00bs like myself. :)

---

### Post by Klein Moebius on 2007-08-01
OK, here you go.

Attached are a 3proxy .deb and sources from latest development version of 3proxy.

You need to check the config file in /etc/3proxy, then enable the daemon by setting ENABLED=1 in /etc/default/3proxy.

Use the configurations off the Tor site to guide you on setting up the config file.

Should work OK on Ubuntu.  If not, scream at me again....

Let me know how it works out for you!

Ciao,
Klein

---

### Post by bslaveboy on 2007-08-02
Thankyou! :)

It seems to work now. I modified the config files as shown on the torrify applications howto ([http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO](http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO)) and with enabling the daemon it seems to work.

Only thing is I can't seem to find a place to test if it is working. I know with http you can check at [http://torcheck.xenobite.eu/](http://torcheck.xenobite.eu/) to see if you're using the tor network. Is there anyway to validate that 3proxy with tor is indeed anonymising your ftp connections? I haven't been able to find one myself.

Again, thanks for all the help.

---

### Post by Klein Moebius on 2007-08-03
Hmm.  That indeed is a good question.  The answer's right on the tip of my so-called brain, but it's late right now.   Lemme cast around a bit, (and sleep) and get back...

---

