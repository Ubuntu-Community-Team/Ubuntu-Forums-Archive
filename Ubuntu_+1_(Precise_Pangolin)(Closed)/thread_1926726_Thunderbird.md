---
title: "Thunderbird"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by clifford junior on 2012-02-16
Anyone else having problems with Thunderbird after the latest updates. I noticed Thunderbird got an update and now when I open it, i'm presented with a blank white space where the email data was.

---

### Post by clifford junior on 2012-02-16
screenshot

---

### Post by effenberg0x0 on 2012-02-16
> **clifford junior said:**
> Anyone else having problems with Thunderbird after the latest updates. I noticed Thunderbird got an update and now when I open it, i'm presented with a blank white space where the email data was.

It's working as usual for me. 

Regards,
Effenberg

---

### Post by clifford junior on 2012-02-16
> **effenberg0x0 said:**
> It's working as usual for me. 

Regards,
Effenberg
are your sound settings opening? i seem to be having many problems at present. ive refrained from partial upgrades.

---

### Post by exploder on 2012-02-16
Thunderbird looks just like the screen shot on my system.

---

### Post by ybytyruzu on 2012-02-16
Same here, last Thunderbird update only open a blank white space....

---

### Post by Gregory Lee on 2012-02-16
Thunderbird works fine here.  I just tried Sound Settings and it seems okay (except "test" plays nothing for left speaker, and says "Left. Right." when the right speaker is tested -- Wait, maybe I don't have a left speaker, and the system has sensed that).

---

### Post by clifford junior on 2012-02-16
> **ybytyruzu said:**
> Same here, last Thunderbird update only open a blank white space....

im glad im not the only one then..

unrelated but i noticed when playing music with either audacious or clementine, the album art under the sound drop down is way over to the right and mainly off screen.

---

### Post by ybytyruzu on 2012-02-16
Here is the some thunderbird error log:

Timestamp: 02/16/2012 11:45:08 PM
Error: [Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: chrome://messagingmenu/content/thunderbirdMenu.js :: <TOP_LEVEL> :: line 41"  data: no]
Source File: chrome://messagingmenu/content/thunderbirdMenu.js
Line: 43

Timestamp: 02/16/2012 11:45:08 PM
Error: uncaught exception: [Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: chrome://edsint
egration/content/overlay.js :: <TOP_LEVEL> :: line 40"  data: no]

Timestamp: 02/16/2012 11:45:08 PM
Error: uncaught exception: [Exception... "Component returned failure code: 0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE) [nsIJSCID.createInstance]"  nsresult: "0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE)"  location: "JS frame :: chrome://calendar/content/calUtils.js :: getCompositeCalendar :: line 1960"  data: no]

---

### Post by Baldrick_NZ on 2012-02-16
Thunderbird is the same for me as screenshot too.

---

### Post by Baldrick_NZ on 2012-02-16
Thunderbird is the same for me as screenshot too. Even tried a PC reboot to no avail. :-(

---

### Post by effenberg0x0 on 2012-02-16
I have verified that I am fully updated, rebooted, and Thunderbird is still working fine (thank God!). All my software are default versions from Ubuntu PP repos. No alternative PPAs are in use here. Are you guys using alternative sources? Are you using specific Thunderbird add-ons? (I'm using none).

Regards,
Effenberg

---

### Post by prana on 2012-02-16
I see the blank screen too after the recent thunderbird update. Also, I tried activating the Activity Manager within Thunderbird and it never comes up.

I am getting the following error if I try to start thunderbird from the command line:

-- Exception object --
+ QueryInterface (function) 3 lines
+ message (string) 'Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]'
+ result (number) 2153185302
+ name (string) 'NS_ERROR_XPC_GS_RETURNED_FAILURE'
+ filename (string) 'chrome://messenger/content/search.xml'
+ lineNumber (number) 109
+ columnNumber (number) 0
+ location (object) JS frame :: chrome://messenger/content/search.xml ::  :: line 109
+ inner (object) null
+ data (object) null
+ initialize (function) 3 lines

---

### Post by prana on 2012-02-16
> **effenberg0x0 said:**
> I have verified that I am fully updated, rebooted, and Thunderbird is still working fine (thank God!). All my software are default versions from Ubuntu PP repos. No alternative PPAs are in use here. Are you guys using alternative sources? Are you using specific Thunderbird add-ons? (I'm using none).

Regards,
Effenberg

Can you try to start Thunderbird after renaming the .thunderbird directory to a backup name - for example .thunderbird.bak?

Mine is a fresh install from the daily build.

---

### Post by Gregory Lee on 2012-02-17
Yes, here too, Thunderbird went blank, after "aptitude safe-upgrade".  Here are some lines shown for the Thunderbird update:
```
Setting up thunderbird (11.0~b2+build2-0ubuntu1) ...
Setting up thunderbird-globalmenu (11.0~b2+build2-0ubuntu1) ...
Setting up thunderbird-gnome-support (11.0~b2+build2-0ubuntu1) ...
Setting up thunderbird-locale-en (1:11.0~b2+build2-0ubuntu1) ...
Setting up thunderbird-locale-en-gb (1:11.0~b2+build2-0ubuntu1) ...
Setting up thunderbird-locale-en-us (1:11.0~b2+build2-0ubuntu1) ...

```

---

### Post by jimv on 2012-02-17
Uninstalled/reinstalled after deleting the .thunderbird folder.  Still just a blank screen with errors logged in the console:

```

Timestamp: 02/16/2012 09:29:29 PM
Error: [Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: chrome://messagingmenu/content/thunderbirdMenu.js :: <TOP_LEVEL> :: line 41"  data: no]
Source File: chrome://messagingmenu/content/thunderbirdMenu.js
Line: 43

Timestamp: 02/16/2012 09:29:29 PM
Error: uncaught exception: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://messenger/content/search.xml ::  :: line 109"  data: no]

Timestamp: 02/16/2012 09:29:29 PM
Error: uncaught exception: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://messenger/content/mailWindow.js :: CreateMailWindowGlobals :: line 120"  data: no]

Timestamp: 02/16/2012 09:31:45 PM
Error: gFolderDisplay is null
Source File: chrome://messenger/content/mailWindowOverlay.js
Line: 345

```

---

### Post by PaulW2U on 2012-02-17
Working fine in Kubuntu but just three empty panels in Unity.

The following error display when starting from terminal:

```
paul@DELL:~$ thunderbird
-- Exception object --
+ QueryInterface (function) 3 lines
+ message (string) 'Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]'
+ result (number) 2153185302
+ name (string) 'NS_ERROR_XPC_GS_RETURNED_FAILURE'
+ filename (string) 'chrome://messenger/content/search.xml'
+ lineNumber (number) 109
+ columnNumber (number) 0
+ location (object) JS frame :: chrome://messenger/content/search.xml ::  :: line 109
+ inner (object) null
+ data (object) null
+ initialize (function) 3 lines
*
```

---

### Post by Harry33 on 2012-02-17
There is definitely something wrong with this new update (beta2).
Downgrading to the beta1 solves the issue of blank windows.

Here (beta1):
[https://launchpad.net/ubuntu/+source/thunderbird/11.0~b1+build2-0ubuntu1]("https://launchpad.net/ubuntu/+source/thunderbird/11.0%7Eb1+build2-0ubuntu1")
Choose your achitecture (64-bit, 32-bit) first.

---

### Post by Elfy on 2012-02-17
> **effenberg0x0 said:**
> Are you guys using alternative sources? Are you using specific Thunderbird add-ons? (I'm using none).

Regards,
EffenbergOnly one PPA for Clementine. I am using some add-ons but there's no way to tell which ones ;)

> **prana said:**
> I see the blank screen too after the recent thunderbird update. Also, I tried activating the Activity Manager within Thunderbird and it never comes up.

I am getting the following error if I try to start thunderbird from the command line:

-- Exception object --
+ QueryInterface (function) 3 lines
+ message (string) 'Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]'
+ result (number) 2153185302
+ name (string) 'NS_ERROR_XPC_GS_RETURNED_FAILURE'
+ filename (string) 'chrome://messenger/content/search.xml'
+ lineNumber (number) 109
+ columnNumber (number) 0
+ location (object) JS frame :: chrome://messenger/content/search.xml ::  :: line 109
+ inner (object) null
+ data (object) null
+ initialize (function) 3 linesSame error.

Xubuntu 12.04.

Clementine also refusing to show album art.

[s]Couldn't find a bug to Me Too it so - [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/934009](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/934009)[/s]

Bug is here [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/933951](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/933951)

---

### Post by jimv on 2012-02-17
The problem can be worked around by disabling the Messaging Menu add-on.  To do this, press alt+f2 and type "thunderbird --safe-mode".  Once Thunderbird comes up, go into the Add-on Manager and disable the Messaging Menu add-on.  Restart Thunderbird.

Relevant bug report here: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/933951](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/933951)

---

### Post by exploder on 2012-02-17
jimv, the workaround fixed things right up! Thunderbird is working again. Thanks!

---

### Post by ArtLaForge on 2012-02-17
> **exploder said:**
> jimv, the workaround fixed things right up! Thunderbird is working again. Thanks!

+1  Thanks Jimv worked for me too.:P

---

### Post by ybytyruzu on 2012-02-17
Hey....Thanks Jimv worked here too :p.

---

### Post by t.rei on 2012-02-17
Now thats something I would not have found for a while - big thanks.

Using gnome-shell, the addon is not even relevant for me, afaik. :D

---

### Post by macstevejb on 2012-02-17
Fixed with latest batch of updates

:p

---

### Post by prana on 2012-02-17
> **macstevejb said:**
> Fixed with latest batch of updates

:p

Yep.

---

### Post by bobcollard on 2012-02-19
After the latest upgrade, Thunderbird 11 is back working on my computer.  Xubuntu 12.04 Precise Pangolin system.

---

### Post by cariboo on 2012-02-19
Merged similar threads.

---

