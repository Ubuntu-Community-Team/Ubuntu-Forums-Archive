---
title: "Virtual tty's"
date: 2010-08-14
forum: The Cafe
---

### Post by Austin25 on 2010-08-14
Just wondering: Who else uses them? I just found out about them recently, but how common of knowledge is it?

---

### Post by nrs on 2010-08-14
I didn't know it was possible to use GNU/Linux and not be aware of their existence.

---

### Post by Austin25 on 2010-08-14
Well I use it now to keep my brother of of my desktop that has a live environment. He doesn't know the command line.

---

### Post by Bachstelze on 2010-08-14
> **nrs said:**
> I didn't know it was possible to use GNU/Linux and not be aware of their existence.

It is, but those who do don't call it GNU/Linux.

---

### Post by Austin25 on 2010-08-14
removed, don't want to start a flamewar.

---

### Post by Zorgoth on 2010-08-14
I used to use them.  Then I found out about screen.  Particularly combined with guake, I don't really need them anymore.  Also, they strike me as insecure.  There is no easy way to make it so that a virtual tty will time out if a program like emacs is running inside of it, so if you left your computer on for a day, anyone could switch to that tty and have a user session as you...

---

### Post by Bachstelze on 2010-08-14
> **Zorgoth said:**
> Also, they strike me as insecure.  There is no easy way to make it so that a virtual tty will time out if a program like emacs is running inside of it, so if you left your computer on for a day, anyone could switch to that tty and have a user session as you...

How is that different from leaving your X session open?

---

### Post by Zorgoth on 2010-08-14
My X session will lock and require my password after 30 minutes.  My ttys will not (well, they can if they aren't doing anything, but then why am I using them anyway).  You have to remember each time to manually log out of a tty if you want it to be secure.

---

### Post by Spike-X on 2010-08-14
I much prefer real tty's. Fake ones just don't do it for me.

---

### Post by Bachstelze on 2010-08-14
> **Spike-X said:**
> I much prefer real tty's. Fake ones just don't do it for me.

Define "real tty's"?

---

### Post by Legendary_Bibo on 2010-08-14
what does tty mean? I've seen it when I have to press Ctrl+Alt+F2 to deal with some things not responding.

---

### Post by Bachstelze on 2010-08-14
> **Legendary_Bibo said:**
> what does tty mean? I've seen it when I have to press Ctrl+Alt+F2 to deal with some things not responding.

tty stands for "teletype". The name dates back to the early days of computing when computers had no monitor and the results of computations were printed on paper. Some examples here: [http://www.columbia.edu/acis/history/teletype.html](http://www.columbia.edu/acis/history/teletype.html)

Nowadays, it can mean a lot of things depending on what the person who speaks thinks it means, but strictly speaking, it can be anything that emulates such a device, ranging from an xterm to a serial VT100-like terminal (with a keyboard and a screen).

---

### Post by Legendary_Bibo on 2010-08-14
> **Bachstelze said:**
> tty sands for "teletype". The name dates back to the early days of computing when computers had no monitor and the results of computations were printed on paper. Some examples here: [http://www.columbia.edu/acis/history/teletype.html](http://www.columbia.edu/acis/history/teletype.html)

Nowadays, it can mean a lot of things depending on what the person who speaks thinks it means, but strictly speaking, it can be anything that emulates such a device, ranging from an xterm to a serial VT100-like terminal (with a keyboard and a screen).

Ah, thanks for clearing that up. I googled it and I only got things related to cell phones.

I like putting my screen into that mode when I'm working on something that I don't want people to see (i.e. my brother), and I just put in random system information commands. I could lock my screen, but deterring them away with something they don't understand is more of an effective investment.

---

### Post by cariboo on 2010-08-14
> **Bachstelze said:**
> tty stands for "teletype". The name dates back to the early days of computing when computers had no monitor and the results of computations were printed on paper. Some examples here: [http://www.columbia.edu/acis/history/teletype.html](http://www.columbia.edu/acis/history/teletype.html)

Nowadays, it can mean a lot of things depending on what the person who speaks thinks it means, but strictly speaking, it can be anything that emulates such a device, ranging from an xterm to a serial VT100-like terminal (with a keyboard and a screen).

Actually, teletypes were used for sending text messages back and forth between offices. You usually typed up the message, the keystrokes were stored in a buffer, then you dialed the teletype number (which were different from normal phone numbers) of the office you were sending the message to, then pressed send.

I worked for a company that still used teletypes, the operators were sort of the geeks of the day.

Just as an aside, my job title at the time was elevator operator. :)

---

### Post by murderslastcrow on 2010-08-15
Haha, interesting to see that texting was around so long ago, and as a primary use of something I use to install encrypted DVD playback.

---

### Post by Austin25 on 2010-08-15
Cool, quite a bit of history in some thing running on my, well chest right now.

---

### Post by Bachstelze on 2010-08-15
> **cariboo907 said:**
> Actually, teletypes were used for sending text messages back and forth between offices. You usually typed up the message, the keystrokes were stored in a buffer, then you dialed the teletype number (which were different from normal phone numbers) of the office you were sending the message to, then pressed send.

True, but that dates back from before computers were invented.  Then, when computers appeared, teletypes were the "standard" user i/o interface (the teletype was wired directly to the computer, not to the "phone" network).

---

### Post by Windows Nerd on 2010-08-15
> **Austin25 said:**
> Well I use it now to keep my brother of of my desktop that has a live environment. He doesn't know the command line.
This. And to kill processes that have messed X up, or made the mouse unable to close the window, ect.

---

### Post by ssam on 2010-08-15
do you remember the days when you would log in to a virtual terminal and the run startx.

---

### Post by linux18 on 2010-08-15
> **ssam said:**
> do you remember the days when you would log in to a virtual terminal and the run startx.
I still do

anyway, tty's are great if you on a command line system

---

### Post by cariboo on 2010-08-15
> **Bachstelze said:**
> True, but that dates back from before computers were invented.  Then, when computers appeared, teletypes were the "standard" user i/o interface (the teletype was wired directly to the computer, not to the "phone" network).

I know you're young, but computers were invented and in use before the early 70's. :)

As another aside. I did my practicum with a company that specialized in servicing printers, the majority of the printers we serviced were [DEC LA-120's]("http://www.recycledgoods.com/products/DEC-LA120-DA-DECwriter-III-DECprinter-III-Terminal-Printer.html") which was basically still a teletype, this was in the late 80's.

---

### Post by koenn on 2010-08-15
> **cariboo907 said:**
> I know you're young, but computers were invented and in use before the early 70's. :).

yes, but they did batch processing. 
hooking up a teletype to a computer allowed for interactive use, and started of computing as we now it today. 

otoh, if you have actually seen telex being used, you must be *old*
:)

---

### Post by jpkotta on 2010-08-16
[The TTY demystified]("http://www.linusakesson.net/programming/tty/index.php")

---

### Post by toupeiro on 2010-08-16
Must this community clamour to elitism so much as to have to nit-pick tty, ttyS# pts or whatever you use?  It's a line out.  who cares if it hits a printer, a real VT220, a Wyseterm, or an ip-based dongle encrypted, aggregated, routed, and ACL'ed 2-factor.  Seriously, who cares. :lolflag:

TTY's on most commodity systems are typically just an out-of-band option for connectivity this day and age, when your LAN interface drops.  Nothing to see here.  9600 8,N,1

---

### Post by Bachstelze on 2010-08-17
> **toupeiro said:**
> 9600 8,N,1

Speak for yourself. 4800 7,E,1 is how I roll.

---

### Post by cariboo on 2010-08-17
> **koenn said:**
> yes, but they did batch processing. 
hooking up a teletype to a computer allowed for interactive use, and started of computing as we now it today. 

otoh, if you have actually seen telex being used, you must be *old*
:)

Yes I did see teletypes in use, while I was working for the Canadian Pacific **Steamship** Company. :)

---

### Post by koenn on 2010-08-17
> **cariboo907 said:**
> Yes I did see teletypes in use, while I was working for the Canadian Pacific **Steamship** Company. :)

:)

---

### Post by Austin25 on 2010-08-17
> **toupeiro said:**
> Must this community clamour to elitism so much as to have to nit-pick tty, ttyS# pts or whatever you use?  It's a line out.  who cares if it hits a printer, a real VT220, a Wyseterm, or an ip-based dongle encrypted, aggregated, routed, and ACL'ed 2-factor.  Seriously, who cares. :lolflag:

TTY's on most commodity systems are typically just an out-of-band option for connectivity this day and age, when your LAN interface drops.  Nothing to see here.  9600 8,N,1
Actually, I only started the thread to see if people used the this or terminal emulators like xterm or gnome-terminal.

---

### Post by cariboo on 2010-08-17
To get back on topic, I use both, virtual TTYs and gnome-terminal, depending on what I have to do, and which computer I'm working. I have 2 systems that are cli only, a server and a G3 running debian stable for playing mp3's, I also use screen on this system.

---

### Post by toupeiro on 2010-08-22
> **Bachstelze said:**
> Speak for yourself. 4800 7,E,1 is how I roll.

lol do you REQUIRE 7E1?!  what old fossil are you connected to? :P  I never see 7,E,1 used anymore.  Last time was some old Data General serial printers...

---

