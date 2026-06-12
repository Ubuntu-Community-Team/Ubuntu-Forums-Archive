---
title: "Internet Explorer"
date: 2009-05-19
forum: Wine
---

### Post by tbullock on 2009-05-19
After upgrading to Jaunty I have been unable to get IE to work. The desktop icon has disappeared and I cannot get it to start again.

I have tried the IE that is in the virtual c drive with wine and get this message:

"Cannot find '%ws'. Make sure the path or Internet address is correct."

I have also tried to download the .exe for IE7 and IE8 from Microsoft and run that. When I try that "The install runs, it then asks to restart now or later. With either option no restart. I really don't need it if there is a way to check OWA email reasonably with Firefox or another browser but I have only saw it look right in IE.

Help please!

---

### Post by cogadh on 2009-05-19
Editorial comments on IE aside, you can't directly install IE in Wine, you need to use [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). Alternatively, you can try using a Firefox plugin like [IETab]("https://addons.mozilla.org/en-US/firefox/addon/1419") or [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59").

---

### Post by wsonar on 2009-05-19
> **tbullock said:**
>  I really don't need it if there is a way to check OWA email reasonably with Firefox or another browser but I have only saw it look right in IE.

Help please!

I use OWA with no problem in firefox can't tell a difference

---

### Post by tbullock on 2009-05-19
I tried IEs4linux and it says there is a system error and has to close like in windows when something crashes. This happens when I try to install right where it tries to install and finish. Usually where the flash install is trying but not always. How are you getting OWA to look like something usable in Firefox. My folders are not on the left, I have to click a link to get to the folders so that destroys the ability to drag and drop emails to correct folders and so forth. If I could get it to look right I would use firefox but it looks like crap IMO.

---

### Post by wsonar on 2009-05-19
I didn't even realize till I compared them..

looks like IE tabs for firefox is the only solution

DAMN MS Proprietary BS need to get companies off the MS crutch

---

### Post by Wiebelhaus on 2009-05-19
Playonlinux will install it wihtin s sandbox more or less and it works great.

---

### Post by tbullock on 2009-05-20
> **cogadh said:**
> Editorial comments on IE aside, you can't directly install IE in Wine, you need to use [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). Alternatively, you can try using a Firefox plugin like [IETab]("https://addons.mozilla.org/en-US/firefox/addon/1419") or [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59").

Ok, since IEs4linux did not work. I look at the IEtab one and it says not for linux. So I downloaded the User Agent switcher. This loads the left hand menu fine. However, everything on the right doesn't load. Any other options? Any way to get IEs4linux to install right?

---

### Post by tbullock on 2009-05-20
Ok, I finally got it to install. The Flash install was the problem. IE7 doesn't work. How can I remove IE7 without losing 6? I told it to create a menu icon and it did nothing. So I am forced to run from the terminal. Any suggestions on getting an icon in the menu?

---

### Post by tbullock on 2009-05-20
I fixed it. Sorry to get anyone excited. There is something going on with my Run dll in wine but that can wait I suppose. Thanks for the advice.

---

