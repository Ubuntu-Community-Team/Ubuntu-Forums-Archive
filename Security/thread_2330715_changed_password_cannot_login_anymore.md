---
title: "changed password cannot login anymore"
date: 2016-07-14
forum: Security
---

### Post by xenon3 on 2016-07-14
wrote 22 characters strong password first on paper, i have very much viruses every day by the way

---

### Post by Bucky Ball on 2016-07-14
Suggest changing it to another password and trying again. There may also be a limitation on password length which you've exceeded, but I think you would have been notified of that when creating the password.

*Please state the flavour and release of Ubuntu you are using*.

Not sure what it has to do with your password not working, but if you are getting viruses everyday I'd suggest you are either using Windows or clicking unthinkingly on any link that offers itself and opening unsolicited emails and attachments in Ubuntu.

Have you done a virus scan with ClamAV or something similar? How are you determining you have these viruses? Can you give evidence or examples of their existence on your machine?

---

### Post by xenon3 on 2016-07-17
> **Bucky Ball said:**
> Suggest changing it to another password and trying again. There may also be a limitation on password length which you've exceeded, but I think you would have been notified of that when creating the password.

*Please state the flavour and release of Ubuntu you are using*.

Not sure what it has to do with your password not working, but if you are getting viruses everyday I'd suggest you are either using Windows or clicking unthinkingly on any link that offers itself and opening unsolicited emails and attachments in Ubuntu.

Have you done a virus scan with ClamAV or something similar? How are you determining you have these viruses? Can you give evidence or examples of their existence on your machine?

I have Rebuild UBUNTU 14.04.03 from ubuntu-14.04.3-desktop-i386.iso burned on LIVE USB with Penlite under Windows

No I'm of course not using Windows, CLAMAV (ClamTK) is finding 4 to 5 Trojans and such viruses every day, I browse and surf normally, it finds every day 4 to 5 viruses, even in periods of several weeks when I'm not on what internet is all about (the three P's of the internet) Porn, Pills and Poker

But this is most important login did not go normally, I type in password, OK could be typo, but always get login screen back, after a flash that is looks like your logged in, always login screen, than I thought it should say something like "&#7812;rong Password" in RED like it use to, but it does not, does not matter what you type in, always login screen NO MESSAGE

---

### Post by sudodus on 2016-07-17
If you have a system with encrypted home, I think you will have problems if you change the password.

-o-

ClamAV might find false positives or files, that are dangerous in Windows but not in linux.

[LIST]
[*]- Are there any indications, that your system is infected except that ClamAV is finding these files?

[*]- Can you sanitize or remove the infected files with ClamAV, and get a clean system afterwards?

[*]- Try to identify the source of the infected files (for example check after visiting each web site, or search for information about that particular malware ID)?
[/LIST]

---

### Post by xenon3 on 2016-07-17
> **sudodus said:**
> If you have a system with encrypted home, I think you will have problems if you change the password.

-o-

ClamAV might find false positives or files, that are dangerous in Windows but not in linux.

[LIST]
[*]- Are there any indications, that your system is infected except that ClamAV is finding these files? 
[*]- Can you sanitize or remove the infected files with ClamAV, and get a clean system afterwards? 
[*]- Try to identify the source of the infected files (for example check after visiting each web site, or search for information about that particular malware ID)? 
[/LIST]


I could change the password in recovery boot "root ..." command prompt giving the installation encrytion passphrase to get in the terminal (not the home directory recovery passphrase by the way, which I first tried) However I still got that reoccurring login screen after each login attempt with changed user password, never the red messages "Wrong Password"

-0-

The virusses I already got today:
PUA.Html.Troyan.Agent-37075
PUA.Html.Exploit.CVE-2015-1692-1

I can delete, rescan, they are indeed gone

I have indications that there is something wrong (viruses) when system responds very slow (sometimes screen goes from color to grayscale) gets non responsive (screen freezes than in color, only mouse can move, no functionality, no UBUNTU main menu for shutdown / reboot)

Nice idea, check after each site, bit laborious, I have sometimes 20 to 40 websites simultaneously open in FireFox tabs

---

### Post by sudodus on 2016-07-17
> **xenon3 said:**
> I could change the password in recovery boot "root ..." command prompt giving the installation encrytion passphrase to get in the terminal (not the home directory recovery passphrase by the way, which I first tried) However I still got that reoccurring login screen after each login attempt with changed user password, never the red messages "Wrong Password"

Have you tried to change back to your original password?
> 
The virusses I already got today:
PUA.Html.Troyan.Agent-37075
PUA.Html.Exploit.CVE-2015-1692-1

I can delete, rescan, they are indeed gone

I have indications that there is something wrong (viruses) when system responds very slow (sometimes screen goes from color to grayscale) gets non responsive (screen freezes than in color, only mouse can move, no functionality, no UBUNTU main menu for shutdown / reboot)

Nice idea, check after each site, bit laborious, I have sometimes 20 to 40 websites simultaneously open in FireFox tabs

Yes a bit laborious, but you can change your habits during a test period, and have only one or very few tabs (with websites simultaneously open) in FireFox. It makes it easier to track the source(s) of malware.

The slowness might be caused by swapping because you have so many tabs open, that you exceed the capacity of your RAM. You can install ***htop*** and use it to monitor the usage of CPU and RAM and swap.

```
sudo apt-get install htop
```

---

### Post by xenon3 on 2016-07-18
> **sudodus said:**
> Have you tried to change back to your original password?
```
sudo apt-get install htop
```

Yes I did, but I got that cryptic message (which I found out later to be because of the NOT r/w mount of the OS disk) initially I thought this is an entropy check or one cannot use old passwords or passwords similar to old passwords check or something, so I only succeeded finally in having this 22 characters completely new password change, I thought also while having these troubles login in maybe UBUNTU truncates passwords of that long or by accident I had CAPS LOCK on while creating new password, so I checked with google on my tablet, it said max 255 or 1023 characters, sources differed

---

### Post by sudodus on 2016-07-18
I'm sorry, but I have no more ideas (at least not now). We need help from other people with new ideas.

[COLOR="#FF0000"] ***You***, who read this and have an idea, please chip in and help solving this problem[/COLOR] :-)

---

### Post by xenon3 on 2016-07-18
> **sudodus said:**
> 

Yes a bit laborious, but you can change your habits during a test period, and have only one or very few tabs (with websites simultaneously open) in FireFox. It makes it easier to track the source(s) of malware.

```
sudo apt-get install htop
```

TIME CLEAN 2016-07-18 19:56
TABS OPEN:
[LIST]
[*]Google 
[*]Facebook 
[*]Gmail 
[/LIST]
TIME CHECK 2016-07-19 2:28
VIRUSES (ClamTK GUI Home Directory 10,095 Files scanned last time ist was 9,716 files scanned?):
[LIST]
[*]PUA.Doc.Tool.LibreOfficeMacro-1 
[/LIST]

Seems to not come from the sites, but through the ports, like that famous worm in the early 00's

Is new for me: not in the Mozilla subdirectories but in the LibreOffice subdirectory

---

### Post by sudodus on 2016-07-19
If no security expert is around here (in the middle of the summer in the northern hemisphere), maybe you can try to get more advanced help in some other security forum, or maybe ask at a LibreOffice forum or corresponding forums for other affected software.

---

### Post by xenon3 on 2016-07-24
> **sudodus said:**
> If no security expert is around here (in the middle of the summer in the northern hemisphere), maybe you can try to get more advanced help in some other security forum, or maybe ask at a LibreOffice forum or corresponding forums for other affected software.

I will do that, your right I am holliday too, I wil do the other forums in a couple of weeks, however the 4 to 5 viruses I usually get a day, were all in the mozilla (browser) subdirectory, so from the internet and not through the ports, however I had google, facebook and gmail open in the tabs, so in principle the macro virus could have come from one of those sites, why would a malicious site only place viruses in the used browser (mozilla firefox) software subdirectories anyway?

> **sudodus said:**
> If no security expert is around here (in the middle of the summer in the northern hemisphere), maybe you can try to get more advanced help in some other security forum, or maybe ask at a LibreOffice forum or corresponding forums for other affected software.

where are these fora? Or are they hypothetical? In other words are they ubuntu fora?

---

### Post by sudodus on 2016-07-24
Please search the internet for ***linux security forum*** - and you will find several security forums.

---

### Post by yoshii on 2016-07-25
i had a problem with a changed password when it turned out that my keyboard was generating the wrong keys! (characters).  I got a new keyboard and that solved the issue of the bad characters, but i was still locked out and had to reinstall.

---

