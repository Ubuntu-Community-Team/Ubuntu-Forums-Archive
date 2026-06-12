---
title: "what's the deal with conky?"
date: 2009-01-02
forum: The Cafe
---

### Post by SonnHalter on 2009-01-02
i thought it was a simple program that displayed your system's status. boring. why do people like it so much?

---

### Post by %hMa@?b&lt;C on 2009-01-02
it is customizable thus making it pretty fun!

---

### Post by OutOfReach on 2009-01-02
You can do a LOT with Conky. That's why I like it so much.

---

### Post by SonnHalter on 2009-01-02
like?

---

### Post by ajcham on 2009-01-02
> **SonnHalter said:**
> like?

Check [thread=281865]here[/thread].

People have some great conky configs for giving weather reports, RSS feeds, music lyrics etc.

---

### Post by OutOfReach on 2009-01-02
Email, RSS, Package management (Pacman), Weather, Music status, uptime. Just to name a few.

---

### Post by chucky chuckaluck on 2009-01-02
i just use it for a clock in openbox (upper right). i don't really need a panel.

[[IMG]http://e.imagehost.org/t/0584/conk.jpg[/IMG]](http://e.imagehost.org/view/0584/conk)

---

### Post by andrewabc on 2009-01-03
I got my conky displaying computer info.
I have it set up to show the weather for my area.
I have it showing my current song playing, thus I don't need music player showing for me to know what song it playing and other music info.

All this and it uses 2mb of ram (2 instances, ~1mb each).

And with my widescreen monitor, I don't have my windows maximized, so the right side of my screen only has conky on desktop, along with cario-dock for when I need to open apps.

---

### Post by xpod on 2009-01-03
I like it mainly for the weather & the network monitoring.
Mines mostly copied from other peoples at the moment,with a few adjustments.

> 
And with my widescreen monitor, I don't have my windows maximized, so the right side of my screen only has conky on desktop, along with cario-dock for when I need to open apps.

I`ve went back to dual screens rather than my usual dual machines so the 22" is great for browser & conky with my 19" for whatever else.Usually keeping an eye/helping on my kids machines around the house.

---

### Post by kaivalagi on 2009-01-03
I have great fun writing python scripts to support the conky "movement". It gives me a challenge now and again, and helps me learn about the possibilities of python development.

Go on, give conky a try...or if not *shameless plug* try my app (link below) which does much the same thing but using html, images and javascript...

---

### Post by laceration on 2009-01-04
I've got all kinds of Conky type stuff without Conky.  I've the got the Gnome-System-Monitor applet and top in a terminal for system info.  Conky for weather?  Can Conky show an animated satellite shot with a mouseover like my ff add-on? I didn't have to install or write a bunch of scripts though.  I can't see that Conky does anything unique or better and it is difficult to set up.   I'm still wondering like the OP, what's the deal with conky?

---

### Post by kaivalagi on 2009-01-04
A couple of things Conky has got going for it AFAIK are

1) what little resources it uses when compared to anything equivalent

2) total customisation of layout. Screenlets and equivalent cannot provide for this, they are fixed in format based on the developers design decisions.

3) decent graphs for cpu/ram/disk and network use that can provide a lot of info whilst keeping to a minimalistic look.

I am sure others will come up with key points of their own for why they use conky. Take a look at _some_ of the screenshots on these forums and you'll see people have used conky to great effect, in some cases where there is no alternative either.

Each to their own is the bottom line really...

---

### Post by dannytatom on 2009-01-04
> **laceration said:**
> I've got all kinds of Conky type stuff without Conky.  I've the got the Gnome-System-Monitor applet and top in a terminal for system info.  Conky for weather?  Can Conky show an animated satellite shot with a mouseover like my ff add-on? I didn't have to install or write a bunch of scripts though.  I can't see that Conky does anything unique or better and it is difficult to set up.   I'm still wondering like the OP, what's the deal with conky?

A lot less resources than it takes to run firefox.
You don't need FF open to see the weather.
You don't need a terminal open to see system info.

It's not that hard to write for it, either, it follows a pretty simple *syntax*.  And, if anything, spend 10 minutes looking at the conky scripts thread.  Find some you like, take the code for it, and put it together in your own.

---

### Post by fwojciec on 2009-01-04
> **laceration said:**
> I've got all kinds of Conky type stuff without Conky.  I've the got the Gnome-System-Monitor applet and top in a terminal for system info.  Conky for weather?  Can Conky show an animated satellite shot with a mouseover like my ff add-on? I didn't have to install or write a bunch of scripts though.  I can't see that Conky does anything unique or better and it is difficult to set up.   I'm still wondering like the OP, what's the deal with conky?

Here's an example for you.  The attached screenshot is from a netbook with a 1024x600 screen resolution.  A panel takes up too much space, also browser statusbar is unnecessary (remember we're working with 600 pixels of vertical space, and we want to use as much of it as possible to view the content of whatever it is we are viewing...)

At the same time, there are certain pieces of information that I want to have easily visible at all time: time, date, battery charge level, connected wifi network, new mail/update notifications, etc.  Conky to the rescue -- it only uses 12 pixels and displays all the info I need:

[[img]http://www.loka.pl/outgoing/conky_nc10-thumb.png[/img]](http://www.loka.pl/outgoing/conky_nc10.png)

This is just one example.  Conky is extremely customizable so whether you can imagine uses for it or not depends, mostly, on your imagination.

---

### Post by markp1989 on 2009-01-04
conky is an amazing program, it can display loads of things, the best thing i like is that it can display the output of any command, so that people can write there own bash script and have the out put in conky (check the left side of the screen shot which shows my torrentflux stats). it can do news weather, hundreds of things. 

check the screen of my current conky, its not finished yet, this conky is for a digital photo frame , i plan on adding my new emails, and a few other things, any ideas?

---

### Post by mobilediesel on 2009-01-04
> **markp1989 said:**
> conky is an amazing program, it can display loads of things, the best thing i like is that it can display the output of any command, so that people can write there own bash script and have the out put in conky (check the left side of the screen shot which shows my torrentflux stats). it can do news weather, hundreds of things. 

check the screen of my current conky, its not finished yet, this conky is for a digital photo frame , i plan on adding my new emails, and a few other things, any ideas?

What did you use for the road conditions at the bottom?

---

### Post by markp1989 on 2009-01-04
> **mobilediesel said:**
> What did you use for the road conditions at the bottom?

i have this in my conkyrc
```
 
Warnings
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 0}${color ffffff}
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 1}${color ffffff}
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 2}${color ffffff}
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 3}${color ffffff}

``` 

just checks the warning rss feeds from the met office site, for south east england, im not sure where you live, so it may not be much use to you

---

### Post by mobilediesel on 2009-01-04
> **markp1989 said:**
> i have this in my conkyrc
```
 
Warnings
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 0}${color ffffff}
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 1}${color ffffff}
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 2}${color ffffff}
${alignc}${color ff0000}${rss http://www.metoffice.gov.uk/xml/warnings_rss_se.xml 10 item_title 3}${color ffffff}

``` 

just checks the warning rss feeds from the met office site, for south east england, im not sure where you live, so it may not be much use to you

Yeah I'm about 3,600 miles west of there. I didn't think to look for RSS feeds for traffic warnings so that does help me. I just have to do the work myself.

---

### Post by cardinals_fan on 2009-01-04
> **laceration said:**
> I've got all kinds of Conky type stuff without Conky.  I've the got the Gnome-System-Monitor applet and top in a terminal for system info.  Conky for weather?  Can Conky show an animated satellite shot with a mouseover like my ff add-on? I didn't have to install or write a bunch of scripts though.  I can't see that Conky does anything unique or better and it is difficult to set up.   I'm still wondering like the OP, what's the deal with conky?
Conky can display information from my own personal scripts (such as the one for my school grades), all while keeping my dwm setup clean of junk like panels.  Also, I can release my inner perfectionist and tweak conky to perfection.

---

### Post by laceration on 2009-01-05
> what little resources it uses when compared to anything equivalent
The resources to run my conky replacements are trivial.  
> total customisation of layout. Screenlets and equivalent cannot provide for this, they are fixed in format based on the developers design decisions
Applets *are* configuarable. Size, colors, vert or horiz etc.  
> You don't need a terminal open to see system info.
I don't worry about space or an open terminal when I have 6 viewports and 4gb of ram.  
> A lot less resources than it takes to run firefox.
You don't need FF open to see the weather.
Doesn't everyone have firefox open all the time anyways?  
> keeping my dwm setup clean of junk like panels
What good is it to clean the junk of panels when you just trade it for the junk of Conky?  At least panels can autohide.  
> people can write there own bash script and have the out put in conky
You can run any script without Conky too.  
> At the same time, there are certain pieces of information that I want to have easily visible at all time: time, date, battery charge level, connected wifi network, new mail/update notifications, etc. Conky to the rescue -- it only uses 12 pixels and displays all the info I need:
Now this makes a lot of sense.  I'm just not sure having a netbook makes any sense.

Face it you guys, Conky is just a geeky toy, something to do while you are in Mom's basement.

Regards,

Laceration
(from Mom's basement;))

---

### Post by cardinals_fan on 2009-01-05
> **laceration said:**
> The resources to run my conky replacements are trivial.  
Trivial to you, but probably not to me.
> **laceration said:**
> 
I don't worry about space or an open terminal when I have 6 viewports and 4gb of ram.  
I have nine workspaces, but I prefer to keep things clean.
> **laceration said:**
> 
Doesn't everyone have firefox open all the time anyways?  
Often I do, but not always.
> **laceration said:**
> 
What good is it to clean the junk of panels when you just trade it for the junk of Conky?  At least panels can autohide.  
Conky is part of my desktop and is covered whenever I open a window.
> **laceration said:**
> 
You can run any script without Conky too.  
I don't want to open a terminal and type "grades" whenever I want to check my grades.  I just want to switch to a blank desktop and glance at the conky one the bottom, which will automatically update the grades every 40 minutes.
> **laceration said:**
> 
Face it you guys, Conky is just a geeky toy, something to do while you are in Mom's basement.
Your PC almost certainly came with either Windows or OS X preinstalled.  Wouldn't you agree that Linux [on your machine] is "just a geeky toy, something to do while you are in Mom's basement"?

Use what works for you.

---

### Post by sarah.fauzia on 2009-01-05
I've tried to use Conky, and while I admire people's setups, I haven't (yet) customized one for myself. For now I'm quite happy using Docker for notification icons, and the time in an openbox pipe menu. Then, I configured a single tap to unmaximize windows so I can easily access the desktop to find the time, to use the right-click app menu (though I changed it to use the left-click--I run Openbox), or to access my docked apps. Very convenient, no mess of panels. And I have 4GB of RAM, too--but that only makes me want to use *less* RAM  so I can have a leaner system :)

---

### Post by jonabyte on 2009-01-05
> **SonnHalter said:**
> i thought it was a simple program that displayed your system's status. boring. why do people like it so much?

Some people do not find system stats boring...:D

---

### Post by sarah.fauzia on 2009-01-14
Can you believe how much changes in a week? I'm using Conky now; just made some slight adjustments to Box Conky (available from GNOME-look). Thanks a lot for the recommendations, everyone :) I find it entirely superior to relying on the GNOME system monitor, ugh! It's exceptionally helpful when I want to quickly check how my resources are being allocated; it's my system monitor, disk monitor, and time, date, and calendar reminder in the most aesthetically pleasing form! :)

---

### Post by HunterK on 2009-01-14
I use windows to check the weather outside. ;)

---

### Post by cardinals_fan on 2009-01-14
> **sarah.fauzia said:**
> Can you believe how much changes in a week? I'm using Conky now; just made some slight adjustments to Box Conky (available from GNOME-look). Thanks a lot for the recommendations, everyone :) I find it entirely superior to relying on the GNOME system monitor, ugh! It's exceptionally helpful when I want to quickly check how my resources are being allocated; it's my system monitor, disk monitor, and time, date, and calendar reminder in the most aesthetically pleasing form! :)
You know what's even stranger?  I'm not ;)

Ratpoison has weaned me off conky.  If I want to check my grades, I just execute 'grade' in the konsole I always have open.

---

