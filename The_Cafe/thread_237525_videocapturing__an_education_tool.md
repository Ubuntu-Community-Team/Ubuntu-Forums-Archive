---
title: "videocapturing : an education tool"
date: 2006-08-16
forum: The Cafe
---

### Post by newbie2 on 2006-08-16
Open source videos capture a new way to do tech support
> Visitors to captorials.com who have questions can request videos, or view the ones already posted at the site, such as "how to change your desktop background," or "copy a file to your USB storage device." My favorite video was "how to install libinstrudeo on Ubuntu," which even showed the same "gcc compiler missing" error that I got the first time I tried to configure the library. The video showed me what packages I needed to install before I could fully configure and compile the code (there were quite a few), saving me at least an hour of Googling.
[http://business.newsforge.com/article.pl?sid=06/07/20/1918210&tid=35&tid=138&tid=132](http://business.newsforge.com/article.pl?sid=06/07/20/1918210&tid=35&tid=138&tid=132)
:cool:

---

### Post by digTro on 2006-08-16
The required package "libinstrudeo" is not available in the repos. I'm trying to install it manually. So far I've typed ./configure a 10 times. Everytime it says some package is missing and I have to search for it in Synaptic, install it, run configure again and so on. Is there an easy way to do an install?

---

### Post by croak77 on 2006-08-16
Did you read the article? It tells you how to install libinstrudeo on Ubuntu. It links to this page;

[http://captorials.com/index.php?cmd=showRecording&rec=6](http://captorials.com/index.php?cmd=showRecording&rec=6)

Or if you go to the Screenkast page they have ubuntu packages.

[http://instrudeo.bpower2.com/packages/ubuntu-dapper/](http://instrudeo.bpower2.com/packages/ubuntu-dapper/)

If you want a GNOME tool install Byzanz. It's in the repo's.

---

### Post by dvarsam on 2006-08-16
Hello!

Even though I have installed the packages, there is no shortcut created for the program to run from the Menu...

How do I run the program?


Thanks.

P.S.> The same is happening, in the case that I install "byzanz"...

---

### Post by %hMa@?b&lt;C on 2006-08-16
for byzanz, you have to run
"byzanz-record finename.gif"
in the terminal

---

### Post by digTro on 2006-08-17
> **croak77 said:**
> Did you read the article? It tells you how to install libinstrudeo on Ubuntu. It links to this page;

[http://captorials.com/index.php?cmd=showRecording&rec=6](http://captorials.com/index.php?cmd=showRecording&rec=6)


Yes. I saw the video. On my slow internet connection, it was taking ages to load. So I figured, what the hell, I'll try it myself.

> Or if you go to the Screenkast page they have ubuntu packages.

[http://instrudeo.bpower2.com/packages/ubuntu-dapper/](http://instrudeo.bpower2.com/packages/ubuntu-dapper/)

If you want a GNOME tool install Byzanz. It's in the repo's.

That information, I overlooked. Thanks for pointing it out.

---

### Post by dvarsam on 2006-08-17
Still, the question remains:

Even though I have installed the packages, there is no shortcut created for the program "Screenkast" to run from the Menu...

How do I run the program?

------------------------------------------

Dear "jeffc313",

thanks for your reply!

> **jeffc313 said:**
> For byzanz, you have to run:
"byzanz-record finename.gif"

In the Terminal.

I have tried using what you suggested:

byzanz-record test.gif

However, the file created - e.g. test.gif - is _not_ a video file, but just a picture!!!

We were talking about a Screen Video Recording Program, not just a still picture/snapshot of my Desktop...

Besides, why would one go ahead and install "byzanz", for snapshots, while he could use the Ubuntu's (embedded program) - from Menu, select: Applications\Accesories\Take Screenshot ?

Thanks.

---

### Post by Polygon on 2006-08-18
it takes video.... i just tried it. but instead of outputting a video file it outputs an animated GIF. once you do "byzanz-record test.gif" by defualt it will start recording for 60 seconds, so move your mouse and try opening some random windows and it will record that

here is a image that i recorded with byzanz:

[http://email.noao.edu/~markgrandi/test.gif](http://email.noao.edu/~markgrandi/test.gif)

if you do "byzanz-record --help" you see the options so you can make the video be longer/have your cursor in it/etc.

the only problem is, if i set it to like to record for a minute, my ram and swap shoot up to 100%, and my computer completly locks up, and on restart the same thing happens unless i delete the gif that byzanz created... strange

---

### Post by fana2 on 2006-12-30
> **croak77 said:**
> 
Or if you go to the Screenkast page they have ubuntu packages.

[http://instrudeo.bpower2.com/packages/ubuntu-dapper/](http://instrudeo.bpower2.com/packages/ubuntu-dapper/)

They are gone. Does anybody have them still on his harddisk ?

---

