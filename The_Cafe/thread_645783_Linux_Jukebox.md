---
title: "Linux Jukebox ?"
date: 2007-12-20
forum: The Cafe
---

### Post by mips on 2007-12-20
Here is the scenario. Have a old PC (4-5yrs old) that needs to be converted into a music player for a restaurant. Needs to be lean and very simple to use by any illiterate tom, dick & harry (sally to). Will have a normal keyboard/mouse and lcd display. Will also upgrade HD and ram if required.

What would you people recommend ?

---

### Post by Whiffle on 2007-12-20
Two options:

1)Run it headless and run mpd on it, then control it from whatever other computer you have around.  You could park it in a closet, make a playlist for it, and let it go.

2) Do a desktop install, create a custom Xsession that only runs the music player of your choice (i would suggest Amarok).  You can administer it by logging into gnome or kde, and then log out and run the custom session, which would make it kind of a kiosk setup.

---

### Post by mips on 2007-12-20
1 is not an option.

I though of 2 but would like something even simpler if possible. Amarok did come to mind though and I might still even go that route.

---

### Post by Whiffle on 2007-12-20
AmarokLive? 

[http://linux.softpedia.com/progDownload/amaroK-Live-Download-5516.html](http://linux.softpedia.com/progDownload/amaroK-Live-Download-5516.html)

---

### Post by adam.tropics on 2007-12-20
Rhythmbox has a very simple 'Party Mode' in the view menu which I guess could be used for such a thing. Less bulk (features) than Amarok, but functional never the less.

---

### Post by koleoptero on 2007-12-20
I'd go for xubuntu with bmpx for the music.

---

### Post by adam.tropics on 2007-12-20
> **koleoptero said:**
> I'd go for xubuntu with bmpx for the music.

Like the look of bmpx. Plus I did get a slight laugh from their [site's front page]("http://bmpx.beep-media-player.org/site/BMPx_Homepage") advertising of reasons to use bpmx...

> [LIST]
[*] You want to be able to use the player even when totally drunk and otherwise drugged, without constant crashes or weird behaviour that actually requires you to **think**?[/LIST]

.....gotta be ideal for a restaurant then.

---

### Post by smartboyathome on 2007-12-20
I would say use GeeXBoX. It is small, loads into RAM, and doesn't take up any hard drive space or cd drive.

---

### Post by boast on 2007-12-20
linux is very customizable, im sure theres a custom linux, with no desktop-evironment, used only for playing music. With just the right modules loaded, giving it ultra-fast booting speed.

edit: well there we go, GeeXboX . lol

---

### Post by blithen on 2007-12-20
Haha. Why not go with a command line only install then run CMUS?
Very easy to get used to.

---

### Post by mips on 2007-12-21
> **blithen said:**
> Haha. Why not go with a command line only install then run CMUS?
Very easy to get used to.

In that case I would much rather install XP with WMP.

Mouse driven would be a requirement.

I think I'm just going to do a server+kdebase+amarok(or one of the other options here after testing) install.

---

### Post by gn2 on 2007-12-21
With PCLinuxOS you can easily set it to auto-login on a user account, then customise the desktop to have just one icon called Jukebox, linking to Amarok.
I have a very similar set-up in my living room, a Dell GX110 Optiplex SFF sits where my CD player used to be and I have a small 800x600 screen that I got cheap on ebay.
Probably doesn't need to have a keyboard connected, because all tunes are selected using the mouse.
My keyboard is tucked down the back out of sight and only gets used very rarely.

---

### Post by bobbob94 on 2007-12-21
I've set up a music system in a similar situation where it needed to be as idiot proof as possible, and after sitting various people in front of it and going "use that" and giving them no help and seeing what happened i finally settled on bmpx as the best option. i just set up a limited user account, deleted the top and bottom panels, added a launcher icon for the media player and a read only music folder on the desktop, and changed the background to a blank screen with some simple instructions on how to use it across the top. This was shortly after Dapper came out and its been in daily use since and still running fine!

---

### Post by mips on 2007-12-21
> **bobbob94 said:**
> I've set up a music system in a similar situation where it needed to be as idiot proof as possible, and after sitting various people in front of it and going "use that" and giving them no help and seeing what happened i finally settled on bmpx as the best option. i just set up a limited user account, deleted the top and bottom panels, added a launcher icon for the media player and a read only music folder on the desktop, and changed the background to a blank screen with some simple instructions on how to use it across the top. This was shortly after Dapper came out and its been in daily use since and still running fine!

Sounds good. I'm actually thinking of using Linux Mint on it and removing all the stuff thats not needed and as far as I know it already comes with amarok but I will look into bmpx.

---

### Post by smartboyathome on 2007-12-21
> **mips said:**
> Sounds good. I'm actually thinking of using Linux Mint on it and removing all the stuff thats not needed and as far as I know it already comes with amarok but I will look into bmpx.

Have you checked out GeeXBoX? I think it meets all your requirements.

---

### Post by hhhhhx on 2007-12-21
I use vlc for all my video's because its fast and can play pretty much anything

and i currently use amarok for music, but i used to use songbird, wich is a fairly nice player

---

### Post by K0va on 2009-01-10
My suggestions r 
1. if u dont need display try installing some music player which u can control from terminal and lirc. so u can use any remote controler and i would add small lcd display 2x16 
2. if u realy need to have display u can install freevo, and disable tv and movie plugins, live only plugins for music, u can also use lirc. 
I would install some ftp server so u can send from other pc files directly to hdd,  u can control it from any other pc over http ( it works i tryed  ), and what is most important it is very easy to set up everything on ubuntu, boot is fast enough (for me).

---

### Post by Xzallion on 2009-01-10
> **K0va said:**
> My suggestions r 
1. if u dont need display try installing some music player which u can control from terminal and lirc. so u can use any remote controler and i would add small lcd display 2x16 
2. if u realy need to have display u can install freevo, and disable tv and movie plugins, live only plugins for music, u can also use lirc. 
I would install some ftp server so u can send from other pc files directly to hdd,  u can control it from any other pc over http ( it works i tryed  ), and what is most important it is very easy to set up everything on ubuntu, boot is fast enough (for me).

1.They already stated they need a display, and it will be mouse driven.
2.freevo has more features then is being requested, but is an option just as MythTV and other media systems are.  But I believe they are looking for an application with a very simple interface that doesn't require much resources.

As an aside, please spell "you" you instead of "u".  It really does make things easier to read on a forum. Sorry to nitpick.

---

### Post by Twitch6000 on 2009-01-10
Wait will you be allowing them to download music?

If not just set up something like banshee or rythmbox and edit whatever settings are needed.

If you are needing music downloaded at the same time, Amarok comes to mind.

---

### Post by teet on 2009-01-10
December 21st, 2007

-teet

Edit:  so what did you finally decide on mips?

---

### Post by Pablo33 on 2011-09-22
...we didn't know, but thanks to everybody, because comments helped me to see the light. 

I think nowadays freevo should be enough almost for anyone. Simply, versatile and pretty configurable.

... and once again, something that made me love linux a little more!. :guitar:

---

### Post by nothingspecial on 2011-09-22
Lay down my dear thread, lay down and take your rest.......

---

