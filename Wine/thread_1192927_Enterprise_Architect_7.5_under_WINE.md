---
title: "Enterprise Architect 7.5 under WINE"
date: 2009-06-20
forum: Wine
---

### Post by fballem on 2009-06-20
I'm just wondering if anyone has had any luck installing the latest version of Enterprise Architect ([http://www.sparxsystems.com](http://www.sparxsystems.com)) under WINE. If you have, some detailed instructions would be most welcomed.

I have tried WINE from the repositories (never got a chance to enter the registration key) and also 1.1.23 from winehq. I noticed that on the wine website, EA 7.1 was rated Platinum and 7.5 is rated Garbage - not an encouraging sign.

Thanks,

---

### Post by Mark Phelps on 2009-06-21
> **fballem said:**
>  EA 7.1 was rated Platinum and 7.5 is rated Garbage - not an encouraging sign.
Thanks,

It's more than a discouraging sign; it's an indication that IT WILL NOT WORK!

But, hey -- credit goes where credit is due.  At least, unlike nearly everyone else who posts here about Wine problems, you had the foresight to check to see what the rating was.

---

### Post by NightMKoder on 2009-06-21
That particular appdb entry doesn't seem very reliable. According to the report the application should be at least bronze (it launches!).

---

### Post by NightMKoder on 2009-06-21
Sorry to double post, but it seems like the app works like a charm after a few tweaks:

So (I was testing on fresh prefix):

wine easetup.exe
sh winetricks mfc42 jet40 native_oleaut32

and that's it. It's a little slow (bufferedrepaint being a stub is reponsible), but seems to be completely usable. Although granted, without the last winetricks it crashes when opening the example project.

---

### Post by fballem on 2009-06-21
> **NightMKoder said:**
> Sorry to double post, but it seems like the app works like a charm after a few tweaks:

So (I was testing on fresh prefix):

wine easetup.exe
sh winetricks mfc42 jet40 native_oleaut32

and that's it. It's a little slow (bufferedrepaint being a stub is reponsible), but seems to be completely usable. Although granted, without the last winetricks it crashes when opening the example project.

I'm not sure what you mean by 'testing on a fresh prefix'. Am I correct that you're executing the two commands (wine and sh winetricks) from the terminal? And once you have executed these, then the Enterprise Architect icon that appears on the desktop is executable? Forgive the basic question - I'm still a relative newbie on ubuntu and a total newbie on wine.

Also, did you use the wine in the ubuntu repository or on the PPA that was specified in the winehq site. I believe that the version in the PPA is 1.1.23. I'm not sure what the version in the ubuntu repository is, but it is quite a bit older.

Thanks,

---

### Post by NightMKoder on 2009-06-23
Sorry for not replying sooner (I tend to only check threads on the front page when I get home), but here are the answers to your questions:

a fresh prefix means that I did not have anything else installed under wine (this is the normal testing environment). It is equivalent to never starting wine before, or remove your .wine folder. You can have mixed success if you don't use a fresh prefix (ie no guarantee itll work, but try it).

The wine version I used was 1.1.23-git, but this is 1.1.24 now so you should be good to go. I don't guarantee anything with the standard version that ships with ubuntu (1.0.1)

Those commands aren't entirely exact. easetup.exe is the setup file I downloaded from the website you gave. If you have it named something different, start that instead. That command just means "start the installer as you would normally".
The winetricks command is a utility for wine. The exact command (including downloading winetricks) would be:
```

wget http://winezeug.googlecode.com/svn/trunk/winetricks
sh winetricks mfc42 jet40 native_oleaut32

```

---

### Post by fballem on 2009-06-24
Thanks for the additional clarification. I'll give this all a try and let you know whether the problem is solved.

---

### Post by fballem on 2009-06-28
Thanks for this - it's a shame that we have to go through all of these hoops, since this is the first version of EA that was supposed to work cleanly in both Windows and Linux. They used to distribute separate executables.

An FYI - the display is not totally clean. For example, if you hover over the New Package icon in the upper right corner, then the text isn't fully displayed. (screenshot is attached). I'm expecting other problems, but hopefully minor.

Thanks!

---

