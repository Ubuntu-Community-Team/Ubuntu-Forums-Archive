---
title: "Strange Firefox+UbuntuForums bug"
date: 2012-02-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-02-27
A strange bug: When accessing UbuntuForums.org with Firefox (Current update, PP) it is impossibe to post or start a thread. As you can see at the attached screenshot, there are no fonts / font sizes available for selection. You can type the message, but after hitting "Submit", I get an error that the message should have at least one character. It seems to only affect UbuntuForums: I can post on other boards using the exact same browser.

And, in this same PC, UbuntuForums works fine with Chromium.

I'm not sure it only affects UbuntuForums, but very weirdly, it seems like it.

Anyone else seeing it?

OBS: FireFox Reinstall, purge/install, erasing my $HOME .Mozilla settings, etc has been tried - no change.

Regards,
Effenberg

EDIT: Actually, no text-formatting icon is clickable. All of them are there, just as static images. Links like "Forum Help", "Quick Links" that should pop a menu when clicked, don't work too. 

I'm confused now if this is FireFox bug, or if somehow UbuntuForums JS/CSS was changed and became incompatible with FireFox...

---

### Post by cariboo on 2012-02-27
We've seen a few things that need fixing, since the upgrade to a newer version vBulletin, but we haven't heard of any problems with not being able to post using Firefox.

---

### Post by scradock on 2012-02-27
> **effenberg0x0 said:**
> A strange bug: When accessing UbuntuForums.org with Firefox (Current update, PP) it is impossibe to post or start a thread. As you can see at the attached screenshot, there are no fonts / font sizes available for selection. You can type the message, but after hitting "Submit", I get an error that the message should have at least one character. It seems to only affect UbuntuForums: I can post on other boards using the exact same browser.

And, in this same PC, UbuntuForums works fine with Chromium.

I'm not sure it only affects UbuntuForums, but very weirdly, it seems like it.

Anyone else seeing it?

OBS: FireFox Reinstall, purge/install, erasing my $HOME .Mozilla settings, etc has been tried - no change.

Regards,
Effenberg

EDIT: Actually, no text-formatting icon is clickable. All of them are there, just as static images. Links like "Forum Help", "Quick Links" that should pop a menu when clicked, don't work too. 

I'm confused now if this is FireFox bug, or if somehow UbuntuForums JS/CSS was changed and became incompatible with FireFox...

I'm using Firefox in PP (updated). No sign of the error that you report - I can [FONT="Book Antiqua"]change fonts[/FONT] and back again....

---

### Post by effenberg0x0 on 2012-02-27
Just found it. 
It was the "User Agent RG 1.0" FireFox add-on. I installed it a while ago to try to trick my Bank I was using IE... And disabling it [COLOR=DarkOrange]_***[SIZE=3]f[/SIZE]***_[/COLOR][SIZE=1]_***[COLOR=DarkGreen]i[/COLOR]***_[/SIZE][COLOR=Red]_***[SIZE=3]x[/SIZE]***_[/COLOR][SIZE=1]_***[COLOR=DarkGreen]e[/COLOR]***_[/SIZE][COLOR=Blue]_***d***_[/COLOR] all problems.

Regards,
Effenberg

**EDIT:** Explanation: Websites commonly keep different css/js code to workaround browsers limitations and poor-adherence to standards, so that pages look more or less the same in all of them. This is detected via parsing the user-agent string. Somehow my user-agent add-on was set to reply to queries as Safari (maybe it's a default or something).

---

