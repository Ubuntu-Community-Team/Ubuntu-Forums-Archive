---
title: "Update manager icon in taskbar"
date: 2012-04-09
forum: System76 Support
---

### Post by MoebusNet on 2012-04-09
I've been waiting for this to be fixed in Oneiric, but I haven't seen a fix in Oneiric or Precise either. I figured I'd ask here first, before going to the larger community -

When updated packages are available, the Update Manager icon shows up in the left taskbar. Unfortunately, I haven't been able to find a way to use this icon to actually show the Update Manager program to see what the updates are. The right-click menu for the icon does show "Install All" and a couple of other choices, but does not show the window for the Update Manager. Instead I must go to the Dash home icon and search for Update Manager to run the program so that I can see what updates are available and get a detail view of the download progress.

Has anyone else run into this issue and come up with a solution? TIA

---

### Post by isantop on 2012-04-10
Try checking your other workspaces to make sure it didn't simply open on a different workspace. Also, when I see this, I can usually work around the problem by focusing a different application, then coming back to Update Manager.

They haven't enabled automatic update notifications yet in Precise, so I couldn't tell you if this is fixed there or not.

---

### Post by MoebusNet on 2012-04-10
Thank you for your response. Of course, you are right about Precise - I've gotten so used to manually updating it in Vbox, I just took for granted it had the same issue. My bad.

However, in Oneiric I typically use 2 and sometimes 3 desktops - I have never been able to left-click on the Updates Available icon in the left taskbar to achieve any result on any desktop. The icon does appear at the proper time, and does display the correct number of updates available. However, I can find no left-click function for that icon.

I will continue to look for the Update icon next time it pops up so that I can get a snapshot to illustrate.

---

### Post by MoebusNet on 2012-04-14
OK, this is weird. The "Updates Available" icon appeared in my left taskbar. As always, I left-clicked on the icon with absolutely no visible response on any of the desktops. I right-clicked on the icon and chose "Update Manager" expecting it to open a window with the Update Manger program to review my updates. Again, no visible response on any desktop. I opened the Screenshot program to be able to show what's going on, but of course if you right-click the "Updates Available" icon to open the menu then attempt to click the screenshot button, the right-click menu for the "Updates Available" icon closes before you can get a screenshot. Frustrating.

After all these gyrations, I left-clicked the little > on the left side of the "Updates Available" icon and the window for Update Manager suddenly opened. Unexpected.

I know I'm still learning Unity, but at this point I still don't know what to expect in the way of behavior from the "Updates Available" icon. Either I'm missing something basic or the GUI behavior is not yet logically developed. Advice welcomed.

---

### Post by ubuntu27 on 2012-04-16
You can have x seconds of delay in screenshot app.

Just open the screenshot app, and chose the delay.

---

### Post by isantop on 2012-04-16
> **MoebusNet said:**
> OK, this is weird. The "Updates Available" icon appeared in my left taskbar. As always, I left-clicked on the icon with absolutely no visible response on any of the desktops. I right-clicked on the icon and chose "Update Manager" expecting it to open a window with the Update Manger program to review my updates. Again, no visible response on any desktop. I opened the Screenshot program to be able to show what's going on, but of course if you right-click the "Updates Available" icon to open the menu then attempt to click the screenshot button, the right-click menu for the "Updates Available" icon closes before you can get a screenshot. Frustrating.

After all these gyrations, I left-clicked the little > on the left side of the "Updates Available" icon and the window for Update Manager suddenly opened. Unexpected.

I know I'm still learning Unity, but at this point I still don't know what to expect in the way of behavior from the "Updates Available" icon. Either I'm missing something basic or the GUI behavior is not yet logically developed. Advice welcomed.

It is somewhat erratic. I'm hoping it's something that gets fixed soon. As for focusing it, you'll want to click on another application first, then click on the Update Manager icon again to bring it up.

Part of the problem is that they open the window up minimized (so as to be unobtrusive), but focused. Thus, it can't refocus it until you focus something else.

---

### Post by gandalf3 on 2012-04-16
> OK, this is  weird. The "Updates Available" icon appeared in my left taskbar. As  always, I left-clicked on the icon with absolutely no visible response  on any of the desktops. I right-clicked on the icon and chose "Update  Manager" expecting it to open a window with the Update Manger program to  review my updates. Again, no visible response on any desktop. I opened  the Screenshot program to be able to show what's going on, but of course  if you right-click the "Updates Available" icon to open the menu then  attempt to click the screenshot button, the right-click menu for the  "Updates Available" icon closes before you can get a screenshot.  Frustrating.

After all these gyrations, I left-clicked the little > on the left  side of the "Updates Available" icon and the window for Update Manager  suddenly opened. Unexpected.

I know I'm still learning Unity, but at this point I still don't know  what to expect in the way of behavior from the "Updates Available" icon.  Either I'm missing something basic or the GUI behavior is not yet  logically developed. Advice welcomed.
 		                   		  		  		 		 			 				__________________
				System76 Serval Pro w/ Oneiric, Dell D800 notebook w/ Lucid 			


the "Print Screen" key will take a screen shot.
(doesn't exactly fix the problem with the update manager though..)
hope this helps..

---

### Post by MoebusNet on 2012-04-17
OK, thank you isantop, gandalf3, ubuntu27 and everyone. One last question, slightly off-topic. I took a screenshot of my desktop to illustrate this thread, but couldn't post it because the resolution and file size both exceeded what the forum allows. I haven't found any way to adjust those properties in Screenshot. I could take a screenshot of just a portion of the screen, but not the whole desktop. Any advice?

---

### Post by isantop on 2012-04-17
Shift+Print Screen will let you drag to select the area. You can also manually crop it from within shotwell. 

Alternatively, you can try uploading it to an image hosting site like [Imgur](http://imgur.com), then post a link to it.

---

### Post by perishable on 2012-04-19
FYI, I encountered this on a non-System76 laptop.  A bug was filed here:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/898295](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/898295)

It seems that the behavior corrected itself for me, but I can't say if it was due to the instructions provided or an update that I did.  Also, the print  screen thing seemed to allow the Update Manager to popup if it got into the stuck state.

--P

---

