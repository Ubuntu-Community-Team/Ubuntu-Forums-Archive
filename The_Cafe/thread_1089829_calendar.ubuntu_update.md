---
title: "calendar.ubuntu update"
date: 2009-03-07
forum: The Cafe
---

### Post by Girya on 2009-03-07
**Time Waster Alert**

I've been using the calendar program to keep track of appointments and the like. I was messing around with the config file to get rid of entries like:

> 8 Mar	&#1052;&#1077;&#1078;&#1076;&#1091;&#1085;&#1072;&#1088;&#1086;&#1076;&#1085;&#1099;&#1081; &#1046;&#1077;&#1085;&#1089;&#1082;&#1080;&#1081; &#1044;&#1077;&#1085;&#1100;

which mean nothing to me, sorry I'm a little rusty in Cyrillic ;)

and keep entries relevant entries like:

> Mar 08 	Ron "Pigpen" McKernan (Grateful Dead) dies in California, 1973

when I came across calendar.ubuntu in /usr/share/calendar, it was last updated since 2005 so I spent some time updating it to include recent releases (since 2005) and the current release schedule for Jaunty Jackalope. 

Just paste it into /usr/share/calendar.ubuntu and enjoy

**important note!when I posted the tabs were removed. Duh; for calendar to properly process this file you have to insert tabs between dates and events and tabs on any lines of events that are longer than one line.  see man calendar for a better explanation**



> 
/*
 * Interesting dates in Ubuntu history
 * Matt Zimmerman <mdz@ubuntu.com>, 2005-10-24
 * updated 2009-03-09 
 */

#ifndef _calendar_ubuntu
#define _calendar_ubuntu

LANG=utf-8

/* Ubuntu releases */
Oct 20  Ubuntu 4.10 (Warty Warthog) released, 2004
Apr 08  Ubuntu 5.04 (Hoary Hedgehog) released, 2005
Oct 13  Ubuntu 5.10 (Breezy Badger) released, 2005
Jun 1   Ubuntu 6.06 (Dapper Drake) released, 2006
Oct 26  Ubuntu 6.10 (Edgy Eft) released, 2006
Apr 19  Ubuntu 7.04 (Feisty Fawn) released, 2007
Oct 18  Ubuntu 7.10 (Gutsy Gibbon) released, 2007
Apr 24  Ubuntu 8.04 (Hardy Heron) released, 2008
Oct 30  Ubuntu 8.10 (Itrepid Ibex) released, 2008
Apr 23  Ubuntu 9.04 (Jaunty Jackalope) released, 2009
Oct     Ubuntu 9.10 (Karmic Koala) released, 2009




/* Misc */

July 8  Ubuntu Foundation created, 2005

/* Release Schedule */
Nov 20  Alpha 1 released (Jaunty Jackalope),[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-November/000513.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-November/000513.html) (Jaunty Jackalope) 2008
December 18
        Alpha 2 Released [http://www.ubuntu.com/testing/jaunty /alpha2](http://www.ubuntu.com/testing/jaunty /alpha2),
         (Jaunty Jackalope), 2008
January 15      Alpha 3 Released, [http://www.ubuntu.com/testing/jaunty/alpha3](http://www.ubuntu.com/testing/jaunty/alpha3)
        (Jaunty Jackalope), 2009
February 5      Alpha 4 Released, [http://www.ubuntu.com/testing/jaunty/alpha4](http://www.ubuntu.com/testing/jaunty/alpha4) (Jaunty Jackalope), 2009
February 26     Alpha 5 Released, [http://www.ubuntu.com/testing/jaunty/alpha5](http://www.ubuntu.com/testing/jaunty/alpha5)
        (Jaunty Jackalope), 2009
March 26        Beta, Released (Jaunty Jackalope), 2009
April 16        Release Canidate!, Released (Jaunty Jackalope), 2009
April 23        Ubuntu 9.04, Realeased (Jaunty Jackalope), 2009



#endif /* !_calendar_ubuntu_ */

If you have any other interesting ubuntu dates, reply so I can keep my calendar.ubuntu current

---

