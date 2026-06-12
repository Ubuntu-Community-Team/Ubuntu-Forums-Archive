---
title: "What is the most ingenious *nix cli program"
date: 2009-03-24
forum: The Cafe
---

### Post by rolandrock on 2009-03-24
Dear All,

I start this thread with the intention of advertising what I think is the greatest cli program in the world of *nix and in the hope of learning about other programs that have passed me by.

THE greatest most ingenious cli program is... screen.

When a friend of mine introduced me to screen a few years ago, i thought 'Eh? So what?' but gradually I found more and more uses for it both at work and play and now it is indispensable.

So, what is screen?  Well here is the definition on the GNU website:
'Screen is a full-screen window manager that multiplexes a physical terminal between several processes, typically interactive shells.'

What??  It is quite an esoteric program so perhaps some examples are in order.  Say you are at work running a program on a remote machine that will take 14 hours to run.  You must ensure that the program continues to run when you shutdown your computer and go home.  There are various ways to do this but screen is so elegant.  Log into the machine, fire up screen, start the program, detach the screen session -  now the screen session is handling the program as though you were logged in and at any point you (or anyone else in the world with access to that account) can log back into the machine and re-attach the screen session.

You can have many screens running on one ssh session on a remote machine so you can easily switch between (or split screen so you can monitor them concurrently) your root session, an SQL session, vim session, whatever... without having lots of windows cluttering your monitor.

If you have an unreliable connection to a remote server that keeps dropping and making a mess of your work, run screen on it.  Whenever the connection drops you can reattach the session and continue from where you left off.

In education, you can share your screen session among several pupils who can follow exactly what you are doing from anywhere in the world.

At home, I run vlc (with ncurses interface) on a screen session on my main computer so I can attach it and control it from any computer in the house.  Very useful for lazy people who want to start/stop/queue music/videos from the comfort of their armchair.

I also have a downloader program running in another screen that reads a fifo and wgets files for me.  I use ssh to dump file names into the fifo from my laptop.  This reduces the load on the wireless network, reduces the hits on my eeepc's SSD and means I don't have to worry about having files held on different computers around the house.

There are myriad uses for it.  It is sturdy, stable and elegant.  In short, it epitomises the whole *nix ethos.  I am almost getting a tear in my eye writing this I love it so much.

So then.  Beat that.  I will be very impressed (and a little bit sad) if someone can come up with anything as beautiful and versatile as GNU screen.

Links:
[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)
[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

Rock

---

### Post by Neo_The_User on 2009-03-24
PowerTerm® InterConnect Linux Edition hands down

[http://www.ericom.com/pti4linux.asp](http://www.ericom.com/pti4linux.asp) for info

XD

---

### Post by rolandrock on 2009-03-24
Nice.  Looks like a very versatile emulator.  Downside is it costs money for full version.  I've always been a fan of PuTTY but I don't think it supports that array of hosts.

Thanks for the contribution.

---

### Post by Dr Small on 2009-03-24
Nothing beats Vim

---

### Post by conundrumx on 2009-03-24
The answer is bash.  :)

---

### Post by rolandrock on 2009-03-24
In the old world I could never understand why people used anything other than korn shell and bash is an improvement.  A truly great shell.

Vim is definitely a hugely powerful weapon in the *nix arsenal and also supports split-screening like screen (have you ever heard anyone say that they love emacs?).  Well spoken for.

Thanks both.

---

### Post by smbm on 2009-03-24
I'm quite partial to NCMPC and more recently NCMPCPP.

If you're after an MPD client you could do worse.

---

### Post by SunnyRabbiera on 2009-03-24
apt-get :D

---

### Post by chris200x9 on 2009-03-24
> **rolandrock said:**
> In the old world I could never understand why people used anything other than korn shell and bash is an improvement.  A truly great shell.

Vim is definitely a hugely powerful weapon in the *nix arsenal and also supports split-screening like screen (have you ever heard anyone say that they love emacs?).  Well spoken for.

Thanks both.

I love emacs!

---

### Post by artir on 2009-03-24
vrms FTW!

---

### Post by Neo_The_User on 2009-03-24
aptitude, itself, is pretty good too. very pretty as a cli program. vlc-nox is good too. nano is nice and simple.

Top Three:

PowerTerm® InterConnect Linux Edition
make
aptitude

---

### Post by kk0sse54 on 2009-03-24
I totally agree about screen, it's a fantastic program

---

### Post by klange on 2009-03-24
Most *ingenious* CLI program?

Are you people nuts? It's [pizza_party](http://www.beigerecords.com/cory/Things_I_Made/PizzaParty), hands down.

---

### Post by sujoy on 2009-03-24
i'd say, 

htop
mutt
mplayer

---

### Post by DeadSuperHero on 2009-03-24
I did a 30-day-hiatus of any sort of X session last year during the summer, so here are the cli apps that I really enjoyed.
 
-Screen. Although not quite for the same reason as the OP. I found screen was excellent for managing multiple tasks on my OWN computer WHILE I was at home. It's fantastic for running multiple CLI apps and switching between each one.
 
-elinks: I really liked this one, it's a neat little text-based web browser.
 
-Finch: a CLI version of Pidgin, bascially. It uses libpurple, so if you're a regular Pidgin user, your accounts are already set up.
 
-irrsi: Great chat client, there are also scripts out there to extend it for things like Twitter.
 
-cplay: I used this to navigate my music folders and jam to some FLAC files.
 
-nano: Others will prefer editors like VIM or EMACS, but nano is really dead simple. It's basically just a text editor. Was useful for keeping self-reminders of controls and things.
 
-cmake: Although I really had no use for it then, the cmake build system is probably the best I've used. Simple, elegant, and very to-the-point. I love it.

---

### Post by MaxIBoy on 2009-03-24
```
bb
```

Try it, it's in the repos.

---

### Post by mcduck on 2009-03-24
I've always liked "false".

It does nothing, and fails. And does it both fast and secure.

The person behind this kind of a program must be absolutely genius. :D

(Seriously, apt-get and Imagemagick.)

---

### Post by Dr Small on 2009-03-24
> **Mr. Psychopath said:**
> -cplay: I used this to navigate my music folders and jam to some FLAC files.

You ought to check out MOC. I was addicted to cplay until I found MOC ;)
 
> **Mr. Psychopath said:**
> -nano: Others will prefer editors like VIM or EMACS, but nano is really dead simple. It's basically just a text editor. Was useful for keeping self-reminders of controls and things.

That's the problem with nano; it's dead simple. I've got to have something that can copy, paste, navigate around, add things to buffer, jump to line numbers, etc, etc, while programming.

---

### Post by Dougie187 on 2009-03-24
Top 3:
man
cd
vim

---

### Post by klange on 2009-03-24
> **Dr Small said:**
> You ought to check out MOC. I was addicted to cplay until I found MOC ;)
 

That's the problem with nano; it's dead simple. I've got to have something that can copy, paste, navigate around, add things to buffer, jump to line numbers, etc, etc, while programming.

Nano does those things... You haven't used it to its fullest until you've used the marker to copy and paste. (Pico did not have go-to-line, Nano added it, as well search-and-replace and a bunch of other stuff we take for granted in other editors these days).

---

### Post by cardinals_fan on 2009-03-24
Screen is a pretty awesome app.  Vim is a superb editor.  Ncmpc is a nice music player.  Greed is a fun game.  Elinks is a good CLI browser.  MC is the best file manager.  In short, there are many :)

---

### Post by t0p on 2009-03-24
**wget** FTW - I'm gonna **wget -r** the whole internet moo-hah-hah!

Also, I find **ddate** indispensible

:p

---

### Post by sertse on 2009-03-24
screen is great, but it takes some..mastery. 

dvtm is more pick up and go, if all you want is multiple apps on one console.

Ofc screen can do more than dvtm though.

---

### Post by Mehall on 2009-03-24
> **t0p said:**
> **wget** FTW - I'm gonna **wget -r** the whole internet moo-hah-hah!

You have no idea how tempting it is :P

---

### Post by spupy on 2009-03-24
> **mcduck said:**
> I've always liked "false".

It does nothing, and fails. And does it both fast and secure.

The person behind this kind of a program must be absolutely genius. :D

Oh, haha, look at the man page:


```
SYNOPSIS
       false [ignored command line arguments]
```

:)

---

### Post by cardinals_fan on 2009-03-24
Doneyet is great too.

---

### Post by Neo_The_User on 2009-03-24
> **MaxIBoy said:**
> ```
bb
```

Try it, it's in the repos.

Is this a dangerous command?? because I know how to use dd to remove all corrupted data off my hard drive by settings each block of data to 0.

---

### Post by yabbadabbadont on 2009-03-24
Busybox.  The most useful tool for rescuing a borked system.

---

### Post by MaxIBoy on 2009-03-24
> **Neo_The_User said:**
> Is this a dangerous command?? because I know how to use dd to remove all corrupted data off my hard drive by settings each block of data to 0.Just install it and read the manpage.

---

