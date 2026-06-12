---
title: "Ubuntu 5.04 Experiences."
date: 2005-04-07
forum: The Cafe
---

### Post by Slapdash on 2005-04-07
Ok i made a clean install of 5.04 ( Hoary Hedgehog )

Like most of you probly know i'm the only linux user between 230+ Windows computers.

Off and on i had to boot back to Windows to do some work that Fedora and even Warty gave me errors or couldnt do or was MUCH slower etc.

I am pleased to say I have been doing my work now without having to boot back into Win for 3 days now and growing.

Terminal Services works faster than on Win 2000 and even on Win XP's remote desktop connection, to a Windows 2000 Server!! i couldnt get this to work on Wart and Fedora Core 3 was SLOOOWWWWW.
This is awesome and thanks to the devs for including it out the box!!!!!

Evolution after upgrading works without a hitch with our Exchange server. Its even traking the meetings like it should etc. AWESOME!  Fedora DID NOT WORK ( I dont know why it just didnt connect. ) Warty  it did work but I could only e-mail and it didnt recognize my address list, witch seems to be mostly there with the new Evolution and Hoary.

Graphic card. Works with my work and home nvidia cards. At work i had a problem with the GeForce 2 DDR 256 but after re-installing them and re-activating the drivers all is fine now, except that my resolution doesnt want to go up over 1024 x 768. my Home pc on a GeForce 5200 goes WAAAAYYY more than that, so i expect it to be a minor issue in the config or something. Well done!

Love the new "places layout" and the new bootsplash!

Networking. With Warty I had ENDLESS trouble - dont ask me why I couldnt figure it out. trying to access our corporate network. it saw the domain and PC's but as soon as wanted to log into PC's that i had permission / access to it poped up password prompts and nothing i put in worked, or it would refuse to connect.
Now it just works after i put in the passwords. WELL DONE!!!! I havent completely tested this all over but i should be ok with a couple of tweaks.

One thing I would like to see happen in Breezy. PLEASE make it so that the Windows partision is recognized and mounted or something if it has after boot. is this possible? Windows users migrating to ubuntu will need to see their partision and might not know of a way to mount it. I know this is possible because there are quite a few distro's that does this. Mandrake for one.

All in all awesomely done. THE BEST DISTRO TO USE NOW. PERIOD.

---

### Post by TjaBBe on 2005-04-07
I've done a clean install of hoary on my laptop yesterday, and it rocked, until I installed my nvidia drivers. When I now start X I get some strange white screen while warty's nvidia drivers worked without an issue. But hey, that's nothing I can't overcome :D.

I look forward to fixing my laptop install and putting hoary on my desktop too tonight :D. I've been waiting for this moment a long time :).

---

### Post by Slapdash on 2005-04-07
Let us know how it goes.

I couldnt wait. i have Snapshot 7 installed and is updatinmg every day to the latest in main.

---

### Post by TjaBBe on 2005-04-07
[QUOTE=Slapdash]Let us know how it goes.

I couldnt wait. i have Snapshot 7 installed and is updatinmg every day to the latest in main.[/QUOTE]

Sure. I must also say that it was quite late when I installed the drivers yesterday, so no doubt I just screwed something up myself :).

---

### Post by MaZiNgA on 2005-04-07
[QUOTE=TjaBBe]Sure. I must also say that it was quite late when I installed the drivers yesterday, so no doubt I just screwed something up myself :).[/QUOTE]
 Did you run glx-config enable?

---

### Post by TjaBBe on 2005-04-07
[QUOTE=MaZiNgA]Did you run glx-config enable?[/QUOTE]

I did edit the xorg.conf myself, and after this was not working I tried glx-config enable. When that didn't work I went to bed ;).

---

### Post by Slapdash on 2005-04-07
hehehehe

---

### Post by defkewl on 2005-04-07
So saying that it will be released on 8th April was only an April fool Joke is it. Haha

---

### Post by TjaBBe on 2005-04-07
[QUOTE=defkewl]So saying that it will be released on 8th April was only an April fool Joke is it. Haha[/QUOTE]

No it isn't. Hoary is still in Release Candidate status...

---

### Post by TjaBBe on 2005-04-07
Just did a re-install and I'm still having the same problem. I did a 
```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo reboot

```
When it starts X now I just get a blank screen. It's on a Dell Inspiron 8100 laptop, and I believe it is using some mobile version of the GeForce2.

---

### Post by poofyhairguy on 2005-04-07
Good mini review. Hoary is miles better.

---

### Post by zenwhen on 2005-04-07
I have been using Hoary for a couple months. All the little Gnome enhancements that have come along, and the quicker boot speeds are pretty awesome.

It is a huge improvement over the already wonderful Warty.

---

### Post by adbak on 2005-04-07
After a brief stint with sound problems (fixed by this post from the fabulous Ubuntu-geek [http://ubuntuforums.org/showthread.php?t=21211](http://ubuntuforums.org/showthread.php?t=21211)) Hoary is great!

Aside from the new Human theme colors (different topic) the only other "fault", if you will, that I see is that the GNOME BitTorrent hogs resources.  No biggie, I still haven't given Azureus or BitTornadio a chance on Hoary yet, but integrating bittorrent technology with GNOME is a step in the right direction.

Thanks, Ubuntu devs and all involved in the making of this great project!

---

