---
title: "Firefox crashes"
date: 2010-04-22
forum: Ubuntuzilla
---

### Post by andreseso on 2010-04-22
Hello,

Lately I have had Firefox (Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100401 Firefox/3.6.3) crash on me almost every time I start it.  

From the command line running /opt/firefox/firefox I get the message : GLib-WARNING **: g_set_prgname() called multiple times and the process instantly dies.

/opt/firefox/firefox -ProfileManager starts the Profile Manager.  As soon as I click on an existing profile, Firefox dies.

I created a new profile copying my passwords and bookmarks from the old profile.  It dies on me as soon as I try to enter it.  I created a new blank profile.  It dies on me.

I can start Firefox with my extensions starting with firefox --safe-mode, exiting the browser and starting again.  If my instance closes, I am unable to start it.

I would love any help on getting my Firefox to work correctly.

The plugins I have installed are 
**Default Plugin**

 File:  libnullplugin.soVersion:  1.0.0.15**Adobe Reader 9.3**

 File:  nppdf.so
**VLC Multimedia Plugin (compatible Totem 2.28.2)**

 File:  libtotem-cone-plugin.so
**Windows Media Player Plug-in 10 (compatible; Totem)**

 File:  libtotem-gmp-plugin.so
**QuickTime Plug-in 7.2.0**

 File:  libtotem-narrowspace-plugin.so
**Shockwave Flash**

 File:  libflashplayer.soVersion:   Shockwave Flash 10.0 r45
**Java(TM) Plug-in 1.6.0_19**

 File:  libnpjp2.so

---

### Post by nanotube on 2010-04-22
Hi
some questions:

What version of ubuntu?

Which method did you use to install firefox 3.6.3?

Try running it in safe mode ("firefox -safe-mode"), and disabling your plugins one by one, then quitting and starting back in normal mode, to see if some particular plugin is at fault?

---

### Post by andreseso on 2010-04-22
Hello,

I am using ubuntu 9.10.  I have installed this from the apt repositories as described in the sticky post on this forum.

The profile manager starts without problem.  Firefox in safe mode starts without any problem.  When I exit safe mode and start Firefox again, it starts without any problem.  The problem is that it soundlessly dies the next time I run it.

I have disabled the three Totem plugins I had installed to see if that is the problem.

Thanks,
Andres

---

### Post by nanotube on 2010-04-23
well let me know what you find after disabling the various plugins...

---

### Post by andreseso on 2010-04-23
> **nanotube said:**
> well let me know what you find after disabling the various plugins...
I disabled the media playback plugins.  I still have Flash and Java enabled.  I am still getting the same behaviour.

When I restart after entering safe mode, Firefox starts normally.  When I start Firefox after that, Firefox exits with error code 1 instantly.  

I am stumped.

Love, 
Andres

---

### Post by nanotube on 2010-04-23
Hi

well see if disabling flash or java helps, just by way of zeroing in on the problem... i also see you have adobe reader plugin in there - try that one too.

did you do anything before this started happening? like install an add-on or a new plugin? or did it just start happening "by itself" ?

---

### Post by andreseso on 2010-04-24
> **nanotube said:**
> Hi

did you do anything before this started happening? like install an add-on or a new plugin? or did it just start happening "by itself" ?

Hello nanotube,

I disabled all plugins including the default plugin.  Same behavior.  I have to enter safe mode and restart to get a normal Firefox session.

Before installing Ubuntuzilla Firefox I had Namoroka (Firefox 3.6) from the PPA installed.  I switched to Ubuntuzilla as it started crashing with Flash pages.  I disabled the PPA repository, uninstalled everything related to Firefox and installed the Ubuntuzilla Firefox.

Love,
Andres

---

### Post by nanotube on 2010-04-26
hi,

and what if you create a fresh, new, blank profile - does the behavior persist? (avoid copying any files from the old profile, just try it with a completely shiny new profile) ?

---

### Post by andreseso on 2010-04-27
> **nanotube said:**
> hi,

  just try it with a completely shiny new profile) ?

Nanotube,  I get exactly the same behaviour with a shiny new profile.

Safemode and restart, Firefox works.  Restart again, it instantly crashes.

---

### Post by nanotube on 2010-04-27
hmm, very weird... 

well, let's try the sledgehammer approach.

first, make sure you have a backup of your entire firefox profile, for "just in case". 

========
SLEDGEHAMMER ATTEMPT #1:

quit firefox completely, then run:
```
mv ~/.mozilla ~/.mozilla$( date -Iseconds )
```
This will move your whole profile dir out of the way into a backup location.

Start firefox again, see if the crashing behavior persists.

=========
SLEDGEHAMMER ATTEMPT #2:

If the above doesn't solve it, try this:

remove firefox, make sure there's nothing is /opt/firefox, then reinstall:

```
sudo apt-get remove --purge firefox-mozilla-build
sudo rm -rf /opt/firefox
sudo apt-get install firefox-mozilla-build
```

From here, follow SLEDGEHAMMER ATTEMPT #1 again, to make sure we have no leftover profile data.

Now, start firefox and see if behavior persists.

=======

Let me know how it goes....

---

### Post by andreseso on 2010-04-28
Hello nanotube,

Exactly the same behavior.  I did both Sledgehammer approaches.  Purging the Mozilla build of Firefox and renaming the profile directory did not help.

Still the same behavior of having to start Firefox in safe mode and then restart to get a normal session.  It still dies restarting again.

Love

---

### Post by nanotube on 2010-05-02
Hi,

Well, sorry to say, but I'm stumped on this one.

Since the problem is reproducible with stock mozilla firefox with nothing in the profile, maybe you'll have some luck if you ask on the mozilla forums. Since ubuntuzilla is nothing more than the official mozilla binaries wrapped into a .deb, they may be able to steer you in the right direction...

---

### Post by lisati on 2010-06-02
Watching with interest: it has started doing it with me too.....

---

