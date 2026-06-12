---
title: "Ubuntu One accounts"
date: 2010-05-04
forum: Ubuntu One (CLOSED)
---

### Post by haydemon on 2010-05-04
I set up 2 different accounts in Ubuntu One, one at work and one at home. I now want to consolidate both accounts into one, using just one login for accessing all my files. How can I, (a) consolidate the files from one account to the other, and (b) get rid of one of the 2 accounts so that files stop syncing to the wrong one?:confused:  I'm currently using Ubuntu Lucid. Thanks!

---

### Post by joshuahoover on 2010-05-04
> **haydemon said:**
> I set up 2 different accounts in Ubuntu One, one at work and one at home. I now want to consolidate both accounts into one, using just one login for accessing all my files. How can I, (a) consolidate the files from one account to the other, and (b) get rid of one of the 2 accounts so that files stop syncing to the wrong one?:confused:  I'm currently using Ubuntu Lucid. Thanks!

This is going to be a bit confusing, apologies in advance! :)

To consolidate the files using Ubuntu One, you could share the files with the other user (e.g. Work user shares all Ubuntu One synced folders with the Home user). Then you would copy the shared files out of the "Shared with Me" folder into a different folder synced by Ubuntu One (like ~/Ubuntu One) on the account you want to keep active. From there you would do the following on the computer you shared the files from:

1. Open Applications->Accessories->Passwords & Encryption Keys
2. Right-click on the "Ubuntu One token" and select "Delete"
3. Open Applications->Accessories->Terminal and run: killall ubuntuone-login ubuntuone-syncdaemon ubuntuone-preferences
4. Open System->Preferences->Ubuntu One
5. You should see a web browser open and prompt you to add your computer. Make sure you're logged in as the Ubuntu One user you want to consolidate to.

Thanks,

Joshua

---

### Post by haydemon on 2010-05-05
Thanks. That helped!

---

