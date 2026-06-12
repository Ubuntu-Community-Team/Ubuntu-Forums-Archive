---
title: "Wine not working right"
date: 2009-04-20
forum: Wine
---

### Post by Quirriff on 2009-04-20
Ubuntu 8.10 64 bit
wine-1.1.19


Wine configuration cannot map drives and the set windows version is always blank.

Terminal output is:

```
err:process:__wine_kernel_init boot event wait timed out
err:winecfg:open_mountmgr failed to open mount manager err 2
```

It also cannot run applications like starcraft's install program (a simple program that I've had no problem with in the past), same error

```
_err:process:__wine_kernel_init boot event wait timed out_
```



I've completely Uninstalled wine, deleted my .wine directory, reverted to version 1.1.17 that I've never had problems with. Nothing has worked, about the only thing that I haven't tried yet is installing from source.

---

### Post by asdfoo on 2009-04-20
> **Quirriff said:**
> Ubuntu 8.10 64 bit
wine-1.1.19


Wine configuration cannot map drives and the set windows version is always blank.

Terminal output is:

```
err:process:__wine_kernel_init boot event wait timed out
err:winecfg:open_mountmgr failed to open mount manager err 2
```

It also cannot run applications like starcraft's install program (a simple program that I've had no problem with in the past), same error

```
_err:process:__wine_kernel_init boot event wait timed out_
```



I've completely Uninstalled wine, deleted my .wine directory, reverted to version 1.1.17 that I've never had problems with. Nothing has worked, about the only thing that I haven't tried yet is installing from source.

is Wine still running?

open a terminal and type 'ps ax'

look for explorer.exe wineserver or anything else related

---

### Post by Quirriff on 2009-04-20
Okay I typed 'ps ax' and here's all I could find that was wine related.

```

 7338 ?        Ss     0:06 /usr/bin/../lib32/../bin/wineserver
 7340 ?        Zsl    0:03 [wineboot.exe] <defunct>
 7341 ?        Sl     0:00 C:\windows\system32\services.exe                    
 7346 ?        Ss     0:00 C:\windows\system32\explorer.exe /desktop           
```

---

### Post by Meow27 on 2009-04-20
> **Quirriff said:**
> I've completely Uninstalled wine, deleted my .wine directory, reverted to version 1.1.17 that I've never had problems with. Nothing has worked, about the only thing that _I haven't tried yet is installing from source._
running wine from the compiled folder takes 550 MB, and is really annoying to run from the folder. 

i dont think make install will help you on this though........

---

### Post by alex.rayu on 2009-04-20
You must really be doing something strange to have caused that error.

---

### Post by Quirriff on 2009-04-20
No not really, it's a pretty fresh install about the only things I've done are install vlc, smplayer, comix, w64codecs, and enabled libdvdnav.

---

### Post by alex.rayu on 2009-04-20
Then uninstall and reinstall WINE. See the error looks a very severe one, something that is caused by the internal problem rather than something else.

---

### Post by NightMKoder on 2009-04-20
If purging wine and the .wine folder doesn't get rid of it, there is a serious problem. So do:

```

rm -Rf ~/.wine
sudo apt-get purge wine

sudo apt-get install --reinstall ia32-libs
sudo apt-get install wine
winecfg

```

---

### Post by Quirriff on 2009-04-20
Tried that, still not working right.

I honestly thought that would work.

---

### Post by NightMKoder on 2009-04-20
Your packages are probably screwed up then. Did you use the multiple wine installer/install wine in some other way?

If not, make sure that it works on a livecd. If it doesn't - file a bug.

---

### Post by krendar on 2009-04-20
I am having exact same problem on Jaunty 64. Since the original poster is using 8.10 it apparently has nothing to do with Jaunty.

I managed to find this bug on winehq:

[http://bugs.winehq.org/show_bug.cgi?id=17662](http://bugs.winehq.org/show_bug.cgi?id=17662)

But it is still an unresolved bug. Has something to do with being a 64-bit system. Strange thing is I install Linux many times, and wine many times and this is the first time I had problems with it.

edit:

I got a backtrace error from wine. Something to do with libgl.so.1. So I took a guess and reinstalled the nVidia drivers, rebooted, and now winecfg runs perfectly.

---

### Post by Quirriff on 2009-04-21
Odd, why would it have anything to do with nvidia drivers, I'll try what you did it's worth a shot.

---

### Post by Quirriff on 2009-04-25
Did not work, this is getting frustrating.


You're right however it is the same as [http://bugs.winehq.org/show_bug.cgi?id=17662](http://bugs.winehq.org/show_bug.cgi?id=17662)

---

### Post by toopi on 2009-05-02
For the following error:
```
 err:process:__wine_kernel_init boot event wait timed out 
```
And wine hanging approximately 30 sec before any windows come up, I did solve it by rebooting, reinstalling and rebooting.  However, I'm using the drivers directly from nvidia.com, if that matters anyway.

---

### Post by abitwise on 2009-11-20
I managed to find a solution for this error without the need of a time consuming system reinstall. (err:process:__wine_kernel_init boot event wait timed out)

Just try this from console:

wineboot --update

Next wait until it runs, for me somehow it started up Steam.exe and EA update manager, i just closed these and did Ctrl+C to the console after 10 minutes. Then when i started a program (Steam.exe) and no more error message!

My wine went broken after Ubuntu version upgrade 9.04 -> 9.10 (I have third party source for 1.33)

---

### Post by Xog on 2009-11-20
> **abitwise said:**
> I managed to find a solution for this error without the need of a time consuming system reinstall. (err:process:__wine_kernel_init boot event wait timed out)

Just try this from console:

wineboot --update

Next wait until it runs, for me somehow it started up Steam.exe and EA update manager, i just closed these and did Ctrl+C to the console after 10 minutes. Then when i started a program (Steam.exe) and no more error message!

My wine went broken after Ubuntu version upgrade 9.04 -> 9.10 (I have third party source for 1.33)

It's been a very common issue for wine to break after an upgrade to 9.10. I'm interested in hearing a cause for it.

---

### Post by Intrepid Ibex on 2009-11-22
@Xog, it's not (at least just) because of the upgrade from jaunty to karmic.

I got Arch (rolling release, only vanilla packages) and the same issue but your suggestion worked.

Maybe it's just the latest wine.

---

