---
title: "I can not grab the edge of windows to pull them bigger"
date: 2014-02-26
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-26
For some reason, today, this is the case.

Is there some setting I can do to change this?

The little arrow briefly appears, but the line is so extremely narrow, it just can not be done anymore.
I was able to do this yesterday, before updates today.

---

### Post by ajgreeny on 2014-02-26
Change your theme?

That is usually the best answer, or just see if the bottom right corner is "catchable".

---

### Post by Cavsfan on 2014-02-26
> **sdowney717 said:**
> For some reason, today, this is the case.

Is there some setting I can do to change this?

The little arrow briefly appears, but the line is so extremely narrow, it just can not be done anymore.
I was able to do this yesterday, before updates today.

What I did to fix that problem was install CCSM and Emerald but, the Windows Decoration check box becomes unchecked at every boot/login.
But, one checked it usually stays and all is well with the windows corners. Sometimes I have to open CCSM back up and check it again but it's getting less often as time goes by.

I opened this bug against Compiz's windows decoration. [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1284266]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1284266")

BTW, I am in Gnome Flashback (with Compiz).

[_How to get Emerald window decorator on Trusty 64bit._](http://ubuntuforums.org/showthread.php?t=2192044)

---

### Post by sdowney717 on 2014-02-26
I was able to do this before an update. 
Why do I have to install a theme now?

---

### Post by mc4man on 2014-02-26
What session are you using?
What theme?
If possible, what was updated.
(have absolutely no issue here in unity session, ambiance, there is an invisible 10px grab area so quite easy..

---

### Post by sdowney717 on 2014-02-26
gnome
whatever theme ships with a beta install.

The corner grips are completely gone, seriously.

This is on the file manager window.
A terminal window works fine.

My file manager also lost its sharing tab.

Maybe my file manager has foobared itself.

---

### Post by mc4man on 2014-02-26
On my straight-up test install when I logged into gnome-shell nautilus could Not be resized. 
This was due to GTK+ being set to 'ambiance'  as seen in tweak tool. Switching GTK+ to Adwaita fixed

If by gnome you mean a session other than gnome-shell then I currently don't have..

---

### Post by sdowney717 on 2014-02-27
running gnome-shell

I installed gnome-tweak-tool

changed to adwaita

Still no handles to resize file manager.

a pic also shows no sharing tab, so it is strangely messed up

Will reinstalling it help?

adding

I reinstalled and nothing. So I found out nautilus share was not installed.
installed, reboot, and sharing tab is back.

still can not resize nautilus.

---

### Post by sdowney717 on 2014-02-27
[http://askubuntu.com/questions/131694/cannot-resize-windows-at-lower-right-corner](http://askubuntu.com/questions/131694/cannot-resize-windows-at-lower-right-corner)

found a workaround.
use alt plus middle mouse click
then the drag icon appears.

seriously I have no size drag ability with nautilus like it used to have.

---

### Post by Cavsfan on 2014-02-27
> **sdowney717 said:**
> I was able to do this before an update. 
Why do I have to install a theme now?

I was not suggesting you install a theme but if you're using gnome shell my point is moot any way.

---

### Post by mc4man on 2014-02-27
Maybe post a screen of gnome-tweak tool > Appearance tab. Will dupe your settings & see
(if you're using same as I posted then you have some other local issue as resize of nautilus works fine here.

Did you install Ubuntu then add gnome-shell or are you using the Ubuntu Gnome image?

---

### Post by sdowney717 on 2014-02-27
installed ubuntu, then installed gnome shell

---

### Post by mc4man on 2014-02-27
> **sdowney717 said:**
> installed ubuntu, then installed gnome shell

As I mentioned you need to change the **GTK+** setting to Awaita to get resize on a nautilus window (at least for the moment & as seen here

---

### Post by sdowney717 on 2014-02-27
I found it

Yes, you fixed it, I can grab the edge now.

---

### Post by Cavsfan on 2014-02-28
> **sdowney717 said:**
> I found it

Yes, you fixed it, I can grab the edge now.

Please mark this thread as solved if you have the solution. Edit the 1st post, go to advanced and then change the Prefix to "Solved".

---

