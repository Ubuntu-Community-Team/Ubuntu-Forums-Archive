---
title: "In Relation To... http://ubuntuforums.org/showthread.php?t=1958969"
date: 2013-11-16
forum: Virtualisation
---

### Post by knc2 on 2013-11-16
So, I get to the websites and download the extension package but it doesn't work an error message comes up... It is...
 [TABLE]
 [TR]
 [TD] Result Code: 
[/TD]
 [TD] NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
 [TR]
 [TD] Component: 
[/TD]
 [TD] ExtPackManager
[/TD]
[/TR]
 [TR]
 [TD] Interface: 
[/TD]
 [TD] IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}
[/TD]
[/TR]
[/TABLE]
I have tried all four versions. :(
Please help.

---

### Post by ibjsb4 on 2013-11-17
You have tried all 4 versions of what?  vBox?  Didn't know we had that many.

Have you tried the general fix command?

```

sudo /etc/init.d/vboxdrv setup
```

---

