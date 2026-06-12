---
title: "New TV - TV / Monitor or Monitor / TV?"
date: 2013-08-28
forum: The Cafe
---

### Post by e_james on 2013-08-28
The TV in my workroom has broken down and now I am wondering what sort of replacement I want to buy.

Basically there are 3 main things I would like to be able to do - 
1. Watch Freeview channels.
2. Watch internet TV streams.Where I live in the UK I can only receive the 2 main multiplexes on Freeview (BBC1  etc. and ITV1 etc.) so I use internet TV for other channels.
3. Watch the many .avi and .ts recordings I have stored on various drives around my home network. (4 netbooks, 1 laptop, 2 desktops, 1 nettop, 2 NAS units + 1 Android tablet and 1 Android smartphone))

I do like to watch TV.

My problem is the rapid development of technology.

Should I buy a digital TV which can also function as a monitor and attach a small PC? Should I buy a monitor (which can also function as a TV) and attach a small PC? Or something different from the above? I would like something reasonably future proof - at least 3 years.

As a further complication the space available is limited. The failed TV is 40cm wide and anything much wider would mean rearranging much of the furniture.

There's also the question of connectors and adapters - hdmi, dvi, vga, scart, audio etc.

Of course the decision is entirely mine but I would be interested to read any comments and suggestions. I think this thread is in keeping with the nature of this forum.

Some of my PCs run Linux and some run Windows (7 or XP). The choice is determined by what works best according to my current level of expertise. All are dual boot.

---

### Post by SeijiSensei on 2013-08-28
My daughter bought herself [this TV]("http://www.amazon.com/gp/product/B0074FGNJ6") which has a variety of nice features at a decent price.  She connects it to her laptop with an HDMI cable if she wants to play games or watch video streams from sites that are not supported natively by the TV's built-in wifi client.

TVs with VGA connectors like my older Sony Bravia seem to be a dying breed.  DVI is a possibility, though it will only carry the video.  Even if the TV doesn't have a DVI jack, you can buy cheap DVI<>HDMI converters.  I've used one myself in the past with an NVIDIA card that didn't have an HDMI output.

40cm is pretty narrow, though, about the equivalent of a 19" monitor.  You'll find few if any TVs that small, and monitors are getting larger than that, too, to accomodate the demands of 16:9 aspect ratios.  A lot of monitors start at 22-24" (55-60 cm) and go up from there.

I'd start thinking about how to rearrange the furniture.

---

### Post by lah7 on 2013-08-28
I think it depends entirely on how you'd like to approach this... you could:
- Build yourself a media centre type PC that has everything in one place ([Ubuntu TV]("http://www.ubuntu.com/tv/") would be excellent for this, but it's still in development at this time of writing.. :( )
- Having different devices offering your various requests and thus juggling around the source inputs between TV/PC.

If it's the latter option, then you'd be better off with a TV with freeview built in. But, if you do decide to go with a PC that does-it-all, you'd be better buying Linux-compatible TV tuners *[check 1]* and connecting it to your home network. Now all you need is the right software.* [checks 2+3]*

Since you have multi-OSs on your devices, such software like [XBMC]("http://xbmc.org/") may be really useful for being the "hub" by retrieving videos from Windows shares and via SSH for your Linux systems. I bet they'll also be software available for Android which allows streaming too. They'll be plenty of tutorials and helping hands too if you need assistance along the way.

Personally, I'd go with the PC with a decent monitor and turn it into my own smart-type-of-TV. It may be fiddly, but once it's set up, it's entirely personalized to exactly what you want it for. :)

---

### Post by e_james on 2013-08-29
SeijiSensei

Yes, I had noticed the size trend but I won't concede defeat easily. I am willing to think well outside the usual boxes - maybe a laptop or tablet with TV tuner attached. How would I look for a computer a bit like an imac which isn't an imac? Does anybody make a PC a bit like an imac (i.e. all in one except for keyboard and mouse)? 

lah7

With the help of a friend I've been looking for hardware options. There's a 15" TV called Curry's Essentials which covers many of the options. It would need a PC attached of course. Alternatively I could just about squeeze in a 17" monitor. With a PC and tuner I have much the same result. One key question is how much PC power do I need? 

Currently I have a Wharfedale TV with an eeeBox B202 bolted on the back and it does everything except the TV tuning. At this time it is running Linux Mint 11 (I think). I also have 3 HDHomerun tuners but only 2 are in use. I must see if I can get the B202 to use the spare. I bought some usb tuners last September and came to some conclusions. If it's currently for sale, it's not compatible with linux. If it's compatible with linux, nobody sells it any more (maybe on ebay).

I also have a problem with media centre software - overkill. It feels like having my first driving lesson in a formula 1 racer. I have been recording programmes I want to watch on my computer since 2003 and I just use Windows Media Player, Classic Media Player, VLC, Totem Movie Player or MX Player (Android) in conjunction with a file manager and SMB/Samba. Just double-click or "open with" and it plays. Surprisingly the B202 can play the .ts files using VLC over a wifi connection. I have essentially no interest in details such as directors and actors except where they help to determine whether I have already seen the episode. I did have some success using Media Portal for recording (it's really good at padding) but MythTV is a nightmare. I haven't tried XBMC yet but the web site explains many of the details required to set it up to do all those things I don't really want to do. 

I hope you noticed that I wrote "many". I have found it to be a consistent characteristic of modern instruction manuals that significant details are left out ("Surely everybody knows that!"). My car manual doesn't explain how to replace a headlamp bulb. My smartphone manual doesn't say how to answer an incoming call. I had to call the help desk on that one and even they weren't immediately sure how to do it. On that subject, this new look forum keeps asking me to log in. The old system used to remember me.

Thanks to you both for your comments. I will continue to think through my options. Any additional comments, suggestions, ideas will also be considered.

---

### Post by SeijiSensei on 2013-08-30
> **e_james said:**
> Does anybody make a PC a bit like an imac (i.e. all in one except for keyboard and mouse)?

Sure.  [Dell]("http://www.dell.com/us/business/p/all-in-one-desktops") does for instance.  [Here]("http://www.dell.com/us/business/p/inspiron-one-20-2020-aio/fs") are some 20" (50 cm) diagonal models.

---

### Post by e_james on 2013-08-30
I forgot about Dell. Initial impressions - definitely bigger and probably more expensive than what I had in mind.

Interim report.

One of my netbooks is an Asus eeePC X101CH with an Atom N2600 cpu. I have Windows 7 Starter and Lubuntu 13.04 installed. In Windows 7 the HDHomerun works tolerably well with the viewer provided. In Lubuntu the viewer is VLC which only works with a reduced picture size 1:2 or 1:4. If there is a simple linux TV application that works with the HDHomerun, I haven't found it yet.

So next I installed XBMC from the ubuntu repository. Of course, it does just about everything you could imagine with regard to multimedia except display live tv.

lah7 please note that XBMC doesn't do live tv by itself (significant details left out). It needs to work with some sort of tuner management software. Also worth mentioning - the XBMC instructions don't match the software. In the absence of any better ideas, I think I will try TVHeadend.

Expect further updates.

---

### Post by lah7 on 2013-08-30
> **e_james said:**
> So next I installed XBMC from the ubuntu repository. Of course, it does just about everything you could imagine with regard to multimedia except display live tv.

lah7 please note that XBMC doesn't do live tv by itself (significant details left out). It needs to work with some sort of tuner management software. Also worth mentioning - the XBMC instructions don't match the software. In the absence of any better ideas, I think I will try TVHeadend.

My apologies e_james, I kind of forgot about the missing live TV out-of-the-box functionality, :( when I wrote my last post I was thinking more towards the recorded TV side of things. Getting Live TV to work will vary depending on how compatible your tuners are for Linux.

I do hope TV for Linux improves in the next few years, especially with the Ubuntu TV project sharing back-end code across projects like XBMC.

But then again, if XBMC suits all your multimedia and internet needs (besides live TV), I would suggest going down the route with a TV with freeview built-in.

---

### Post by e_james on 2013-08-30
TVheadend report.

"In order to crack this nut it is necessary to carry out a customer survey to determine which sledgehammer is most appropriate."

As usual, the help system is not helpful. I can't set up the HDHomerun so far. It's noticeably absent.

---

