---
title: "date locale, language-format account issue"
date: 2024-08-12
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-08-12
Hello,

both in noble and oracular I was changing account language and account format language. 

When both account language and format language are greek then things are ok except case iii (see below).

When account language is english us and format language is greek then:

i) the top panel date format is us instead of el e.g. &#913;&#965;&#947; 12 (Aug 12) instead of 12 &#913;&#965;&#947; (12 Aug)
ii) clicking on the date of the top panel, the date that appears is wrong again: &#913;&#965;&#947;&#959;&#973;&#963;&#964;&#959;&#965; 12 2024 (August 12 2024) instead of 12 &#913;&#965;&#947;&#959;&#973;&#963;&#964;&#959;&#965; 2024 (12 August 2024)
iii) events are wrong as well, e.g. &#913;&#965;&#947;&#959;&#973;&#963;&#964;&#959;&#965; 14 (August 14), instead of 14 &#913;&#965;&#947;&#959;&#973;&#963;&#964;&#959;&#965; (14 August).

The only thing that works it to use English UK for language, yet the Trash is called Rubbish Bin and Wastebasket. The thing it that I cannot choose any other english languages apart from Canada and Australia, since even doing so, the account language goes back to us.

The weird thing is that the login screen clock-date language is correct. 

I tried to un-comment /etc/locale.gen and then to issue the command: sudo locale-gen to no avail.

As a result there is an issue about gnome shell and date format.

Regards!

---

### Post by Claus7 on 2024-08-12
Hello,

I created a new user under oriole and found out that a new option is available: someone can change the language and format of the login screen, option that is not available under noble and under my first user under oriole. 

Still gnome shell refuses to comply with the format of date when us language is selected.

Regards!

---

