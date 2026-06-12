---
title: "Disable Clear History Button in IE 6"
date: 2007-09-30
forum: Windows
---

### Post by rahimveron on 2007-09-30
Hello,
My computer is also used by my little sister and i want to know the sites visited by her.
How could i disable the Clear History Button so that she is unable to clear her history.

I googled and found this solution
1. Open REGEDIT.
2. Navigate to section: HKEY_CURRENT_USER\ Software\ Policies\ Microsoft\ Internet Explorer\ Control Panel.
3. Create a new DWORD value.
4. Name it "History". Give it a value of "1".
5. Close REGEDIT.

But i dont find that registry entry in Regedit. In my regedit it shows the following link:
HKEY_CURRENT_USER\ Software\ Policies\ Microsoft\SystemCertificates\

I use Win XP SP2 with IE 6.0.2900.2180

---

### Post by netwrkengeer on 2008-10-06
Simply create the Key's you need and create the dword required and it works great.

Also check out here for other options.
[http://www.onecomputerguy.com/ie_tips.htm#restrictions_1](http://www.onecomputerguy.com/ie_tips.htm#restrictions_1)

---

### Post by DrMega on 2008-10-06
It doesn't take very much effort at all to clear the history in IE. The safest easy way to monitor internet activity is to tell your router to keep a log, and set an good pasword on the admin account in your router's control panel.

---

