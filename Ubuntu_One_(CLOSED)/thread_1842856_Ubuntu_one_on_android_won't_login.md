---
title: "Ubuntu one on android won't login"
date: 2011-09-12
forum: Ubuntu One (CLOSED)
---

### Post by DC80 on 2011-09-12
Hi there,

I have some problems regarding the usage of ubuntu one on my Samsung Galaxy S2 which is running Android. I got the app from Android Market.

The following happens:

I have to sign-in, which i did, with my credentials and after starting the app it is trying to connect. I do not know if it got a connection (i used WiFi) however i got an error. The error i got was: error:null and does nothing after that. 

When i check the settings it says under username: unknown.

I did the following steps to solve this:

- reinstall the app
- in the ubuntu one account ([https://one.ubuntu.com](https://one.ubuntu.com)) try to add or remove my smartphone.
- remove credentials and add them again.
- Check password and login name
- search google for an answer
- search this forum for an answer

Also if I try to create an new account i get an error on the website: Invalid OpenID transaction

Any information about my smartphone:

Model: GT-I9100 (samsung galaxy S2, NOT ROOTED)
Android version: 2.3.3
Ubuntu one version: 1.0.3

How do i solve this? I filed a report already via e-mail.

Kind regards,

DC80

---

### Post by mkarnicki on 2011-09-12
That's the right place to ask. I've asked our support people, we'll look into that. The error you mentioned, although not descriptive at all, is an authentication issue.

---

### Post by DC80 on 2011-09-12
Thank you for your reply. I'm sorry for not providing you with more information. This is what Android showed me. If there is a log file then i'm happy to look for it. 

Kind regards,

DC80

---

### Post by DC80 on 2011-09-14
Hi all,

I have set this topic to solved because I found out what the error was. While Android (or the Ubuntu One client) was returning a error (error:null). I began to realize that when I did sign up for Ubuntu One I had to fill out a password with minimal requirements like uppercase, lowercase, numbers and so on.

I changed my account password according to these requirements and it working like a train!

So this topic is no longer valid. I'd like to suggest to have more descriptions with the error. 

Thanks for the help guys!

Kind Regards,

DC80

---

### Post by mkarnicki on 2011-09-21
Hello,

Thanks for getting back with the update. I doubt, however, that you would be able to set up a Single Sign On account with a weak password. It was probably just the case of logging out and in to the app.

Anyway, much thanks! Take care.

---

### Post by Th3Alchemist on 2011-09-25
I've got the same problem... After login:

> Loading files -> Error: null -> This folder is empty

---

### Post by mkarnicki on 2011-10-26
That's an authentication issue. This will throw you back to the login screen in the soon-to-come update. Please use the Menu > Settings > Advanced options > Remove device from U1, and try logging in again. It might help.

---

### Post by Th3Alchemist on 2011-10-28
> **mkarnicki said:**
> That's an authentication issue. This will throw you back to the login screen in the soon-to-come update. Please use the Menu > Settings > Advanced options > Remove device from U1, and try logging in again. It might help.

I tryed that... Still nothing... waiting for the update

---

### Post by barrydrake on 2012-12-27
Hi - I got exactly the same problem on my Samsung Galaxy Ace.  The login authentication fails and takes me straight back to the login screen with no error message that I can see.

As this is marked 'solved' is the thread still being watched?

The U1 version installed is 1.2.5

---

### Post by TRPrecht on 2013-01-03
I had a similar issue on my HTC G2. I removed the app and reinstalled a power reset of the device in between and my solution was changing my password after all the fuss.

---

