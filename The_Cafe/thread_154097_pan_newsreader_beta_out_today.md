---
title: "pan newsreader beta out today"
date: 2006-04-02
forum: The Cafe
---

### Post by BoyOfDestiny on 2006-04-02
Weird, pan cvs [from last year] crashed (tried to queue a 1000 files when I already had a 1000 files in queue).

Anyway, lo and behold, there is an update on their page after almost 2 years.

[http://pan.rebelbase.com/](http://pan.rebelbase.com/)

Just a heads up for all the binaries fans. ;)

---

### Post by htinn on 2006-04-03
Good news. :D I always hated how much memory old Pan was wasting.

---

### Post by htinn on 2006-04-03
In totally unrelated news, it seems this is also now working (in Wine 0.9.11):

[http://www.utorrent.com/index.php](http://www.utorrent.com/index.php)

---

### Post by ice60 on 2006-04-03
i have a really slow box and the memory useage was too much for me to use the synaptic version - Pan 0.14.2.91 - if that was the synaptic version?? how does the new version compare? is it worth trying? thanks

---

### Post by BoyOfDestiny on 2006-04-04
[QUOTE=ice60]i have a really slow box and the memory useage was too much for me to use the synaptic version - Pan 0.14.2.91 - if that was the synaptic version?? how does the new version compare? is it worth trying? thanks[/QUOTE]

I'm going to try and build it right now. The memory usage is likely going to be greater compared to i386 (I'm on dapper amd64).

EDIT: Thumbs up! It loads headers/articles much much much faster. It's using 36mb of ram. The version in the repos would go up to around 800mb of ram for me. Great interface, feels fast as lightning.

---

### Post by Mr. Electric Wizard on 2006-04-04
This is really good news (no pun intended)!
I have been banging my head against the wall trying to get a "quality" newsreader to work.](*,)

---

### Post by Nordoelum on 2006-04-04
[quote=htinn]In totally unrelated news, it seems this is also now working (in Wine 0.9.11):

[http://www.utorrent.com/index.php]("http://www.utorrent.com/index.php")[/quote]
Why would you list a BT client in a newsgroup software tread? And Azureus is better then uTorrent anyway!

---

### Post by ice60 on 2006-04-04
i can't install it. i firstly unuinstalled the old version then did 
./configure - that looked to be OK, or it looked that way with double vision - i don't normally drink but did tonight - is that a good excuse?, or would it be better to say i have no clue what's going on when i'm sober too?, 
then 
make - there's no make file :D i admit i have been to the pub tonight so maybe i missed somethng somewhere, ill have another go tomorrow, but have i done something wrong :confused: 

i downloaded pan-0.91.tar.bz2. i don't suppose there's a deb ;) thanks

---

### Post by htinn on 2006-04-04
> **ice60]i downloaded pan-0.91.tar.bz2. i don't suppose there's a deb  said:**
> 

The fun part was getting it to configure in the first place. Thank goodness for mailing lists.

[http://lists.gnu.org/archive/html/pan-devel/2006-04/msg00002.html](http://lists.gnu.org/archive/html/pan-devel/2006-04/msg00002.html)

[QUOTE]You'll need to fix some lines in configure.in, since the libpcre in debian does not have .pc files for pkgconfig:

# PKG_CHECK_MODULES(PCRE,  libpcre     >= $PCRE_REQUIRED)
PCRE_CFLAGS=$(pcre-config --cflags)
PCRE_LIBS=$(pcre-config --libs)
AC_SUBST(PCRE_CFLAGS)
AC_SUBST(PCRE_LIBS)


after you added (and fixed the first with a comment) these lines, rerun `autoconf`, and `./configure`.

---

### Post by Rumor on 2006-04-06
Where do I find configure.in so that I can modify it?

---

### Post by Rumor on 2006-04-06
[QUOTE=Rumor]Where do I find configure.in so that I can modify it?[/QUOTE]

/me thumps Rumor in the head with a clue.

Check the pan-0.91 directory, foo!

---

### Post by Rumor on 2006-04-06
Bah, still no go. Here's the output of sudo make:

```

make  all-recursive
make[1]: Entering directory `/home/matthew/pan-0.91'
Making all in po
make[2]: Entering directory `/home/matthew/pan-0.91/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/matthew/pan-0.91/po'
Making all in pan
make[2]: Entering directory `/home/matthew/pan-0.91/pan'
Making all in general
make[3]: Entering directory `/home/matthew/pan-0.91/pan/general'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT file-util.o -MD -MP -MF ".deps/file-util.Tpo" -c -o file-util.o file-util.cc; \
then mv -f ".deps/file-util.Tpo" ".deps/file-util.Po"; else rm -f ".deps/file-util.Tpo"; exit 1; fi
/usr/include/libintl.h:40: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:40: error: expected `)' before ‘const’
/usr/include/libintl.h:40: error: expected initializer before ‘const’
/usr/include/libintl.h:44: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:44: error: expected `)' before ‘const’
/usr/include/libintl.h:44: error: expected initializer before ‘const’
/usr/include/libintl.h:51: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:51: error: expected `)' before ‘const’
/usr/include/libintl.h:51: error: expected initializer before ‘const’
/usr/include/libintl.h:81: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:81: error: expected `)' before ‘const’
/usr/include/libintl.h:81: error: expected initializer before ‘const’
/usr/include/libintl.h:85: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:85: error: expected `)' before ‘const’
/usr/include/libintl.h:85: error: expected initializer before ‘const’
/usr/include/libintl.h:90: error: expected unqualified-id before ‘const’
/usr/include/libintl.h:90: error: expected `)' before ‘const’
/usr/include/libintl.h:90: error: expected initializer before ‘const’
make[3]: *** [file-util.o] Error 1
make[3]: Leaving directory `/home/matthew/pan-0.91/pan/general'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matthew/pan-0.91/pan'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matthew/pan-0.91'
make: *** [all] Error 2

```

Any clues?

---

### Post by htinn on 2006-04-06
Whoa. Hard to imagine your g++ doesn't like libc6-dev.

What version of g++ do you have? I have 4.0.3-1 here.

---

### Post by daveg on 2006-04-07
Looks like somebody has created packages for ubuntu already to save some pain:

[http://pan.rebelbase.com/download/releases/0.91/UBUNTU/](http://pan.rebelbase.com/download/releases/0.91/UBUNTU/)

---

### Post by Rumor on 2006-04-07
[QUOTE=htinn]Whoa. Hard to imagine your g++ doesn't like libc6-dev.

What version of g++ do you have? I have 4.0.3-1 here.[/QUOTE]

Same here.

---

### Post by Rumor on 2006-04-07
[QUOTE=daveg]Looks like somebody has created packages for ubuntu already to save some pain:

[http://pan.rebelbase.com/download/releases/0.91/UBUNTU/](http://pan.rebelbase.com/download/releases/0.91/UBUNTU/)[/QUOTE]

Cool, the .deb package worked :)

---

### Post by DaMasta on 2006-04-07
I gave up on newsreaders awhile ago and now I just use Google Reader. Not as robust but I don't need for it to be.

---

### Post by confused57 on 2006-04-09
I see there is a new beta release of Pan(.92) out today:

[http://pan.rebelbase.com/download/](http://pan.rebelbase.com/download/)

It's a deb file and I was wondering if it would be best to not remove the old pan from the Breezy repositories that I've installed, because of all the dependencies.  I've never dpkg'd a deb file before, but I've heard about "dependency hell".  Thanks for any assistance.

---

### Post by BoyOfDestiny on 2006-04-16
Just built version 0.93 beta, as for the workaround for libpcre, it's in ubuntu as libpcre3 (so make sure you have the -dev), so just change it in configure.in (line 43, libpcre to libpcre3). Then it will build :)

---

### Post by futz on 2006-04-16
I installed 0.93 and tested it out, but it's unuseably buggy still, so I gave up and went back to 0.14.2.91

Still waiting for an Agent clone (or NewsLeecher) for linux...

---

### Post by Meat Plow on 2007-03-23
Is there a part of these Ubuntu forums to discuss specific questions regarding  Pan newsreader?

---

### Post by futz on 2007-03-23
> **Meat Plow said:**
> Is there a part of these Ubuntu forums to discuss specific questions regarding  Pan newsreader?
Not so far as I know, but I'm a heavy user. Maybe I can help?

---

### Post by Meat Plow on 2007-03-23
I'd like to know how to kill filter an author using the <from@from.com> part of the Reply To field. This idiot is using that bogus part of the From field along with a name of a user that I don't want to kill filter. I tried contains <blah@blah.blah> but that doesn't work. Even tried it without the brackets and still no workie.

---

### Post by futz on 2007-03-23
Sorry. Can't help ya. I occasionally plonk someone, but usually just very quickly and don't pay too much attention to the details.

Pan is pretty rough around the edges still. It's possible that it won't even do what you want.

---

### Post by Meat Plow on 2007-03-23
Hey that's cool, I'll figure it out sooner or later.

---

