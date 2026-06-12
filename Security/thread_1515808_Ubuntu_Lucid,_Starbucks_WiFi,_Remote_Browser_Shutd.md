---
title: "Ubuntu Lucid, Starbucks WiFi, Remote Browser Shutdown, Browserjacked/Hacked?"
date: 2010-06-22
forum: Security
---

### Post by 2nubu on 2010-06-22
Hi,

I was just at Starbucks a couple hours ago.

I was probably browsing the Web (Firefox) for about half an hour, and all the sudden, some browser tabs closed without my doing, and then the whole browser. I open the browser again, and after a while, the browser shuts down AGAIN.

Was I hacked at Starbucks?

What could possibly happen?

-2n

---

### Post by CharlesA on 2010-06-22
VNC.

Make sure it isn't enabled.

System > Preferences > Remote Desktop

---

### Post by 2nubu on 2010-06-22
Yeah, thanks.

Remote Desktop is NOT checked.

ADD: Does anyone have any other thoughts? Thanks.

-2n

---

### Post by wilee-nilee on 2010-06-22
What FF addons are you using. If your not using the remote desktop function also turn if off in system-preferences-startup applications.

---

### Post by JT9161 on 2010-06-22
Could just as easily have been a bug/crash, can't hurt to look into that possibility.

---

### Post by CharlesA on 2010-06-22
If that's not enabled, do you have any listening services running?

---

### Post by matt-fender on 2010-06-22
Can you remember EXACTLY what websites you were on?

---

### Post by wilee-nilee on 2010-06-22
n

---

### Post by 2nubu on 2010-06-23
Thanks for the replies everyone, I just got back.

> What **FF addons** are you usingNot much, I think, mainly AdBlock Protector, Exif Viewer, and the Ubuntu Mod. Addon

> If your not using the remote desktop function also turn if off in  system-preferences-startup applications.I'll check on that. Thanks.

> Could just as easily have been a bug/crash, can't hurt to look into that  possibility.I guess. But although I don't know much about Linux and I keep hearing all about how Linux is impenetrable, for me it kinda seems, I don't know what's the word or expression to put it, to easy to pass off as "coincidential."

> If that's not enabled, do you have **any listening services** running?Yeah. I don't know for sure. How can I check?

I have ufw on default, and I ran rkhunter earlier, but for some reason I can't open the log because of the "X" on the file icon.
 > Can you remember **EXACTLY what websites** you were on?That's an interesting question. Both times, I believe, I was trying to play videos on YouTube.

-2n

---

### Post by 2nubu on 2010-06-23
>  system-preferences-startup applications

Yes, it is check there. WTF?

Sorry if I sound paranoid or something, but something like this, could someone duplicate saved cookies for active login sites, keylog (though I don't think I logged into anything then), etc. etc. getting any sensitive information?

Thanks,
2n

---

### Post by wilee-nilee on 2010-06-23
> **2nubu said:**
> Yes, it is check there. WTF?

Sorry if I sound paranoid or something, but something like this, could someone duplicate saved cookies for active login sites, keylog (though I don't think I logged into anything then), etc. etc. getting any sensitive information?

Thanks,
2n

The remote desktop should be there, but if you haven't activated it, or use it I believe that turning it off in this area just turns off a daemon.

I would be using noscript at the least it is a cross script and flash blocker. The easiest way to use it for me is to also add the icons from the right click customize on the top panel of firefox, you can allow for sessions and stop the flash from there until you get the hang of the icon in the bottom panel and what to allow and what to block.

It is hard to say what happened at starbucks but noscript is a good way to protect yourself in the end.

Personally I have FF set up to remove all cookies on closing, to run in private to accept no 3rd party cookies and I also have the better privacy FF addon which removes flash cookies and cookies which are still there even if FF is set to remove them.
[https://addons.mozilla.org/en-US/firefox/addon/6623/](https://addons.mozilla.org/en-US/firefox/addon/6623/)
Another tracker blocker is FF addon ghostery. The Wot (web of trust) addon will also give you a icons on searches in google and on web pages for reported safety of sites.

---

### Post by 2nubu on 2010-06-23
> Personally I have FF set up to remove all cookies on closing, to run in  private to accept no 3rd party cookiesSo you don't mind logging into email and other online accounts everyday? No worries about keylogging?

What about "Remember Password"? Is that trustworthy?

I'm new to Ubuntu; been used to Win a long time.

I'm more comfortable with Win security merely bc of ZA.

With Ubuntu and its FF, I don't know what to expect. I set cookies to "Ask every time" and "Decline 3rd Party", so I save the cookies I want to: like email and other trusted sites. And then, I save the password with "Remember Password" with a master password, because I don't trust typing in my login information in public, such as Starbucks.

Is that way of thinking valid? Is there better way to reduce risk of data theft?

-2n

---

### Post by wilee-nilee on 2010-06-23
> **2nubu said:**
> So you don't mind logging into email and other online accounts everyday? No worries about keylogging?

What about "Remember Password"? Is that trustworthy?

I'm new to Ubuntu; been used to Win a long time.

I'm more comfortable with Win security merely bc of ZA.

With Ubuntu and its FF, I don't know what to expect. I set cookies to "Ask every time" and "Decline 3rd Party", so I save the cookies I want to: like email and other trusted sites. And then, I save the password with "Remember Password" with a master password, because I don't trust typing in my login information in public, such as Starbucks.

Is that way of thinking valid? Is there better way to reduce risk of data theft?

-2n

I use a encrypted FF bookmark and password saver, and none of the bookmarks or passwords will do any good to anybody that could even get on my computer.

A keylogger has to get in root to work off your computer, but a site that your accessing could be compromised, I don't go to any sites that would be an advantage to a key logger. I don't need to do any online banking...etc.

I'm not going to comment anymore here it is a waste of time from your questions and responses you don't seem to know much about security, may I suggest you go to the security section of the forum and read the sticky to begin with.

---

### Post by 2nubu on 2010-06-23
Ok.

Well, thank you for your responses and honesty.

-2n

---

### Post by Rubi1200 on 2010-06-23
This link will explain how you can secure Firefox on Ubuntu:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

This link provides general security tips:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by OpSecShellshock on 2010-06-23
> **2nubu said:**
> Both times, I believe, I was trying to play videos on YouTube.

-2n

If this is the case, then the most likely cause of the browser crash was Flash Player. Happens sometimes, and it's hard to predict. To be honest, when something like this happens I usually presume it's a performance issue rather than security issue. It's just more likely.

Still, public WiFi is not the place to conduct even slightly sensitive activity. If you don't control the access, always assume your traffic is being intercepted and browse accordingly. No big deal.

---

### Post by 2nubu on 2010-06-23
> Still, public WiFi is not the place to conduct even slightly sensitive activity. If you don't control the access, always assume your traffic is being intercepted and browse accordingly. No big deal.  So, really stupid question, even for noobs...  Not even email? :redface:

---

### Post by Noz3001 on 2010-06-23
Possibly a problem with Flash, it's evil. I doubt anyone "hacked" you, especially at Starbucks! :|

---

### Post by 2nubu on 2010-06-23
ok ok... i get it.

i'm gonna shut now...
for the time being.

---

### Post by OpSecShellshock on 2010-06-23
> **2nubu said:**
> ok ok... i get it.

i'm gonna shut now...
for the time being.

Oh no, that's not a good idea at all. Never stop asking questions. That's where all this "awareness" that folks in my profession are always yammering on about comes from!

---

### Post by cdenley on 2010-06-23
> **2nubu said:**
> 
Yeah. I don't know for sure. How can I check?


```

sudo netstat -tulnp

```

---

