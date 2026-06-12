---
title: "Ubuntu one quit working"
date: 2010-03-21
forum: Ubuntu One (CLOSED)
---

### Post by Vrekk on 2010-03-21
I'm using the Ubuntu 10.04 beta and the Ubuntu one just quick working today and I can't figure it why.  I added a few files using my Desktop and now my netbook client won't update.  The netbook says all the files are upto date but the files aren't there.  They show up on the web interface.

I'm sorry if this doesn't help any, I don't know anyone information to provide.

---

### Post by joshuahoover on 2010-03-22
> **Vrekk said:**
> I'm using the Ubuntu 10.04 beta and the Ubuntu one just quick working today and I can't figure it why.  I added a few files using my Desktop and now my netbook client won't update.  The netbook says all the files are upto date but the files aren't there.  They show up on the web interface.

I'm sorry if this doesn't help any, I don't know anyone information to provide.

Sorry to hear Ubuntu One isn't working properly for you. I'm thinking you might need to restart Ubuntu One on the netbook for it to see the updates. You can connect/disconnect to do this. In Lucid, you do this through the Ubuntu One preferences which can be found in the "Me menu" or System->Preferences->Ubuntu One and then under the Devices tab.

If that doesn't solve the problem, please file a bug or hop on #ubuntuone on Freenode IRC for real time support. Ask for joshuahoover there. I'm normally on Monday-Friday, 13:00 - 21:00 UTC.

Thank you,

Joshua

---

### Post by Vrekk on 2010-03-22
> **joshuahoover said:**
> Sorry to hear Ubuntu One isn't working properly for you. I'm thinking you might need to restart Ubuntu One on the netbook for it to see the updates. You can connect/disconnect to do this. In Lucid, you do this through the Ubuntu One preferences which can be found in the "Me menu" or System->Preferences->Ubuntu One and then under the Devices tab.

If that doesn't solve the problem, please file a bug or hop on #ubuntuone on Freenode IRC for real time support. Ask for joshuahoover there. I'm normally on Monday-Friday, 13:00 - 21:00 UTC.

Thank you,

Joshua

Thanks for the reply; Ill head over to the IRC when I have more time, but for now here is my update:

After several rebooting the netbook, The preferences opens again (when this bug first showed up, Ubuntu One would crash when I  tried to open it, didn't notice it at first) but connecting and disconnecting it didn't help. After I made sure I had a internet connection and waited a little while, the files still didn't show up on the computer :'(

---

### Post by Johanano on 2010-03-23
I got similar issues. I'll head over to the IRC channel tonight. UbuntuOne just won't start, hmm. I thought maybe there would be some icon to clikc to start the client but nope. We'll get this sorted out, I'm sure.

---

### Post by joshuahoover on 2010-03-23
> **Vrekk said:**
> Thanks for the reply; Ill head over to the IRC when I have more time, but for now here is my update:

After several rebooting the netbook, The preferences opens again (when this bug first showed up, Ubuntu One would crash when I  tried to open it, didn't notice it at first) but connecting and disconnecting it didn't help. After I made sure I had a internet connection and waited a little while, the files still didn't show up on the computer :'(

OK, if you're not able to get on IRC, please file a bug:

[LIST=1]
[*][https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command on your netbook (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[/LIST]
Thank you,

Joshua

---

### Post by dabomb1022 on 2010-03-23
Don't file it! I have the same problem and somebody else already reported it. see here:
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/539581](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/539581)

---

### Post by duanedesign on 2010-03-23
Unless you can determine  from the logs that you have the **exact** same problem it is better to file a new bug.

---

### Post by serfcx on 2010-03-24
I have what looks like the same problem. I carried out instructions as per post #2 on buglist 539581 but nothing has changed.
I have all the folders on my laptop running Lucid beta1 but no files, and the folders have a symbol saying "awaiting sync". All files are on the web interface.
Also on the Services tab in preferences the tick boxes for Bookmarks and Contacts are "greyed out" and cannot be actified.

---

### Post by joshuahoover on 2010-03-24
> **serfcx said:**
> I have what looks like the same problem. I carried out instructions as per post #2 on buglist 539581 but nothing has changed.
I have all the folders on my laptop running Lucid beta1 but no files, and the folders have a symbol saying "awaiting sync". All files are on the web interface.
Also on the Services tab in preferences the tick boxes for Bookmarks and Contacts are "greyed out" and cannot be actified.

I just left a comment on the bug for something to try. I'm curious if it's related to bandwidth settings being turned on. Since there are no log files that indicate that might be the case, I'm guessing but I'd like to know if turning those settings off works around the problem for people.

Thank you,

Joshua

---

### Post by dabomb1022 on 2010-03-24
I can't open the preferences on ubuntu one or open it at all. It just says opening for 10 seconds and goes away.

---

### Post by serfcx on 2010-03-25
> **joshuahoover said:**
> I just left a comment on the bug for something to try. I'm curious if it's related to bandwidth settings being turned on. Since there are no log files that indicate that might be the case, I'm guessing but I'd like to know if turning those settings off works around the problem for people.

Thank you,

Joshua

Although I didn't have bandwidth settings on I tried your deleting the .conf file but with no change.

Still broke !

EDIT Sorry but dropbox works perfectly so bye-bye U1

---

### Post by jaco223 on 2010-03-28
**I can't open  the preferences on ubuntu one or open it at all. It just says opening  for 10 seconds and goes away.**

I'm having the same issue. I'm using lucid beta 1

---

### Post by joshuahoover on 2010-03-29
> **jaco223 said:**
> **I can't open  the preferences on ubuntu one or open it at all. It just says opening  for 10 seconds and goes away.**

I'm having the same issue. I'm using lucid beta 1

In this case, you may want to try deleting your ubuntuone token in Applications->Accessories->Passwords and Encryption Keys under the "Passwords: default". Once you do that, open a terminal session (Applications->Accessories->Terminal) and run: ubuntuone-preferences

If that doesn't open the preferences window it should output something that will help us troubleshoot the problem. You can then file a bug explaining the problem and including any output there: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

Thank you,

Joshua

---

### Post by PaiSand on 2010-03-30
Please verify inside ~/.config/ubuntuone/ if you have any file. You should see the config file there, and if not, go and do your stuff in this bug report: [https://bugs.launchpad.net/ubuntuone-client/+bug/551813](https://bugs.launchpad.net/ubuntuone-client/+bug/551813)

I just filled it and could be helpful if more people add their own reports using this on the terminal:
$ apport-collect -p ubuntuone-client 551813

---

### Post by tin_truc22 on 2010-03-31
I have a problem with Ubuntuone-preference, I can't even start it from termial (just wait no error, no return).
After that I found the problem may be in the "Passwords and Encryption Keys" because I enable password less login (by check Don't ask for password on login). So I don't have the keyring for ubuntuone

I don't know how the password is stored but sometime it locks the screen (when switch user) and I can't unlock even I entered the password I set when created new user (unikey). I can't change password by 
sudo passwd unikey
It has error
> 
passwd: System error
passwd: password unchanged
And when change in the it in the user and group (from unikey user) The change user password dialog just freeze. When I login to antother user (has administrator right) to change unikey's password It's don't free but i unchecked "don't ask for password on login" I couldn't login in use the password i has set.

Finally In the "Passwords and Encryption Keys" when I added new keyring it's just a problem "Error communicating with gnome-keyring-daemon"
So maybe these is the reason for my Ubuntuone client.

I'll test more about this bug and report it with a use case in launchpad (it's maintaining now) but i don't know which package to report because "the don't ask for password on login" just appeared recently after I updated ubuntu.
Be free to contact me on IRC afterlastangel at freenode

---

