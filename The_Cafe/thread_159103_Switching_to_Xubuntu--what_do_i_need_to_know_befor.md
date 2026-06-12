---
title: "Switching to Xubuntu--what do i need to know before hand?"
date: 2006-04-12
forum: The Cafe
---

### Post by DigitalDuality on 2006-04-12
I'm currently running Kubuntu.  But as i've grown tired with the short comings of both KDE and Gnome, i'd like to try something different.

My question is, is there anything i should be aware of before going this route? 

Other than speed, what are some of the benefits and downfalls of the Xfce DE?

Would i be better off doing something like Fluxbox?  I'm pretty much looking to escape both KDE and Gnome, but i want less headaches, not more.

---

### Post by Darkriser on 2006-04-12
why not to install xfce to your existing environment to test it out?

just run 'sudo apt-get install xubuntu-desktop' from console and select XFCE at login screen.

---

### Post by stuporglue on 2006-04-12
> My question is, is there anything i should be aware of before going this route? 

Just that it rocks. :-) I've switched to Xubuntu and it's great. The Dapper version is much better than the Breezy version though, in my opinion. When the Breezy version came out, it was a pretty new project, and wasn't really polished. The Dapper version however is great!

Darkriser is right though, Install xubuntu-desktop and try it out before switching full time.

---

### Post by DigitalDuality on 2006-04-12
lol Dapper scared me.  I used Dapper for a bout a month.  Mainly just Flight 4 and during one update my entire X crashed and i never figured out how to restore it.  Part of that is my own ignorance i'm sure.

---

### Post by stuporglue on 2006-04-12
> lol Dapper scared me. I used Dapper for a bout a month. Mainly just Flight 4 and during one update my entire X crashed and i never figured out how to restore it. Part of that is my own ignorance i'm sure.

It does that from time to time. :-) 

If you want to try Xubuntu out on Breezy, just keep in mind that there are vast improvements comming once Dapper hits. Breezy Xubuntu was good, Dapper is just so much better. 

There's talk that Xubuntu live CDs (Dapper) will be built soon. There will probably be a "daily-live" section on this page when that happens: [http://cdimage.ubuntu.com/xubuntu/](http://cdimage.ubuntu.com/xubuntu/)

---

### Post by Kindred on 2006-04-12
Indeed, the xfce you'll get with Dapper is much better than the 4.2 you'll get with Breezy.  I've been using the latest xfce lately, and like it a lot.

---

### Post by bonzodog on 2006-04-12
Yeah, Install Xubuntu Dapper off it's ISO - if you have an nvidia Graphics card and can get the composite extensions enabled, then Xubuntu really rocks.

---

### Post by DigitalDuality on 2006-04-12
I'm not going to be able to burn cd's for a while.

could i just install the Ubuntu Dapper Flight 4 disc as a server and install xfce on to that and get the same experience as the Xubuntu ISO??

---

### Post by DigitalDuality on 2006-04-12
speaking of burning cds, i've come across where xfce doesn't auto-mount removable media.

Anyone have success with cd-burning with xubuntu?

---

### Post by Stormy Eyes on 2006-04-12
[QUOTE=DigitalDuality]I'm not going to be able to burn cd's for a while.

could i just install the Ubuntu Dapper Flight 4 disc as a server and install xfce on to that and get the same experience as the Xubuntu ISO??[/QUOTE]

Yes, I think you could. Just do **sudo apt-get install xubuntu-desktop**, and apt should do the rest for you.

---

### Post by transactionlogfiller on 2006-04-12
[QUOTE=DigitalDuality]speaking of burning cds, i've come across where xfce doesn't auto-mount removable media.

Anyone have success with cd-burning with xubuntu?[/QUOTE]

Yes, but I cheated. I installed gnome-volume-manager and gnomebaker.

---

### Post by Kindred on 2006-04-12
[QUOTE=DigitalDuality]speaking of burning cds, i've come across where xfce doesn't auto-mount removable media.

Anyone have success with cd-burning with xubuntu?[/QUOTE]

There are a few ways to automount, with ivman or gnome-volume-manager for example. 

For cd burning I use Graveman.

---

### Post by mips on 2006-04-12
I just installed xubuntu desktop a few minutes ago and it is pretty cool. Much faster than KDE. Looks a bit gnomish though.

---

### Post by roderikk on 2006-04-12
I also just installed xfce4 just to give it a try. However I can't seem to get the File Manager (thunar) to run. When I click on it nothing happens.

Hmm... just figured it out while typing the above... Thunar wasn't installed. I've just been using this for an hour now but it feels really snappy and fast.

Also the automount just works for me. I did install xcfe from gnome so it might work because gnome-volume-manager is already installed...

Are there any other pros over gnome on a (very) fast pc? Where can I find some nice themes?

---

### Post by DigitalDuality on 2006-04-12
I also got it installed, and i'm suprised.  I mean nothing i hate about it by any means but people have been going on and on about how fast it is.  

And umm.. both Gnome and KDE are faster.

---

### Post by stuporglue on 2006-04-12
> I also got it installed, and i'm suprised. I mean nothing i hate about it by any means but people have been going on and on about how fast it is.

And umm.. both Gnome and KDE are faster.

That's interesting. Did you play with it much? It's not the king of speed, but it uses less resources than Gnome or KDE, so you should notice improvements. 

Did you notice anything specific that was slower than G/K? How about program launch times, login times, etc? 

On my system neither Gnome nor Xubuntu are poor performers, but login seems quicker to me, and it seems more responsive when I have a lot of programs open. 

On older systems (~350MHz, 256 Mb RAM), I notice definate improvements with Xubuntu over Gnome.

---

### Post by DigitalDuality on 2006-04-12
My boot time is insanely fast.   Apps open at about the same speed as Gnome.  

I'm having alot of problems getting gnome-volume-manager to set up auto mounting.  No idea what to do after install.

Also can't play any audio out of amaroK.  And having problems installing most of the RestrictedFormats.  Basically java, flash,...and i forgot where to get msfonts from.

Got the composite manager working and things seem a little smoother now visually speaking.

I installed it off a Ubuntu Dapper flight 4 disc and did a dist-upgrade before installing xfce.

---

### Post by stuporglue on 2006-04-12
> I'm having alot of problems getting gnome-volume-manager to set up auto mounting. No idea what to do after install.

If you're on Dapper, you don't need to. Just open up Thunar, and click the icon of your disk to be mounted.

> Also can't play any audio out of amaroK. And having problems installing most of the RestrictedFormats. Basically java, flash,...and i forgot where to get msfonts from.

Search the forums for those. They're installed exactly the same as in U/Kubuntu. If you're the EasyUbuntu/Automatix types, those will work as well.

> Got the composite manager working and things seem a little smoother now visually speaking.

Great.

> 
I installed it off a Ubuntu Dapper flight 4 disc and did a dist-upgrade before installing xfce.

Did you install xfce, or xubuntu-desktop? xubuntu-desktop is the one you want. If you didn't grab it before, just do it now. Xubuntu-desktop in dapper will (should) have automounting working. I didn't do anything to make it work here, and it works fine. Xfce on the other hand probably doesn't configure it for you.

---

### Post by DigitalDuality on 2006-04-12
i did xubuntu-desktop.  I'll see what else i can find.

---

### Post by 3rdalbum on 2006-04-13
I'm on a low-memory system, and when I experimented with Xubuntu I found it much faster than GNOME. This was due in part to it using less memory and therefore not swapping data to and from disk so much.

---

### Post by DigitalDuality on 2006-04-14
lol i can't seem to get a decent music organizing player to work

Banshee has failed, Listen has failed, amaroK won't play at all.  Rhythmbox has failed.  

I'm gonna stick it out though, i'll get one of these damned things to work.

I got my video working, but i have to turn off composite effects in order to do so.  I can't life without that i guess.

---

### Post by Zodiac on 2006-04-14
[QUOTE=DigitalDuality]lol i can't seem to get a decent music organizing player to work

Banshee has failed, Listen has failed, amaroK won't play at all.  Rhythmbox has failed.  

I'm gonna stick it out though, i'll get one of these damned things to work.

I got my video working, but i have to turn off composite effects in order to do so.  I can't life without that i guess.[/QUOTE]

Make sure you are starting KDE and GNOME apps when you start XFCE... and the speed will diminish if you have to boot both of those btw...

P.S. - I could not get XFCE to auto mount my DVD/CD-RW removable drive at all on my IBM T30... 
 
Just a heads up.

---

### Post by stuporglue on 2006-04-14
> lol i can't seem to get a decent music organizing player to work

Banshee has failed, Listen has failed, amaroK won't play at all. Rhythmbox has failed.

I'm gonna stick it out though, i'll get one of these damned things to work.

Try Quod Libet.  [http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)

---

### Post by tom-ubuntu on 2006-04-14
What are Xubuntu-Users using as their default browser? I think Firefox is a little bit to heavy for an old machine. Any other recommendations?

---

### Post by bonzodog on 2006-04-14
[QUOTE=stuporglue]Try Quod Libet.  [http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)[/QUOTE]

Quod Libet is in the repos, and it's what I am now using with my installation. I was using Xmms.

---

### Post by DigitalDuality on 2006-04-14
[QUOTE=tom-ubuntu]What are Xubuntu-Users using as their default browser? I think Firefox is a little bit to heavy for an old machine. Any other recommendations?[/QUOTE]

Definatley not a full featured browser, but if you're looking for just the basics try Dillo.


[http://www.dillo.org/](http://www.dillo.org/)

---

### Post by LordMau on 2006-04-15
[QUOTE=tom-ubuntu]What are Xubuntu-Users using as their default browser? I think Firefox is a little bit to heavy for an old machine. Any other recommendations?[/QUOTE]

Try opera

---

### Post by vendetta red on 2006-04-15
Ok, I just installed xubuntu, and there is one thing that bugs me. Where in the heck did they stick the trashcan? It says permanently deletes files if I choose to delete them.....does that mean there is no trashcan? What kind of modern desktop doesn't have idiot-proof protection like a trashcan?

---

### Post by 5-HT on 2006-04-15
[quote=vendetta red]Ok, I just installed xubuntu, and there is one thing that bugs me. Where in the heck did they stick the trashcan? It says permanently deletes files if I choose to delete them.....does that mean there is no trashcan? What kind of modern desktop doesn't have idiot-proof protection like a trashcan?[/quote] 
I don't think there is one.

---

### Post by vendetta red on 2006-04-15
[QUOTE=5-HT]I don't think there is one.[/QUOTE]

well, thats....thats.....just weird.

---

### Post by 3rdalbum on 2006-04-16
[QUOTE=vendetta red]well, thats....thats.....just weird.[/QUOTE]

I don't think so. How many times do you look in the trashcan and think "Hey, I didn't mean to put that in there!" I've only done it once on Ubuntu.

How many times do you put something in the trashcan then immediately empty the trash? Almost every time!

I didn't even notice that XFCE doesn't have a trashcan.

---

### Post by dannysauer on 2006-04-18
[QUOTE=vendetta red]well, thats....thats.....just weird.[/QUOTE]

It's weird that someone would hit "delete" when they didn't want to delete something, yet.  And it's weird that someone who does that often wouldn't have a backup solution in place yet. :D

Here's a howto that the above weird people may want to write on a post-it (in case they delete their bookmarks)...
[http://tldp.org/HOWTO/Ext2fs-Undeletion.html](http://tldp.org/HOWTO/Ext2fs-Undeletion.html)

---

