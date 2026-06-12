---
title: "Super Cow Powers?"
date: 2007-01-23
forum: The Cafe
---

### Post by Big_Croc7 on 2007-01-23
Ok, what's with the last line...???

> 
$ apt-get
apt 0.6.45ubuntu14 for linux i386 compiled on Sep 27 2006 23:43:26
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(eight)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(eight), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       **This APT has Super Cow Powers.**


---

### Post by 23meg on 2007-01-23
Try and see if you don't believe: ```
apt-get moo
```

---

### Post by Big_Croc7 on 2007-01-23
lol!! looks like someone was very bored!

that settles it... ubuntu _has_ to be the best distro 8)

---

### Post by Brunellus on 2007-01-23
> **Big_Croc7 said:**
> lol!! looks like someone was very bored!

that settles it... ubuntu _has_ to be the best distro 8)
that was Debian.  credit where credit is due (even though there's no such provision in the GPL).

---

### Post by total wormage on 2007-01-23
darn, i thought this was only possible with aptitude
it was one of the reasons i disliked aptitude

still dislike it though ;]

---

### Post by Maxwell7 on 2007-01-23
Oh no ! :D 

That is so funny. I remember the first time I something like that .. i was _very_ new to linux and i loved it . 


this was it : 
```

ubuntu@ubuntu:~$aptitude kate
...
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
```

---

### Post by hiippari on 2007-01-23
aptitude -v moo
aptitude -v -v moo
:p

---

### Post by wesley_of_course on 2007-01-23
wesley@Ratdog:~$ aptitude -v -v -v moo
Stop it!
wesley@Ratdog:~$ 

:rolleyes:

---

### Post by MkfIbK7a on 2007-01-23
do 

aptitude moo -v
aptitude moo -vv
aptitude moo -vvv
aptitude moo -vvvv
aptitude moo -vvvvv
aptitude moo -vvvvvv
aptitude moo -vvvvvvv
aptitude moo -vvvvvvvv

i think thats all...:D

---

### Post by MkfIbK7a on 2007-01-23
acctually this is much easier

```
 aptitude moo && aptitude moo -v && aptitude moo -vv && aptitude moo -vvv && aptitude moo -vvvv && aptitude moo -vvvvv && aptitude moo -vvvvvv
```

copy and paste that:D

---

### Post by yabbadabbadont on 2007-01-23
I know that the emerge command on Gentoo has the same thing, and portage was based on BSD's ports system.  So I would guess this has been around as long as BSD.

---

### Post by phoqueyoo on 2007-01-23
Haha. Did anyone else get the little prince reference?

---

### Post by neoflight on 2007-01-23
more weired is :

try these:

1. sudo apt-get autoremove
2. sudo aptitude autoremove (no super cow power here...:D )

eeeeeeee.

---

### Post by MkfIbK7a on 2007-01-24
> **phoqueyoo said:**
> Haha. Did anyone else get the little prince reference?

yeah a snake eating a elephant:wink:

---

### Post by MrHorus on 2007-01-24
```
apt-get install cowsay
```

cowsay, that most essential of utilities...

---

### Post by rolando2424 on 2007-01-24
> **MrHorus said:**
> ```
apt-get install cowsay
```

cowsay, that most essential of utilities...

It's the only thing you have to have installed in you pc :D

---

### Post by Aetherius on 2007-01-24
I'm in work so what I'm about to post is purely speculation....but if someone could test it for I'd be grateful.

install cowsay

> sudo apt-get install cowsay

and then copy and paste this

> sudo apt-get moo > temp.dat && cowsay grep ' (|/|~' temp.dat


probably won't work, but let me know 


also thought i'd show that some[COLOR="DarkOrange"][SIZE="5"] **cows** have **super apt powers**[/SIZE][/COLOR]

[IMG]https://gallery.debconf.org/albums/wborgert/cow_001.sized.jpg[/IMG]

Aeth

---

### Post by moefh on 2008-05-05
> **Aetherius said:**
> (...)
and then copy and paste this
(...)


That doesn't seem to work, but what you probably intended to do:

```
apt-get moo | cowsay -n
```

This is also funny:

```
apt-get moo | cowsay -n | cowsay -f apt -n
```

PS: I know, replying to a year-old message... But I'm new to Ubuntu (just installed 8.04), saw the message in "apt-get -h" and found this page... I just though I'd share... :-)

---

### Post by graysky on 2008-11-29
[img]http://img511.imageshack.us/img511/2663/aptitudemoors1.png[/img]

---

### Post by koenn on 2008-11-29
> **moefh said:**
> That doesn't seem to work, but what you probably intended to do:

```
apt-get moo | cowsay -n
```

This is also funny:

```
apt-get moo | cowsay -n | cowsay -f apt -n
```

PS: I know, replying to a year-old message... But I'm new to Ubuntu (just installed 8.04), saw the message in "apt-get -h" and found this page... I just though I'd share... :-)

beautiful

---

### Post by lukjad on 2008-11-29
Talk about necromancing. ;)

---

### Post by koenn on 2008-11-29
> **lukjad007 said:**
> Talk about necromancing. ;)
super cow powers and moo never get old

---

### Post by lukjad on 2008-11-29
Moooooooooooooooooooo!
I guess you're right! :D

---

### Post by GemiPiggy on 2009-07-08
I'm a Chinese.
I'm brought to this thread when trying to search the meaning of "Super Cow Powers" in English by google. This phrase looks so much like a Chinese phrase translated litteratim. Cow means powerful in Chinese (while bear means weak).

So are you guys sure that Super Cow Powers has no special means in English?

---

### Post by brian183 on 2009-07-08
> **GemiPiggy said:**
> I'm a Chinese.
I'm brought to this thread when trying to search the meaning of "Super Cow Powers" in English by google. This phrase looks so much like a Chinese phrase translated litteratim. Cow means powerful in Chinese (while bear means weak).

So are you guys sure that Super Cow Powers has no special means in English?

... wow.

I have no opinion on "Super Cow Powers" meaning something more then it seems in english language (which is just a funny phrase). Even so, that last post made my day.

---

