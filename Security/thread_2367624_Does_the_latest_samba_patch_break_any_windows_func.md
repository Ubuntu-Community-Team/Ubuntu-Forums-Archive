---
title: "Does the latest samba patch break any windows functionality?"
date: 2017-08-01
forum: Security
---

### Post by link626 on 2017-08-01
[https://launchpad.net/ubuntu/+source/samba/2:4.3.11+dfsg-0ubuntu0.16.04.7](https://launchpad.net/ubuntu/+source/samba/2:4.3.11+dfsg-0ubuntu0.16.04.7)


I regularly use samba to download large files from linux server to windows client over the internet, and to sync files and timestamps. It has been very reliable and fast.

However, my 16.04 is still on samba version 4.3.11.

Will patching break Windows in any way?


I'm new to linux, and don't want to break anything if I have to revert something on linux.

---

### Post by deadflowr on 2017-08-01
Not sure what you mean by you're still on 4.3.11.
Are you not keeping your system up to date?
Which current version does
```
apt-cache policy samba
```
tell you?
Current version should be
```
2:4.3.11+dfsg-0ubuntu0.16.04.9
```

Generally speaking, the patches are included in the regular system updates, and they try to make any patches as minimal to the affect of which ever program they are for.

Being that the last samba security updates were just a few weeks ago and there has not been any updates for regressive behavior, it looks like it should be good to go, at least on that front.

Any issues would more likely be on your side: mis-configured config files, or what not.

> Will patching break Windows in any way?

Don't see how it would affect whatever Windows does.
If samba broke, then Windows would not be able to connect to it, is all.
If by chance you have something in Windows that relies on a file in the samba directories, then that would be broke, but overall Windows would run fine.

That's my 2 cents
overall or underall or middleall or something.

---

