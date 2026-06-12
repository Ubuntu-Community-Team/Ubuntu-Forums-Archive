---
title: "Internet scripts getting even more annoying?"
date: 2008-08-07
forum: The Cafe
---

### Post by Dremora on 2008-08-07
I had used the Noscript add-on, on my Windows version of Firefox for some time, considering that Windows is as vulnerable as it is to injection vulnerabilities and such, it made sense from a security standpoint.

But I've been bouncing around the web on Stumbleupon and have started noticing some very odd things.

Some are teenagers indexing Rick Roll sites that display endless "Never gonna give you up" and "Never gonna let you down" dialogs.

This was bad enough.

Then I noticed that every once in a while Firefox would block out the page and give the "Reported Attack site" warning, so now people are using Stumbleupon to index spyware sites.

But last night, I noticed it sent me to a site called tweaktown.com, and as I was reading an article, I noticed it took me to a page that said "We notice you use an adblocker.....yada yada"

So I hit the back button, and 10 seconds later, it took me back.

they have a javascript checking the page to make sure their ads load and if they don't, they give you the harassment page.

I've loaded the NoScript add-on and it's stopped all the annoying or malicious behavior I've noted above, sad thing is that now whenever a site truly needs to load a legitimate script, I have to whitelist it, it only takes a few seconds though, I've already whitelisted obvious good sites like my bank and such, and set NoScript to not alert me when it blocks scripts, but this is ridiculous.

---

### Post by VitaLiNux on 2008-08-07
Well, to tell you the truth, I sometimes feel paranoid while websurfing.

---

### Post by Newuser1111 on 2008-08-07
> But last night, I noticed it sent me to a site called tweaktown.com, and as I was reading an article, I noticed it took me to a page that said "We notice you use an adblocker.....yada yada"I do have an ad-blocker and they didn't tell me that.

Edit: 
That's because it failed to block them.

---

### Post by Sealbhach on 2008-08-07
I find the persistent nagging of noscript settings almost as bad as having a virus. It totally ruins my browsing experience.

I'd rather take the risk.


.

---

### Post by LaRoza on 2008-08-07
In Opera, dialog boxes have a box in them you can check to prevent scripts from running so you don't get suck.

---

### Post by Dremora on 2008-08-07
[http://www.tweaktown.com/supportus.html](http://www.tweaktown.com/supportus.html)
------

I replied to them with a parody of that message:

Hello,

I noticed that you’re using a lame javascript to fish out my adblock
plus. I would ask you to please disable this nonsense, but blocking your
script will probably yield better results. 

By doing this, I am blocking a collection of seizure-inducing annoyances
that I am not interested in buying anything from.

If you can't afford the hosting cost and the time and effort you put in
to this site, then please get better content and an honest way of
earning revenue. I strive to not be annoyed by every egomaniacal website
owner that thinks they are God's gift to the internet. I will not
continue to see your message, and will also not disable the Ad blocker. 

I thank you for the convenient link back to the article after the 2
seconds it took to bypass your script, but browsers also have this thing
called a back button.

Thank you for supporting us,

Internet users everywhere

---

### Post by init1 on 2008-08-07
> **Sealbhach said:**
> I find the persistent nagging of noscript settings almost as bad as having a virus. It totally ruins my browsing experience.

I'd rather take the risk.


.
Yeah I absolutely hate that. I can't stand any pop up alert; Gnome does it ("Your battery is now full", "Update your system"), and now FF3 does it ("All downloads complete"). 

> **LaRoza said:**
> In Opera, dialog boxes have a box in them you can check to prevent scripts from running so you don't get suck.
Yeah, it's a great feature. Is there a FF extension that does that?

---

### Post by GodsMadClown on 2008-08-08
> **init1 said:**
> ...Is there a FF extension that does that?

You mean like Noscript?
([http://noscript.net/](http://noscript.net/))

---

### Post by LaRoza on 2008-08-08
> **init1 said:**
> 

Yeah, it's a great feature. Is there a FF extension that does that?

Probably not. It would have to alter the implementation of ECMAScript.

NoScript is a good thing to have, but it doesn't work the same way I think (can you activate it in the middle a script executing?)

---

### Post by Canis familiaris on 2008-08-08
> **LaRoza said:**
> In Opera, dialog boxes have a box in them you can check to prevent scripts from running so you don't get suck.

<insert random number here /> reason to use Opera.

---

### Post by billgoldberg on 2008-08-08
Expo plugin on right top screen edge + pkill firefox.

or in fluxbox, switching to a new screen with the side button on the mouse + pkill firefox.

I have the terminal (gnome-terminal on gnome and xterm on fluxbon) on f12.

---

### Post by LaRoza on 2008-08-08
> **billgoldberg said:**
> Expo plugin on right top screen edge + pkill firefox.

or in fluxbox, switching to a new screen with the side button on the mouse + pkill firefox.

I have the terminal (gnome-terminal on gnome and xterm on fluxbon) on f12.

I use xmonad, so I just press alt + p, and type "xkill" and click on things if they are misbehaving.

The terminal comes up on alt + shift + enter (configurable)

---

### Post by cardinals_fan on 2008-08-08
> **LaRoza said:**
> I use xmonad, so I just press alt + p, and type "xkill" and click on things if they are misbehaving.

The terminal comes up on alt + shift + enter (configurable)
Even now that I'm back on Openbox, I still use those shortcuts.  They're perfect :)

---

### Post by LaRoza on 2008-08-08
> **cardinals_fan said:**
> Even now that I'm back on Openbox, I still use those shortcuts.  They're perfect :)

I liked wmii's "alt + enter" but I didn't bother to change it.

---

### Post by Canis familiaris on 2008-08-08
I have set Compiz Shortcut for Super + X for xkill and click on the window to kill it. I also use Force Quit.

---

### Post by aaaantoine on 2008-08-08
> **LaRoza said:**
> Probably not. It would have to alter the implementation of ECMAScript.

NoScript is a good thing to have, but it doesn't work the same way I think (can you activate it in the middle a script executing?)

Well, by default it's whitelist based.  So you would have to enable scripts on a page to have that script execute in the first place.

But I could easily see someone saying "Yeah, I'll try running scripts on this page because otherwise it's all jacked up." Only to get spammed to death with while(1) alert("Never gonna give you up.");

The other day I was trying to program something, and accidentally created a setTimeout based infinite loop.  Firefox caught that after a while and asked me if I wanted to stop running scripts on the page.  I don't know how much that's worth for this conversation, but I thought I'd mention it.

---

### Post by LaRoza on 2008-08-08
> **aaaantoine said:**
> Well, by default it's whitelist based.  So you would have to enable scripts on a page to have that script execute in the first place.

But I could easily see someone saying "Yeah, I'll try running scripts on this page because otherwise it's all jacked up." Only to get spammed to death with while(1) alert("Never gonna give you up.");

That is why I liked Opera's often simpler but more functional built in tools. AdBlock? Block content. Less flexible, but it works the way you want 99% of the time and don't make you tweak it. (Plus, it is built in in every Opera)

---

### Post by picpak on 2008-08-08
> **Anurag_panda said:**
> I have set Compiz Shortcut for Super + X for xkill and click on the window to kill it. I also use Force Quit.

I have Ctrl-Esc set to xkill on Openbox. But Openbox has its own "Force Quit" built into it so I mostly use that :)

---

