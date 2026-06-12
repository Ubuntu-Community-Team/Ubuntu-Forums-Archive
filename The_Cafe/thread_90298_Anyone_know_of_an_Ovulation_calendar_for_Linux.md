---
title: "Anyone know of an Ovulation calendar for Linux?"
date: 2005-11-14
forum: The Cafe
---

### Post by fragmental on 2005-11-14
Anyone know of an Ovulation callendar for Linux?

By that I mean, something like this:  [http://www.ovulation-calendar.com/](http://www.ovulation-calendar.com/) which is, of course, only for windows and also $29USD.

Maybe a plugin for some other calendar program?  It would, preferably be free and/or open source, but doesn't have to be as long as it works in Linux.

---

### Post by Stormy Eyes on 2005-11-14
I don't think it's occured to anybody developing for Linux that somebody might need an ovulation calendar. It's something most Linux geeks don't do, after all. :)

---

### Post by endy on 2005-11-14
Take a look here: [http://linuxorg.sourceforge.net/]("http://linuxorg.sourceforge.net/")

On a quick glance it looks like it would do the job :)

[[IMG]http://linuxorg.sourceforge.net/shots/pcal_main.png[/IMG]]("http://linuxorg.sourceforge.net/shots/pcal_main.png")

---

### Post by fragmental on 2005-11-14
[QUOTE=Stormy Eyes]I don't think it's occured to anybody developing for Linux that somebody might need an ovulation calendar. It's something most Linux geeks don't do, after all. :)[/QUOTE]


I would believe that if these two assumptions were true:
A.  No Linux programmers are women.
B.  No Linux programmer has a girlfriend or wife.

I believe that those two assumptions are false, however so I think it must have  occured to somebody.  Maybe they either kept it to themself or didn't feel like writing it.

Edit:
[QUOTE=endy]Take a look here: [http://linuxorg.sourceforge.net/]("http://linuxorg.sourceforge.net/")

On a quick glance it looks like it would do the job :)

[[IMG]http://linuxorg.sourceforge.net/shots/pcal_main.png[/IMG]]("http://linuxorg.sourceforge.net/shots/pcal_main.png")[/QUOTE]

Looks like it might.  Thanks.  Sometimes google just doesn't seem to find any good results.

---

### Post by endy on 2005-11-14
Admittedly it wasn't that easy to find, especially with sourceforge down for maintenance :)

---

### Post by izmaelis on 2005-11-14
[QUOTE=Stormy Eyes]It's something most Linux geeks don't do, after all. :)[/QUOTE]
Now that made me lough for about 15 minutes. No geek with ovulation here... ehrm, sorry... :)

---

### Post by fragmental on 2005-11-15
I can't seem to compile it.  The configure script keeps dumping me at the console at "checking for gtkmm-2.4...".  I have libgtkmm-2.4.  It's automaticaly installed.  Did not have libglademm-2.4 which I installed and the configure script did the same thing.

If I try to run make it says there is no makefile.

---

### Post by nocturn on 2005-11-15
[QUOTE=fragmental]I can't seem to compile it.  The configure script keeps dumping me at the console at "checking for gtkmm-2.4...".  I have libgtkmm-2.4.  It's automaticaly installed.  Did not have libglademm-2.4 which I installed and the configure script did the same thing.

If I try to run make it says there is no makefile.[/QUOTE]

./configure generates the makefile, so it will not exist until configure finishes correctly.

Maybe it looks for gtkmm in the wrong place?

---

### Post by Pablo_Escobar on 2005-11-15
Fragmental - do you have dev packages for libgtkmm-2.4 and other missing dependencies ??

---

### Post by izmaelis on 2005-11-15
Look what I have found:
```

izmaelis@boxzilla:~$ sudo apt-cache search ovulation
cycle - calendar program for women

```
You may try install and use it. Who knows maybe it will fit your ovulational needs.

---

### Post by majikstreet on 2005-11-15
at all the guys here that made comments: just shut up. honestly! who knows, the calendar may be for their wife :P

---

### Post by uberlinux on 2005-11-15
NOTE: This program is not a reliable contraceptive method. It does neither help to prevent sexual transmision diseases like AIDS. It is just an electronic means of keeping track of some of your medical data and extract some statistical conclusions from them. You cannot consider this program as a substitute for your gynecologist in any way.
Now thats a funny readme

---

### Post by fragmental on 2005-11-15
[QUOTE=Pablo_Escobar]Fragmental - do you have dev packages for libgtkmm-2.4 and other missing dependencies ??[/QUOTE]

Yeah...installing those worked.  I thought maybe that was it but hoped I wouldn't have to install them.  There were like 20 dependencies for the dev packages.

---

### Post by public_void on 2005-11-16
> You cannot consider this program as a substitute for your gynecologist in any way.

LOL. That had me laughing for ages.

---

### Post by baRRacuda on 2005-11-16
My friend had application like that in his SymbianOS Mobile phone. I think it's more useful than others on a pc. :)

---

### Post by Tsukino Kyuuketsuki on 2008-04-23
> **Stormy Eyes said:**
> I don't think it's occured to anybody developing for Linux that somebody might need an ovulation calendar. It's something most Linux geeks don't do, after all. :)


I find that comment really sexist and offensive. Even though I don't consider myself a geek (I don't know THAT much about computers, lol), it's really offensive when people think of geeks as just dudes. It sounds like girls are just not smart enough or something. And it's not about being a dude or a girl, I've seen men that doesn't even know how to turn on the computer and women that might know way more about programming that any of the people on this forum... so yeah, next time think before you post.

Hey fragmental, I was looking for the same stuff for linux, I use to have 'victoria-woman-calendar' on windows, wasn't free but I had it cracked (like most of the software I had on windows, lol). I tried to run it with wine but couldn't make it work, guess the crack was messing up. Anyways, have you tried 'cycle'? That's way better than that stuff I had on windows and it's free.

---

### Post by macogw on 2008-04-23
I use Cycle to remember when I need to pull out the pads.  I don't have to worry about the ovulation part, but the fertile days are highlighted in light green and ovulation date is in turquoise.  It shows the days that are "safe" (based on the rhythm method) for sex as well.  You can set if it shows fertile, safe, or both days.  

I just use it to track when my next period is because 1) I'm bad at remembering and 2) it can take into account things that a "repeat every 28 days" on a normal calendar won't to predict what day it will start based on the average length of the menstrual cycle for the last 6 months.  

The colors are configurable if you don't like the default.  It also has you set a password so that if someone wanders up to your computer they can't just go snooping about what day you're up, when you marked your first pill of the month, and what notes you've added to what days.

Tsukino:
/me points at user title

---

### Post by LaRoza on 2008-04-23
> **Tsukino Kyuuketsuki said:**
> I find that comment really sexist and offensive. Even though I don't consider myself a geek (I don't know THAT much about computers, lol), it's really offensive when people think of geeks as just dudes. It sounds like girls are just not smart enough or something. And it's not about being a dude or a girl, I've seen men that doesn't even know how to turn on the computer and women that might know way more about programming that any of the people on this forum... so yeah, next time think before you post.

Hey fragmental, I was looking for the same stuff for linux, I use to have 'victoria-woman-calendar' on windows, wasn't free but I had it cracked (like most of the software I had on windows, lol). I tried to run it with wine but couldn't make it work, guess the crack was messing up. Anyways, have you tried 'cycle'? That's way better than that stuff I had on windows and it's free.

This thread was been dead since November 16th, 2005.

[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

For popch:

[img]http://www.freesmileys.org/smileys/violent083.gif[/img]

---

