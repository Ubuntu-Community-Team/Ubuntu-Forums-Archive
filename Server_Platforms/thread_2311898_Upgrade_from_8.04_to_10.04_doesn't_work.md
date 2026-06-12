---
title: "Upgrade from 8.04 to 10.04 doesn't work"
date: 2016-01-31
forum: Server Platforms
---

### Post by mattia7 on 2016-01-31
Hello.
I'm trying to do a release-upgrade on my old 8.04 LTS server.
The procedure says that I have to upgrade to 10.04 LTS and then, if I want, to newer releases.

The problem is that running "do-release-upgrade" gives an error on python:

[SIZE=1][I]Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'
/tmp/tmpCShxHS/DistUpgradeMain.py:102: Warning: 'with' will become a reserved keyword in Python 2.6
Traceback (most recent call last):
  File "/tmp/tmpCShxHS/precise", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmpCShxHS/DistUpgradeMain.py", line 102
    with open(fname, "a"):
            ^
SyntaxError: invalid syntax[/I]

[SIZE=2]If you read among the lines, you can see that the upgrade manager is trying to get directly 12.04 (precise) not 10.04 (lucid).
So the upgrade manager is tryning to skip 10.04 and go directly to 12.04. That's why I've got the error (surely related to some old version of python).
Is there a way to force the upgrade manager to install 10.04 enad not 12.04? This update should be supported:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

[/SIZE][/SIZE][SIZE=2]Why the upgrade manager isn't working correctly? Is there a way to fix it?
Thanks in advance.
Mat[/SIZE]

---

### Post by darkod on 2016-01-31
Why did you wait so long to try the upgrade???

1. Important question: Did you modify the sources.list because 8.04 is End Of Life since long time ago? I assume you did, otherwise do-release-upgrade should not even offer any upgrade.

2. Because you have waited that long, 10.04 is also EOL now (not supported any more). That might be a reason the process is offering you 12.04 even though the usual way would be to offer 10.04. Don't trust too much the page you linked, that was written before 10.04 went EOL. I'm not sure it applies any more...

---

### Post by QIII on 2016-01-31
I believe that most members here would agree with me in recommending that you back up your important files and do a fresh installation of a supported release.  If you want to do the LTS to LTS cycle from now one, install 14.04.  16.04 will be out in a few months and you can upgrade then.

As support is withdrawn from releases, their repositories are moved to graveyards for old releases.  They can still be found, but they have been withdrawn for good reason.

Although it is possible to upgrade through a dozen unsupported releases, the chances that you will have a working OS after the third one are very close to nothing.

---

