---
title: "Chromium"
date: 2011-11-30
forum: Security
---

### Post by Merisi on 2011-11-30
I was wondering if I am less secure online by using Chromium.  When I use Firefox, I use No Script, Request Policy and numerous security add ons and I have also activated the AppArmor profile.  I wouldn't mind using Chromium a bit more but it makes me feel a bit vulnerable.  If I use it just for surfing and don't ever access any of my accounts or passwords, will I be okay?

(Note: I'm not trying to start a Chrome vs Firefox debate.  It's great that we have lots of browsers to choose from and can make a personal choice for what suits us best)

---

### Post by FuturePilot on 2011-11-30
There are similar extensions available for Chrome/Chromium for the ones you mentioned.

---

### Post by haqking on 2011-11-30
Make sure you have the latest versions, chrome's sandbox was cracked so can be vulnerable.

However NOTscript is the chrome/chromium version of NOScript.

Read here for more info and links [https://wiki.ubuntu.com/BasicSecurity#Make_Your_Browser_More_Secure](https://wiki.ubuntu.com/BasicSecurity#Make_Your_Browser_More_Secure)

---

### Post by Merisi on 2011-12-01
I didn't express clearly enough in the first post but the main question I was trying to ask is if I use Chromium just for surfing and don't ever enter any passwords into that browser, is there anyway it can compromise my passwords which I would enter into a well armed Firefox and my general security?

---

### Post by haqking on 2011-12-01
> **Merisi said:**
> I didn't express clearly enough in the first post but the main question I was trying to ask is if I use Chromium just for surfing and don't ever enter any passwords into that browser, is there anyway it can compromise my passwords which I would enter into a well armed Firefox and my general security?

YES.

Chances are remote but there is always a chance.

Sorry but nothing in a networked world is 100% secure, a web browser is close to being its own OS these days, and as such have tons of security vulnerabilities.

Just because you dont enter your passwords into the browser itself, doesnt mean a script cannot run which escapes your browser.

There are too many attack vectors to be specific but yes there is always a chance.

Hence the need for NoScript or NOTScript in chrome/chromium, use latest versions to keep in the line with the sadnbox vulnerability, configure apparmor for application control, tight firewall rules to prevent unauthorised outgoing connections etc etc.

Cheers

---

### Post by Merisi on 2011-12-01
> **haqking said:**
> YES.

Chances are remote but there is always a chance.

Sorry but nothing in a networked world is 100% secure, a web browser is close to being its own OS these days, and as such have tons of security vulnerabilities.

Just because you dont enter your passwords into the browser itself, doesnt mean a script cannot run which escapes your browser.

There are too many attack vectors to be specific but yes there is always a chance.

Hence the need for NoScript or NOTScript in chrome/chromium, use latest versions to keep in the line with the sadnbox vulnerability, configure apparmor for application control, tight firewall rules to prevent unauthorised outgoing connections etc etc.

Cheers

Thanks for the response, I shall bear that in mind.  I've tightened up most of my security.  I think I'll just stick with firefox.

---

### Post by Dangertux on 2011-12-01
I would say use chrome with notscripts. If you have the apparmor profile for chrome you should be okay. It's important to understand chrome isn't as latched onto your home directory as firefox is. So with apparmor if the browser IS compromised I would wager you would have less of a loss with chrome. 

Either way use the one you feel best about. Hope this helps.

---

### Post by Merisi on 2011-12-02
> **Dangertux said:**
> I would say use chrome with notscripts. If you have the apparmor profile for chrome you should be okay. It's important to understand chrome isn't as latched onto your home directory as firefox is. So with apparmor if the browser IS compromised I would wager you would have less of a loss with chrome. 

Either way use the one you feel best about. Hope this helps.

Hi Danger, you went through apparmor with me the other day and I think some Chromium rules were there too.  Am I right in thinking Chrome and Chromium are different? Chrome has a sandbox, while Chromium doesn't.

---

### Post by haqking on 2011-12-02
> **Merisi said:**
> Hi Danger, you went through apparmor with me the other day and I think some Chromium rules were there too.  Am I right in thinking Chrome and Chromium are different? Chrome has a sandbox, while Chromium doesn't.

The main differences are/were tracking and branding.

See here [http://en.wikipedia.org/wiki/Chromium_(web_browser)#Differences_from_Google_Chrome](http://en.wikipedia.org/wiki/Chromium_(web_browser)#Differences_from_Google_Chrome)

sandboxing is still part of its architecture, the sandbox was compromised though so make sure you use the latest version.

Cheers

---

### Post by Dangertux on 2011-12-02
> **Merisi said:**
> Hi Danger, you went through apparmor with me the other day and I think some Chromium rules were there too.  Am I right in thinking Chrome and Chromium are different? Chrome has a sandbox, while Chromium doesn't.

Pretty much what haqking said in regard to this.

---

