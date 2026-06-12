---
title: "Securing publicly accessed computers. Need Help"
date: 2010-07-31
forum: Security
---

### Post by onesimus7 on 2010-07-31
WARNING : This idea might sound crazy, stupid or hellishly hard for others, but since ubuntu is open-source i'm pretty sure someone can help me on this.

Hello everyone, Although this could be my first post on this community, I'm pretty serious on what am i going to ask. Right now I'm currently looking for a way to customize the system behavior of a certain account on ubuntu(e.g Guest/Student/Visitor Accounts), which can be defined via administrator account. Only administrator can shutdown, logoff, logout the said account, locking also certain functions/applications/hotkeys that could over-ride the system settings(more like Lockdown Editor[Pessulus])

Basically this is the idea: 
A publicly accessed computer that can only surf the net and use certain applications more like a cloud-based/netbook way(e.g. Open Office) with a timer on display(which will prompt when time is near expiration). 

Timer can be triggered and bumped with a certain key/key combination. (Example scenario : Everytime the staff presses [ctrl+alt+0] It will add 5 minutes to the timer) After the certain time alotted for that user, all applications will be closed(reset in original configurations and settings) all files added on desktop will be wiped, closing also the browser and clearing its cache. This is to secure firstly the users accounts and files and to make the computer clean from anything.

When account is on-standby, screen will only go on screensaver mode(not logging off), showing pictures on a specified folder which the system admin will define.

I'm open to suggestions and ideas. I know this might sound a little bit promising or somewhat sh*tty, we are willing to spend or donate to actually make this possible(but not really big, that's why we're here on an open-source community).

PS. I'm a noob in ubuntu but i searched and I've found/sourced out a behavior that have similarities on this idea. [http://www.fatwallet.com/forums/technology/981157/](http://www.fatwallet.com/forums/technology/981157/)

Thanks in Advance!
Onesimus

---

### Post by bodhi.zazen on 2010-07-31
google search the term "kiosk" + gnome or kde

There are several distors you may want to look at as well

[http://www.zencafe.web.id/](http://www.zencafe.web.id/)

---

### Post by ubunterooster on 2010-07-31
[http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)

---

### Post by onesimus7 on 2010-08-01
I'm not really looking for a "cafe management software", i need a standalone kiosk program that has a timer for itself..

---

### Post by bodhi.zazen on 2010-08-01
> **onesimus7 said:**
> I'm not really looking for a "cafe management software", i need a standalone kiosk program that has a timer for itself..

If you google search as I suggested you will find several how-tos, here is an example

[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html)

You will need to adapt the how tos to your needs.

So while you may call it "cafe management software" , the term kisok if used in a google search should yield the information you seek, although yes you may need to adapt a bit as well.

---

### Post by onesimus7 on 2010-08-01
Yes, i did google that even before posting this thread. As i mentioned on my first post, i found a way to lock down features etc. But currently i'm looking for way to do this "Timer can be triggered and pumped with a certain key/key combination. (Example scenario : Everytime the staff presses [ctrl+alt+0] It will add 5 minutes to the timer) After the certain time alotted for that user, all applications will be closed(reset in original configurations and settings) all files added on desktop will be wiped, closing also the browser and clearing its cache. This is to secure firstly the users accounts and files and to make the computer clean from anything."

I saw internet kiosks that will disable everything but will only browse the net, i also found a way to make chrome incognito-default so that no data will be saved while users browse that the net. 

But i really need to find a way that after the users allotted time, all application will close automatically,  without saving anything, clearing all the files that the user saved on his desktop. Locking also the mouse and keyboard, then turn to screensaver mode.

---

### Post by HermanAB on 2010-08-01
Use a virtual machine.  Store a tar ball and restore the tar ball when the time is up.

---

### Post by grg3 on 2010-10-19
I have built a kiosk system similar to the one discussed here: [http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

I used most of the ideas listed here, but I did not employ bastille. I started building a kiosk system using Gutsy Gibbon and have continuously updated it as new releases come out. I have been tweaking the Lucid version recently by adding a few custom scripts. 

Let me know if you have any questions.

---

