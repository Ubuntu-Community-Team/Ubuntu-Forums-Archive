---
title: "Diablo 2 LOD instal error"
date: 2010-10-19
forum: Wine
---

### Post by grafoman on 2010-10-19
```
Setup was unable to add the following file to c:\Program Files\DiabloII\d2char.mpq:

binkw32.dll

Error 0x85200064:

(P:\Data\D2\TOOLS\Diabinst\Source\MpqUtil.cpp:32)

Installation aborted.
```
Can anyone help pls?

---

### Post by Grenage on 2010-10-19
Hi there,

You're best off posting in the WINE section, you'll likely get more pertinent help.  If you Report your post, an admin may move it for you.

---

### Post by grafoman on 2010-10-19
I did. Thanks Grenaga.

---

### Post by beastrace91 on 2010-10-19
Sounds like you have corrupted install files. Redownload them and try again.

~Jeff

---

### Post by JedMeister on 2010-10-29
Hey grafoman, Did you work this one out? I'm having exactly the same issue.

I found a post on a relevant [Wine bug]("http://bugs.winehq.org/show_bug.cgi?id=2367#c11") that hints at a fix/workaround but I'm not sure how to do it:

> Torsten Schönfeld 2009-04-02 09:45:20 CDT

I recently ran into this problem as well.  In the end it turned out to be due to what [comment #8]("http://bugs.winehq.org/show_bug.cgi?id=2367#c8") refers to already: if you mount the installation CDs/ISOs of Diablo II with the 'unhide' option (as AcetoneISO does, for example), your installation will be contain corrupted files.  Installing Lord of Destruction will fail when it tries to update one of those corrupted files.

So I think this is not a wine bug.PS I've been using AcetoneISO.

Any ideas how we might try this?

---

### Post by grafoman on 2010-11-02
> **beastrace91 said:**
> Sounds like you have corrupted install files. Redownload them and try again.

~Jeff
I have 2 different images, both are correct.

For JedMeister: Still have the same error. I don't know how to mount my image with unhide option. Any new ideas? :confused:

---

### Post by eoliveira14 on 2012-05-29
Sorry to ressurect this thread, but I have the **exact same** problem and can't find anything in AcetoneISO such as unhide option... I'd much apreciatte any help! :???:

*Edit: Let me add that after getting this error for like 3 times, I also tried to install only Diablo II classic, without LoD expansion. Then the game just won't run, even though installation seems succesfull (about its end, when the graphics testing starts, the 'top taskbars', with close, minimize and maximize buttons vanishes)...

---

### Post by misskitty3681 on 2012-06-10
I have had the same error occur. I have never had this problem until recently when I installed the game. I have a feeling with all the windows XP service packages that this is the reason it is occurring. 

Anyways, I could only install diablo II as a single player and not as a full version (not having to swap CDs). On blizzard it mentioned downloading the patch from the game. I clicked on battle.net from the start up menu option in the game. It automatically downloaded the patch. I could then exit the game and upgrade my game to full version. 

For video porblems, after doing the video test it set my video it set the video and would not work. I could hear sound, but not images. I exited the game and changed the video setting to the not recommended one. It worked after that. 

My on going issue is not being able to install the expansion set. I read to download the game from battle.net so I am trying that. You can register your game and download from the site. It is also showing char2 error. I deleted all the diablo II files I saw before installing again. 

If it works, I will let you know. If it doesn't I hope someone figures it out and posts it.

---

### Post by misskitty3681 on 2012-06-13
I  have solved it! Well I got help from  Blizzard, but it worked! I knew it had a link with windows. I have CD  games in good working order and that I have had since diablo II came  out.  What the issue is that something on your computer is blocking the  d2char.mpq to be downloaded. You need to find that "thing." Now, I  downloaded both games and installed them from the digital downloads. I  have not tried the CDs. I did have the same problem occurring prior to  the changes that I made to fix the problem. 


1.) Turn off windows firewall. (you can find out later how to make diablo II and LOD an exception for blocking)
2.) Make sure to have up to date versions of any other virus checkers you may have
3.)  Find a norton virus tool remover. Any of those virus checkers like that  see if there is an official remover for it. I have not had norton on my  computer in a long time, but after I did that I saw an immediate  difference. 
4.) Make sure your account is administrator. If not, create another login and make that an administrator.

5.) Try downloading it from the battle. net site with a digital download to make sure that there is nothing wrong with your CDs


Overall: Need to find out what is blocking the installation. Hope this helps!

---

