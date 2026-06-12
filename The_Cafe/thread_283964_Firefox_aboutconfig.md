---
title: "Firefox about:config"
date: 2006-10-24
forum: The Cafe
---

### Post by bruenig on 2006-10-24
I am interested in seeing the about:config changes in firefox people have made.

Here are some I have made in firefox 2.0.

To get remove that stupid red x from all of the tabs.

```
browser.tabs.closeButtons - set the value to 2
```



Make more tabs visible on the tab bar instead of having to use the scroll arrows to see them.

```
browser.tabs.tabMinWidth - set the value to 0.
```

This will resize the tabs when you get pressed for space. This generally allows for 25 tabs to be opened before it starts forcing the scrolling arrows.

---

### Post by aysiu on 2006-10-24
I prefer 3, which is the old Firefox behavior--one "close tab" button on the far right.

---

### Post by FISHERMAN on 2006-10-25
```
browser.tabs.tabMinWidth - set the value to 0.
```
Is the only I use, I just hate those <>-buttons(actually one of the reasons why I don't want to switch to Epiphany) when you many tabs open.

---

### Post by bonzodog on 2006-10-25
other about:config tricks:

To stop it polling for IPv6:

network.dns.disable.IPv6  - set to 'true'

network.http.pipelining - set to 'true'

network.http.pipelining.maxrequests - if on a good connection, set to between 15 - 30.

The last one there will download images and text simultaneously.

---

### Post by aysiu on 2006-10-25
Is there a trick for Control-W closing Firefox if only one tab is open? Firefox 2.0 seems to have disabled this previously available functionality.

---

### Post by roderikk on 2006-10-25
And what about an option to not display the vertical scrollbar (at all). I use the mouse for scrolling and thinks it looks much tighter without. I did this in FF1.5 using the userChrome.css and setting something like scrollbar display:none, but when I try it in FF2.0 it doesn't work. Anybody figured it out already?

---

### Post by .t. on 2006-10-25
In FF2.0, the option to force all new pages to openin new tabs has gone. I hate new windows. Does anyone know what option changes this?

---

### Post by roderikk on 2006-10-25
> **.t. said:**
> In FF2.0, the option to force all new pages to openin new tabs has gone. I hate new windows. Does anyone know what option changes this?
This option is still there. However, it doesn't work the first time, so you should explicitly press the New windows should be opened in "a new tab" select button again in the preference->tab menu if you want this option. After this it works flawlessly. I guess this is a bug...

Now only how to get rid of the vertical scrollbar, anyone?

---

### Post by Ramses de Norre on 2006-10-25
[This](http://www.ubuntuforums.org/showthread.php?t=179540) has always been pretty useful for me, and thanks for the tabMinWidth thing ;)

---

### Post by Rackerz on 2006-10-25
browser.urlbar.clickSelectsAll - Set to true

For all former IE lovers this one is a must :D. Also for Windows users too.

---

### Post by aysiu on 2006-10-25
> **Rackerz said:**
> browser.urlbar.clickSelectsAll - Set to true

For all former IE lovers this one is a must :D. Also for Windows users too.
You mean mouse users, right?

Control-L has always worked for me...

---

### Post by .t. on 2006-10-25
> **roderikk said:**
> This option is still there. However, it doesn't work the first time, so you should explicitly press the New windows should be opened in "a new tab" select button again in the preference->tab menu if you want this option. After this it works flawlessly. I guess this is a bug...

Now only how to get rid of the vertical scrollbar, anyone?
Doesn't seem to force all new windows to tabs though... Links here in this forum still open in new windows.

---

### Post by .t. on 2006-10-25
> **aysiu said:**
> You mean mouse users, right?

Control-L has always worked for me...
Yeah, I like that short cut too!

---

### Post by Ramses de Norre on 2006-10-25
> **.t. said:**
> Doesn't seem to force all new windows to tabs though... Links here in this forum still open in new windows.

Middle clicking links opens them in new tabs, I always open links that way.
I don't know if you have to configure that but I don't think so.

---

### Post by aysiu on 2006-10-25
> **Ramses de Norre said:**
> Middle clicking links opens them in new tabs, I always open links that way.
I don't know if you have to configure that but I don't think so.
Middle-clicking Javascript pop-up windows doesn't let you open them.

---

### Post by Rackerz on 2006-10-25
> **aysiu said:**
> You mean mouse users, right?

Control-L has always worked for me...

That's exactly what I meant, I use F6 normally.

---

### Post by Ramses de Norre on 2006-10-25
> **aysiu said:**
> Middle-clicking Javascript pop-up windows doesn't let you open them.

No, that's true. And it has annoyed me pretty much already..

---

