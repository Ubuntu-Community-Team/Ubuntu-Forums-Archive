---
title: "Lost high resolution in VirtualBox"
date: 2010-01-23
forum: Virtualisation
---

### Post by Stevo0687 on 2010-01-23
Hey all!

I have Ubuntu 9.10 and have been running Windows 7 in VirtualBox for a few months.  When I installed VirtualBox and Windows 7, I installed the Guest Additions.  Everything worked great at the time.  I could move between VirtualBox and Linux without a problem or needing to press the host key and I could enter full screen mode and the virtual OS would fill the entire screen to 1440x900 resolution.  In fact, any size I made the window automatically changed the resolution so that I never had bars on the side to scroll around.  About a week ago, I had some sort or problem shutting down VirtualBox while running Windows 7 and since then, the resolution doesn't automatically adjust.  I'm not sure if the "crash" is related to that or not, but it happened around that time.  I have since tried to install the guest additions just in case they were lost and everything appears to install correctly, but I still can't get the full resolution. 

When I decreased my resolution today, it took away any options above that resolution, even though it existed before. 

Does anyone know what the problem might be from and how I could fix it.  I'd prefer to not have to start over with a new "installation."  I would assume that the guest additions are installed on the virtual OS file so uninstalling and reinstalling VirtualBox won't fix it, correct?  Any help would be greatly appreciated.  Thanks.

---

### Post by Stevo0687 on 2010-01-23
About 30 seconds after posting this, I found my problem.  While not in full screen mode (which decreases VirtualBox menu options), I went to Machine->Auto Resize Guest Display.  I have never adjusted that before so I didn't think to mess with it before.  I guess that is something that was set when I installed the Guest Additions and was somehow "unchecked."  Once I checked that I could RightCtrl+F and the virtual OS would use the whole screen at 1440x900 resolution and resizing the screen when not in full screen mode now changes the resolution.

---

### Post by blackened on 2010-01-23
> **Stevo0687 said:**
> EDIT: I tried to edit my original post to mark it solved, but couldn't see how to.  Maybe that is up to admins...  If not, please explain.  Thanks...

Odd, it should have let you edit the original post.

I take it then that you've sorted out the problem on your own? If so, then could you be coerced into taking some time and posting how you went about it so that others may refer to your fix in dealing with comparable problems?

---

### Post by Stevo0687 on 2010-01-23
> **blackened said:**
> Odd, it should have let you edit the original post.

It lets me edit it, but it wasn't letting me change the drop-down box that listed SOLVED when I originally posted.  I edited the title though.

> **blackened said:**
> 
I take it then that you've sorted out the problem on your own? If so, then could you be coerced into taking some time and posting how you went about it so that others may refer to your fix in dealing with comparable problems?

I'm sorry.  I did type up an explanation and thought it posted, however it now shows as a double-post.  I'm not sure where my second post and explanation went.  I will try to update my second post with an explanation.

---

### Post by blackened on 2010-01-23
Good deal, glad you got it sorted out. In the not-so-immortal words of Gavin Rossdale: it's the little things that kill.

---

