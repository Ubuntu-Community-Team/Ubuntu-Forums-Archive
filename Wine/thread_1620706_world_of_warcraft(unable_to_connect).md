---
title: "world of warcraft(unable to connect)"
date: 2010-11-13
forum: Wine
---

### Post by Fonzdude on 2010-11-13
wow loads up to login screen and after entering details sits on "connecting" for several minutes then "unable to connect"

Ubuntu 10.10
wine 1.2.1
using network card to d-link dsl502t 
loading wow from previous windows folder via wine

i recently installed ubuntu for the first time.... i had trouble with firefox so i searched around and did....

"the following works for me....... Open your Firefox and type 
      about:config at URL address bar and hit enter. U will get a list 
      of lines. Search for the lines given below( simply copy & paste in 
      search bar. Eg-paste'network.http.pipelining'). Make the following 
      changes. To make a False into True, select the line to change, and 
      double click. On the 2nd option change, right click and select Modify 
 
      - network.http.pipelining > Make it True 
 
      - network.http.pipelining.maxrequests > Make it 8 or 10 
 
      - network.http.proxy.pipelining > Make it True 
 
      - network.dns.disableIPv6 > Make it True"

which then allowed me to surf using firefox



could this effect wow?

any suggestions?

do i need to set up wine for internet games?

---

### Post by Fonzdude on 2010-11-13
firefox and ubuntu have access to internet but other programs sit there and not retrieve any data

---

### Post by cwwilson721 on 2010-11-13
Search this forum Question has been asked/answered NUMEROUS TIMES, and no sense repeating it AGAIN.

Read the sticky on the top of the forum, too, about asking questions.

---

### Post by Fonzdude on 2010-11-14
i have searched around and cant find a solution

---

### Post by cwwilson721 on 2010-11-14
You WHAT????

Used the word 'connection' in forum search, turned up 250 results
Of the first 25, 2 have 'WoW' in the title.

SEARCH IS YOUR FRIEND

If you won't even TRY to learn and help yourself....

---

### Post by ricardojcampo on 2013-01-26
> **cwwilson721 said:**
> You WHAT????

Used the word 'connection' in forum search, turned up 250 results
Of the first 25, 2 have 'WoW' in the title.

SEARCH IS YOUR FRIEND

If you won't even TRY to learn and help yourself....

You are one of those unfelpful elitist that think know everything, how hard would it have been to put the link to the right chat, instead of bullying the poor fellow. Who obviously doesnt know much about computers and is trying. Proof of that is that he is asking here. He obviously wants to learn and went into the trouble of doing a search to find the right forums.

---

### Post by frank604 on 2013-01-26
> **Fonzdude said:**
> 
loading wow from previous windows folder via wine

do i need to set up wine for internet games?

These two sentences are the error.  First of all you must install WoW in a wine environment.  You can issue a wine command to launch a wow.exe installed on your windows partition.

This is a good link on this forum regarding WoW + Wine. [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

Also look at WineHQ they have some user experience for WoW and some setup/config help. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

If you do not know much about wine, use a bottler like PlayOnLinux to set it up for you.

```
sudo apt-get install playonlinux
```I prefer playonlinux as it is a gui interface for wine/registry edits/winetricks/etc.

Edit: Also to those who like to write sarcastic comments that provide no insight or value, I'd reconsider how you approach the Ubuntu forums.  This isn't Archlinux where KISS is key.  Read up on what the word 'ubuntu' means. In fact, I have copied and pasted for your sake. 
> Ubuntu: "I am what I am because of who we all are." (From a definition offered by Liberian peace activist [Leymah Gbowee]("http://en.wikipedia.org/wiki/Leymah_Gbowee").)

---

### Post by Lightning Dragon on 2013-01-27
Hello,

Fonzdude, have you tried the HOW TO WoW thread? It is linked to in my signature, but I can post some things about the issue that might help you. Otherwise,  you can check out the thread in my sig and ask around there. They seem to know a lot about issues concerning WoW and whatnot.


[http://ubuntuforums.org/showthread.php?t=566876](http://ubuntuforums.org/showthread.php?t=566876)
[http://ubuntuforums.org/showthread.php?t=398662](http://ubuntuforums.org/showthread.php?t=398662)
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Also, if you can do it fast enough, disable Peer-to-Peer downloading under the Options menu. That might just do it for you. You can also try an older version of WINE, like 1.3 or 1.4, or even PlayOnLinux. 

Otherwise, I suggest looking into your Network settings, ISP settings and your Firewall because it sounds like Internet security problems, especially since you had problems with Firefox.

If you want to look into your Firewall or Network settings and need help doing so, I will be glad to offer my assistance. But for the ISP,  you will have to contact your provider.

[SIZE=1]cwwilson721, if you do not wish to help him, you do not have to.  It seems Fonzdude's thread is not your  first thread you have acted so aggressively in, either. [/SIZE]

[SIZE=1]frank604, good work posting that! Here are the other[SIZE=1] definitions[/SIZE] in case others would like to[SIZE=1] read it.[/SIZE][/SIZE]

> 
[SIZE=1]Tutu;

A person with Ubuntu is *open and available to others*,  affirming of  others, does not feel threatened that others are able and  good, based  from a proper self-assurance that comes from knowing that  he or she  belongs in a greater whole and is *diminished when others are humiliated  or diminished*, when others are tortured or oppressed.

One of the sayings in our country is Ubuntu &#8211; the essence of being   human. Ubuntu speaks particularly about the fact that you can't exist as   a human being in isolation. It speaks about our interconnectedness.  You  can't be human all by yourself, and when you have this quality &#8211;  Ubuntu  &#8211; *you are known for your generosity*. We think of  ourselves far too  frequently as just individuals, separated from one  another, whereas you  are connected and what you do affects the whole  World. **When you do _well_,  it spreads out; it is for the whole of  humanity**[/SIZE]**.**We have Ubuntu. We all are in this together.

EDIT:

And......I just realized two people posted in a 2010 and I contributed to the necro posting. Well, I hope our posts help others either way, if the thread isn't archived or locked for our rule breaking.

---

