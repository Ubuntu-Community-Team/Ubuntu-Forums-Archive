---
title: "Authentication Failed error on Desktop"
date: 2012-08-09
forum: Ubuntu One (CLOSED)
---

### Post by masticate on 2012-08-09
I'm trying to set up Ubuntu One client on my desktop. When I try to sign in, I received "The authentication failed." error message. I am able to successfully sign in using the browser and Android app.

I have tried changing the password. I am able to log in to the browser with the new password but not the desktop client.

My desktop is Wubi Ubuntu 12.04.

I see that some people were able to fix a similar issue by setting their desktop time to the correct time. My time is correct and doesn't need to be changed.

Any ideas on resolutions or further troubleshooting?

---

### Post by aff92 on 2012-08-09
Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
Check if you computer is listed as a linked device. If it is, remove it from the list by pressing Remove Device. Now try to add your device/sign in again using the ubuntu one app.

I'm not sure if this will solve your problem, but i hope it helps!

---

### Post by masticate on 2012-08-10
Hi,

Thank you for the reply. I had already tried this. The only device on that link is my Android phone.

---

### Post by Irihapeti on 2012-08-10
Try opening [https://one.ubuntu.com](https://one.ubuntu.com) in Internet Explorer (or Google Chrome) in Windows, and see if that helps. You may need to reboot Windows and then Ubuntu. (I'm guessing a bit here - I've never used Wubi.)

Reference: [https://one.ubuntu.com/help/faq/why-am-i-getting-an-the-authentication-failed-error-on-windows-225/](https://one.ubuntu.com/help/faq/why-am-i-getting-an-the-authentication-failed-error-on-windows-225/)

---

### Post by masticate on 2012-08-15
My SSL certificates were messed up.

I posted my solution at [http://ubuntuforums.org/showthread.php?p=12173674#post12173674]("http://ubuntuforums.org/showthread.php?p=12173674#post12173674")

---

