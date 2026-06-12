---
title: "Scopes installing/using not intuitive"
date: 2016-03-14
forum: Ubuntu Phone and Tablet
---

### Post by wskellenger on 2016-03-14
Here is my brief experience with scopes so far.  I've had Ubuntu installed on my Nexus 4 and I'm going to try to use it for the whole day today.  

I think I can get my head around the concept of scopes after reading the developer documentation.  Yet, their installation and use is really not intuitive at all.



[LIST]
[*]To get scopes, one goes to the app store, finds a scope, and installs it like an app.
[*]After installation, the scope won't be visible in the list of apps.
[*]To see the scopes installed, you must 'manage' apps (in app screen, swipe up from bottom).
[*]To actually use a scope, I have to mark it as a favorite (star it), and then it is available with a swipe left.
[*]Scopes are only available in the apps screen with left swipes.
[*]To uninstall a scope, I have to go to the app store again, find the scope that is installed, and tap uninstall.
[*]My understanding is that scopes can be customized, yet the "Today" scope only seems to have Weather and Tasks?  Can I further customize this, or is this the limit?
[/LIST]

Is there anything wrong/incorrect about these statements?

---

### Post by David_Farkas on 2016-03-16
I treat scopes as app previews (maybe the only exception is the Apps scope). So you need at least one application which is responsible for the scope. E.g. the My Music scope lists your audio files and you can listen to the individual files but if you need other functionalities (like playlists) you need to use the Music app. Same with the Instagram, My Photos, My Videos, Youtube etc. scopes.
1st 2 statements are correct.
If you want to manage scopes, you can swipe up on either scope (not only on Apps scope).
You can rearrange the scopes by pressing and holding them (under Manage). So you are free to place a newly installed scope before the Apps scope as well.
As far as I know, 6th statement is correct. Apps can be uninstalled by pressing and holding but for scopes I couldn't find a similar approach.
For me the Today scope offers much more than 2 options. The Today scope is basically a summary of other scopes. I.g. you can have a separate Weather scope if you want.

---

### Post by wskellenger on 2016-03-25
> **David_Farkas said:**
> I treat scopes as app previews (maybe the only exception is the Apps scope). So you need at least one application which is responsible for the scope. E.g. the My Music scope lists your audio files and you can listen to the individual files but if you need other functionalities (like playlists) you need to use the Music app. Same with the Instagram, My Photos, My Videos, Youtube etc. scopes.
1st 2 statements are correct.
If you want to manage scopes, you can swipe up on either scope (not only on Apps scope).
You can rearrange the scopes by pressing and holding them (under Manage). So you are free to place a newly installed scope before the Apps scope as well.
As far as I know, 6th statement is correct. Apps can be uninstalled by pressing and holding but for scopes I couldn't find a similar approach.
For me the Today scope offers much more than 2 options. The Today scope is basically a summary of other scopes. I.g. you can have a separate Weather scope if you want.

Thank you David, sorry for my delayed response.

Regarding the today scope, I must not have enough apps installed yet to make full use of it.

I've thought more about this -- scopes share some similarities to Android widgets, but they're different:

(MAY OR MAY NOT BE CORRECT BELOW, please make corrections if not?)

[TABLE="class: grid, width: 800"]
[TR]
[TD]**Feature/Behavior**[/TD]
[TD="align: center"]**Android Widget**[/TD]
[TD="align: center"]**Scope**[/TD]
[TD="align: center"]**Notes**[/TD]
[/TR]
[TR]
[TD]Installed as an app from the app market/store[/TD]
[TD="align: center"]Y[/TD]
[TD="align: center"]Y[/TD]
[TD="align: center"][1][/TD]
[/TR]
[TR]
[TD]Shows up as an app in the app launcher[/TD]
[TD="align: center"]Depends on developer[/TD]
[TD="align: center"]N[/TD]
[TD="align: center"][2][/TD]
[/TR]
[TR]
[TD]Can be ***provided*** by an app[/TD]
[TD="align: center"]Y[/TD]
[TD="align: center"]N?[/TD]
[TD="align: center"][4][/TD]
[/TR]
[TR]
[TD]Can aggregate data from other apps[/TD]
[TD="align: center"]Maybe?[/TD]
[TD="align: center"]Y[/TD]
[TD="align: center"][5][/TD]
[/TR]
[TR]
[TD]Uninstall not intuitive[/TD]
[TD="align: center"]Depends[/TD]
[TD="align: center"]Y[/TD]
[TD="align: center"][2] [3] [4][/TD]
[/TR]
[TR]
[TD]Can be displayed only in a full screen view[/TD]
[TD="align: center"]N[/TD]
[TD="align: center"]Y?[/TD]
[TD="align: center"][/TD]
[/TR]
[/TABLE]


[1] Android widgets are provided in the Play Store as apps, very similar to how Scopes are offered.
[2] The app providing the widget MAY OR MAY NOT make itself visible in the app launcher.  An example of one that DOES NOT: [https://play.google.com/store/apps/details?id=at.bleeding182.flashlight&hl=en](https://play.google.com/store/apps/details?id=at.bleeding182.flashlight&hl=en)
[3] If the widget doesn't manifest itself as an app (see [2]) then uninstallation is difficult.  You must go to Settings --> Apps --> Downloaded --> find the widget --> Uninstall.  Ubuntu Touch is similarly difficult, see the discussion above.  My mom will not know how to do this.
[4] In Android, you may have widgets available that you weren't aware of, as they are provided by applications.  These widgets cannot be uninstalled unless you remove the app providing them.
[5] Scopes seem to offer the opportunity to aggregate data from many sources, i.e. the today scope can collect information from OTHER APPS that you have installed?  This offers some interesting possibilities that widgets, to my knowledge, don't offer *easily*.  An Android app I guess could provide an interface for other installed apps and provide similar functionality?

I guess I'm so far not really sold on the lack of a home screen...  On a PC I have a desktop, which is sort of my home screen.  Here I can arrange my 'stuff', just like I arrange my real physical desk.  On Ubuntu Touch why is there no desktop analog, if 'convergence' is really the endgame?

---

