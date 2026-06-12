---
title: "antivirus2008scanner.com hijacking the FireFox 2"
date: 2008-08-02
forum: Security
---

### Post by dandellion on 2008-08-02
I thought it's just something that passed the pop-up blocker, but it came second time. Out of regular browsing, new tab popped out, aiming to antivirus2008scanner.com. It is obviously a fake virus scanner that told me that my Vista is infectedd by spyware and that I should click OK to install something .exe with regular you-click-cancel-I-open-alert-box-again behaviour. 

OK, I know it is fake scanner, but how it can open its site out of nothing, and even more important, how to kill it?

FireFox 2.0.0.16
Ubuntu 7.10

Thanks.

---

### Post by benny bronx on 2008-08-02
I'm not sure this is happening on your ubuntu partition or vista partition.

If Ubuntu, try emptying your cache and deleting private data (under tools), including cookies.

If vista, do the same, then download and run Superantispyware free.

[http://www.superantispyware.com/]("http://www.superantispyware.com/")

---

### Post by arsenic23 on 2008-08-02
[B][COLOR="DarkRed"]EDIT::  Oh, ignore me - your not in windows, are you?
So yeah, What Benny Bronx said should work. [/COLOR][/B]
---------------------------------------------------------------


> **benny bronx said:**
> [http://www.superantispyware.com/]("http://www.superantispyware.com/")

I'd recomend [spybot]("http://www.download.com/Spybot-Search-Destroy/3000-8022_4-10122137.html?hhTest=1&tag=lst-1&cdlPid=10861988") and [adaware]("http://www.download.com/Ad-Aware-2008/3000-8022_4-10045910.html?hhTest=1&tag=lst-1&cdlPid=10844457") over that thing.

I've had the best luck removing that thing doing this:

## Using spybot's advance features, remove all your BHO and ActiveX listing.
## Using spybot's advance features, remove anything supsicous from your startup, opening the sidepanel will give you an explanation of each item.
## Run spybot, make a list of everything that could not be removed, don't bother letting it scan on startup.
## Do the same for adaware.
## Boot into linux, mount your windows drive, and remove all of the files on your list manually. ( Use a liveCD if this machine doesn't dual boot. )
## Look for these files/folders and remove them if you find them:
[INDENT]C:\Program Files\Antivirus 200*
C:\Windows\Antivirus*
C:\Windows\system32\Antivirus 200*
C:\WINDOWS\krln32.exe
C:\Program Files\Common Files\trjdwnl.dll
C:\trjdwnl.dll
C:\WINDOWS\shlext32.exe
C:\WINDOWS\system32\scvh0st.exe **Exact spelling!!**
C:\Program Files\XPAntivirus
C:\WINDOWS\system32\ieupdates.exe
C:\Program Files\Antivirus 2009\av2009.exe
C:\WINDOWS\system32\winsrc.dll
C:\Program Files\Power-Antivirus*[/INDENT]

If you don't have an antivirus software I recomend you try out the trail for [Kaspersky]("http://usa.kaspersky.com/trials/home-users/anti-virus-7/"), it norally doesn't have a probelm removing the Antivirus200[89] variants.

---

### Post by spike_strip on 2008-08-02
> **arsenic23 said:**
> ## Look for these files/folders and remove them if you find them:
[INDENT]C:\Program Files\Antivirus 200*
C:\Windows\Antivirus*
C:\Windows\system32\Antivirus 200*
C:\WINDOWS\krln32.exe
C:\Program Files\Common Files\trjdwnl.dll
C:\trjdwnl.dll
C:\WINDOWS\shlext32.exe
C:\WINDOWS\system32\scvh0st.exe **Exact spelling!!**
C:\Program Files\XPAntivirus
C:\WINDOWS\system32\ieupdates.exe
C:\Program Files\Antivirus 2009\av2009.exe
C:\WINDOWS\system32\winsrc.dll
C:\Program Files\Power-Antivirus*[/INDENT]

I understand there appears to be plenty of moderation on this forum, however, why are the users of Ubuntu forum able to provide MS windows, support?  

I do not agree that just because he is dual booting – Ubuntu and M$ - he/she should be able to seek MS support hear on this forum.
Am I missing something?  

This is not totally directed to this specific post...I would just appreciate some clarification on the issue; where is the moderation? 

No M$ support hear please!

---

### Post by btdown on 2008-08-02
I agree...but if his intent is to run a linux virus scanner on his windows partition, don't bother. I wound up with the xpantivirus2008 and virtumonde viruses...Not one of these fully updated scanners detected or fixed the virus on the windows partition (even though they claim to):
ClamAV
F-Prot
Avira
Avast

---

### Post by atoc on 2008-08-02
dandellion is NOT running Vista.
Look at the end of his post:


> FireFox 2.0.0.16
Ubuntu 7.10

The POPUP says his "Vista" is infected. The creator of the popup is banking on the fact that most n00b users who will click on the ad will be running MS Vista.

@dandellion - install adblock plus for FF. It takes care of things that the built-in popup blocker misses (coders of those popups are getting smarter in their techniques. adblock has never faile me yet.

---

### Post by arsenic23 on 2008-08-02
> **spike_strip said:**
> I understand there appears to be plenty of moderation on this forum, however, why are the users of Ubuntu forum able to provide MS windows, support?  

I do not agree that just because he is dual booting &#8211; Ubuntu and M$ - he/she should be able to seek MS support hear on this forum.
Am I missing something?  

This is not totally directed to this specific post...I would just appreciate some clarification on the issue; where is the moderation? 

No M$ support hear please!

Why not?  If an Arch user asked a question about Arch and I knew the answer I wouldn't just ignore him out of spite.  The same is true for OSX, Windows, and any other thing you might have a problem with.  Also for this particular problem ( or the problem I thought he had the first time I read his post ) the easiest way to fix it is from another OS other then the effected Windows install.

On another note, I've never seen Antivirus 2008(9) effect firefox, and would love to see a screenshot of it.

---

### Post by btdown on 2008-08-03
> [The same is true for OSX
Just for the record, I'd ignore him out of spite if he was asking about OSX.

---

### Post by benny bronx on 2008-08-18
>  Originally Posted by benny bronx  
[http://www.superantispyware.com/]("http://www.superantispyware.com/")

> I'd recomend spybot and adaware over that thing.

If you google Superantispyware, you would see that it is highly recommended at many security forums and sites. Adaware, unfortunately, has become a glorified cookie manager that tends to choke on tougher malware.

---

### Post by moonpup on 2008-08-18
> **benny bronx said:**
> If you google Superantispyware, you would see that it is highly recommended at many security forums and sites. Adaware, unfortunately, has become a glorified cookie manager that tends to choke on tougher malware.

LOL, my mother's computer (WinXP) got infected with some brand new virus that even her installed version of Kaspersky could not remove even though it identified it. After working with a Kaspersky support rep over 3 days, he finally suggested using SuperAntiSpyware to remove it and that worked flawlessly.

Kaspersky finally updated their definitions to basically disinfect whatever my mother had installed, but it was SuperAntiSpyware to the rescue first...

---

### Post by todb on 2008-08-18
> **arsenic23 said:**
> Why not?

1) Because there are plenty of other forums where people can participate in the endless "run anti-spyware Brand X and post the results" threads, if they want.

2) Because the question was really "how does this spyware distributor get my **Ubuntu** install of Firefox to do weird things?" I, for one, am interested in the real answer, and not HKLM dumps.

---

### Post by rustybronco on 2008-08-18
> **dandellion said:**
> I thought it's just something that passed the pop-up blocker, but it came second time. Out of regular browsing, new tab popped out, aiming to antivirus2008scanner.com. It is obviously a fake virus scanner that told me that my Vista is infectedd by spyware... 
OK, I know it is fake scanner, but how it can open its site out of nothing, and even more important, how to kill it?

The problem is not with firefox, most likely it is a problem with a hacked server you are trying to access.
probably a hacked .hta.
antivirus2008/2009, windows-defender ect. (it goes by a **lot** of other names) should be able to be removed by malwarebytes.org Anti-Malware.
thegsresources, another site I go to, had their server hacked, redirecting traffic to this "fake" product.

just remember there are a lot of windows users looking toward linux that are tired of the "krap" the have to deal with when using windows.
IMHO, help them.

---

### Post by todb on 2008-08-18
> **rustybronco said:**
> The problem is not with firefox, most likely it is a problem with a hacked server you are trying to access.

Hmm, I don't think so. According to the OP:

[QUOTE=dandelion]
Out of regular browsing, new tab popped out, aiming to antivirus2008scanner.com.[/QUOTE]

Reading this, it sounds like there's some mechanism that the evil site is using to create new windows in Firefox without (obvious) user interaction. This sounds likely something that Firefox's Popup blocker is designed to prevent.

Without a reference site, though, it's impossible to say what the event is that's escaping the popup blocker. It may be something as simple as a 

```
<body onClick=window.open("http://www.example.com/")>
click anywhere, even <a href="http://www.planb-security.net/">here</a>
</body>
```

..which of course Firefox's popup blocker interprets as an "intended" action, even though your click got hijacked non-obviously.

---

### Post by Titan8990 on 2008-08-18
These are the forums that you are looking for: [http://www.geekstogo.com/forum/Malware-Removal-HijackThis-Logs-Go-Here-f37.html&](http://www.geekstogo.com/forum/Malware-Removal-HijackThis-Logs-Go-Here-f37.html&)

---

### Post by rustybronco on 2008-08-18
> **todb said:**
> Hmm, I don't think so. According to the OP:
you're entitled to an opinion. but we have been through it
[http://www.thegsresources.com/_forum/showpost.php?p=881111&postcount=1](http://www.thegsresources.com/_forum/showpost.php?p=881111&postcount=1)
I use 8.04 with ff3. I have downloaded the viri and played with it. no problems with firefox.

---

### Post by cariboo on 2008-08-19
This isn't the first post about this particular bit of malware, a couple of nights ago someone posted the url to site where this thing was resident. Sometimes I enjoy playing with these things just to see what kind of trouble some unsuspecting user can get themselves into.

Jim

---

### Post by todb on 2008-08-19
> **cariboo907 said:**
> a couple of nights ago someone posted the url to site where this thing was resident.

I don't suppose you saved off the triggering html/js? None of the reports of the behavior ("hacked hta," "built-in link to Google," etc) are making any sense, absent sample code.

---

### Post by todb on 2008-08-20
This thread looks like a good candidate for an explination for your problem, Dandelion:

[http://ubuntuforums.org/showthread.php?t=894752](http://ubuntuforums.org/showthread.php?t=894752)

If so, could you mark this thread as [SOLVED] ?

---

