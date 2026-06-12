---
title: "freshclam cramps my shutdown speed. help."
date: 2009-11-18
forum: Security
---

### Post by kelvin.illa on 2009-11-18
this only happens when I shutdown during the times I don't have internet connection, or whenever I'm in school (wherein freshclam is just a good as no internet connection). freshclam turns on even when I don't even turn on the GUI Virus Scanner; I'm assuming it initializes at start-up, and I don't have control over it. 

my regular shutdown speed in Karmic is about a couple of seconds, with freshclam unsuccessful with updating, it's about 11 seconds longer.

i know my linux isn't susceptible to viruses (as much as windows) that I don't really need an anti-virus software but I don't want to be a carrier if ever.

**is it possible to prevent _freshclam_ from initializing at start-up **(so it doesn't cramp my shutdown time when it can't update properly due to lack of internet connection)**?**

---

### Post by EJeanmaire on 2009-11-18
> **kelvin.illa said:**
>  is it possible to prevent _freshclam_ from initializing at start-up (so it doesn't cramp my shutdown time when it can't update properly due to lack of internet connection)**?**

If it isn't running in the background it isn't going to help you much... However, to remove it from rc.d runlevels (aka startup)
type:
```
sudo update-rc.d -f freshclam remove
```

That is of course assuming the process is called 'freshclam'... look in /etc/ folder to confirm that is the name of it.

---

### Post by kelvin.illa on 2009-11-18
> **EJeanmaire said:**
> If it isn't running in the background it isn't going to help you much... However, to remove it from rc.d runlevels (aka startup)...

It's actually running in the background under "devkits-disks-daemon" when viewing 'All Processes' in 'System Monitor.' I knew that it was this that was slowing my shutdown because after the Ubuntu logo gets tired of staring at me, lines appear with the first line writing that it's stopping 'freshclam;' the succeeding lines were too quick to read suggesting that 'freshclam' was indeed the culprit.

_**Is there a text file for this "rc.d"? If so, can you point me to it?** I want to know so I could more easily reverse it if anything goes wrong. I still want to keep my anti-virus and my 'freshclam' virus signatures update._ And I'm not used to the command line; I'm quite happy that Ubuntu is moving more into GUI.

Thanks.

---

### Post by cariboo on 2009-11-18
You can set how often freshclam looks for new definitions in /etc/clamav/freshclam.conf. By default it checks 24 times a day.

You need to edit the file as root.

---

### Post by kelvin.illa on 2009-11-18
> **cariboo907 said:**
> You can set how often freshclam looks for new definitions in /etc/clamav/freshclam.conf. By default it checks 24 times a day.

You need to edit the file as root.

OK. 

[U]**If I edit it to "Checks 0", would I (still) be able to update it?** I want it to update when I want it to, not automatically.

[/U]
edit: oh yeah, thanks for the response

---

