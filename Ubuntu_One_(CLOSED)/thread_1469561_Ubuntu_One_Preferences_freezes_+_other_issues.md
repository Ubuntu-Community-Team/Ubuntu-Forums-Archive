---
title: "Ubuntu One Preferences freezes + other issues"
date: 2010-05-02
forum: Ubuntu One (CLOSED)
---

### Post by Jim Danner on 2010-05-02
Yesterday Ubuntu One stopped syncing properly: all files and folders were listed on the web site grayed out and tagged with "uploading", while there was "0 bytes Used". I could still upload files manually to the website fairly quickly, so it probably wasn't purely server overload. Anyway, **a number of things happened** after that:
[LIST=1]
[*]uninstalled the Ubuntu One client packages and reinstalled them
[*]in Account settings on the website, I removed my computer, hoping to make a fresh start
[*]the Ubuntu online account login system for some reason forced me to change my password (presumably it wasn't strong enough)
[/LIST]
After all that, I can still login to the website (with the new password), but **the computer can't login**. When I type *u1sdtool -s* in terminal, the result is ```
State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

```
When I open Ubuntu One Preferences from the Me menu, **it completely freezes** at the Account tab; I can't click anything or even close it (have to kill it in terminal).

I suppose the login failure has to do with the old password whcih was saved in the keyring. The removed computer from the account probably complicates the issue. Help!

---

### Post by Jim Danner on 2010-05-02
OK, I went to Applications... Accessories... Passwords and Encryption keys. I removed the old password, and then I could login with the new password, add my computer, and now the Preferences don't freeze anymore. (It is still a bug in the Preferences program I would say, but not a problem now.)

Now I'm left with just the original problem: it doesn't actually sync anything, although it says it is "Synchronizing". The results of *u1sdtool -s* are
```
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH

```

---

### Post by joshuahoover on 2010-05-03
> **Jim Danner said:**
> OK, I went to Applications... Accessories... Passwords and Encryption keys. I removed the old password, and then I could login with the new password, add my computer, and now the Preferences don't freeze anymore. (It is still a bug in the Preferences program I would say, but not a problem now.)

Now I'm left with just the original problem: it doesn't actually sync anything, although it says it is "Synchronizing". The results of *u1sdtool -s* are
```
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH

```

I'm sorry to hear Ubuntu One has not been working properly for you. Our service has been experiencing large spikes with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. Without seeing any logs, I can guess that you're being affected by these issues. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

Again, apologies for the inconvenience and thank you for your patience.

Thank you,

Joshua

---

### Post by karlstad on 2010-05-03
I'm having the same issue. Deleting my Ubuntu One token doesn't help either and I've tried downloading the Ubuntu One nightly build.

The ***u1sdtool -s*** command gives me this output:

> State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH


---

### Post by Jim Danner on 2010-05-03
> **joshuahoover said:**
> I'm sorry to hear Ubuntu One has not been working properly for you. Our service has been experiencing large spikes with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. Without seeing any logs, I can guess that you're being affected by these issues. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

Again, apologies for the inconvenience and thank you for your patience.

Thank you,

JoshuaThanks for your reaction, it is reassuring to know you're reading the threads on this forum. I'll wait for a week or so and check on the situation after that.

---

### Post by Jim Danner on 2010-05-12
I checked a little later, and it has started syncing. After un-syncing the folders and then selecting them for syncing again, everything is now working well.

---

### Post by joshuahoover on 2010-05-12
> **Jim Danner said:**
> I checked a little later, and it has started syncing. After un-syncing the folders and then selecting them for syncing again, everything is now working well.

Thank you for the follow up reply Jim! We made some changes on the server last night that appear to be speeding things up quite a bit. We're still tweaking various settings but we can see it's getting better overall.

Joshua

---

