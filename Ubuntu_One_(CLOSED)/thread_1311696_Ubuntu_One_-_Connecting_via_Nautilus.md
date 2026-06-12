---
title: "Ubuntu One - Connecting via Nautilus"
date: 2009-11-02
forum: Ubuntu One (CLOSED)
---

### Post by Roger Allott on 2009-11-02
I've just subscribed to the freebie version of Ubuntu One. I'm still on 9.04, so it wasn't installed by default as it is in 9.10.

The [explanation of how to set up]("https://one.ubuntu.com/support/installation/") is jolly nice and simple, but step 4 seems to either be wrong or out-of-date. I didn't get the automatic opening of the web page from step 3, although I did get the panel widget. From the widget, it was easy to open the web page, and I was easily able to upload a test file.

However, I've been less successful getting Nautilus to connect to my Ubuntu One account, and I can't figure out why.

From the panel, I clicked on 'Open Folder' and a Nautilus screen duly appeared. There was a button saying 'Connect', which I've clicked, and it turned grey with the text 'Connecting' greyed out, as one might expect. But it's now been 'Connecting' for about 20 minutes!

Anyone with any idea as to what I should do?

---

### Post by lavinog on 2009-11-03
First check for updates.
You may need to log out then log back in if you haven't done so since installing it.

---

### Post by Roger Allott on 2009-11-03
> **lavinog said:**
> First check for updates.
Yes, I did that, but no updates were found.


> **lavinog said:**
> You may need to log out then log back in if you haven't done so since installing it.

I've done that now. No change, I'm afraid.

A curious thing though from the package list in Synaptic. The packages installed are:
ubuntuone-client
ubuntuone-client-gnome
ubuntuone-ppa-beta (this appears to be the GPG key from 14th May)

Curiously, a non-installed package is the presumably non-beta key:
ubuntuone-ppa
except that seems to have an earlier date (27th April) than the beta version. Very confusing!

Also showing as non-installed are:
ubuntuone-client-tools
ubuntuone-storage-protocol

---

### Post by lavinog on 2009-11-03
can you see what version of the client you are using?

---

### Post by Roger Allott on 2009-11-03
> **lavinog said:**
> can you see what version of the client you are using?

Strangely enough, no! If I right-click on the widget, there's no option saying 'About'. There's an option saying 'Preferences', but there's nothing there about version.

---

### Post by lavinog on 2009-11-03
```
aptitude show ubuntuone-client
```

---

### Post by Roger Allott on 2009-11-03
> **lavinog said:**
> ```
aptitude show ubuntuone-client
```

Ah, sorry, didn't understand what you meant.

```
:~$ aptitude show ubuntuone-client
Package: ubuntuone-client
State: installed
Automatically installed: yes
Version: 1.1+r273-0ubuntu1~ppa2~jaunty
Priority: optional
Section: net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 471k
Depends: python-ubuntuone-client (= 1.1+r273-0ubuntu1~ppa2~jaunty),
         python-configglue, python-apport
Conflicts: nautilus-ubuntuone, ubuntuone-oauth-login, ubuntuone-storagefs
Replaces: nautilus-ubuntuone, ubuntuone-oauth-login, ubuntuone-storagefs
Description: Ubuntu One client
 Ubuntu One is a suite of on-line services. This package contains the
 synchronization daemon for the Ubuntu One file sharing service.
```

---

### Post by lavinog on 2009-11-03
it looks like a bug report was filed: [https://bugs.launchpad.net/ubuntuone-client/+bug/470056](https://bugs.launchpad.net/ubuntuone-client/+bug/470056) You may want to mention that you have the same issue.

---

### Post by Roger Allott on 2009-11-04
> **lavinog said:**
> it looks like a bug report was filed: [https://bugs.launchpad.net/ubuntuone-client/+bug/470056](https://bugs.launchpad.net/ubuntuone-client/+bug/470056) You may want to mention that you have the same issue.

Ah. Thanks for that. It's somehow better to know that it's a bug and not me being a drongo!

---

