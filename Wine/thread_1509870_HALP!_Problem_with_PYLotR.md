---
title: "HALP! Problem with PYLotR"
date: 2010-06-14
forum: Wine
---

### Post by Mosskins on 2010-06-14
Running on Ubuntu Karmic 9.10

Hey! Well after a few months on linux I decided to finally test Wine by installing it and installing a video game titled- Dungeons and Dragons Online.

Well after a few attempts I finally got it installed and ready to play- only to find out that I missed the last step. I need a game launcher.

I was referred to launcher- [http://www.lotrolinux.com/download.php](http://www.lotrolinux.com/download.php)

I've followed the steps and finally found how to download and import the key(I think) but I've come across a problem that always pops up right when I think I've finally got it installed- 
[B]
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0[/B]

  I've imported the source key, though it took blood and sweat to figure that part out. And I've gone in every way that I can think of to try and get it working. 

There is a step by step I found an am planning on trying but the third left me with questions. Yay newbies!

> 3) Open a terminal emulator (xterm, konsole, whatever) and cd to the folder you downloaded the PyLotRO source code to.

Okay maybe just one question.... '*huh*?'

Much appreciated! 

-Mosskins

---

### Post by Mosskins on 2010-06-16
Please help me--- I don't usually beg but... I'm feeling a little stressed out with this.

---

### Post by Bölvaður on 2010-06-17
just logging what I am doing:

adding 
```
deb http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu karmic main
```
to the source list through "software sources"

saving this key to the desktop```

http://www.lotrolinux.com/ajackson-public.key
```

software sources &#8594; authenticate, import key

reloading the sources via synaptic by the blue reload button

find the game in synaptic, mark for install

applications &#8594; games &#8594; lord of the rings online


ok it seems to be working fine, but I wouldnt know because I dont have this game.
you do realise you just download the key to your desktop, load it into software sources and refreshing the list.
there are many different ways of doing it, some are more prone to error than other

---

### Post by Elfy on 2010-06-17
moved to wine forum

---

### Post by Mosskins on 2010-06-18
(sorry for posting in the wrong category...)

Thank you so much!!!!!! I've got the launcher working properly, as far as I know, and the game starts just fine(In fact the video intro worked more smoothly and in a higher quality than my brother's- who runs on windows)... but I've run into yet another pickle.


Ok so in order to play, I need to update the game. I've retraced my directions a thousand times but the patcher keeps telling me that there is an error and cannot load the patch.

   ```

err:rundll32:wWinMain Unable to load L"lotropatchclient.dll"
 
 err:rundll32:wWinMain Unable to load L"lotropatchclient.dll"
 
 err:rundll32:wWinMain Unable to load L"lotropatchclient.dll"
 

```

Once again I've tried coming at it in many different angles but I guess I really simply don't know enough about what I'm doing to have much of a chance on getting it right. 

If you can help me again that's great, but if you can't without actually installing the game- I won't ask you to.

---

### Post by schtufbox on 2010-06-18
download and copy this into the LOTRO folder

[http://www.mediafire.com/?idnitkd5tyw]("http://www.mediafire.com/?idnitkd5tyw")

It's a copy of the patchclient.dll that's in my LOTRO folder so it should work as mine patches!

---

### Post by Mosskins on 2010-06-18
Hmmm still not working....


I'm starting to think that I'm putting it in the wrong folder. Can you give me a step by step tutorial... partly because my brain has fried and will not connect the dots as easily and partly because I am a newbie and certain things that an experienced Linux user would not have to say to another experienced Linux user needs to be said. xD


When I put it in under patchclient.dll I get this;
```

 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"

```I'm following these directions... maybe you can see what I'm doing wrong?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785)

---

### Post by schtufbox on 2010-06-18
Might be worth checking here: [http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X]("http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X")  if you haven't already. Very useful guide.

---

