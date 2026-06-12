---
title: "Pidgin"
date: 2007-05-12
forum: Ubuntu Backports
---

### Post by DivineOmega on 2007-05-12
I'm curious. Will Pidgin be backported to Feisty?

---

### Post by Schalken on 2007-05-12
You can grab it from getdeb.net. It may or may not show up in Ubuntu backports, but not in the main repository.

**Edit:** Sorry I didn't realise this was actually in the backports forum. :P

---

### Post by angrykeyboarder on 2007-05-22
> **Schalken said:**
> You can grab it from getdeb.net. It may or may not show up in Ubuntu backports, but not in the main repository.

**Edit:** Sorry I didn't realise this was actually in the backports forum. :P

I just installed the package from getdeb.net in Feisty.

It segfaults at startup. ;)

---

### Post by tonyhawz on 2007-05-25
maybe you have to uninstall gaim first
[http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb](http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb)
[http://fosswire.com/2007/05/08/installing-pidgin-under-ubuntu-feisty/](http://fosswire.com/2007/05/08/installing-pidgin-under-ubuntu-feisty/)

---

### Post by angrykeyboarder on 2007-05-25
> **tonyhawz said:**
> maybe you have to uninstall gaim first
[http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb](http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb)
[http://fosswire.com/2007/05/08/installing-pidgin-under-ubuntu-feisty/](http://fosswire.com/2007/05/08/installing-pidgin-under-ubuntu-feisty/)

All things Gaim were removed. nautilus-sendto along with it. :(

```
$ pidgin
Pidgin has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

If you can reproduce the crash, please notify the Pidgin
developers by reporting a bug at
[http://pidgin.im/bug.php](http://pidgin.im/bug.php)

Please make sure to specify what you were doing at the time
and post the backtrace from the core file.  If you do not know
how to get the backtrace, please read the instructions at
[http://pidgin.im/gdb.php](http://pidgin.im/gdb.php)

If you need further assistance, please IM either SeanEgn or
LSchiere (via AIM).  Contact information for Sean and Luke
on other protocols is at
[http://pidgin.im/contactinfo.php](http://pidgin.im/contactinfo.php)
Aborted (core dumped)
```

---

### Post by DizzyTech on 2007-05-26
While this just isn't quite as good as having Pidgin itself in the actual repos, I use the Debuntu repos.

**[COLOR="Red"]Command-line method[/COLOR]**

Run either:
```

gksudo gedit /etc/apt/sources.list

```
or
```

sudo nano /etc/apt/sources.list

```

Paste the following code into the resulting file (simply Control+V if you used the first command, or Ctrl+Shift+Enter in the terminal):
```

deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse

```

Then, to trust their repositories, run:
```

wget http://repository.debuntu.org/GPG-Key-chantra.txt -O- | sudo apt-key add -

```

Then update:
```

sudo aptitude update

```

**[COLOR="Red"]GUI Method:[/COLOR]**

Open Software Sources, located in the System >> Administration menu.  It will ask for your password, input it and hit Enter.  In the new window that opens, navigate to the "Third-Party Software" tab.  Click "Add..." near the bottom.  Copy and paste the following line into that window:
```

deb http://repository.debuntu.org/ feisty multiverse

```

Repeat the process, but add "-src" (sans quotes) after "deb", like so:
```

deb-src http://repository.debuntu.org/ feisty multiverse

```

Now that that's done, navigate to the "Authentication" tab.  Use your web browser to download [this file](http://repository.debuntu.org/GPG-Key-chantra.txt).  You can use right-click, and "Save Link As...".   At the bottom of the Software Sources window, click on "Import Key File..." and navigate to where you saved the above file.

Now, click the Close button at the bottom of the window.  You will get a message about updating software information, click "Yes" or "Update".  The update software icon will appear in your task tray within a minute or so.

This repo is special, 'cause it has a GAIM transitional package to stay safe for Feisty updates.  This packages depends on the new Pidgin package, but has nothing else to speak of in the package.

(Sorry for my over-simplifying speak, I'm trying to make sense to all).

Extra note:  If you used to use the mlind repositories, you will have to update the Pidgin packages.  In Synaptic, use the buttons in the bottom-left to select Status, and then "Installed (local or obsolete)."  Click on each Pidgin package, and press Ctrl+E, and select the most recent version as long as it isn't "(now)".  If no Force Version dialog appears when you use Ctrl+E, then it's not in the new repo.  Run a search to make sure.

---

### Post by johnpaulett on 2007-06-04
I tried installing from source and it was actually very easy, I wrote a quick guide:

[http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/]("http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/")

~John

---

### Post by jamyskis on 2007-06-05
I've just had it pushed through as a security update. I was pretty surprised to find my GAIM gone and replaced by Pidgin.

---

### Post by kinkdxm on 2007-06-05
> **jamyskis said:**
> I've just had it pushed through as a security update. I was pretty surprised to find my GAIM gone and replaced by Pidgin.

sweet!
can't wait!
it's not showing up yet for me but hopefully soon.
was hoping that it would be done this way.
YAY! ubuntu!
:D

---

### Post by DizzyTech on 2007-06-06
How as a security update?  Doesn't ubuntu-desktop have to be updated as well because of its gaim dependency?

---

### Post by kinkdxm on 2007-06-07
it still didn't show up for me.

---

### Post by jamyskis on 2007-06-07
My mistake, it came through on another repo. I know for sure that it came in through updates though because I was a little confused when my GAIM suddenly disappeared and I mysteriously had something called Pidgin Instant Messenger in my menu. Yet my Synaptic says it was installed locally.

Never mind, Pidgin's available at the repository described [here]("http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn").

---

### Post by DizzyTech on 2007-06-07
Okay, but does that repo have the GAIM transition package for Feisty (or else you'll have both GAIM and Pidgin).

---

### Post by Mark76 on 2007-06-07
I got the following error at the config stage

/pidgin-2.0.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

What!? :|

Oh wait, I just remembered. I'm in Dapper :lol:

---

### Post by jamyskis on 2007-06-09
> **DizzyTech said:**
> Okay, but does that repo have the GAIM transition package for Feisty (or else you'll have both GAIM and Pidgin).

Yes it does. However, I would recommend shutting down GAIM and anything that is linked to it (Evolution etc.) when you go to install it as apt-get will remove the important stuff related to Evolution and GAIM access. If you leave them on, your desktop could get quite unstable.

From what I see, it leaves the GAIM extensions and data pack (gaim-data, gaim-guifications) installed, you'll need to get rid of these manually.

---

### Post by tommcdo on 2007-06-10
> **jamyskis said:**
> I've just had it pushed through as a security update. I was pretty surprised to find my GAIM gone and replaced by Pidgin.

Do you know if it will be pushed as an update on Kubuntu as well (as Gaim is not part of the default desktop)?

---

### Post by raccoonone on 2007-06-12
hey, I'm pretty new to Ubuntu, and I had a couple questions. One, anyone know, approximately, when Pidgin will be in the Ubuntu software installer? And, two, if I install it from one of these other repositories will that cause any problems when the "official" Ubuntu one has it?

---

### Post by DizzyTech on 2007-06-15
Use the repo in either of the posts above (I prefer the one my post references, 'cause it includes Thunderbird 2, also).  Both the newest Thunderbird and the newest Pidgin will be in Ubuntu 7.10, released in October.  (Sorry!)

---

### Post by mevets on 2007-07-05
thank you for the guide on how to install from that persons repo! I reinstalled and couldnt remember what repos I had in my sources.list!

---

### Post by Bruno Abinader on 2007-07-06
Hi guys,
Pidgin 2.0.2 Ubuntu Gutsy package *backported* to Ubuntu Feisty are available [here]("http://www.dcc.ufam.edu.br/~boa/pidgin"). More info about this on my blog post: [http://brunoabinader.blogspot.com/2007/07/pidgin-202-package-for-ubuntu-feisty.html](http://brunoabinader.blogspot.com/2007/07/pidgin-202-package-for-ubuntu-feisty.html)

Questions/Comments are welcome!

---

### Post by Artemis3 on 2007-07-07
2.0.2 is also at getdeb.net and it works.

---

### Post by MystaMax on 2007-07-14
> **DizzyTech said:**
> While this just isn't quite as good as having Pidgin itself in the actual repos, I used the repository discussed in [this topic]("http://ubuntuforums.org/showthread.php?t=446029").

To save you some clicking, the following goes into your /etc/apt/sources.list:
```

deb http://www.telemail.fi/mlind/ubuntu feisty main

```Then, to get his or her key, run:
```

wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | sudo apt-key add -

```Then update:
```

sudo aptitude update

```This repo is special, 'cause it has a GAIM transitional package to stay safe for Feisty updates.  This packages depends on the new Pidgin package, but has nothing else to speak of in the package.  The same repo works for Thunderbird 2.

(Sorry for my over-simplifying speak, I'm trying to make sense to all).

Hello DizzyTech does the repo you mention have pidgin-libnotify  ([http://www.debuntu.org/pidgin-libnotify-gaim-libnotify-for-pidgin-2.x](http://www.debuntu.org/pidgin-libnotify-gaim-libnotify-for-pidgin-2.x)) available? I did a quick search after adding the repos, but didn't see it. But, I wanted to ask anyway.

---

### Post by sharperguy on 2007-08-03
thanks

Now i just ned to figure out how to get the old smilie set back

---

### Post by fd0man on 2007-08-06
For those that have not seen this as of yet, Pidgin 2.1.0 is available through a repository maintained by myself and my friend Neatchee and contains both packages and plugins for i386 and AMD64 systems.  The information on the repository and everything that is in it can be found at:

 [http://www.trausch.us/pidgin](http://www.trausch.us/pidgin)

    — Mike

---

