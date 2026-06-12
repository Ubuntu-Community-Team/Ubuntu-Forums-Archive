---
title: "Computer infected via thundird, help!"
date: 2010-09-03
forum: Security
---

### Post by Camilia on 2010-09-03
I noticed after clicking on a link posted on thread at forum that visit frequently that my computer was running slower. Thus downloaded clamtk and scanned my computer. Found 3 viruses. I am suppose to be able to delete or quarantine them but not able to do so. Can't get them selected. Virus scanner is missing GUI version and antivirus engine. I am going to remove firefox and reinstall it. I don't understand this. I thought viruses won't affect me using ubuntu. Anybody know what is happening?

Info is:
/home/brain/.mozilla/firefox/4okaet3z.default/Cache/96568D37do1 PUA.Script.Packed-2

/home/brain/.mozilla/firefox/4okaet3z.default/Cache/9EEO953FdO1 PUA.HTML.Infected.WebPage

/home/brain/.mozilla/firefox/4okaet3z.default/Cache/8OE74C3AdO1 
PUA.HTML.Infected.WebPage

Meant to put firefox as header so started another thread.

---

### Post by Camilia on 2010-09-03
I noticed after clicking on a link to info on breeding fish on an aquarium forum that my computer was running slower. Thus downloaded clamtk and scanned my computer. Found 3 viruses. I am suppose to be able to delete or quarantine them but not able to do so. Can't get them selected. Virus scanner is missing GUI version and antivirus engine. Could this why I can't get them selected? I am going to remove firefox and reinstall it. I don't understand this. I thought viruses won't affect me using ubuntu. What can I do to prevent this occurring again? 

Info is:
1./home/brain/.mozilla/firefox/4okaet3z.default/Cache/96568D37do1 PUA.Script.Packed-2

2./home/brain/.mozilla/firefox/4okaet3z.default/Cache/9EEO953FdO1 PUA.HTML.Infected.WebPage

3./home/brain/.mozilla/firefox/4okaet3z.default/Cache/8OE74C3AdO1
PUA.HTML.Infected.WebPage

I am going to remove firefox and reinstall it. Did this and still virus scanner show same virus present. Thus next will remove from hidden files the .recently used(globe) Also removed cache in hidden files. Third virus is gone.

What else can I do? I hate to have to reinstall windows and ubuntu again. Until the viruses are gone I don't feel safe doing any money transfers.

---

### Post by OpSecShellshock on 2010-09-03
The "PUA" that you see in the definitions refers to potentially unwanted applications. What that means is that they are meant to do suspicious things the user may not be aware of, but may have been put there by the user. It's a bit of a convoluted mess, but basically there are some applications which do shady things, and AV vendors want to classify them as suspicious or malicious in order to protect users, but sometimes they get legal threats from the makers of the suspicious applications on the grounds that they have user agreements that need to be accepted in order for them to be installed. It's all very stupid.

In this specific case, it appears that the scanner found things in cached web browser data. Two of them were just web pages, while the other was a script contained within a web page. They are harmless in the cache since they can't be rendered. Clearing the browser cache, which in Firefox can be done through Tools-->Clear Recent History, will remove them. It's also possible to change the Firefox preferences so that the cache is cleared every time the browser is closed. It would not have been necessary to uninstall the browser; clearing the cache and closing it would have been enough.

I suspect the reason that your computer slowed down is that the scripts on the page you browsed to were trying to do something they were not able/allowed to do, but which would have worked in Windows. Happens all the time. In Ubuntu it usually just causes numerous errors, which in turn slows down the browser and occasionally causes it to freeze. In those moments, it's best to simply shut down the browser and not return to whatever page it was. Using a virus scanner is not necessary.

---

### Post by OpSecShellshock on 2010-09-03
I answered over on the other one before seeing this one. I expect the threads will be merged before long.

---

### Post by Camilia on 2010-09-03
> **OpSecShellshock said:**
> 
Clearing the browser cache Tools-->Clear Recent History. It's also possible to change the Firefox preferences so that the cache is cleared every time the browser is closed.

I suspect the reason that your computer slowed down is that the scripts on the page you browsed to were trying to do something they were not able/allowed to do

Oh now I see where it was. I have been going in the preference to clear the cookies. I thought virus only attached to cookies. Now got history set to clear when I close firefox. You don't know how many times I have reloaded windows and ubuntu because of the slowness. I feel very relieved now! 

Yeh got windows on the computer, too. Need it for netflix and other applications occasionally.

---

### Post by bodhi.zazen on 2010-09-04
I merged your two threads.

There are no known active viruses for Linux, your system was patched against the known viruses long ago.

Although Linux has vulnerabilities, viruses are not something I would concern myself with, this is not windows.

See the stickies at the top of these forums.

Use apparmor to confine thunderbird / firefox.

---

