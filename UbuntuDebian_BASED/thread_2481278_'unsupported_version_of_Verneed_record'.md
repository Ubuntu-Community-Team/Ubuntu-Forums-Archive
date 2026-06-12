---
title: "'unsupported version of Verneed record'"
date: 2022-11-23
forum: Ubuntu/Debian BASED
---

### Post by bbolker2 on 2022-11-23
Have just started to get errors, which seem (??) to be confined to snap-based programs (specifically the problem has occurred with Skype and Zulip):

```
$ zulip
/snap/zulip/43/zulip: /lib/x86_64-linux-gnu/libuuid.so.1: unsupported version 0 of Verdef record
/snap/zulip/43/zulip: error while loading shared libraries: /lib/x86_64-linux-gnu/libuuid.so.1: unsupported version 0 of Verneed record
```

Skype:

```
 $ skype
+ [ -f /home/bolker/snap/skype/common/.config/skypeforlinux/settings.json ]
+ export SKYPE_LOGS=/home/bolker/snap/skype/235/logs
+ [ ! -d /home/bolker/snap/skype/235/logs ]
+ exec /snap/skype/235/usr/share/skypeforlinux/skypeforlinux
/snap/skype/235/usr/share/skypeforlinux/skypeforlinux: /lib/x86_64-linux-gnu/libuuid.so.1: unsupported version 0 of Verdef record
/snap/skype/235/usr/share/skypeforlinux/skypeforlinux: error while loading shared libraries: /lib/x86_64-linux-gnu/libuuid.so.1: unsupported version 0 of Verneed record
```

I've tried "snap refresh" for both, with no luck.

I can see that linux-image-6.0.6-76060006-generic was installed fairly recently, but I don't know if that's related to the problem?

According to this: [https://askubuntu.com/questions/1438252/jammy-unsupported-version-0-of-verneed-record-processes-like-vscode-exit-an](https://askubuntu.com/questions/1438252/jammy-unsupported-version-0-of-verneed-record-processes-like-vscode-exit-an) there is a problem with 6.0.6 

I think I can probably figure out how to roll back using this: [https://unix.stackexchange.com/questions/79050/can-i-rollback-an-apt-get-upgrade-if-something-goes-wrong](https://unix.stackexchange.com/questions/79050/can-i-rollback-an-apt-get-upgrade-if-something-goes-wrong) but would be interested in any advice.

---

### Post by ajgreeny on 2022-11-24
Which OS are you actually using?
You have added this thread to the ***Ubuntu/Debian based *** section which means it is not Ubuntu, Kubuntu, Xubuntu, etc, but you have told us no more and it is therefore impossible to give you any detailed help.

---

### Post by shaviro on 2022-12-17
I have had this problem with numerous snap programs. The problem is supposedly resolved in Linux kernel 6.0.7. When will this appear in the Ubuntu software updates?

---

### Post by #&amp;thj^% on 2022-12-17
You can use a temporary solution until it is resolved is to choose 5.x version from grub menu and then boot up.
Just for info here I'm still using kernel 5.19 on lunar and see no issues.

---

