---
title: "Ubuntu Server, hardware question"
date: 2010-06-20
forum: The Cafe
---

### Post by GreenDance on 2010-06-20
Hi, would ubuntu server run happly on a 800mhz cpu?

---

### Post by Bachstelze on 2010-06-20
> **GreenDance said:**
> Hi, would ubuntu server run happly on a 800mhz cpu?

Yes. On a 100MHz one, too.

---

### Post by The Real Dave on 2010-06-20
> **GreenDance said:**
> Hi, would ubuntu server run happly on a 800mhz cpu?

That depends. It'll install and boot on it, but what do you want it to do? Different wants have different power requirements.

---

### Post by GreenDance on 2010-06-20
> **The Real Dave said:**
> That depends. It'll install and boot on it, but what do you want it to do? Different wants have different power requirements.

would like it to run a lamp + torrent :)

---

### Post by GreenDance on 2010-06-20
> **GreenDance said:**
> would like it to run a lamp + torrent :)

forgot to mention, SSH as well, will that be ok?

---

### Post by Bachstelze on 2010-06-20
> **GreenDance said:**
> forgot to mention, SSH as well, will that be ok?

Probably, as long as your LAMP does not serve one million visitors per day. ;)

---

### Post by zuerston on 2010-06-20
> **Bachstelze said:**
> Probably, as long as your LAMP does not serve one million visitors per day. ;)

OK I was wondering about the same thing, Running a hypothetical website at home,assuming no ISP bandwidth problems, How many hits/pages/visitors could said server running say,on a P4 2.8gb HT, 1.5gb, handle daily? CPU maybe at 90% load.
What kind of server load will the above computer take?
:popcorn:
This thread is monitored on my website page 
[http://www.zuerst1.com/index.php/this-weeks-videos/](http://www.zuerst1.com/index.php/this-weeks-videos/)

---

### Post by Bachstelze on 2010-06-20
> **zuerston said:**
> OK I was wondering about the same thing, Running a hypothetical website at home,assuming no ISP bandwidth problems, How many hits/pages/visitors could said server running say,on a P4 2.8gb HT, 1.5gb, handle daily? CPU maybe at 90% load.
What kind of server load will the above computer take?
:popcorn:
This thread is monitored on my website page 
[http://www.zuerst1.com/index.php/this-weeks-videos/](http://www.zuerst1.com/index.php/this-weeks-videos/)

The load is relative to the server power. A good rule of thumb is that if the load always stays below 100%, the server will stay responsive. So assuming n visitors per minute put your server load at 90%, then you should be able to serve n*60*24 visitors per day assuming the visitor flow is roughly constant (with some room for small bursts).

---

### Post by juancarlospaco on 2010-06-20
Ubuntu yes.
*The Apps/Services depends.*

---

### Post by kevin11951 on 2010-06-20
Personally, I would run Debian Stable (Lenny) on that, or maybe Ubuntu 8.04.  Ubuntu 10.04 still has a few issues with PHP (depreciated syntax still used in different packages, php5-imap for one.)

---

### Post by lisati on 2010-06-20
The idea might work. I have an older machine with 64Mb RAM, a 3Gb HDD, and which runs at 133MHz. On the rare occasions I've had it running while my main server machine has been down, it has seemed to cope with the modest traffic on my website, if a bit slower than I'd like. Then again, I don't have it configured to cope with incoming email - that's on the "to do list" and what I am thinking of doing there is probably better suited to a thread of its own.

---

### Post by GreenDance on 2010-06-21
this is a little off-topic, sorry, but I was just browsing this website [http://www.mini-itx.com/store/?c=38](http://www.mini-itx.com/store/?c=38) and it says that 800mhz would video capture at mpeg2 fine, I'm supprised on a 800mhz cpu.

---

### Post by ukripper on 2010-06-21
I am running Ubuntu server 9.10 - Apache + zoneminder(connected 2 cameras at 5 FPS stream with motion capture) + Dropbox daemon( to upload capture images to dropbox service so that i can download on my Android phone) + Samba file server + ssh + FTP server all on Asus Eeepc netbook underclocked to 575 Mhz, 512 RAM, running without any problem. So IMHO your server is more than enough for LAMP. You got to worry more about limitation of your bandwidth provided by your internet connection.

---

### Post by wojox on 2010-06-21
The link in my signature is an old Dell Optiplex EX. You should be able to get away with those specs.

---

### Post by GreenDance on 2010-06-21
> **ukripper said:**
> I am running Ubuntu server 9.10 - Apache + zoneminder(connected 2 cameras at 5 FPS stream with motion capture) + Dropbox daemon( to upload capture images to dropbox service so that i can download on my Android phone) + Samba file server + ssh + FTP server all on Asus Eeepc netbook underclocked to 575 Mhz, 512 RAM, running without any problem. So IMHO your server is more than enough for LAMP. You got to worry more about limitation of your bandwidth provided by your internet connection.

:D Fantastic!, Thanks for that info. No problems from my ISP, unlimited upload cap :D.

---

### Post by Johnsie on 2010-06-21
Just a little slow to install but once it's all up and running it should be ok. Delivering webpages actually takes very little processing power unless you're using very complex php scripts or have a very, very popular site. The best way to find out is to actually do it :-)

---

### Post by GreenDance on 2010-06-21
I Love Ubuntu! :D.

It's a privilage to be a member on this forum! :D.

Thanks to all who replied.

---

### Post by GreenDance on 2010-06-22
I inserted the Ubuntu Server 9.10 CD into my "Server", the CD loads up to the first menu on screen, but when pressing Enter to Install, a few seconds later the screen is scrambled, I see the colors blue and red, text isn't readable, so I tried the Ubuntu Alternative 9.10 CD and Debian 504 CD, it's the same, can anyone help please.

Thank You So Much! :)

---

### Post by kevin11951 on 2010-06-22
> **GreenDance said:**
> I inserted the Ubuntu Server 9.10 CD into my "Server", the CD loads up to the first menu on screen, but when pressing Enter to Install, a few seconds later the screen is scrambled, I see the colors blue and red, text isn't readable, so I tried the Ubuntu Alternative 9.10 CD and Debian 504 CD, it's the same, can anyone help please.

Thank You So Much! :)

Would you mind taking a picture?

also, if you know how, add "vga=normal" at the boot screen on the debian cd.

---

### Post by CharlesA on 2010-06-22
Sounds like it doesn't like the video card. I had that happen when I tried to boot off a regular desktop livecd on an ancient IBM server, couldn't read anything, since it was all jacked up.

---

### Post by samalex on 2010-06-22
> **GreenDance said:**
> Hi, would ubuntu server run happly on a 800mhz cpu?

Yeppers, and quiet well too.  I haven't read all the replies, but I assume others are saying the same thing.  My home server is 600Mhz IIRC and it works great for web sites, SSH, IRC, the works.  It's running Ubuntu Server 8.10, but I just downloaded 10.04 Server and will install it whenever Time Warner gets my Internet going again (it went out last night).  

Just get as much ram as possible, and if you run Ubuntu Server with no GUI it'll take about anything you can throw at it.  Just don't let a site hosted on it get on Digg or /. :)

Sam

---

### Post by GreenDance on 2010-06-23
Hi, I tried vga=normal and the same thing happened :( (Debian), I tried WXP (sorry!) and that installed fine, but I want linux not windows.

---

### Post by GreenDance on 2010-06-23
> **GreenDance said:**
> Hi, I tried vga=normal and the same thing happened :( (Debian), I tried WXP (sorry!) and that installed fine, but I want linux not windows.

I've just noticed I've started a second topic inside this one, sorry.

---

### Post by GreenDance on 2010-06-24
> **GreenDance said:**
> Hi, I tried vga=normal and the same thing happened :( (Debian), I tried WXP (sorry!) and that installed fine, but I want linux not windows.

Bump, Thank You!

---

