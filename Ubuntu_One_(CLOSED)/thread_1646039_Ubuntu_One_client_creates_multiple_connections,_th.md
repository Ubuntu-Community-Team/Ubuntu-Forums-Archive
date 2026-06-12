---
title: "Ubuntu One client creates multiple connections, then quits on iBook g4"
date: 2010-12-15
forum: Ubuntu One (CLOSED)
---

### Post by j_anthony on 2010-12-15
I installed Maverick PPC on my iBook g4 12", then used the Ubuntu One preferences gui to connect to my U1 account. I synchronized Tomboy notes, then signed in online and verified that they had been correctly synced.

It appeared to be working correctly, except that the web interface showed 4 instances of the connection from my iBook, instead of just one. Thinking it was a simple glitch with the first connection, I disconnected all but one. Now I can't get the iBook to sync, although it says it's connected. I'm sure there's some simple explanation of this, but it eludes me. 

Will someone please help me troubleshoot? Thanks!

---

### Post by duanedesign on 2010-12-18
hello j_anthony, good to see another okie on the forums. :)

Ubuntu One should actually have two entries. You have to authorize your computer once for the File Sync and again for the Tomboy Notes. I like to append Tomboy to the end of the latter to distinguish it from the other entry. If you have deleted the key on the server and not the computer that could be the issue. The easiest way to rectify that is the following steps to re-add your computer.

1. Quit the Ubuntu One Preferences, if open
2. Open (Lucid): Applications->Accessories->Passwords and Encryption Keys (Maverick): System -> Preferences -> Password and Encryption Keys
3. Click on the arrow next to "Passwords"
4. Right-click on the Ubuntu One token and select "Delete"
5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
6. Click on the checkbox next to your computer
7. Click the "Remove selected computers" button
8. (Maverick): killall ubuntu-sso-login; u1sdtool -q; u1sdtool -c
(Lucid): u1sdtool -q; killall ubuntuone-login; u1sdtool -c
9. a web page, if in Lucid, or a window, in Maverick, should open,prompting you to add your computer to your Ubuntu One account
10. Add your computer

---

