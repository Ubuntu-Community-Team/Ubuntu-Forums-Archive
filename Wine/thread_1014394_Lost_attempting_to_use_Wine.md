---
title: "Lost attempting to use Wine"
date: 2008-12-17
forum: Wine
---

### Post by northmantim on 2008-12-17
hrmm...I am attempting to get my Lord of the Rings Online game working. So, I downloaded "Wine" and installed it as per this link
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14566](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14566)
and this post;
> 
you will need to start by having wine instaled copy and paste this into your terminal,hit return ,enter your password then return (your password wont be visible)
Code:

sudo apt-get install wine

And I almost finished with the directions in the How to section on the link I have here, but I am stuck on what it means, "add the keys from regedit section". I followed the directions given to me by Vantrax by "alt f2", "regedit" and the registry editor window pops up. What do I do now in order to add the keys? I dont understand...:confused:
O, so :confused:
Can someone Please help? 
Just remember, I am no geek, and I barely have any understanding of computers aside form the EVIL Windows settings which I have thrown out the door when I wiped my computer to put in Ubuntu.
Thanks in advance.

---

### Post by m_a_b on 2008-12-17
You might consider saving yourself a LOT of time and frustration tinkering around with Wine and pay the good guys at Codeweavers to do it for you.

[http://www.codeweavers.com/compatibility/browse/group/?app_parent=4029;](http://www.codeweavers.com/compatibility/browse/group/?app_parent=4029;)

I started using this program about 6 years ago and haven't looked back since - I'll GLADLY pay them their $40 to avoid having to try to configure wine myself.

---

### Post by northmantim on 2008-12-17
hehe would be nice, but money's short right now. Just got out of the Army last month and still cant find any work. I should probably learn how to do it myself anyway, after all, I am sure there are jobs out there where this type of experiance would come in handy.
I can learn this stuff pretty quickly, but I just need someone to coach me along on it. maybe there is a "Dummies" book out there on how to do alot of this stuff...hrmm...might have to find out, after I can find work that is hehe.

---

### Post by m_a_b on 2008-12-17
hehe... book = $25... Crossover = $40...  I'd just get crossover!  :lolflag:

---

### Post by northmantim on 2008-12-18
I still can't get Wine running so I can load Lord of the Rings Online game. I followed all the directions I can find, followed the replies to my last 2 posts about it, and still nothing.
This is what I did:
   "
hrmm...I am attempting to get my Lord of the Rings Online game working. So, I downloaded "Wine" and installed it as per this link
Quote:
[http://appdb.winehq.org/objectManage...sion&iId=14566](http://appdb.winehq.org/objectManage...sion&iId=14566)
and this post;
Quote:
you will need to start by having wine instaled copy and paste this into your terminal,hit return ,enter your password then return (your password wont be visible)
Code:

sudo apt-get install wine
And I almost finished with the directions in the How to section on the link I have here, but I am stuck on what it means, "add the keys from regedit section". I followed the directions given to me by Vantrax by "alt f2", "regedit" and the registry editor window pops up. What do I do now in order to add the keys?"
(Copied and pasted from my last post about the subject)

The only reply to the post told me to buy a Cross Over. I would actualy like to NOT buy anything to get it running.
Can anyone PLEASE tell me how to get this running PLEASE? Or should I just go back to windows and forget the whole thing?

---

### Post by snova on 2008-12-19
What they want you to do is add a value to the "registry" that Wine emulates.

I assume that by "regedit section" they mean this bit furthur down:

[QUOTE]
From an exported terminal insert the following as string values:
HKEY_CURRENT_USER/Software/Wine/Direct3D/VideoMemorySize = < amount of video memory ie 256 >
[QUOTE]

I'm mostly guessing here, but I believe it means to navigate the tree on the left to "HKEY_CURRENT_USER/Software/Wine/Direct3D", and then set the value on the right named "VideoMemorySize" to 256 (or create a new key if it doesn't exist already).

---

### Post by 3rdalbum on 2008-12-20
The main problem here is that you're trying to shoehorn Windows programs onto a non-Windows operating system. It can sometimes be done, but by the very nature of it (reverse-engineering) it is difficult to do. **Linux is not designed to run Windows programs, just as Windows isn't designed to run Linux programs.**. The best attitude to take with Wine is to assume that it won't run the program you want, and be pleasantly surprised if it does.

Please tell us what about snova's post you are finding difficulty with, and we can take things from there. One thing he didn't mention is that there is a menu item to "Create a new key" once you've reached the location that you want to add it in.

Alternatively, is it urgent that you get your game running ASAP? It looks like you're jumping into the deep end a little.

If you decide to move back to Windows, note that you may well have to learn to use the registry editor on Windows anyway; the Wine registry is actually a simulation of the Windows one, and I've seen lots of "How to do xyz on Windows" articles that involve the use of Regedit.

---

