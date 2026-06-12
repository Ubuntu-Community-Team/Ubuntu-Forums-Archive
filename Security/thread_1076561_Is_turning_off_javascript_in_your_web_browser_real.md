---
title: "Is turning off javascript in your web browser really necessary in Linux?"
date: 2009-02-21
forum: Security
---

### Post by Nixie Pixel on 2009-02-21
I use Firefox as my web browser, and when I am on Windows I use the NoScript plugin to shut off javascript except for trusted web sites.

What are the real dangers, if any, of leaving javascript on while running Linux, as compared to under Windows?

Thanks!

---

### Post by brandon88tube on 2009-02-21
Its probably about the same. It just depends on if anything is written for it to work on your system.

---

### Post by yther on 2009-02-21
Browsers these days have an OS-independent environment in which programs can run.  Just in these forums I have seen people complaining that their Firefox browser got hijacked, usually by a malicious script in a banner ad on some legitimate site.  At least in Linux, these scripts probably can't infect the rest of the user's environment (such as installing a trojan that hooks itself into the system and runs as a service), but they can still screw up your browser and potentially compromise your personal information.

So I'd say the danger to your entire system is less, but the total damage could still be significant.  Maybe your computer doesn't become part of a huge botnet, but you become a victim of identity theft.  Which is worse?

---

### Post by Thirtysixway on 2009-02-21
I see why someone would turn off javascript, but at least use some type of add-on.  A lot of web 2.0 sites depend on javascript to function correctly.  Turning it off could kill user experience.

---

### Post by doas777 on 2009-02-21
I'm inclined to say yes, for a few reasons. 

your correct in assuming that most windows malware will not function on linux (with or without wine) because they attempt to alter or otherwise use the operating system and settings. 

Most spyware and adware however, focus on the browser for all they need to work. thus a weakness in the firefox javascript engine, or whatever will function just fine regardless of the environment in which the browser runs.
Likewise vulnerabilities in flash or acrobat that attempt to exploit the browser only, would also run.

Traditionally, everyone focuses on protecting the OS from the user, and your right, malicious javascript can never hose your system, but since firefox is running under your credentials, and you can access all your user data, so can it. this model is great for a mission-critical multi-access server, but terrible for a user desktop, where the OS is far less valuable than the user data. I can restore an os in a few hours, but if I don't have good backups, the data might take years to regenerate.

thats the paranoid view of things. just analyze your risk. if your data/privacy is valuable enough to you to be worth protecting, take measures, and if not, don't worry about it.

PS: Noscript rocks!

have fun,
franklin

---

### Post by Nixie Pixel on 2009-02-21
Ok, thanks for your help - so are there any add-ons that protect against data theft/damage but still allow javascript to function?

---

### Post by Dave_Connor on 2009-02-21
Use NoScript for FF as this disables alot of scripts on the page to prevent these types of attacks.

---

### Post by doas777 on 2009-02-21
> **Nixie Pixel said:**
> Ok, thanks for your help - so are there any add-ons that protect against data theft/damage but still allow javascript to function?

theoretically a strong apparmour profile would allow you to prevent ff from accessing files outside of it;s remit, but you would still be suceptible to anything that is designed to happen exclusively within the browser.

---

### Post by Nixie Pixel on 2009-02-21
> **Thirtysixway said:**
> I see why someone would turn off javascript, but at least use some type of add-on.  A lot of web 2.0 sites depend on javascript to function correctly.  Turning it off could kill user experience.
Ok, I get it now.  The poster above must not have seen in my original message that I use NoScript to turn off javascript in FF.

Thanks, everyone!

---

### Post by bodhi.zazen on 2009-02-21
> **Nixie Pixel said:**
> I use Firefox as my web browser, and when I am on Windows I use the NoScript plugin to shut off javascript except for trusted web sites.

What are the real dangers, if any, of leaving javascript on while running Linux, as compared to under Windows?

Thanks!

The "problem" is that web browsers and things such as flash and javascript are OS independent.

This means that a malignant flash or javascript or "borwers hack" as I call them will work on any OS.

The good news, on Linux it will not affect anything outside of home, or most likely your .mozilla directory.

The bad news is, you are still vulnerable and some of these scripts do things such as search for passwords and cookies (to banks and such).

So while your "Operating System" is invulnerable to these things, they can do damage.

Just look in this section and there are several threads regarding browser cracks in the last few weeks.

So do with that information what you will. Personally I use Adblock and NoScript.

See also : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

Some additional tips there as well.

---

