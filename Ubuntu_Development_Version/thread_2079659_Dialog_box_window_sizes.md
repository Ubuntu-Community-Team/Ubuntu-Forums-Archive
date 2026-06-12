---
title: "Dialog box window sizes"
date: 2012-11-02
forum: Ubuntu Development Version
---

### Post by bash321 on 2012-11-02
Gtk window placement not remembering size when it is an open or save dialog window. 
Problem:
1. Open the open dialog on libreoffice. 
2. Window overlaps off screen. Does not fit on screen. 
3. Click the maximise button and the window adjusts as a maximised window that fits on the screen. 
4. Close window. 
5. Open window again. 
6. Same problem overlaps on screen does not remember that it was in a maximised state when I closed it from last time. 
7. Have to click maximise again!:confused:

What it needs to do:
1. The 2nd window should remember where it was in a maximised state (not overlap when i open it again) as I had left it when I had closed the 1st window. 
2. Window open and save dialog s should remember there state no matter how they are adjusted.  

I have filed a gtk bug. 
My response so far is that it is a Ubuntu problem. 

What I think is happening:
The open and save dialog window knows that it needs to be at a resolution as it was before... And that is what it is directly doing.  But, What the window needs to do though is to be told when it is opened to go to that size and resolution but to also go back into maximise mode as I had left it before.

Links:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760645](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760645) launchpad bug:
Bug filed with gtk developer: [https://bugzilla.gnome.org/show_bug.cgi?id=685347](https://bugzilla.gnome.org/show_bug.cgi?id=685347)
Screenshots in both links of what is going wrong. 

I have had this problem with many versions of ubuntu since 10.04.. Earlier. It would be great if it could be fixed... still happens in quantal 12.10.

It is quite annoying when the dialog doesn't remember its position or fits on the screen??
this happens on any open or save window in ubuntu on any program. Including Firefox... Chromium... Libreoffice... Archive manager.... Nautilus.... And many many many others.




Please help,
bash321.

---

### Post by dino99 on 2012-11-02
hm, the gtk report is marked as "solved" now

have you tested without compiz installed (like with gnome-session-fallback) ?

---

### Post by bash321 on 2012-11-02
No I have not tried gnome session fallback. But I will give it a go without compiz. 
I will try and unresolve the bug as well as its not resolved on launch pad I will unresolve it on the gtk bug.

---

### Post by bash321 on 2012-11-03
I have tried with gnome session fallback. And the size is remembered when I open and close the open dialog box on libreoffice writer. 

This works for gnome session fallback with effects. I even uninstalled compiz. 
Without effects you cannot maximise open and save dialog boxes on Ubuntu no option is displayed. 

The window remembers its size but it does not remember that it was in a maximised state where I had left it before. Thus I have to right click on the window and hit maximise for the window to maximise. 
I then close it. And the application.  re open libreoffice writer and the open dialog box right click on it and it hasn't remembered so I have to click maximise on the window. This included shutdown and restart tests with the same problem still occurring. 

Is there a way for the window to remember that it had been left in a maximised state as it then would fit onto the screen properly in a maximised window all the time. Especially for open and save dialog boxes. 

Bash321

---

### Post by bash321 on 2012-11-06
Edited reports and changed status of reports. 

Could this also be a unity window decorator problem? With open and save dialog boxes on Ubuntu because I tried the same tests on xubuntu and they worked perfectly compared to using the normal Ubuntu. 

Bash321

---

### Post by mc4man on 2012-11-06
it would seem the problem is some windows like the ones you've mentioned won't/can't open integrated into the unity panel so they open 'semi-maxed' but below the unity panel.
So it would appear to be a Unity only issue & Not a low resolution display issue

If one was to set an 'open' window to only open maximised in compiz > window rules then it  **likely** would open  integrated into the unity panel.
Though in a quick test of vlc's open file dialog window it's not seen as any different than vlc
(so the setting would be for vlc, not just it's open <whatever> window

Edit: in the case of libreoffice you could set the open window itself to only open maxed - 
class=Soffice

---

### Post by bash321 on 2012-11-19
I have tried setting those settings with window rules in compiz to make the windows auto resize and stay maximised... I tried it with VLC, and it's open dialog window to maximise with the unity window decoration. It did not work.

It did not stay auto resized and maximised when I had closed it.

I am not sure.. if I am doing the correct compiz rules for the windows and specifically for the open dialog in VLC.

It would be great if there was some feedback or wiki to help me setup the correct commands for the compiz maximised windows and unity window decorations rules using ccsm to stay maximised and resized.

I am currently now using raring 13.04 on my desktop to fix this issue.

bash321

---

### Post by dino99 on 2012-11-19
i propose you open a new report, and add into it the related old bugs  seen on post #1; maybe against debconf.

---

### Post by mc4man on 2012-11-20
> **bash321 said:**
> I have tried setting those settings with window rules in compiz to make the windows auto resize and stay maximised... I tried it with VLC, and it's open dialog window to maximise with the unity window decoration. It did not work.

It did not stay auto resized and maximised when I had closed it.


Was actually using vlc as one example of many where the  "Dialog box" would be treated as an app itself window so maybe a case where you wouldn't want to set the max window rule (unless you want vlc  only & always  maximized.

As far as the " open dialog on libreoffice", just do as in screen
(- enable window rules > add
class=Soffice 

Libreoffice is more the exception here.

---

### Post by bash321 on 2013-01-01
window rules has no effect and it has the exact same problem..
will create a new bug report with all of the information about the problem.
will also post a new bug on libreoffice bugzilla as well as launchpad.

all links are here from ubuntuforums, and libreoffice and gtk gnome bugzilla are all in this launchpad post.
hopefully somebody can resolve this problem quickly.
[https://bugs.launchpad.net/df-libreoffice/+bug/1097089](https://bugs.launchpad.net/df-libreoffice/+bug/1097089) 
bash321

---

### Post by bash321 on 2013-02-11
Bug has partially been resolved in LO 4.0.0.3.
Version 4.0.0.3 (Build ID: 7545bee9c2a0782548772a21bc84a9dcc583b89)
Ubuntu 13.04 Raring 64 Bit.

Open Dialogue Window does not overlap any more when checkbox is checked in CompizConfigSettings manager for maximised windows under the Window Rules Option.

The WIndow is fully maximised with Unity Integration in LibreOffice, and it remembers its maximised state in the application.

The problem is that this only occurs when it is checked using CompizConfigSettings Manager, can this now be constructed as being the default process for Open and Save Dialogue windows that are maximised in Ubuntu? 
Without having to check the maximised windows option in CompizConfigSettings Manager, so that they may have full unity integration on the display monitor. 
I would also like to escalate this query to other programs within Ubuntu, as it has the same maximise issue for open and save dialogue windows in programs such as Rhythmbox, and Evince Document Viewer.
It is a common bug on Ubuntu Systems with Unity.

---

### Post by bash321 on 2013-02-11
mc4man = your solution worked for the gtk open and save dialogue box windows problem with maximised windows. I wish it was integrated into Unity by default, as it would reveal a cleaner less time consumer interface for Open and Save Dialogue Box Windows in Ubuntu, and for its users.

---

### Post by bash321 on 2013-05-20
It is a common bug on Ubuntu Systems with any version of UNITY installed.
Please Help!
I have received no communication lately from anyone who can resolve this issue.
This is still an occurrence on the latest development release of Ubuntu Saucy 13.10 and it should be RESOLVED ASAP. As there is clearly a design error with gtk+ integration the file manager and open and save dialog windows running on any gtk+ program in Ubuntu.


A LibreOffice Developer has even posted that they cannot fix this issue as it is clearly a design error and issue with Ubuntu "Unity".
I can also provide a desktop recording video attachment to show my exact problem and bug. 
bash321.

---

### Post by dino99 on 2013-05-20
Well, you already know that actual unity is based on gtk; and the "next" unity is rewritten with qt. Meaning that actual issues with the gtk design is not receiving much attention, but the "critical" ones.
Thats the actual transitional "unstable" status: actual unity/compiz is slowly dying and the "next" is still a work in progress.
So on my side i have opt-in for gnome-shell (gnome3-team ppa) which is closely the same as unity regarding many features (but not all, GS is also a work in progress)

---

