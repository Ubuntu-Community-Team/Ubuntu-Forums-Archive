---
title: "Update information"
date: 2018-03-06
forum: Security
---

### Post by cam17 on 2018-03-06
Where ca I find Ubuntu update information such as the date it was posted and its function?

---

### Post by Bashing-om on 2018-03-06
cam17; Hello -

This ?
```

apt changelog <package>

```

[INDENT][INDENT][INDENT]hope this is the help
[/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2018-03-06
If you mean Ubuntu versions, links to the release notes are [here]("https://wiki.ubuntu.com/Releases").

If you mean for individual packages, run this in Terminal -
```
apt-get changelog <package>
```
replacing [FONT=Courier New]<package>[/FONT] with the name of the package you want the update info for.

* oops, collided posting with Bashing-om.  [FONT=Courier New]apt changelog <package>[/FONT] does the same thing as [FONT=Courier New]apt-get changelog <package>[/FONT] .

---

### Post by cam17 on 2018-03-07
When I perform    	 	 	 	   apt list --upgradable I get the following 
```
compiz/xenial-updates,xenial-updates 1:0.9.12.3+16.04.20180221-0ubuntu1 all [upgradable from: 1:0.9.12.3+16.04.20171116-0ubuntu1]
compiz-core/xenial-updates 1:0.9.12.3+16.04.20180221-0ubuntu1 amd64 [upgradable from: 1:0.9.12.3+16.04.20171116-0ubuntu1]
compiz-gnome/xenial-updates 1:0.9.12.3+16.04.20180221-0ubuntu1 amd64 [upgradable from: 1:0.9.12.3+16.04.20171116-0ubuntu1]
compiz-plugins-default/xenial-updates 1:0.9.12.3+16.04.20180221-0ubuntu1 amd64 [upgradable from: 1:0.9.12.3+16.04.20171116-0ubuntu1]
libcompizconfig0/xenial-updates 1:0.9.12.3+16.04.20180221-0ubuntu1 amd64 [upgradable from: 1:0.9.12.3+16.04.20171116-0ubuntu1]
libdecoration0/xenial-updates 1:0.9.12.3+16.04.20180221-0ubuntu1 amd64 [upgradable from: 1:0.9.12.3+16.04.20171116-0ubuntu1]
libunity-core-6.0-9/xenial-updates 7.4.5+16.04.20180221-0ubuntu1 amd64 [upgradable from: 7.4.5+16.04.20171201.3]
unity/xenial-updates 7.4.5+16.04.20180221-0ubuntu1 amd64 [upgradable from: 7.4.5+16.04.20171201.3]
unity-schemas/xenial-updates,xenial-updates 7.4.5+16.04.20180221-0ubuntu1 all [upgradable from: 7.4.5+16.04.20171201.3]
unity-services/xenial-updates 7.4.5+16.04.20180221-0ubuntu1 amd64 [upgradable from: 7.4.5+16.04.20171201.3]
```
----------------------------------------------------------------------------------------------------------------------------

If I perform apt changlog compiz It gives the following
> 
compiz (1:0.9.12.3+16.04.20180221-0ubuntu1) xenial; urgency=medium

  * Region: define static const functions returning infinite and empty
    regions (LP: #1750619)

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Wed, 21 Feb 2018 17:42:11 +0000

compiz (1:0.9.12.3+16.04.20171116-0ubuntu1) xenial; urgency=medium

  [ Eleni Maria Stea ]
  * Added option to disable blend in grid plugin (LP: #1700859)
  * Move: add options for showing only the window shape (filled or not)
    (LP: #1700859)

  [ Alberts Muktup&#257;vels ]
  * Ensure that surfaces used by metacity theme have device scale set to
    1 . (LP: #1530277) (LP: #1530277)
  * Use AnyPropertyType when getting _MOTIF_WM_HINTS property. (LP:
    #1702297)

  [ Martin Wimpress ]
  * mate: Avoid artefacts of Windows Thumbnail Previews (LP: #1606369)
----------------------------------------------------------------------------------------------------------------------------------------------------

Does this mean that this update came out in Wednesday 28-Feb-2018? Because I updated the system a few days ago ?

---

