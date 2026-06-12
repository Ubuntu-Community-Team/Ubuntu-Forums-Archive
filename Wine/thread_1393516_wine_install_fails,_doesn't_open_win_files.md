---
title: "wine install fails, doesn't open win files"
date: 2010-01-29
forum: Wine
---

### Post by jamoncillo on 2010-01-29
Ok. So I had my karmic up and running, wine V36 included

I had some conflicts with compiz and my installation died on me, so I just reinstalled everything from zero.

However, I saved 1 folder from wine: the one that has my progress in Rosetta Stone. So once my notebook was customized with all my programs and codecs. I went for wine. But it turns out I can't install it! If i click on the link provided on winehq an error says something about some dependencies or something like that.

Same thing happens when I try from Software Center

However, I downloaded the deb from version 36, the same version I was using before reinstalling karmic, but nothing happens when I try to open any exe file! 

also nothing happens when I click under Wine-> configure wine

thanks

Jamoncillo

---

### Post by beastrace91 on 2010-01-30
In terminal please try:

```
sudo apt-get install wine1.2
```

Regards,
~Jeff

---

### Post by jamoncillo on 2010-01-30
yupe, done that. even thought wine was installed, version 36 now it's upgraded to V37. But, still nothing happens. not even when I try to open an exe, nor when trying to configure wine =(

---

### Post by jamoncillo on 2010-02-01
hmm... think it's fixed. Still get the install error, somethin about dependencies unmet or something like that. But I managed to run Rosetta Stone's installer from Terminal. I think it had something to do with the folder permissions being set to Root, 'cause I just changed owner permissions and now it runs quite good. Thanks! I'll leave the thread open for a couple of days and see if anything fails again

---

### Post by beastrace91 on 2010-02-01
Well glad you got it working at any rate - just for curiosities sake, since you said the wine install failed, can you post the output of:

dpkg -l wine*

~Jeff

---

### Post by jamoncillo on 2010-02-01
sure jeff.

The error I got was the 'Package dependencies cannot be resolved'  but only when installing from GUI. If I tried from terminal, or the Beta version from Ubuntu Software Center then it did got installed. The problem was I couldn't open anything related to wine, but browse .Wine in my home folder.

Anyway, what apparently did the trick was changing ownership with chown AND running my setup from terminal. Once I installed rosetta from Terminal it all went smooth 

As you requested, my terminal output is:

```
jamon@jamuntu:~$ dpkg -l wine*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
rc  wine                              1.0.1-0ubuntu8                    Microsoft Windows Compatibility Layer (Binary Emulator and Library)
un  wine-doc                          <none>                            (no description available)
un  wine-gecko                        <none>                            (no description available)
un  wine-utils                        <none>                            (no description available)
ii  wine1.2                           1.1.37-0ubuntu2                   Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.2-gecko                     1.0.0-0ubuntu3                    Microsoft Windows Compatibility Layer (Web Browser)
un  winesetuptk                       <none>                            (no description available)

```

thanks, and have a nice day

Jamoncillo

---

### Post by Mana Whyrl on 2010-02-02
i think u should reinstall wine ...
try thise one
1.st remove all wine components, rm-wine.sh
2.nd install wine by script...(it`s include directx, quicktime player, also u can uncomment some commands, and install more features

---

### Post by jamoncillo on 2010-02-02
> **Mana Whyrl said:**
> i think u should reinstall wine ...
try thise one
1.st remove all wine components, rm-wine.sh
2.nd install wine by script...(it`s include directx, quicktime player, also u can uncomment some commands, and install more features


Why, Mana Whyrl? is ther something wrong with my Terminal output?
sorry, I'm not a newbie but neither even close to being a Linux expert, so I don't quite understood my Terminal's output.

And prior to my last Wine installation I removed the whole .Wine folder and it's content, so I wouldn't have any weird configuration messing up my Wine.

Also, I'm trying the betas. Thanks

Jamoncillo

---

### Post by beastrace91 on 2010-02-02
> **jamoncillo said:**
>  it's fixed.

If its working how you need - just leave it alone. No need to fix what isn't broken...

~Jeff

---

