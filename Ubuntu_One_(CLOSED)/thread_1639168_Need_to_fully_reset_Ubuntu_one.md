---
title: "Need to fully reset Ubuntu one"
date: 2010-12-06
forum: Ubuntu One (CLOSED)
---

### Post by Malacath on 2010-12-06
I accidentally deleted the computer i'm using from the Ubunto one devices screen on the website.

Now my computer won't sync and it is impossible to add it to the devices because the machine is now listed as [local Machine] instead of the actual computer name.

Is there a way to full reset Ubuntu one so it asks for username again?
I've tried uninstalling and reinstalling using the software centre but it doesn't reset it. Is there a configueration file somewhere I can delete to reset it?


EDIT: Nevermind. Found the other thread. Got it working now.

---

### Post by duanedesign on 2010-12-07
Thank you for updating the thread and letting us know you found a solution. I am going to post the steps here in case someone else with your issues finds this post.

1. Quit the Ubuntu One Preferences, if open
2. Open Applications->Accessories->Passwords and Encryption Keys
3. Click on the arrow next to "Passwords"
4. Right-click on the Ubuntu One token and select "Delete"
5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
6. Click on the checkbox next to your computer
7. Click the "Remove selected computers" button
8. killall ubuntu-sso-login; u1sdtool -q; u1sdtool -c
NOTE: (For Lucid): u1sdtool -q; killall ubuntuone-login; u1sdtool -c
9. a web page, if in Lucid, or a window, in Maverick, should open,prompting you to add your computer to
your Ubuntu One account
10. Add your computer

thank you,
duanedesign

---

### Post by unisubzero on 2010-12-21
Hi duanedesign,

Could you explain how to do step 2, 3 and 4 in command-line ?

Thanks.

Gr. Uni

---

