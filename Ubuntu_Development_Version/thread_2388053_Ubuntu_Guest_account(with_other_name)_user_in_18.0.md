---
title: "Ubuntu Guest account(with other name) user in 18.04"
date: 2018-03-27
forum: Ubuntu Development Version
---

### Post by stylus3530 on 2018-03-27
[COLOR=#000000]Hello[/COLOR]
[COLOR=#000000]I want to create a User that has the same properties like a Guest Account user in 16.04, this means that everything will be deleted when he logs off. The name of the user must be &#8216;STYLUS&#8217;. Is there anyone who have a tutorial to do this?[/COLOR]

[COLOR=#000000]Thanks in advance[/COLOR]

[COLOR=#000000]Stylus[/COLOR]

---

### Post by TheFu on 2018-03-27
userids need to be lowercase on Unix sytems, including Linux.  Mixed case can break things and all uppercase usually will put a terminal into an uppercase-only mode.  At least it worked that way for 30 yrs.  In short, bad idea.

[https://askubuntu.com/questions/46739/case-sensitivity-of-account-usernames](https://askubuntu.com/questions/46739/case-sensitivity-of-account-usernames) might explain better and offer an override.  I would strongly suggest NOT overriding, but only you know the requirements.

You can make the name that gets displayed where it isn't the formal userid to be STYLUS, if you like.

Of course, I haven't tested the all CAPS userid in years.  Some things I've learned to do which avoid problems later.  Using all lowercase letters + numbers is something I've found avoids issues.

As for guest accounts, I cannot help from experience, but you should have the account wiped at the session logout and reboots and perhaps overnight, if you like.
google found this: [https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

---

### Post by wildmanne39 on 2018-03-27
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by mc4man on 2018-03-27
Guest sessions are disabled now due to some security issues, you can enable if wished.
A discussion, [https://community.ubuntu.com/t/guest-sessions-in-18-04-lts-are-they-needed/1714](https://community.ubuntu.com/t/guest-sessions-in-18-04-lts-are-they-needed/1714)
A method, [https://community.ubuntu.com/t/guest-sessions-in-18-04-lts-are-they-needed/1714/85](https://community.ubuntu.com/t/guest-sessions-in-18-04-lts-are-they-needed/1714/85)

---

### Post by Qassis on 2018-05-14
Ubuntu 18.04 Guest Account is NOT secure.  Enabling and using the current version of guest sessions that comes with Ubuntu 18.04 may give some a false sense of security.  
Current Security Issues include: 1. The guest's data is not secure (can be exploited after logoff) and 2. Normal users are NOT protected from the guest's snooping/taking their files/data, 3. guests can see/access system files.
1.  Protecting your guest:  For now, I'm continuing to use Ubuntu 16.04 on the machines I place with security in mind (mostly for senior citizens' use, using guest account to ensure there is no data left behind after they log out).  An example is a computer I placed in our local Senior Citizen Center for their use.
2.  Protecting your normal users: The current guest account in 18.04 does NOT prevent guests from accessing user files/data.  They can see/access them.  I have a work around which works for me at home but I would not recommend putting it out for others.
I have locked my Ubuntu 18.04 Guest Sessions (guest user account) out of the normal users files by running the following in the home directory:
[FONT=Ubuntu]  sudo chmod -R o-rwx *
[/FONT]NOTE:  My 18.04 guest sessions (guest account) even with this does NOT meet the minimum standards to be considered 'secure'.  The guest can still get to system folders/files.
The guests' data can still be found and exploited after logout.
I use 18.04 imperfect, unsecure guest account ONLY at home for my granddaughters' visits.
I would love to hear what others have done to improve the current guest sessions (guest account) Security on their Ubuntu 18.04 boxes.
Thank you.

---

### Post by slickymaster on 2018-05-15
Bionic is already released. Thread closed.

---

