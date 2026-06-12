---
title: "packages.ubuntu.com is down and no-one can connect to it"
date: 2008-06-29
forum: The Cafe
---

### Post by nowshining on 2008-06-29
repeat - it's down, if this was in the news - and u knew about it - please let me know please and ty.

edit: now it's waiting but then doesn't proceed after that right now..

---

### Post by NovaAesa on 2008-06-29
If that's where you install stuff from then it's working for me. If it's something else, n/m.

Nevermind, I thought you meant [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com)

---

### Post by fluteflute on 2008-06-29
It happens quite often - I don't know why - but its certainly rather fustrating.

---

### Post by bobbocanfly on 2008-06-29
> **fluteflute said:**
> It happens quite often - I don't know why - but its certainly rather fustrating.

Theres been a lot fo discussion about this on ubuntu-devel mailing list (I think, might have been -motu). They are having some trouble trying to get people to host it, so there are large outages when the owner runs out of bandwidth or something. Very annoying as it is an incredibly useful resource.

---

### Post by fluteflute on 2008-06-30
Can Canonical not host it, like they host everything else?

Edit: I've found [this message]("https://lists.ubuntu.com/archives/ubuntu-devel/2008-April/025333.html") although no replies.

2nd edit: I've found the [rest of the discussion]("https://lists.ubuntu.com/archives/ubuntu-devel/2008-May/025370.html") which [concludes by saying that Canonical can host it]("https://lists.ubuntu.com/archives/ubuntu-devel/2008-May/025445.html"). There is [evidence that this did happen]("http://blog.djpig.de/2008/06/13"). So why is it still going down regularly?

---

### Post by Happy_Man on 2008-06-30
Well, it's up and running now.

---

### Post by nowshining on 2008-07-01
happy yes it is, but, pidgin.im is not down nor I can connect to it and icq pop-ups a message about upgrading and tells to go pidgin.im, so I guess they changed the way it connects then/again - of course tho icq and aim are both from aol :P but aim works fine. However tho looking at the debug - it shows to go to the icq site and download the new icq client.

---

### Post by lys1123 on 2008-08-02
I can't connect to it right now.  After Firefox tries for what seems like ten minutes I get "The server at packages.ubuntu.com is taking too long to respond." Here is the current trace to packages.ubuntu.com.

 1:  Wireless_Broadband_Router.home (192.168.1.1)           0.672ms 
 2:  71.244.24.1 (71.244.24.1)                             12.872ms asymm  3 
 3:  P1-1.LCR-04.DLLSTX.verizon-gni.net (130.81.48.150)    11.456ms 
 4:  130.81.29.182 (130.81.29.182)                         15.195ms asymm  5 
 5:  0.so-1-2-0.XT4.DFW9.ALTER.NET (152.63.1.165)          17.057ms asymm  6 
 6:  0.so-7-0-0.XL4.DFW13.ALTER.NET (152.63.98.81)         15.501ms asymm  7 
 7:  0.so-7-0-0.BR1.DFW13.ALTER.NET (152.63.98.69)         15.548ms asymm  8 
 8:  204.255.169.26 (204.255.169.26)                       16.829ms asymm  9 
 9:  so-1-2-0.bbr1.Dallas1.Level3.net (209.244.15.161)     15.290ms asymm 10 
10:  ae-1-0.bbr2.London2.Level3.net (212.187.128.45)      125.515ms asymm 16 
11:  ae-16-53.car2.London2.Level3.net (4.68.117.80)       192.794ms asymm 17 
12:  195.50.121.2 (195.50.121.2)                          131.860ms asymm 19 
13:  gw0-0-gr.canonical.com (91.189.88.10)                133.327ms asymm 19 
14:  no reply
15:  no reply
16:  no reply
17:  no reply


So it does look like Canonical is hosting it now... but it is still down.

---

### Post by gsmanners on 2008-08-02
91.189.94.219 is where I see it. Maybe a DNS issue?

---

### Post by master_kernel on 2008-08-02
It's down again.

---

### Post by original_jamingrit on 2008-08-02
I'm unable to connect to it as well.  Trying to download the latest aMSN deb.

---

### Post by blithen on 2008-08-02
Hmm..weird thing is you can ping it.

---

### Post by kostkon on 2008-08-02
> **original_jamingrit said:**
> I'm unable to connect to it as well.  Trying to download the latest aMSN deb.
Why not head to [*getdeb.net*]("http://getdeb.net/") for that?

---

### Post by Joeb454 on 2008-08-02
Or compile it from source? It's not that hard...

---

### Post by gsmanners on 2008-08-02
Or one of the many mirrors. For example:

[http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/)
[http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/)
[http://mirrors.acm.jhu.edu/ubuntu/](http://mirrors.acm.jhu.edu/ubuntu/)
[http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/)

---

### Post by original_jamingrit on 2008-08-02
> **kostkon said:**
> Why not head to [*getdeb.net*]("http://getdeb.net/") for that?

> **Joeb454 said:**
> Or compile it from source? It's not that hard...

> **gsmanners said:**
> Or one of the many mirrors. For example:

doh, thanks folks.  It's for a buddy's computer, and I wanted the deb because I wanted him to be able to manage it through synaptic or apt.

---

### Post by shirsch on 2008-08-03
> **gsmanners said:**
> Or one of the many mirrors. For example:

[http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/)
[http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/)
[http://mirrors.acm.jhu.edu/ubuntu/](http://mirrors.acm.jhu.edu/ubuntu/)
[http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/)

Perhaps I'm missing the obvious, but none of those appear to support the search function used by 'getlibs' (install 32-bit compatibility libs in x86_64 Ubuntu).

---

### Post by fluteflute on 2008-08-03
If you pull up a terminal you can do "aptitude search ****".

---

### Post by hellmet on 2009-08-10
It seems to be down again.

---

### Post by t0p on 2009-08-10
Not from here mate.  (Here being somewhere you aren't.)

---

### Post by Irihapeti on 2009-08-10
Was down briefly from NZ but is now back up again.

---

### Post by Vistaus on 2009-12-06
It's down again since yesterday :(

---

### Post by fluteflute on 2009-12-12
Still down now. :(
It's rather important for the getlibs script, so hoping it comes back online sooner rather than later!

---

### Post by Vistaus on 2009-12-12
> **fluteflute said:**
> Still down now. :(
It's rather important for the getlibs script, so hoping it comes back online sooner rather than later!

It's not down anymore here. I can connect to packages.ubuntu.com again since a few days :)

---

### Post by Physical Hook on 2009-12-12
> **Vistaus said:**
> It's not down anymore here. I can connect to packages.ubuntu.com again since a few days :)

Nah, it's down ( speaking from what I see ).

---

### Post by joneswm on 2009-12-12
It's still down here for me too. 
This seems to be a pretty fundamental thing to be down - a rare Ubuntu disappointment.

---

### Post by NoaHall on 2009-12-12
Have you tried going to System -> Admin -> Software Sources -> Select best server?

---

### Post by fluteflute on 2009-12-12
> **NoaHall said:**
> Have you tried going to System -> Admin -> Software Sources -> Select best server?
That is irrelevant. 

packages.ubuntu.com is a completely different service to archive.ubuntu.com

---

### Post by hsmak_linux on 2009-12-12
> **fluteflute said:**
> Still down now. :(
It's rather important for the getlibs script, so hoping it comes back online sooner rather than later!

Even me that I'm in need to this packages website just to get "getlibs" script working.

I'm wondering why they don't have a back-up server???

---

### Post by hsmak_linux on 2009-12-12
At last [packages.ubuntu.org]("http://packages.ubuntu.com/") is up!

Hurry up before it gets down :D

---

### Post by fluteflute on 2009-12-13
Yay, now I can install the Amazon MP3 whatsit with getlibs :D

---

