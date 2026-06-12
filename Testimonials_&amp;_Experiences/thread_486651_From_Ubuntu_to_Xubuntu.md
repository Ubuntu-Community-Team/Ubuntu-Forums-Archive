---
title: "From Ubuntu to Xubuntu"
date: 2007-06-28
forum: Testimonials &amp; Experiences
---

### Post by Jouke74 on 2007-06-28
There are a some things that I want from my desktop, these are quick responsiveness, easy access , transparent windows when I move them around (so I can see where they land) and no crashing of programs... 

For the last half-year I have been using Ubuntu (Gnome + XGL server + Compiz) extensively and about some things (many have become worse in Feisty) I was not too happy. Programs failed to start, lack of responsiveness, lots of programs + libs preinstalled and resulting memory + disk loss. The Gnome foot logo clearly stands for a large footprint disk and memory wise...

After seeing some review of XFCE 4.4 I thought why not to try Xubuntu instead, since it has transparency by default and less things are installed to begin with. I have to say, I am really happy I made this switch. 

Some findings which may interest people:

> For windows transparency the "Vesa driver + composite from XFCE" is JUST AS FAST as the "Restricted FGLRX driver + XGL-server + composite from XFCE" (X1600 Ati card). This surprised me a lot. The XGL server is the bottle neck when looking at the processes. Using the Vesa driver saves 40(!) mb of internal memory and ironically I get equal performance. It also means that tinkering around with any video settings, XGL servers, startup scripts etc belongs to the past.

> Response of everything increased drastically. Program startup time reduced, system startup time smaller, inlog time reduced, closing time reduced.

> Memory use is about half of what gnome uses (programs only not cache). I sometimes run programs which need 1.5-2 GB so this is an issue.

> I have not found any serious loss of DE functionality as compared to the Gnome desktop, but it took me some time to find everything.

Issues:
> I deleted openoffice Word with synaptic. This affected the font cache, and as a result  slowed everything down drastically. "Touching" all of the affected directories and a "sudo apt-get autoremove" (thanks forum) restored everything nicely as it was supposed to be.  

> If you want to use multimedia (sound, video, codecs etc.) you are better of with Ubuntu (IMHO). Xgine and mplayer failed to do anything on my machine. For me this is no problem as I am not using linux for multimedia (but dual boot windows).

> I removed the pcspkr module to get rid of the login Beep (very annoying).

> Menu editing is not easy in XFCE.

> Somehow my fonts in Firefox became very big. After adjusting a DPI setting in"about:config" this was solved as well (thanks forum again). 

Overall I am more happy, and I think that naming "Xubuntu" as being the distro for less powerful computers is severely underrating it's full potential. Thanks Xubuntu team, :D

PC Specs: AMD 4200 X2, 2 GB 3200 Twin Corsair, 74 GB WD raptor, 250 GB WD Caviar, 2 x DVD burner, ATI X1600, Asus SLI premium.

---

### Post by weblordpepe on 2007-06-28
Good post.

Yeah I installed IceWM and boy what a difference. The split second I hit enter key after typing my login/password, the desktop is there.

Im on a 1.6ghz pentium M. Really aye it just doesnt load - it just goes click! And its there. AWESOME!

---

### Post by buntunub on 2007-06-28
This thread is pretty good thus far but, for Fiesty -

1. How to install Xubuntu over Ubuntu?

2. How to then remove Ubuntu (and all GNOME libs, extra files, etc etc) safely, without losing any data contained within my /home, or /etc, or /dev

3. Final goal to basicly migrate to a pure Xubuntu whilst keeping my current tailorization that I have so far made on Ubuntu.

I got that whole "sudo apt-get install xubuntu-desktop" thing. So after that do I then "sudo apt-get remove ubuntu-desktop" ? And will doing that keep my system files intact (while at the same time removing GNOME)?

---

### Post by weblordpepe on 2007-06-29
As to my understanding, I think you go apt-get remove gnome-desktop.

---

### Post by Jouke74 on 2007-06-29
I did a clean Xubuntu install after saving my important files from the home directory... Sorry about not writing that.

 I think if you change then it's better to do a reinstall of everything, because lots of stuff is not installed with Xubuntu which is installed with Gnome. Including lots of stored config files + libs etc. It will take a lot of time to clean everything out in detail. Of course, this depends also a lot on which programs you use and the amount of tweaking you have already done.

It was also written as a statement, not as a complete tutorial to install Xubuntu instead.

---

### Post by buntunub on 2007-06-29
> **weblordpepe said:**
> As to my understanding, I think you go apt-get remove gnome-desktop.

What about "sudo apt-get remove ubuntu-desktop"? Would that mess up my settings enough that doing an apt-get remove gnome is more appropriate?

I apt installed xubuntu last night. I now have both gnome and xfce and ALL my setups migrated over to the xfce login! Quite slick IMO. I can even choose between thunar and nautlius and that is kinda nice, although nautilus is just god aweful slow :(

So I guess the final results of this are that with both gnome and xfce setup, you can migrate settings between the two no problem (same /home, /etc, /dev, /media, etc..), but now you also have dependant files for BOTH setups -- quite the bloat! It would be heaven if I could just remove my ubuntu-desktop (and all GNOME dependancies) but not lose my /home or setup files that are not dependant on gnome. I am going to try this tonight. IE. the whole remove ubuntu-desktop thing, and then do a deep search to see if that left behind a bunch of garbage files.

---

### Post by weblordpepe on 2007-06-29
Oh yep. Yeah I meant to put a sudo infront of that. I haven't uninstalled the gnome-desktop yet on Ubuntu. I don't intend to but I am very much liking icewm.

---

