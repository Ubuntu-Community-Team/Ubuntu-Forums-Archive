---
title: "44 security holes"
date: 2004-12-16
forum: The Cafe
---

### Post by p!=f on 2004-12-16
Source:
Posted by Robert Penz, Adamantix User Mailing List.
[http://lists.adamantix.org/users-l/archive/2004/2004-12/1103190732810](http://lists.adamantix.org/users-l/archive/2004/2004-12/1103190732810)

Direct Link:
[http://tigger.uic.edu/~jlongs2/holes/](http://tigger.uic.edu/~jlongs2/holes/)

I don't use most of the programs listed there, however, imagine how many security holes could be in applications we use every day.

To be safe I should unplug my network cable at once...

---

### Post by jdong on 2004-12-16
Well, it is quite disturbing to see some of the stuff listed,

However, I don't think most of them can be serously exploited. i.e. you don't run a public CUPS server , or a shell server, on systems with sensitive, important data!

---

### Post by CowPie on 2004-12-16
Hi jdong,
From [email]djb@cr.yp.to[/email] Wed Dec 15 14:21:17 2004
Date: 15 Dec 2004 08:18:11 -0000
From: D. J. Bernstein <djb@cr.yp.to>
To: [email]securesoftware@list.cr.yp.to[/email], [email]mplayer-users@mplayerhq.hu[/email]
Subject: [remote] [control] MPlayer 1.0pre5 get_header overflows data buffer

Ariel Berkman, a student in my Fall 2004 UNIX Security Holes course, has
discovered a remotely exploitable security hole in MPlayer. I'm
publishing this notice, but all the discovery credits should be assigned
to Berkman.

You are at risk if you use MPlayer to play an ASF video stream from the
web (or from any other source that could be controlled by an attacker).
Whoever provides that stream then has complete control over your
account: he can read and modify your files, watch the programs you're
running, etc.

Proof of concept: On an x86 computer running FreeBSD 4.10 with ucspi-tcp
installed, type

   wget [http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2)
   bunzip2 < MPlayer-1.0pre5.tar.bz2 | tar -xf -
   cd MPlayer-1.0pre5
   ./configure
   gmake

to download and compile the MPlayer program, version 1.0pre5 (current).
Then save the file 17-s.c attached to this message, and type

   gcc -o 17-s 17-s.c
   tcpserver 0 1755 ./17-s &
   ./mplayer mmst://127.0.0.1/new_video.asf

with the unauthorized result that a file named x is removed from the
current directory. (I tested this with a 538-byte environment, as
reported by printenv | wc -c.)

Here's the bug: In asf_mmst_streaming.c, get_header() uses get_data()
to copy an input-specified amount of data into a 102400-byte data[]
array.

---D. J. Bernstein, Associate Professor, Department of Mathematics,
Statistics, and Computer Science, University of Illinois at Chicago

    [ Part 2, Text/PLAIN  103 lines. ]
    [ Unable to print this part. ]

Yes this is serus, I use mplayer daily!  of course I'm sure this will affect movies played stremaing through Firefox/mplayer.

---

### Post by jdong on 2004-12-16
I did say 'most'. :D

---

### Post by Lovechild on 2004-12-16
I think this is great, free code review for security. I'm surprised they didn't find more.

---

