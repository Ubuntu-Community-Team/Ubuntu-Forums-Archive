---
title: "Arora browser - Firefox clone"
date: 2009-03-09
forum: The Cafe
---

### Post by forcecore on 2009-03-09
i found this browser and i can say it is 100% firefox but faster and passes 100/100 Acid3 test, i tested 21.02.2009 release and it was very fast (faster than ff3).

Test yourself:
[http://www.arora-browser.org/](http://www.arora-browser.org/)

---

### Post by Grant A. on 2009-03-09
If it was 100% Firefox, it would be Firefox. ;)

By "clone" did you mean derivative?

And is it still using the Gecko engine, or WebKit engine?

---

### Post by smbm on 2009-03-09
Arora uses webkit AFAIK

---

### Post by Faolan84 on 2009-03-09
This browser looks like a pretty decent project. A slim'd down version of Firefox written in QT 4 does sound like a great idea -- and with GTK support in QT 4.4 it won't look butt ugly either. Plus webkit beats gecko any day of the week. I've been looking for a decent extend-able browser that works integrates good with Gnome and uses webkit.

I thought that Epiphany was going to start using webkit as of 2.24, guess they delayed that to 2.26.

---

### Post by Dekkon on 2009-03-09
> **Faolan Devyn Aodfin said:**
> This browser looks like a pretty decent project. A slim'd down version of Firefox written in QT 4 does sound like a great idea -- and with GTK support in QT 4.4 it won't look butt ugly either. Plus webkit beats gecko any day of the week. I've been looking for a decent extend-able browser that works integrates good with Gnome and uses webkit.

I thought that Epiphany was going to start using webkit as of 2.24, guess they delayed that to 2.26.

OMG!!!111?!1 A web browser based on QT and using Webkit, everyone start embracing this now, now I tell you, this exactly what I need, I am sick of Firefox on KDE 4.2. :)

lol, this is serious. :o

---

### Post by Chemical Imbalance on 2009-03-09
Any way to get a 64-bit deb or do I have to compile?  Running the deb even with 32-bit libs installed still gives wrong architecture.

---

### Post by Faolan84 on 2009-03-09
> **Dekkon said:**
> OMG!!!111?!1 A web browser based on QT and using Webkit, everyone start embracing this now, now I tell you, this exactly what I need, I am sick of Firefox on KDE 4.2. :)

lol, this is serious. :o

I'd rather use something written in pure GTK+ but now that QT 4.x has a method to integrate into Gnome, i consider it a viable solution. Anyways, QT4 is actually quite speedy, even more-so that GTK. Just don't expect to see a speed improvement when using the GTK theme engine.

---

### Post by ghindo on 2009-03-09
How is Arora like Firefox?  Is uses the Webkit engine, whereas Firefox uses Gecko; it's written in QT, whereas Firefox is GTK...seriously, how are they alike?  :???:

---

### Post by Dekkon on 2009-03-09
> **ghindo said:**
> How is Arora like Firefox?  Is uses the Webkit engine, whereas Firefox uses Gecko; it's written in QT, whereas Firefox is GTK...seriously, how are they alike?  :???:

The GUI, it looks exactly the same as Firefox.

---

### Post by Faolan84 on 2009-03-09
Firefox is not written in GTK+. It's rendering engine "Gecko" provides the interface and Gecko uses GTK to display the widgets. In fact if you look real carefully at some of the widgets in Firefox and Thunderbird, you will notice that they do not theme totally consistent with the GTK+ theme.

The Mozilla team could just as easily create a "port" of Gecko that uses QT4 or even FLTK for the theming but they don't.

---

### Post by JackieChan on 2009-03-09
I'm downloading it now

---

### Post by Grant A. on 2009-03-09
> **Faolan Devyn Aodfin said:**
> Firefox is not written in GTK+. It's rendering engine "Gecko" provides the interface and Gecko uses GTK to display the widgets. In fact if you look real carefully at some of the widgets in Firefox and Thunderbird, you will notice that they do not theme totally consistent with the GTK+ theme.

The Mozilla team could just as easily create a "port" of Gecko that uses QT4 or even FLTK for the theming but they don't.

Firefox uses XULRunner for its interface.

---

### Post by Faolan84 on 2009-03-09
From what I understand Gecko and XULrunner seem to be the same thing. Maybe Gecko is just the rendering engine for the HTML and XUL is the interface and I was just a bit confused then. But I was close.

---

### Post by Gramps on 2009-03-09
I just installed it and I must say it is fast. Tried it on several sites and all I can see that will be a problem is flash. I went to Youtube and got the message that either I didn't have Java script enabled or was missing a plugin.

---

### Post by Skripka on 2009-03-09
> **Dekkon said:**
> OMG!!!111?!1 A web browser based on QT and using Webkit, everyone start embracing this now, now I tell you, this exactly what I need, I am sick of Firefox on KDE 4.2. :)

lol, this is serious. :o

Use Konqueror.

---

### Post by swoll1980 on 2009-03-09
> **Dekkon said:**
> OMG!!!111?!1 A web browser based on QT and using Webkit, everyone start embracing this now, now I tell you, this exactly what I need, I am sick of Firefox on KDE 4.2. :)

lol, this is serious. :o

Doesn't konqueror use  QT, and Webkit? I think konqueror is the slowest browser I've ever used, renders web pages 3 times slower than firefox

---

### Post by FuturePilot on 2009-03-09
> **Faolan Devyn Aodfin said:**
> From what I understand Gecko and XULrunner seem to be the same thing. Maybe Gecko is just the rendering engine for the HTML and XUL is the interface and I was just a bit confused then. But I was close.

XUL is what is used for the interface and widgets and what not. Gecko is the actual rendering engine.

---

### Post by Bios Element on 2009-03-10
> **swoll1980 said:**
> Doesn't konqueror use  QT, and Webkit? I think konqueror is the slowest browser I've ever used, renders web pages 3 times slower than firefox

Yes, It is. And it's for KDE.

---

### Post by Skripka on 2009-03-10
> **swoll1980 said:**
> Doesn't konqueror use  QT, and Webkit? I think konqueror is the slowest browser I've ever used, renders web pages 3 times slower than firefox

The problem is Qt4.4....evidently At4.5 is far faster.

PS-Konqueror uses KHTML, not webkit.

---

### Post by Dekkon on 2009-03-10
> **Skripka said:**
> The problem is Qt4.4....evidently At4.5 is far faster.

PS-Konqueror uses KHTML, not webkit.

Just what I was about to say, I heard awhile ago they were going to drop KHTML for WebKit but it never happened, so I refuse to use it because it can't render sites properly. :(

---

### Post by Skripka on 2009-03-10
> **Dekkon said:**
> Just what I was about to say, I heard awhile ago they were going to drop KHTML for WebKit but it never happened, so I refuse to use it because it can't render sites properly. :(

If you want a Qt4 native browser-your choices are either Konqueror or Arora.  That is it, really.

---

### Post by igknighted on 2009-03-10
> **Skripka said:**
> If you want a Qt4 native browser-your choices are either Konqueror or Arora.  That is it, really.

Opera 10?  If you are on 32bit at least...

---

### Post by Giant Speck on 2009-03-10
Questions:

1. **How RAM-intensive is Arora compared to Firefox?**  My main reason for asking this is because I'm trying to find a lighter browser that is based off of Firefox.  I've tried Swiftfox, which is nice and all, but hasn't budged from version 3.0.4pre1.  I've also been considering Swiftweasel, but there doesn't seem to be a version for my system.

2. **Are you able to install Firefox addons and themes using Arora?**  The ability to use Firefox addons, including WOT, Stylish, New Tab Homepage, and others is very important to me.  Also, very few Firefox themes actually theme well using my Macchiato GTK theme.  The best I have found so far is the Camifox theme.

---

### Post by sertse on 2009-03-10
Arora is more similar to a QT version of Midori, rather than anything to do with firefox...

---

### Post by Skripka on 2009-03-10
> **igknighted said:**
> Opera 10?  If you are on 32bit at least...

You'll note how I say Arch64 in my sig. ;)

---

### Post by venekirsa on 2009-03-10
I hope this Aurora bomber finally flattens IE!

---

### Post by Giant Speck on 2009-03-10
> **venekirsa said:**
> I hope this Aurora bomber finally flattens IE!

I doubt it.  As much as I don't like Internet Explorer, I seriously doubt another obscure browser is going to cut into its "market share."

---

### Post by cb951303 on 2009-03-10
> **sertse said:**
> Arora is more similar to a QT version of Midori, rather than anything to do with firefox...

gui design is almost the same :)

---

### Post by BGFG on 2009-03-10
> **Chemical Imbalance said:**
> Any way to get a 64-bit deb or do I have to compile?  Running the deb even with 32-bit libs installed still gives wrong architecture.

I tried it a while back and I run 64bit also. just compile. grab the tar.gz, extract it then read the README file. gives installation instructions. It's how i usually do it. Have fun....

---

### Post by k2t0f12d on 2009-03-10
I like it..its very nice.  Just needs and advert and flash blocker to be perfect.  =D

---

### Post by Faolan84 on 2009-03-10
You can block most ads through the hosts file:
/etc/hosts

A list of adservers is provided here:
[pgl.yoyo.org/adservers/](pgl.yoyo.org/adservers/)

That will take care of most of your ads and if you run windows several spyware related sites are blocked in that mix too.

---

### Post by OutOfReach on 2009-03-10
> **Giant Speck said:**
> Questions:

1. **How RAM-intensive is Arora compared to Firefox?**  My main reason for asking this is because I'm trying to find a lighter browser that is based off of Firefox.  I've tried Swiftfox, which is nice and all, but hasn't budged from version 3.0.4pre1.  I've also been considering Swiftweasel, but there doesn't seem to be a version for my system.

2. **Are you able to install Firefox addons and themes using Arora?**  The ability to use Firefox addons, including WOT, Stylish, New Tab Homepage, and others is very important to me.  Also, very few Firefox themes actually theme well using my Macchiato GTK theme.  The best I have found so far is the Camifox theme.

(Heads up: Talking about arora w/ stable Qt, not snapshot Qt)

TBH I think the OP was exaggerating a bit when they said it was a 'firefox clone'.

To answer your questions:
1. RAM: It is a bit lighter than Firefox, uses 72 MB with Myspace, Youtube, and the Ubuntuforums open. Considering that it does not yet support Flash, this is expected.

2. No. Plain and simple.

Arora only really resembles Firefox in the interface. That's it.

---

### Post by spupy on 2009-03-10
1. It looks like Firefox, but doesn't support its extensions?
2. Use Epiphany with WebKit. It also has "100%" Acid3 score, with some hacks I think.
3. [The hell is this?(link)]("http://picasaweb.google.co.uk/icefox/AroraScreenshots#5231439838670741538") It's an official screenshot of the program. Under linux it has OS X styled widgets? LOLWUT, again?

---

### Post by Chemical Imbalance on 2009-03-10
> **BGFG said:**
> I tried it a while back and I run 64bit also. just compile. grab the tar.gz, extract it then read the README file. gives installation instructions. It's how i usually do it. Have fun....

Thanks BGFG.  I usually try to install only .deb because I like knowing that I can easily find and uninstall through synaptic or apt if I have to.  Compiling's not hard, its just my last resort.

---

### Post by Faolan84 on 2009-03-10
> **Chemical Imbalance said:**
> Thanks BGFG.  I usually try to install only .deb because I like knowing that I can easily find and uninstall through synaptic or apt if I have to.  Compiling's not hard, its just my last resort.

Use checkinstall. It's a program that you can run during compilation to create a deb file.
Here's a small howto:

user@ubuntu$ ./configure
user@ubuntu$ make
user@ubuntu$ sudo checkinstall
DONE!

It's really that simple. Just follow the prompts when checkinstall is running and you'll be done in no time.

---

### Post by Chemical Imbalance on 2009-03-10
> **Faolan Devyn Aodfin said:**
> Use checkinstall. It's a program that you can run during compilation to create a deb file.
Here's a small howto:

user@ubuntu$ ./configure
user@ubuntu$ make
user@ubuntu$ sudo checkinstall
DONE!

It's really that simple. Just follow the prompts when checkinstall is running and you'll be done in no time.

Thanks Faolan :KS

---

### Post by k2t0f12d on 2009-03-11
> **Faolan Devyn Aodfin said:**
> You can block most ads through the hosts file:
/etc/hosts

A list of adservers is provided here:
[pgl.yoyo.org/adservers/](pgl.yoyo.org/adservers/)

That will take care of most of your ads and if you run windows several spyware related sites are blocked in that mix too.

No Windows, but /etc/hosts works great here.  Thanks!

---

### Post by binbash on 2009-03-11
I will check it out but FF3.1b also passes 100/100 acid tests.

---

### Post by zika on 2009-03-11
> **binbash said:**
> I will check it out but FF3.1b also passes 100/100 acid tests.
last time I checked (today) FF3.1=93/100, FF3.2=94/100.

---

### Post by khelben1979 on 2009-03-11
Are this Arora web browser available for my ppc architecture over here? And if it is, post the link in this thread, please.

---

