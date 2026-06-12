---
title: "Problems Google Calendar sync"
date: 2015-04-21
forum: Ubuntu Phone and Tablet
---

### Post by rolandbreedveld on 2015-04-21
Can't get the Google Calendar-sync working, tried it with multiple accounts:

Apr 21 10:30:53 ubuntu-phablet syncevo-dbus-server[17630]: [ERROR] error code from SyncEvolution fatal error (local, status 10500): no datastores active, check configuration
Apr 21 10:30:58 ubuntu-phablet syncevo-dbus-server[17630]: [ERROR] error code from SyncEvolution remote, status 400: REPORT 'meta data': bad HTTP status: <status 1.1, code 400, class 4, Bad Request>
Apr 21 10:30:58 ubuntu-phablet syncevo-dbus-server[17630]: [ERROR] local, status 10400
Apr 21 10:30:58 ubuntu-phablet syncevo-dbus-server[17630]: [ERROR] error code from Synthesis engine local, status 10400
Apr 21 10:30:58 ubuntu-phablet syncevo-dbus-server[17630]: [ERROR] error code from SyncEvolution local, status 10400: failure on target side @google-calendar-5 of local sync
Apr 21 10:30:58 ubuntu-phablet syncevo-dbus-server[17630]: [ERROR] @default/calendar_uoa_5: aborted on behalf of user (local, status 20017)

Running Ubuntu 14.10-r21 on Aquarius 4.5 Ubuntu

someone any idea how to fix this ?

---

### Post by rolandbreedveld on 2015-04-25
Reported as bug on launchpad:
[https://bugs.launchpad.net/address-book-app/+bug/1448426](https://bugs.launchpad.net/address-book-app/+bug/1448426)

---

