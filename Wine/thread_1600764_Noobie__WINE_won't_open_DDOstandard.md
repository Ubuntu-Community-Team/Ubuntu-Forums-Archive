---
title: "Noobie ? WINE won't open DDOstandard"
date: 2010-10-19
forum: Wine
---

### Post by brndndvr on 2010-10-19
Hey everyone,
I just got ubuntu 10.10 (new as of yesterday) and I'm having trouble getting DDO to download.  Here's what happens:
When I go to their website to download ddo standard it says I have chosen to open ddostandard.exe, so I tell firefox to open it with wine windows program loader. It then says "blocked because it's a .exe" so I go to my downloads->properties->permissions->allow executing file as program. 
From there, I double click the download and it asks if i'm sure I want to launch ddostandard.exe.  I say 'ok', and then nothing at all happens.  

I realize I am a total noob, but if anyone can point me in the right direction, I would really appreciate it. I'm trying to get away from the evil microsoft empire, which requires a lot of computer knowledge I frankly don't have yet :)

---

### Post by Chameco on 2010-10-19
Are you trying to execute right from firefox? If so, you might want to download it to a folder then right click-run with wine.

---

### Post by spydeyrch on 2010-10-19
Hello!! Welcome to the forum and welcome to Ubuntu. :)

First off, what is DDO? 

-Spydey :KS

---

### Post by brndndvr on 2010-10-19
:P Thanks for the replies and the warm welcome from Spydey!
I knew I'd leave out a few details. I hastily wrote that post about 2 minutes before class started.  DDO is an online rpg game that is supposedly compatible with ubuntu if you use wine.  Like I said, I'm a total noob and this is probably a bit ambitious for my first real attempt at doing anything with this OS, but I prefer baptism by fire - I learn more that way.

Specs, like I previously mentioned, I'm using Ubuntu 10.10.  I am not positive what version of WINE I have, how can I check that? I got whichever version you get by searching for it on the ubuntu software center... it's either 1.0.1 or 2.1  lol sorry I can't be any more help.  

@ Chameco: I have a file called ddostandard.exe located in my "downloads" folder.  This is where I went to alter the properties to make it executable and also where I right click it and select "open with wine"

Is there something I need to do before wine will work properly? Because it doesn't seem to do anything at all..

---

### Post by spydeyrch on 2010-10-19
Ok, got ya. I would imagine that DDO is for Dungeon & Dragons Online?????  :confused:

Something I would recommend is going to the WINE website and checking their database to see which version of wine was used with which version of DDO. Also, I don't really like using the wine interface. I have found Play-On-Linux (or something very similar to that name) to be much more user frendily. Granted it is just a front-end to wine but it looks cleaner and simpler.

-Spydey

---

### Post by brndndvr on 2010-10-19
Yeah, dungeons and dragons online. 
I've found some tutorials to get it working on ubuntu, but in all honesty, they go over my head.

I think I'm going to try to uninstall wine and download a newer version and see if that fixes it...something is quite clearly not working with wine.

Play-on-linux is similar to wine?  I may have to look into it if the new version of wine still isn't functioning.  My one question would be this..if i use play on linux, does anyone know of a tutorial to try to use to install and play it?  Or could I still use the tutorials that use wine?

*Late Edit*
I couldn't get wine off by typing stuff in the terminal and it wouldn't go away when I found the folder it was located and hit 'delete' it wouldn't go away either so....I just finished a clean re-install of ubuntu 10.10.  Let's see how long before I mess it up this time :p

---

### Post by Shakz on 2010-10-19
You will need to have the game downloaded first but after you have it go to youtube and do a search on "How to install lotro on linux"

I have a 5 video series on how to set it up. They are not great videos but I get a lot of good feedback from them. I have also had folks tell me ddo works using the same procedure. 
Shakz

---

### Post by ajackson on 2010-10-19
Or read the sticky at the top of this forum and pop along to the [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2910") page for DDO.

---

### Post by brndndvr on 2010-10-19
Thanks guys.
I'll definitely check out the videos, but my problem has been getting the game simply to install.  Do I need wine to get it to install onto my computer since it's a .exe file?

I just finished downloading wine and got the file to start loading through wine, but I ran into this problem: "your system is not allowing access to our servers. check your firewall/security settings to allow PMB.exe to run."  How can I do this?

@ajackson: I'm hoping to use the resources you mentioned once I know what I'm doing, but as of right now, my level of ubuntu/wine/etc competence is so low it's embarrassing :p

---

### Post by ajackson on 2010-10-20
> **brndndvr said:**
> @ajackson: I'm hoping to use the resources you mentioned once I know what I'm doing, but as of right now, my level of ubuntu/wine/etc competence is so low it's embarrassing :p
But the information on that link tells you how to download and install DDO. If you don't understand it, fair enough you are new to linux, ask questions but use the information that is available.

---

### Post by brndndvr on 2010-10-20
> **ajackson said:**
> But the information on that link tells you how to download and install DDO. If you don't understand it, fair enough you are new to linux, ask questions but use the information that is available.

That's what I'm trying to do...I searched out the AppDB by myself and tried to follow the directions.  My system wasn't doing what I thought it was supposed to, so I did a google search to try to find a fix, did the stuff I mentioned in my previous posts in an attempt to fix it and was still running into problems.  When I tried everything my google search came up with, I decided I needed more personal help because I truly felt lost.  

I promise you I'm not a lazy pile who expects the world's answers to magically fall into my lap...sorry if I came across like that.

Also, I think I found a way to work around the pmb.exe not working properly because it looks like ddo might be downloading. I'll know for sure in a couple of hours

---

### Post by brndndvr on 2010-10-20
> **Shakz said:**
> You will need to have the game downloaded first but after you have it go to youtube and do a search on "How to install lotro on linux"

I have a 5 video series on how to set it up. They are not great videos but I get a lot of good feedback from them. I have also had folks tell me ddo works using the same procedure. 
Shakz

Thanks for the video series Shakz, it was EXTREMELY helpful being able to see all of the actions as well as listen to explanations of how to do it.  I've made good headway on getting the game downloaded and I got pylotro installed, but I've run into trouble and haven't been able to find a fix..yet.  
**EDIT** 
Nevermind, I think I may have got it! :o

Lesson of the day: It's amazing what can be accomplished when you're avoiding studying for an animal anatomy and physiology test you have the next morning at 8 a.m.!

---

### Post by brndndvr on 2010-10-21
Premature excitement.  Patching took most of the night and when I tried to load it this morning, wine just gave me a black screen with nothing on it.  Any ideas?

---

