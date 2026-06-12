---
title: "trojan problem in windows"
date: 2008-06-12
forum: Windows
---

### Post by mykalreborn on 2008-06-12
hi there!
because i'm a music composer and because i can't get around jack and all the linux apps, i tried windows because it's easier.
and it's free anyway :) :P
but now i have a problem with this trojan which i can't seem to be able to delete. i've tried all sorts of software, including sdfix.

every day almost there's a dll created in the system32 folder, which is named in a random manner (like iiGhfpt.dll) and every time the rundll32.exe works and loads this dll. if i struggle with software like unlocker i can delete the file, but usually the next time i start windows - even from hibarnate - it's at it again.
it's not really showing that it's doing much - rarely a new tab appears out of the blue in firefox, and that's pretty much it, but since it's allways running, who knows what it's doing. 

then i used comodo to see the internet activity and firefox has about 10 or more connections when rundll32 loads the trojan. comodo also shows that all the connections - apart from 2 or 3 - are working - that is downloading and uploading, allthough i wasn't downloading or uploading anything.

i know it's a trojan because mostly all of the software i've scanned the system with saw those dlls and toled me they're trojans. the problem is that every time i delete one, another one appears.

i turned to linux people, because i know you usually have better solutions to these manners than the others. so do you have any recomandations?

---

### Post by karellen on 2008-06-12
spybot: [http://www.safer-networking.org/](http://www.safer-networking.org/)
spyware terminator: [http://www.spywareterminator.com/](http://www.spywareterminator.com/)
superantispyware: [http://www.superantispyware.com/](http://www.superantispyware.com/)

---

### Post by cmay on 2008-06-12
hi.
i had the same problem when i was recording in windows.
there is a lot of spyware in free plugins and stuff like that for windows.
here is the one solution i had adjusted to.
1 
always use the computer dedicated for audio whitout any internet connection.
2
if you wanna be sure you dont have trojans spyware and rootkits in a computer you already know is infected there is no other alternative than reinstall. 

if you are a pro composer then you have to think about if 
you can afford to loose a lot of work. 

you can try the spyware and trojan removal tools first to see if it helps.
but that one sounds very bad and the best adwise i can think of is to start working offline whit the pc you use for music production  and then get a cheap second hand computer to use for internet acces. 
windows or linux or what ever you like as personal pref.
i hope this could help you as much as it did for me back then.

---

### Post by Kevbert on 2008-06-12
+1 for Spybot.
For free antivirus and firewall try [ZoneAlarm]("http://majorgeeks.com/ZoneAlarm_Free_d388.html") 
Majorgeeks website has lots of useful stuff especially for things like [spyware]("http://forums.majorgeeks.com/showthread.php?t=35407")

---

### Post by r76 on 2008-06-12
Good advice cmay,

> **cmay said:**
> if you wanna be sure you dont have trojans spyware and rootkits in a computer you already know is infected there is no other alternative than reinstall.

I would add to that, learn how to image your windows disk (there are free tools to do this).  Once you have a clean install of Windows + updates etc., image a good working version of Windows.  Restoring that image if you encounter such problems in the future (and it sounds like you might with downloads of dubious character) will be many, many times faster than reinstalling.

---

### Post by mykalreborn on 2008-06-12
well, i would buy a new computer, but i really don't have the money.
the thing is it didn't happen to me before. i've been running windows with internet and only firewall - no antivirus - for quite some time now, and this is basically the first time i have problems.
it's really silly that these people from microsoft ask money for this os when you have linux. this is one of the reasons i'll never feel guilty for pirating windows. :P
thanks for the many replies. will try the software recommended and i'll even post the result here. :D

---

### Post by mykalreborn on 2008-06-12
so i tried spybot and it detected the fellow. it's called - it was called, now it's gone ^_^ - virtumonde, and he was really nasty to remove. 
in case anyone has any problems like this, here is a great guide to the problem: [http://www.bleepingcomputer.com/forums/topic18610.html](http://www.bleepingcomputer.com/forums/topic18610.html)
thanks for the help again. now my windows box is finally working right. 
cheers!

---

### Post by karellen on 2008-06-12
> **mykalreborn said:**
> so i tried spybot and it detected the fellow. it's called - it was called, now it's gone ^_^ - virtumonde, and he was really nasty to remove. 
in case anyone has any problems like this, here is a great guide to the problem: [http://www.bleepingcomputer.com/forums/topic18610.html](http://www.bleepingcomputer.com/forums/topic18610.html)
thanks for the help again. now my windows box is finally working right. 
cheers!

glad you solved your problems ;)

---

### Post by dacorr on 2008-06-12
I would check the registry and specifically the autorun locations of it.

Would try a live CD option to exact the registry files and use an external editor to remove the keys and delete the infected files, bypass windows generally to fix it.

Dac

---

### Post by mykalreborn on 2008-06-12
> **dacorr said:**
> I would check the registry and specifically the autorun locations of it.

Would try a live CD option to exact the registry files and use an external editor to remove the keys and delete the infected files, bypass windows generally to fix it.

Dac

well, spybot deleted entries from my registry too, so i won't have to. :)

---

### Post by Nessa on 2008-06-12
Good for you. I hope you kept the anti-virus software.

---

