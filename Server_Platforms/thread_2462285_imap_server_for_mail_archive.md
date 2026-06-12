---
title: "imap server for mail archive"
date: 2021-05-17
forum: Server Platforms
---

### Post by shortmort372 on 2021-05-17
I'm considering setting up Ubuntu on a VPS, to replace my current managed shared server account.  I've managed Ubuntu on the desktop before, but I'm new to using it on a server.

I'm using Google Workspace to send and receive my current mail, but I archive mail to an imap instance on the shared server.  I'll need something basic to replace it; something that will communicate with Outlook on my desktop via imap, and permit me to copy email from the Google account to the imap folder on my VPS server.  I won't need SMTP; no mail will be sent from the account, nor will it receive mail - it will get there via a SSL transfer from Outlook.

I can do something like this on my Windows desktop, using hMailServer.  I'm basically looking for a linux equivalent to hMailServer.  Can anyone make a recommendation?

adTHANKSvance,
Dan

---

### Post by HermanAB on 2021-05-18
The absolutely easiest mail system to set up is Citadel. Get it at citadel.org and run the Easy Install script.  It will have more features than you need for less hassle.

---

### Post by spjackson on 2021-05-18
I would say that Dovecot is the main candidate, followed by Courier and Cyrus. All of these are in the repositories.

---

### Post by slickymaster on 2021-05-18
*Thread moved to **Server Platforms**.*

---

### Post by shortmort372 on 2021-05-18
Thanks for the responses - I'll review the options.  -Dan

---

