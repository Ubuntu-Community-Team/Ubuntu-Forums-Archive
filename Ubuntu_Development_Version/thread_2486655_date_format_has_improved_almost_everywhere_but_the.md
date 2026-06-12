---
title: "date format has improved almost everywhere but the lock screen"
date: 2023-05-07
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-05-07
Hello,

during the last gnome shell versions the date locale has improved over the time. Now, on top panel the date is not only displayed correctly as far as order is concerned, but also displayed correctly as far as orthography is concerned (actually intonation) at least for the Hellenic (Greek) language.

Of course there is the date menu formatter extension which allows many modifications, yet in the latest ubuntu versions, unless someone wishes to change the default, no corrections are necessary. The changes can be made under Settings->Region & Language->Manage Installed Languages->Regional Formats and from there picking up the desired format and then Apply System-Wide.

The only problem that remains is the format of the lock screen. Searching the net I found two different solutions:
i) the first one requires some tampering with the ubu box, which I haven't tested:
[https://askubuntu.com/questions/1343639/how-can-i-custom-format-the-lock-screen-date-in-ubuntu-20-04-without-extensions](https://askubuntu.com/questions/1343639/how-can-i-custom-format-the-lock-screen-date-in-ubuntu-20-04-without-extensions)

ii) the second one uses the Customize Clock on Lock Screen extension to fix the date format by following the steps:
a) install the extension
b) open its options
c) click "Reset to system date" 
d) enable "Turn on to customize date format" 
e) and add to the box underneath (Enter valid time format) the string: %A %-d %B
for the: day of the week-day-month format, e.g. Mon 9 May

Just for a quick reference in case someone wants to fix it.

Regards!

---

