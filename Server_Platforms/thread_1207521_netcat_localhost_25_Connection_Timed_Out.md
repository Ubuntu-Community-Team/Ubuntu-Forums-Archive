---
title: "netcat localhost 25: Connection Timed Out"
date: 2009-07-08
forum: Server Platforms
---

### Post by NickBudi on 2009-07-08
I've just begun to follow the direction on setting up a Postfix mail server here:
 [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)
I got as far as installing Postfix and Mailx and am about to test the default postfix settings. I added a test user, fmaster, and then typed 'netcat localhost 25'.

Instead of the expected reply:
Trying 127.0.0.1...
Connected to UServer... etc.

After about 5 minutes of a blank reply screen, this shows up:
localhost [127.0.0.1] 25 (smtp) : Connection timed out

Does anyone know the problem?

---

### Post by NickBudi on 2009-07-08
Closed, issue resolved

---

### Post by bhart007 on 2009-10-02
What was the cause?

---

