---
title: "Wine 1.1.13 won't install"
date: 2009-01-19
forum: Wine
---

### Post by xeddog on 2009-01-19
I have been trying to install Wine 1.1.13 for a couple of days now.  Tried just about everything I can think of which isn't really much.  I'm still a newbie at this.  Anyway, I have my Sources updated so I get the latest version.  Synaptic tells me that the latest is 1.1.13 so that should be good.  When I select Wine in synaptic it also marks Wine-gecko and then I clo\ick the apply icon.  It all SEEMS to work just fine.  Synaptic ends with no errors, but I have no icons in the Applications menu, and no .wine directory in my home directory.  No nuttin.  Then I can use Synaptic to remove them and again, no errors.

The last thing I tried was using command line.  I started by 
 sudo apt-get autoremove  
 sudo apt-get autoremove
 sudo apt-get purge wine
 sudo apt-get purge wine-gecko

All that appeared to do what I wanted it to do with no eror messages 

then 
sudo apt-get install wine

This last command installed wine, wine-gecko, and ttf-liberation.  Again, no error messages, and again no icons, no .wine directory, no nuthin.  But I can run "wine --version" and get a response of "wine-1.1.13"  

So what's the deal????   Anybody?????

xeddog

P.S.  I read about package trouble with 1.1.12, but also that the problems were fixed in 1.1.13.

Oh yeah.  Almost forgot.  I am installing this (or trying to) on Ubuntu Intrepid 32-bit.  Machine is a 3GHz P-4 with 1GB ram.

---

### Post by cogadh on 2009-01-19
Wine doesn't create the .wine directory untill you run winecfg to create it. If you can run "wine --version" and it reports something back, then it is installed and you just need to start using it.

As for the missing shortcuts, that is a common problem, but you don't actually need them to use Wine anyway.

---

### Post by Kow on 2009-01-20
I would NOT recommend using Wine 1.1.13. It is buggy as hell. Good example: World of Warcraft will not install using the Blizzard downloader. With the intrepid repo version of wine (1.0.1 i think) you can at least download WoW but you cannot install the game due to a Licensing GUI bug.

Conclusion: Wine is broken in Intrepid. You'll need to manually install a good working version. I recommend 1.1.8'ish.

---

### Post by hikaricore on 2009-01-20
> **Kow said:**
> I would NOT recommend using Wine 1.1.13. It is buggy as hell. Good example: World of Warcraft will not install using the Blizzard downloader. With the intrepid repo version of wine (1.0.1 i think) you can at least download WoW but you cannot install the game due to a Licensing GUI bug.

Conclusion: Wine is broken in Intrepid. You'll need to manually install a good working version. I recommend 1.1.8'ish.

I'm sorry but you seem to be mistaken.

1.1.13 is quite good.  I have run 10-20 different software titles on it without so much a hickup.

Also the version of wine included in the Intrepid repos is also fine.
Just because there is one bug does not mean WINE is broken, please try to be more accurate in the future.

You want broken?  Install the intrepid package for 1.1.12, you'll see broken.

---

### Post by xeddog on 2009-01-20
I'm afraid that my experiences with Wine are . . .well . . not good.  I have about 4 or 5 apps that I have been testing since before Wine 1.0 and none of them work yet.  These programs are the ones that are keeping me from switching from Windows XP to Linux.  There are about 4 more that I haven't even tried yet because so far there just isn't any point.  I will probably go ahead and try them at some point, but I just don't really see the need at the moment.

Anyway, regarding 1.1.13.  With most of the earlier releases of Wine the apps would install ok.  With this latest Wine, there are some problems during install that I did not have before, and one of the apps that used to at least "run" now does not.  So for ME, 1.1.13 is a step backward.  But that is ok because as I understand it, the structure of Wine itself is being changed so I would expect some things to "break" for a while.  But I am VERY hopeful that things will improve for me soon.

Now I don't mean to belittle the Wine effort in any way.  Quite the contrary.  I have been keeping the Wine AppDB updated with a couple of my apps.  Ones I think more people than me would be interested in.  So to the Wine effort itself, Keep up the good work.  

Xeddog

---

### Post by Skylara on 2009-01-23
I got Wine 1.1.13 installed just fine using the instructions for Ubuntu linked from the [Wine download page]("http://www.winehq.org/download/deb").  Easiest way to to enable the repository in your Package Manager, Authenticate it, get the release, and done.  All the instructions are there.

In regards to the comment about Wine 1.1.13 not installing WoW, I am having the same issue.

I had Wine 1.0.1 installed and I downloaded the client from the WoW account admin page. It downloaded the InstallWoW.exe file, then that opened up to get the WoW Installer and it brought me to the EULA. Then I wasn't able to agree to the EULA after scrolling to the bottom as you are supposed to.

Forum searches told me that installing Wine 1.1.13 would fix this problem. Maybe, but I can't get that far.  Now when I try to open the WoW Installer, I get the following error: "Unable to initialize streaming. Please check your Internet connection. If this problem persists, please contact Blizzard Technical Support."

It's not Blizzard. It's not my connection. Nothing at all has changed in the ten minutes between trying Wine 1.0.1 and Wine 1.1.13.  For some reason, it simply will not sync up with Blizz to get the streaming files it needs for installation.

Any thoughts?

---

### Post by gjoellee on 2009-01-23
Please notice that Wine 1.1.3 is a development release, the latest stable release i v.1.0.1

---

### Post by phillies on 2009-01-26
> **gjoellee said:**
> Please notice that Wine 1.1.3 is a development release, the latest stable release i v.1.0.1
Yes, but the stable release has a bug which makes it impossible to run some applications, e.g. the WoW installer.
But the development release is buggy to, something with the new gecko went wrong as neither can I install WoW.

I tried 1.1.8 from here [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html"). I first had to completely remove wine and gecko, removed all developmental repositories from synaptic and reloaded the package lists. Then I installed the stable wine 1.0.1 + gecko 0.1.0 and then replaced wine with the 1.1.8 package:
dpkg -i wine_1.1.8~winehq0~ubuntu~8.10-0ubuntu1_amd64.deb

So I was able to get beyond EULA, currently the installer is dl'ing all the stuff but it seems to work.

Thanks for the hint, Kow!

---

