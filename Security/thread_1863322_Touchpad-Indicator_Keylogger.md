---
title: "Touchpad-Indicator Keylogger?"
date: 2011-10-17
forum: Security
---

### Post by rekh127 on 2011-10-17
So I recently installed touchpad-indicator from [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu)

And I just found it's recording every keypress in a file called screenkey.log in my home folder. Should I be worried about this program? It has a semi-legitimate reason to watch keys, to use as a hotkey, but I don't like that it's recording them.  

 I'm a little scared now.  I know I need to be cautious with what I install from non official sources, but theres several programs (indicators and such) that I've installed that I assumed were fine because they were reccommended several places on the web.

Thanks guys,
Rekh127

---

### Post by in·ter·punct on 2011-10-21
I've had touchpad-indicator installed since 11.04 and this wasn't there before, at least not in the home folder.

---

### Post by tcamdg on 2011-10-25
Hmmm, just noticed it now, too.

I'm guessing it's a legitimate debug file, mostly because I'm assuming an attacker wouldn't name a keystroke log file "screenkey.log" and store it visibly in his victim's home folder...

Anyhow, I've just uninstalled touchpad-indicator and deleted the log file. The program never really worked correctly for me in the first place, and since upgrading to 11.10, it doesn't work at all, except that it's disabled the touchpad entirely while logged in.

---

