---
title: "Virus attack"
date: 2011-04-29
forum: Security
---

### Post by Ron W on 2011-04-29
Hello

I'm using Ubuntu 10.04 LTS on my desktop computer.

I've just done a Google search using Mozilla Firefox (3.6.16). Instead of getting a Google page I have got [http://freescannerdefeformationcne.com](http://freescannerdefeformationcne.com) saying 'Your Computer in infected' and a list of 9 infections. The page in Firefox shows up as a Windows page with the tab saying 'Windows Security'.

Also, there is s box wanting me to open 'AntiSpyWareSetup.exe. I have neither asked for this software to be downloaded and I've NOT downloaded this.

I've turned the computer off, and restarted it. The above security message comes up again when I try to start Firefox. I've taken the desktop off line and am now using my netbook.

I've done a search on 'freescannerdefeformationcne' and nothing comes up.

Can anyone advise me of what is happening, please?

I know not to download the software they appear to want me to do, but how do I stop this page coming up when I start up Firefox.

Thanks

Ron

---

### Post by dazthejunglist on 2011-04-29
exe files wont run on ubuntu

---

### Post by dazthejunglist on 2011-04-29
check your firefox settings and see if its been set up as your home page also advise switching to firefox 4 hell of alot faster browsing

---

### Post by Bucky Ball on 2011-04-29
Check it is not your home page, as suggested (good thought). Boot Firefox, open a terminal and paste this in (with Firefox and the message up and running):

```
killall firefox
```Boot Firefox.

---

### Post by dazthejunglist on 2011-04-29
that website is a reported web attack page my firefox automaticly blocks those sites plus you cant really get virusus on linux

---

### Post by Bucky Ball on 2011-04-29
Yep, Daz. My Firefox version 3.6.16 (same version as OP) blocks that as a Reported Attack Site also. I wonder why this is not happening for you, Ron W???

---

### Post by Ron W on 2011-04-29
Thanks for advice. 

I think I've got the homepage back (I've not yet brought the desktop back on line), and am confident that nothing untoward has happened to my computer. I've enough stress at the moment with revision!

> **dazthejunglist said:**
> that website is a reported web attack page my firefox automaticly blocks those sites plus you cant really get virusus on linux

How can I get Firefox to automatically block these sites?

---

### Post by Bucky Ball on 2011-04-29
Dunno. Mine just automatically does. I haven't changed a thing. ???

---

### Post by Ron W on 2011-04-29
> **Bucky Ball said:**
> Dunno. Mine just automatically does. I haven't changed a thing. ???

That is interesting because as far as I'm aware I've not changed anything either - I tend to keep things as default as if things go wrong and I have to reinstall, then I don't have to mess around getting things back to the way I like them.

---

### Post by walt.smith1960 on 2011-04-29
> **Ron W said:**
> Thanks for advice. 

I think I've got the homepage back (I've not yet brought the desktop back on line), and am confident that nothing untoward has happened to my computer. I've enough stress at the moment with revision!



How can I get Firefox to automatically block these sites?

This is FireFox4 but I think they're all the same.  Click  edit > preferences > security and check "block reported attack sites" and anything else you feel appropriate.

---

### Post by SeijiSensei on 2011-04-29
Do browsers generally allow javascripts to alter the user's home page?  That's the only way one of these phony virus scanners could become so persistent on a Linux platform.  I don't see why any script should have permission to change things like the user's designated home page.

I had an instance of Antivirus 2010 run on my Linux machine when the New York Times site carried an infected ad.  It appeared to use an "onclose()" handler to open another window and connect to the phony virus scanning page.  That's a lot different from actually changing my Firefox configuration settings, though.

---

### Post by bodhi.zazen on 2011-04-29
Personally I suggest you use NoScript, that extension will block almost all of this behavior.

---

### Post by dfreer on 2011-04-29
Also note: Depending on your firefox settings, it may automatically resume the previous session or last page. So if it wasn't the OP's home page that got changed, it may have just been the browser picking up where it left off at.

---

### Post by Bucky Ball on 2011-04-29
> **dfreer said:**
> Also note: Depending on your firefox settings, it may automatically resume the previous session or last page. So if it wasn't the OP's home page that got changed, it may have just been the browser picking up where it left off at.

+1. Another thought.

dfreer, are you *really* running 7.10??

---

### Post by dfreer on 2011-04-29
> **Bucky Ball said:**
> +1. Another thought.

dfreer, are you *really* running 7.10??

I probably haven't ran ubuntu as an OS since 8.04, but in response I just never got around to changing that.

---

### Post by timothy48342 on 2011-04-30
> **dfreer said:**
> Also note: Depending on your firefox settings, it  may automatically resume the previous session or last page. So if it  wasn't the OP's home page that got changed, it may have just been the  browser picking up where it left off at.

Had that happen to me with firefox under WinXP. Some page that I went to  crashed Firefox and every time I tried to run fireFox it automatically  tried to load the previous session and crashed again. 

I don't know how to turn it off, but I got around it by explicitly  typing "http://www.google.com" in XP's "Run" window, then closing  Firefox normally. (I am a newbie here, but I am sure ubuntu has the  equivelent of a "run" window that you can type any command or webpage.  Clicking on ANY internet shortcut should fix it too if that is what is happening. You just neen firefox to go to some other page once instead of automatically reloading the problem page.)

--tim

---

