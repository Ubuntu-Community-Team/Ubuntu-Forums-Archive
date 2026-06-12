---
title: "how to change timestamp format in logs?"
date: 2008-11-12
forum: Server Platforms
---

### Post by anystupidname on 2008-11-12
Hi, my syslog/dmesg/auth.log etc all have a timestamp "Nov 12 08:05:00" but I'd like to switch it to "1112 00:00:00". Does anybody know how to do this?
Thanks!

---

### Post by ciscosurfer on 2008-11-12
Use an editor ;-)  On a more serious note, if you want to modify how timestamps are presented, take a look at the manpage for date```
man date
```This should put you on the right track.

---

### Post by anystupidname on 2008-11-12
OK, I'll phrase the question more carefully. I would like to permanently change the date/time format used by the system when writing any/all logs.

If I'm reading "man date" properly, it only tells me how to change the system date (not format/region) or output the date in a specific format a single time manually...

---

### Post by hictio on 2008-11-12
This is an interesting question, well, at least, I think it is...
I *think* you have to look at the 'locale' settings; start by reading the man page, I see that there is an environmental variable called 'LC_TIME' that is used for "Date and time formats".

Your nick is hilarious :D

---

### Post by ciscosurfer on 2008-11-12
@anystupidname,

I sent you to the manpage so you could see how the *format* characters work.  You can find more information [by going here]("http://manpages.ubuntu.com/manpages/intrepid/man1/date.html") or running```
info date
```Another page to read is the [localedef manpage]("http://manpages.ubuntu.com/manpages/intrepid/man1/localedef.html").  

The discussion centers around how date and time are interpreted based on the specific locale that you have set.  You can either modify your locale (change to a different locale) to better align with the formatting you desire, or you can modify the current locale itself.  Some of the codes used inside your locale will be Unicode (see ref. link below); codes like %d, %X, %u, %F are conversion specifiers and are interpreted, for example, by functions like strftime(), the date command, and your locale settings.

**Pages of interest**:
[URL="http://en.wikibooks.org/wiki/Unicode/Character_reference/0000-0FFF"]Unicode/Character reference/0000-0FFF
[/URL]
[Locale pages]("http://manpages.ubuntu.com/cgi-bin/search.py?cx=003883529982892832976%3A5zl6o8w6f0s&cof=FORID%3A9&ie=UTF-8&q=locale&titles=Title&lr=lang_en")

[Date pages]("http://manpages.ubuntu.com/manpages/intrepid/man1/date.html")

[strftime]("http://manpages.ubuntu.com/manpages/intrepid/man3/strftime.html")

**Directories/Files of interest**:
/usr/share/i18n/locales

**See what's what**:
man date
info date
man 1 locale
man 5 locale
man 7 locale
locale
locale -ck LC_TIME

[This particular discussion]("http://ubuntuforums.org/showthread.php?t=193916") gets at the heart of what you want to accomplish.  It's from the middle of '06, but is still relevant.  [Here's another page]("http://www.gentoo-wiki.info/Locales") that discusses modification of the locale as well.  Both are decent in their own rights.

---

