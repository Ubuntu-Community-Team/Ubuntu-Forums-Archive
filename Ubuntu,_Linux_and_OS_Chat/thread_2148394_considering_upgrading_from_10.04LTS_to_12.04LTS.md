---
title: "considering upgrading from 10.04LTS to 12.04LTS"
date: 2013-05-25
forum: Ubuntu, Linux and OS Chat
---

### Post by Capetownlad on 2013-05-25
I have using 10.04 for some time and absolutely love my system.  It was recently suggested to me that I consider upgrading. My issue with that is I really like the layout of 10.04 and what I mean is I like where to find things like having the three locations(Applications, Places and System) at the top with the drop down menus. To me everything is easily accessible from here. Would it be possible to recreate this in 12.04?

---

### Post by Irihapeti on 2013-05-25
Gnome-fallback in 12.04 gets close to it, though it doesn't have the third menu of System. The system options are at the bottom of the Applications menu.

I believe that Xubuntu can be configured to be very similar also, though I've not used Xubuntu in 12.04. (Currently running Xubuntu in 13.10)

Then there's MATE desktop. I'll leave others to elaborate on that, as I've not used it at all.

---

### Post by ajgreeny on 2013-05-25
I was also very dismayed at the loss of support for gnome 10.04 recently, but I made the jump a few weeks back when I bought a new desktop machine and moved from 32 to 64 bit OS.

I have not managed to get used to, nor like unity, which simply is not right for my way of working on a computer, so I installed Xubuntu 12.04.2, added the packages that I have to have such as Libreoffice, VLC, and others I can't think of at the moment, and very quickly fell in love with it.

I have moved to XFCE 4.10 using the ppa available for precise, which seems to work brilliantly.  If I have any problems they are very small, eg parole, the movie-player, which refuses to play any DVDs that I try it with, even though I have all the gstreamer codecs, the w64codecs, libdvdcss2, and just about everything else I can think of installed.  However that is of little consequence to me as I have VLC as my main media player, and have now removed parole as it seems quite useless.

Xubuntu is now so much more configurable than it used to be, as far as I can remember, and you can indeed make it look just like gnome 2 if you want; a quick search of [www.googlubuntu.com]("http://www.googlubuntu.com") will find several suggestions, so here you go.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=xfce+look+like+gnome+2&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=xfce+look+like+gnome+2&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by ibjsb4 on 2013-05-25
Yep, gnome classic (fallback) is a pretty good knock-off of the old desktop.  If you want to give it a spin ..
```

sudo apt-get install gnome-session-fallback
```

[Here's some tips]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

---

### Post by craig10x on 2013-05-25
If you ever used a mac computer, then you might like unity desktop because it is very mac like with it's dock (although on the left instead of the bottom) which can autohide of course, global menu and search that is like what the mac has also) if you don't like docks then one of the other suggestions might meet your needs...

I will say that many who initially either hated or wasn't thrilled with unity (including myself) came around after spending a few weeks with it...i was lukewarm at first and now absolutely love it!
They key is to put your favorites and most used apps on the dock for quick easy access and just use the search for less frequent apps...

Unity is not highly configurable but you can shrink the size of the icons (i do...to around 38 pixels) autohide it, control the "sensitivity" and add the workspaces into it (all from the appearance section of the system settings)...

---

### Post by martinr on 2013-05-25
I've upgraded to Ubuntu 12.04 LTS one year ago and I've really tried Unity, but I keep finding it extremely annoying. I also tried the classic look and tweaked the heck out of it, but I keep running into bugs, missing menu items, failures, etc. etc. etc.

I like Ubuntu a lot, but because of my great annoyance with Unity, I'm contemplating the Mint distro or Xubuntu in order to get a likeable desktop environment again. 

Ubuntu 10.04 was great and I would have hapily continued using it, but it has run out of support now. :(

---

### Post by ibjsb4 on 2013-05-25
> **martinr said:**
> I also tried the classic look and tweaked the heck out of it, but I keep running into bugs, missing menu items, failures, etc. etc. etc.

Of course mileage will vary, but I find Classic 12o4 (with meticily window manager) to be quite solid.

---

### Post by Capetownlad on 2013-05-25
Thanks for all the advice here. I'll start reading

---

### Post by stalkingwolf on 2013-05-25
i just install the Mate desk top and get all i want. there were 3 aplets for the panel that i have come to want and they are available in mate.

---

### Post by MadmanRB on 2013-05-25
I say try unity and if its not for you just install xubuntu.
XFCE is very much like gnome2

---

### Post by martinr on 2013-05-25
> **ibjsb4 said:**
> Of course mileage will vary, but I find Classic 12o4 (with meticily window manager) to be quite solid.
It is stable enough, but it's a lot of little things. I didn't keep track, but I'll try to recall:
[LIST]
[*]Some of my favourite taskbar applets haven't been ported.
[*]There are significantly less panel applets.
[*]I can't tweak the top level menu structure
[*]Some things have been hidden away or removed.
[*]It is much less customizable
[*]It consumes a lot of resources
[*]I'm missing menu items
[*]Things are lost
[*]Integration of apps with the desktop sometimes is flaky or not working.
[/LIST]

I still keep running into annoyances a year onward. It's an annoying mess that keeps accumulating clutter. I'd like something that just works without the never ending annoying distractions. I'd like something that just worked like in Gnome 2 in Ubuntu 10.04.

Maybe other people can add things to this list that I missed?
Just try it, keep score and report back here.

---

### Post by ibjsb4 on 2013-05-25
> **martinr said:**
> It is stable enough, but it's a lot of little things. I didn't keep track, but I'll try to recall:
[LIST]
[*]Some of my favourite taskbar applets haven't been ported. 
[*]There are significantly less panel applets. 
[*]I can't tweak the top level menu structure 
[*]Some things have been hidden away or removed. 
[*]It is much less customizable 
[*]It consumes a lot of resources 
[*]I'm missing menu items 
[*]Things are lost 
[*]Integration of apps with the desktop sometimes is flaky or not working. 
[/LIST]

I still keep running into annoyances after a year.

Just try it and keep score for us.
Can other people add things to this list which I missed?

Im sorry, but that sounds more like a rant.  I would think after a year you would of moved on to something you liked.  Fire back at me if you want, but I do not intend to highjack this thread with any further discussion that does not come from the OP :)

---

### Post by Ender Shadow on 2013-05-25
MATE is an *awesome *desktop. Vastly superior to Unity, in my opinion. It has much more customizability, and it has all of GNOME's applets.

---

### Post by LordDelta on 2013-05-25
I can't speak to MATE or Cinnamon, but I had to switch to KDE.

I don't think either system was usable, or even around, when I switched, and I was getting tired of hoping UI's and having problems.

That said last time I tried Unity on a system that was set up for it, it was quite nice, I just wouldn't want to start tweaking it myself.

But yeah, things are pretty good here otherwise in 12.04 land.

---

### Post by Capetownlad on 2013-05-26
I would prefer to try live distros. to see what they look like because I have a fair amount of fiddling to do once installed. I use a tv card with Kaffeine and cctv card with zoneminder and the latter can be a challenge to set up. 
The closest solution I can find is Debian. I have this on an old laptop which I use for emergencies but can't seem to get the latest release 7 to work on a live usb?

---

### Post by Capetownlad on 2013-05-26
If anybody has any screenshots of the desktop showing their workaround to this, it would be appreciated?

---

### Post by cacycleworks on 2013-05-26
Ubuntu's shift away from Gnome actually made me switch to Windows 7. :P  Recently I re-discovered Linux Mint. I just installed Mint 15 Cinnamon Beta on my desktop computer at work and am very pleased. Everything works and it feels like *Ubuntu should feel like* to me. It installed easily and boots quite handily on a Core i3. I have Mint 13 on my latest dual boot laptop (with Windows 7) and Mint 15 seems more snappy to me. 

Ultimately, my favorite linux was kubuntu with KDE 3.51. :/  It had been downhill ever since, but Mint has brought me back with its somewhat stability. I really tried to like the new Ubuntus, even sticking with 12.10 for a looooong time. Ultimately, I had my regular desktop and our shop's "Adobe+CAD" computer with Windows 7 next to it. I normally went to the Windows computer for day-to-day stuff until I had to work on teh website or the server, when I appreciated linux's ease of connectivity with ssh and sshfs.

I was a linux die-hard until KDE4 and then Unity switched me back to sanity and Windows 7. Thanks and praise to Mint for being normal, sane, and consistent.

:D Chris

---

### Post by mastablasta on 2013-05-26
> **cacycleworks said:**
> 
...Ultimately, my favorite linux was kubuntu with KDE 3.51. :/  It had been downhill ever since, ...

i never used 3.51 KDE but what is so downhill at currect LTS Kubuntu for example? i know i have some hardware issues but they are not KDE (and probably not specific Kubuntu) problems. system is fast, responsive, menues make sense and it does not crash easilly. what more could you want?

---

### Post by cacycleworks on 2013-05-26
> **mastablasta said:**
> i never used 3.51 KDE but what is so downhill at currect LTS Kubuntu for example? i know i have some hardware issues but they are not KDE (and probably not specific Kubuntu) problems. system is fast, responsive, menues make sense and it does not crash easilly. what more could you want?

Ha, being able to run programs! All the new GUIs are so occupied with looking slick that I can't find how to just DO stuff. KDE3 let me connect anything to anywhere so easily! Webserver in canada, file server at work, ftp here, whatever. KDE3 also had very strong inter-program connectivity. I call it "the computer should know that" and it did. KDE4 came along and they broke that infrastructure along with changing where every option was and how everything worked. khotkeys being removed really got me, since I had a few dozen productivity macros for all the work email I do.

Going from KDE3 to KDE4 made me feel like a moron and lost. So off to Gnome, which felt dumbed down, but I learned ssh, scp, and sshfs and was able to get back to productivity -- especially once I realised autokey was a rough fullfillment of khotkeys (another thing lost in KDE4). The 11.xx ubuntus just wouldn't run on my hardware, so I didn't do anything for a few years. Tried 12.04 and just couldn't come to grips with unity launcher thing always thwarting how I work.

KISS ... keep it simple, software! Mint is the homecoming to linux I haven't felt since finding KDE3 upon my reentry into linux from the 90s...

---

### Post by mastablasta on 2013-05-26
well i haven't used the first couple of KDE editions due to bad reviews, but these ones lately have plenty of functions. i guess they are adding them... looks preety similar to windows to me.oh i don't use the K launcher (there is also homerun, netbook plasma and touch interfaces). instead i use classic. seems all stuff is preety easy to find and form the looks of it it seems classic menu is the KDE 3 interface.

---

### Post by Capetownlad on 2013-05-27
Thanks for the ideas here. I have had a look at a few suggestions and decided that if and when I leave my beloved 10.04 LTS I will probably go to Debian which meets my needs.

---

### Post by martinr on 2013-05-27
> **Capetownlad said:**
> I will probably go to Debian which meets my needs.
I'm curious, what made you decide to go for plain Debian?

I've invested a lot of time in configuring and tuning the Classic look in gnome 3 to resemble gnome 2. I thought it would just take some getting used to, but as ibjsb4 correctly points out, I've been tolerating the little annoyances for much too long. I'm not looking forward to a new install and all the data migration and nasty reconfiguration again at all (and the risk of killing the software on my machine). That's why I try to stick with the LTS releases. Heck I even recognised myself in cacycleworks' posting. I also find myself booting straight into Windoze 7 and only occasionally into Ubuntu 12.04 any more (to my dismay). Whereas on my laptop I boot straight into Ubuntu 10.04 and rarely into Windoze, but 10.04 desktop has EOL'ed now so I also need to migrate. Please enlighten us to the reasons for your decision to go with plain Debian?

and what made you shy away from:
Xubuntu
Mate
Mint
Others

---

### Post by groggin on 2013-05-27
i'm multibooting 3 flavs of linux w/winxp and 7, the most reliable of all is artistx 1.0 (ubuntu 10.4 lts, gnome II) and i will keep that os untill it crumbles from lack of support. biggest problem i have with that os is in there i cannot play a blue ray disc (= no problem) i'm also running artistx 1.4 (ubuntu 12.10 upgraded to 13.4  mate) i installed the mate desktop, (it was very buggy in the early versions, but it's good and solid now)
i'm enjoying refining my new system, but there are several issues with it that need debugging

---

### Post by prusswan on 2013-05-29
> **Capetownlad said:**
> Thanks for the ideas here. I have had a look at a few suggestions and decided that if and when I leave my beloved 10.04 LTS I will probably go to Debian which meets my needs.

Mint would be worthy of serious consideration if you do not wish to contend with the 12.04 LTS and want to enjoy the same Gnome 2 experience that is light on system resources. I am still on 12.04 but probably would move on to another distro before the next LTS comes, even as it stands now my config is very far from the defaults, and gnome-session-fallback will not be properly maintained or exist in the newer releases.

---

### Post by buzzingrobot on 2013-05-31
I'm currently running MATE on 12.04 LTS and it's quite nice. Looks and feels like Gnome 2.  Dunno if you can duplicate 10.04LTS themes. though, if that's really important for you.

Disregard assertions that Unity is like OS X.  I've used Macs for years and using Unity is not at all like OS X.  OS X has a very configurable dock; Unity has a not very configurable dock.  Beyond that, they're different, and OS X is more capable.

---

### Post by craig10x on 2013-05-31
I'd agree that the Mac OSX dock is very configurable but unity is a dock even if less configurable...interestingly, my friend who has an imac placed his osx dock on the left side of the screen just like unity because he likes it better that way :D

I think it would nice if we had the option of putting unity on the bottom area and smaller in width (more like mac's dock or the cairo dock)...

The reason why you always see me comparing unity to the mac desktop experience is because like the mac it has a dock, global menu and the dash search reminds me of the search int the mac...that is why i call it a mac-like experience...i ran an mac for a year between dumping windows and discovering linux, so i am well familiar with the mac desktop...

---

### Post by buzzingrobot on 2013-06-01
Unity's lenses are reminiscent of the Spotlight searching built into OS X for some years now, but I think Apple's implementation is much better.  They don't rely on search as the intended way for users to find and launch executables, as Unity does.  Spotlight is also much less intrusive compared to the 25 percent of screen size the lenses soak up.

Search as used in Gnome Shell and Unity is an attempt to deal with the complexity of modern desktops.  Menus are sufficient for finding and launching a limited number of executables, but fall down beyond that.  In theory, search should work just fine.  In reality, current implementations have to assume users have a good idea what they are searching for.  That's more often than not a bad assumption.

Underneath the GUI, OS X is a more capable and versatile desktop platform than Ubuntu, with a greater variety of third-party apps leveraging those capabilities.

---

### Post by craig10x on 2013-06-01
Agree...i loved my Mac...just didn't like the high priced software....now if you could use osx on any windows computer....well, then i think i'd be tempted back :D
As it is, i guess i'll stay with ubuntu with unity....at least it reminds me a bit of what it was like...LOL

---

