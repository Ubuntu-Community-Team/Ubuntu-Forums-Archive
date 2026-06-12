---
title: "Deleting Flash Cookies"
date: 2011-04-20
forum: Security
---

### Post by Dry Lips on 2011-04-20
I use the BetterPrivacy Add-on in Firefox, but is there a way to delete 
flash cookies when using other browsers? FF is my main browser, 
but I also use Opera and Chromium now and then.

---

### Post by bodhi.zazen on 2011-04-20
You can try this:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

Or manually deleting them.

This is the #1 advantage of firefox, IMO, better privacy settings (in general) then other browsers and a wide range of add ons.

---

### Post by Dry Lips on 2011-04-20
> **bodhi.zazen said:**
> You can try this:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

Bookmarked!
> 
Or manually deleting them.

Do you know where on your computer the flash cookies are stored?
> 
This is the #1 advantage of firefox, IMO, better privacy settings (in general) then other browsers and a wide range of add ons.

I agree that FF is the better choice. But when using FF with NoScript and a couple of cookie-blockers, I've found that sites that use lots of scripts sometimes becomes unstable. Having to click “allow scripts” in the middle of a financial transaction is something that I don't want to do. So I use Opera for net-banking and online-shopping.

---

### Post by bodhi.zazen on 2011-04-20
> **Dry Lips said:**
> Bookmarked!

Do you know where on your computer the flash cookies are stored?


I agree that FF is the better choice. But when using FF with NoScript and a couple of cookie-blockers, I've found that sites that use lots of scripts sometimes becomes unstable. Having to click “allow scripts” in the middle of a financial transaction is something that I don't want to do. So I use Opera for net-banking and online-shopping.

I open a new private session, allow everything, only connect to financial institutions, allow cookies and everything, do my business, then clear cookies, lock down firefox, and close the private session.

---

### Post by bodhi.zazen on 2011-04-20
> **Dry Lips said:**
> Do you know where on your computer the flash cookies are stored?

Yes

look in ~/.macromedia

---

### Post by Dry Lips on 2011-04-20
> **bodhi.zazen said:**
> I open a new private session, allow everything, only connect to financial institutions, allow cookies and everything, do my business, then clear cookies, lock down firefox, and close the private session.

I guess that's great solution. Haven't thought about that one... Normally I would just click &#8220;allow everything on this site&#8221; but when you proceed, new scripts are often introduced as you go, which is a bit of a pain since the action you're trying to do can become disrupted.  
 

 Thanks a lot for your help! :)

---

### Post by movieman on 2011-04-21
Personally I linked ~/.macromedia to a directory in /tmp, and /tmp is a RAM disk, so the Flash crap gets deleted every time I reboot. It did require updating rc.local to create the relevant directories in /tmp on every boot though.

---

### Post by ChrisWells on 2011-04-21
You could install bleachbit that does flash and other stuff you select all in one

---

### Post by james_mcl on 2011-10-16
I know this thread's been dead a while, but if you're using Gnash (possibly without realising it) you should be aware that the Flash cookies will in fact be stored at

~/.gnash/SharedObjects

and this doesn't seem to be common knowledge!

---

### Post by OpSecShellshock on 2011-10-16
And as long as it's been revisited anyway, it might help to point out that BetterPrivacy can be used to remove Flash cookies even when they are put there by other browsers. They all use the same folder for those objects since Flash is a plugin.

---

