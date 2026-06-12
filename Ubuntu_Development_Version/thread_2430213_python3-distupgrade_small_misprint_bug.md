---
title: "python3-distupgrade small misprint bug"
date: 2019-10-29
forum: Ubuntu Development Version
---

### Post by zika on 2019-10-29
```
Setting up python3-distupgrade (1:20.04.1) ...
/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradePatcher.py:76: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if end_str is "":
```

In situ:

```
# if we don't have end, set it to the next line  
     if end_str is "":
     end = start + 1
     else:
     end = int(end_str)
```

BugReport: [URL="https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1850406"]https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1850406
[/URL]
Update&#8321;: Bug is still alive...
```
Unpacking python3-distupgrade (1:20.04.5) over (1:20.04.4) ...
Setting up python3-distupgrade (1:20.04.5) ...
/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradePatcher.py:76: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if end_str is "":
```

Update&#8322;:
```
Setting up python3-distupgrade (1:20.04.7) ...
/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradePatcher.py:76: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if end_str is "":
```

---

