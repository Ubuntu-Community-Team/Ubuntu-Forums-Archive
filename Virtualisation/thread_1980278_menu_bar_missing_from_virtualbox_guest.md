---
title: "menu bar missing from virtualbox guest"
date: 2012-05-14
forum: Virtualisation
---

### Post by sarhound on 2012-05-14
I'm in my virtualbox Windows 7 guest now, but I don't have a devices tab showing anywhere. All I have is the title bar of the guest saying "Windows7 (ScreenResolution) [Running] - Oracle VM VirtualBox". Beneath it, I have a regular Windows 7 desktop showing.

Watching the YouTube videos that I've been able to locate, everyone seems to have a Machine... Devices... Help bar beneath the title bar.

How do I get that bar back?

---

### Post by CharlesA on 2012-05-14
Check to make sure you do not have "scale mode" enabled:
[http://www.virtualbox.org/manual/ch01.html#intro-resize-window](http://www.virtualbox.org/manual/ch01.html#intro-resize-window)

Ctrl + C will toggle scale mode.

---

### Post by sysarc on 2012-07-14
My Ubuntu version 12.04 system update today.

Virtualbox version 4.1.18
This solution work for me.

Close open VM's. 
Go to Virtualbox **File**>>**Preferences** menu.
Click **Input** button.
Click reset icon.
Click Host Key area and set new host key "**Alt Gr** + **Right Ctrl**"
Restart VM press "**Alt Gr** + **Right Ctrl**" .
Now VM menu is showing.

---

### Post by cmcanulty on 2012-10-31
I also have this problem no devices show and on input there is no reset button. Also what is alt gr?

---

### Post by CharlesA on 2012-10-31
Alt key, I think.

---

### Post by largewhale on 2013-02-26
> **sysarc said:**
> My Ubuntu version 12.04 system update today.

Virtualbox version 4.1.18
This solution work for me.

Close open VM's. 
Go to Virtualbox **File**>>**Preferences** menu.
Click **Input** button.
Click reset icon.
Click Host Key area and set new host key "**Alt Gr** + **Right Ctrl**"
Restart VM press "**Alt Gr** + **Right Ctrl**" .
Now VM menu is showing.

thanks. It works. 
And I changed to "right shift" key as host key , due to the key is more bigger than the "ctrl" key on my Thinkpad. It's convenient for use. :p

---

### Post by largewhale on 2013-02-26
> **cmcanulty said:**
> I also have this problem no devices show and on input there is no reset button. Also what is alt gr?

I don't know what is "alt gr" neither. You just choose a key you like (follow the message showed in Vbox), and take it active. That's all.

---

### Post by CharlesA on 2013-02-26
AltGr is on certain keyboards, usually ones that have special symbols on them.

[http://en.wikipedia.org/wiki/AltGr_key](http://en.wikipedia.org/wiki/AltGr_key)

---

### Post by ravipuliyath on 2013-10-30
Press right ctrl+C (Host + C) for changing to scale mode

---

