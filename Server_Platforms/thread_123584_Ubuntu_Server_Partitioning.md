---
title: "Ubuntu Server Partitioning?"
date: 2006-01-30
forum: Server Platforms
---

### Post by jeeproject on 2006-01-30
I am reinstalling Ubuntu server on a new Segate 120GB hard drive and do not want to go with the default partitioning.  I would rather have these locations as seperate partitions...

/ 
/etc
/home
/var
/tmp
Swap

...the problem is that I do not know the optimal sizes to make these partitions for a 120GB hard drive.  Any help would be greatly appreciated.

---

### Post by spade_shark on 2006-01-30
just my $.02  This depends on your servers needs as well.  

125 MB /boot      Primary
2GB      /swap     Logical  (2 X RAM)
10GB    /             Logical  (Min of 8GB for root)
10GB    /home    Logical  (Not needed ie WWW, unless accounts are local ie. docs)
                           For a www server the above  (/home) will not be needed
100GB /var         Logical  (all www, ftp, are here)  any dynamic data
 
optional:
25GB   /tmp        Logical (good place for email to be scanned for virus then moved)
10GB   /opt         Logical (all additional custom programs?) does anyone use?

Just as important as the structure is the format you choose.  For large files stored in the /var (ISO of DVD) maybe use a more robust JFS or XFS system.  

Why do all of this?

Recovery is one reason...just backup / image only partions needed
Rebuild the server?  can format the / and start fresh...leaving all the other partions untouched. ;)

---

### Post by Glut on 2006-01-30
Use LVM, you will need a separate /boot partition but it will solve issues with further expansion. The scheme you have is fine, though some have separate partitions for /usr, /var/log and /var/spool or /var/spool/mail. With LVM you can resize the partitions dynamically so the size that you select now wont be a problem in the future.

I'm not sure of the server's purpose, if it were a www server I'd have a separate www partition. Here's my suggestion:
swap: swap - 4gb
/boot: ext3  - 1gb 
LVM: 115gb
/etc: 2gb
/var: 4gb
/home: 10gb
/tmp: 4gb
/: 8gb (will include /usr where most software is installed)
The rest: LVM space for future expansion.

---

### Post by LordHunter317 on 2006-01-30
[QUOTE=jeeproject]I am reinstalling Ubuntu server on a new Segate 120GB hard drive and do not want to go with the default partitioning.  I would rather have these locations as seperate partitions...[/quote]Based on your scheme given, you sohuld go with teh default, because you have no clue what should and shouldn't be partitioned.

Here's a hint: /etc shouldn't ever be seperated from /.  In fact, I'm not sure your system would even boot with it seperate.

/var should only be seperate on large servers that need it to be.  Even then, /var itself probably shouldn't be seperate, but the necessary subportions of /var.

Seriously, unless you have a good reason, just use a single /.  If you think you may have one, post what you want the server to do.

Almost all the other recommendations made are grossly wrong, but I don't have time to go into them.

---

### Post by jeeproject on 2006-01-31
The server is going to be used for WWW, FTP, TFTP, FILE, EMAIL and possibly in the future as a DHCP server.

---

### Post by LordHunter317 on 2006-01-31
[QUOTE=jeeproject]The server is going to be used for WWW, FTP, TFTP, FILE, EMAIL and possibly in the future as a DHCP server.[/QUOTE]Why all of that in teh same box?  FILE and EMAIL shouldn't be capitalized, either.

TFTP is exceptionally dangerous to run with anything else if you don't know what you're doing.  A dedicated DHCP/boot box would be recommended.

And what specifically is this for?  Virtual hosting?

---

### Post by MJN on 2006-01-31
[quote=LordHunter317]Why all of that in teh same box?  FILE and EMAIL shouldn't be capitalized, either.[/quote] 
FFS Lord Hunter, whilst it may live up to your title do you *really* have to be so pompous all the time?

You clearly know your stuff and have much knowledge to impart on others (I've learnt many things from your posts in the last few days alone), however do you really have to do it with such sheer arrogance?

Everyone is here to learn and whilst you may be far down the path there are others who have only just joined it.... please make allowances for them - you were there once.

Mathew :) (said with good intentions)

---

### Post by nocturn on 2006-01-31
I would seperate / /home /var and /tmp

Why?

If /var fills with log files, it should not clog the root fs (and cause problems), the same goes for /tmp.

Additionally, /home and /tmp can be mounted with  at least nosuid and possibly noexec for security. 

The sizes depend of the purpose of your server.  I make /tmp 1-2 GB and / about 10 GB.  /var may need more space for the mailserver.  To determine the space you need, try to estimate how much mail it will have to hold and if the mails stays on server (Imap) or is downloaded (POP).

---

### Post by LordHunter317 on 2006-01-31
[QUOTE=MJN]You clearly know your stuff and have much knowledge to impart on others (I've learnt many things from your posts in the last few days alone), however do you really have to do it with such sheer arrogance?[/quote]:rolleys: The only arrogance impacted in that post is the arrogance you're creating in your head.

Do you really want me to add several sentences explaining why FILE and EMAIL aren't acronyms and politely ask him not to do it in the future?  It's really just an excessive waste of my time -- he's wrong.  So?  It's not a big deal.  I'm wrong all the time and get proven wrong usually 10 times a day, at least.  Such is the life of a college student.

It's only a big deal if you choose to make it one.  Being corrected doesn't impact arrogance *per se*, even if it's done in a direct fashion.  No where did I say, "You're wrong and *stupid* for saying that" or, "You're wrong and I'm smarter than you."  I just said, "You're wrong."  There's a huge difference, and remember this is a forum.  Assuming emotional feedback you're not seeing is dangerous, though we're all guilty of doing it.

> If /var fills with log files, it should not clog the root fs (and cause problems),Unless you're running applications that could possibly cause unbounded logs, it's generally just not a risk anymore.  It's easy to make / large enough to ensure /var will never, ever be capable of filling it up.

I still stand by my policy of partitioning out the parts of /var that need it.  Realistically, I have to, because I'm frequently putting those parts on different disks or arrays.

> the same goes for /tmp.If you're worried about /tmp filling up your system, then memory mount it via tmpfs (you might want to do this anyway, for performance) unless you know people will be placing huge files there, or you know you'll have enough files in there it'll impact memory peformance.

---

### Post by Cl1mh4224rd on 2006-06-03
[ Argh. No delete? ]

---

