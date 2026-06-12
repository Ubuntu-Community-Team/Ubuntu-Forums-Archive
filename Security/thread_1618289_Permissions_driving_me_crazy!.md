---
title: "Permissions driving me crazy!"
date: 2010-11-10
forum: Security
---

### Post by Historynut on 2010-11-10
How can I get rid of all the permission requirements that pop up whenever I do the following? To retrieve mail in Evolution, I must enter a password. To access the files on my Windows hard drive, I must enter a password. To move a font file from the desktop to one of my usr files, I must enter a password. Is there any way to get rid of all these password requirements? I can be notified of an answer at [email]wileye@sonic.net[/email].

---

### Post by HermanAB on 2010-11-10
Howdy,

To some degree yes.

Evolution can remember your mail password.  You just have to configure the mail account properly.

If you are using Active Directory, then you can make your Ubuntu machine a domain member using  and then the Windows password problem will go away.

For doing super user stuff, use sudo.  It will only ask for a password once per session.

---

