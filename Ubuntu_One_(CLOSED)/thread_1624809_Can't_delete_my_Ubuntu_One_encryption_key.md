---
title: "Can't delete my Ubuntu One encryption key"
date: 2010-11-18
forum: Ubuntu One (CLOSED)
---

### Post by fabdango on 2010-11-18
Guys,

I can't get U1 to work. I removed my machine from U1 site and then I tried to add it again, but the login screen won't appear. I purged Ubuntu One completely (config files, local cache, packages, etcetera) but there's one thing I can't do: deleting my encryption key.

[img]http://dl.dropbox.com/u/6111247/2010-11-18-UbuntuOne.png[/img]

It's simply not there and since I can't remove it, I'm not able to add my machine to U1.

It happened in Maverick so I upgraded to Natty, but the problem is still there.

---

### Post by duanedesign on 2010-11-19
The Ubuntu One Token will be in the folder above the Passwords:login folder. Seahorse did this to me as well, where it opens and the Passwords:default folder does not have the option to expand the folder. Right-click on the Passwords:default folder and select 'unlock'. The triangle should then appear telling you that you can expand the folder. You should then be able to find the Ubuntu One Token. Right-click and delete it. Then go to a Terminal and run this command:

killall ubuntu-sso-login; u1sdtool -q; u1sdtool -c

The window should open allowing you to add your computer. At the bottom there is a link for existing accounts.

good luck,
duanedesign

---

### Post by fabdango on 2010-11-19
LOL, it was so easy. I feel kinda stupid. Thank you **very** much!!

---

