---
title: "[Android] Ubuntu One Files 1.0.3"
date: 2011-08-24
forum: Ubuntu One (CLOSED)
---

### Post by mkarnicki on 2011-08-24
Hi guys!

It's been a while since we last updated Ubuntu One Files for Android, but we've kept ourselves busy!
Please give it a spin and post in this thread if notice anything out of place, it's about to land on the Market.

Most notable changes since v. 1.0.2:
*tr;dr : SSO login (token stored in AccountManager), better notifications, robust up down service, bugfixes*

- login via SSO (fixed 'failed login' issue)
- much better background service, that allowed us:
  - to finally craft some nicer notifications, some of them with progress bars
  - to download files while we're uploading others, and vice versa
- many small bugfixes, some more visible for affected users than others
- you'll notice we require more permissions - indeed, we use AccountManager to store your OAuth token (we do not store your launchpad password). This is to support future features, sharing token between our apps, and even sharing the token (with your explicit permission) to 3rd party apps. Much like Gnome keyring
- you'll notice you can turn on more verbose logging in the 'Report problem' section of settings screen, and even send the logs so we can investigate any issues - no, we do not require READ_LOGS permission for that \o/

Direct link: [http://goo.gl/RlQRk](http://goo.gl/RlQRk)
QR code: [http://goo.gl/RlQRk.qr](http://goo.gl/RlQRk.qr)

Sincerely,
Micha&#322;

---

### Post by mkarnicki on 2011-08-29
Updated the links in the first post to u1f-1.0.3.apk

- Fixed failed login issue.

---

### Post by mkarnicki on 2011-08-31
Hi everyone,

Just to let you guys know, we have to sit a while longer on 1.0.3 update. We have successfully fixed 'failed login' issue, but it turns out there's a related issue in Single Sign On, that causes people with non-synced clock/time on their device, to receive 'Unauthorized' response.

Sorry about that, we hope to release it soon.

---

### Post by mkarnicki on 2011-09-01
Ok guys, we're live on the Market with U1F v1.0.3, thanks for testing!

---

### Post by mkarnicki on 2011-09-12
We've pushed 1.0.3.1 update with a fix for slower devices. We didn't play nice enough and put some stress on the notification manager, which in turn could crash the notification bar and the system itself.

I am really sorry about that, we hope the fix will resolve the issue. Make sure you update Ubuntu One Files and.. happy browsing :) !

---

