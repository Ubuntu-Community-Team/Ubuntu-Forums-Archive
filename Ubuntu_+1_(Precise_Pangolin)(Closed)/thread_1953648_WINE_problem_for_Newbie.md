---
title: "WINE problem for Newbie"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Heinrich_Evers on 2012-04-06
Just recently I thought it'd be a great idea to migrate from Ubuntu 11.10 workstation to 11.10 server and upgrade to 12.04.

However, I have a problem that I know is probably really simple but I don't know what to do.

I remember when I installed  Workstation 11.10 and downloaded and installed WINE 1.4 I could simply right click one of my Windows executables after running winecfg and it would work with no problems at all.

After installing server, and Wine when I try to run the same executables that ran they don't
Wine reports an invalid parameter  and Q4wine says:   p, li { white-space: pre-wrap; }  Error while loading application settings by key: 'WineLibs'. File or path not exists: "/usr/lib/wine"
 Please, go to q4wine options dialog and set it.


I think that when I installed server it did a minimal install and some common libs are missing since I went to see if that directory is present and it is not.


How can I fix this problem?
What packages does Ubuntu 11.10 Workstation install that the Server does not automatically?
If I could get this package list I'll sudo apt-get install them myself and I think it will then work correct?

---

### Post by Fwission on 2012-04-06
you can try re-installing lib32 or the location changed, sometimes it changes to your root folder, check there

EDIT: the folder should be called lib32, that's where mine were

---

### Post by sandyd on 2012-04-06
> **Heinrich_Evers said:**
> Just recently I thought it'd be a great idea to migrate from Ubuntu 11.10 workstation to 11.10 server and upgrade to 12.04.

However, I have a problem that I know is probably really simple but I don't know what to do.

I remember when I installed  Workstation 11.10 and downloaded and installed WINE 1.4 I could simply right click one of my Windows executables after running winecfg and it would work with no problems at all.

After installing server, and Wine when I try to run the same executables that ran they don't
Wine reports an invalid parameter  and Q4wine says:   p, li { white-space: pre-wrap; }  Error while loading application settings by key: 'WineLibs'. File or path not exists: "/usr/lib/wine"
 Please, go to q4wine options dialog and set it.


I think that when I installed server it did a minimal install and some common libs are missing since I went to see if that directory is present and it is not.


How can I fix this problem?
What packages does Ubuntu 11.10 Workstation install that the Server does not automatically?
If I could get this package list I'll sudo apt-get install them myself and I think it will then work correct?
There is no difference between Ubuntu Server and Ubuntu Desktop, except for the packages installed. At the beginning of each install, the correct metapackage is installed for the system (ubuntu-desktop for Ubuntu Desktop, and ubuntu-standard for Ubuntu Server (I think it is)).

A metapackage is a 'dummy' package that has dependences on a list of packages that are required for the metapackage's functionality. For example, the ubuntu-desktop metapackage will contain the empathy, gwibber, etc packages, because it is required for the functionality of Ubuntu Desktop.

For more information, check out [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

P.S. There is no such thing as Ubuntu Workstation. I think you are refering to Ubuntu Desktop.

Anyhow, if the package *wine* is installed, it should pull in all its dependencies as well. 

Try something like
```

sudo apt-get --purge remove wine1.3 wine1.3-dbg wine1.3-dev wind1.3-gecko wine wine1.4 wine1.4-amd64 wine1.4-common wine1.4-dbg wine1.4-dev wine1.4-i386

sudo apt-get install wine.

```

Also, you **should not be testing 12.04 if you are still a newbie.**

---

### Post by Heinrich_Evers on 2012-04-06
I thank the both of you for the suggestions.
I figured upgrading to 12.04 since from what the site says it's to be released sometime at the end of this month, and I install wine1.5 hoping it would resolve the issue.

I'm not sure if I can can revert the kernal back to Ubuntu 11.10 or not but I will remove wine1.5 and try your suggestion.

> **sandyd said:**
> There is no difference between Ubuntu Server and Ubuntu Desktop, except for the packages installed. At the beginning of each install, the correct metapackage is installed for the system (ubuntu-desktop for Ubuntu Desktop, and ubuntu-standard for Ubuntu Server (I think it is)).

A metapackage is a 'dummy' package that has dependences on a list of packages that are required for the metapackage's functionality. For example, the ubuntu-desktop metapackage will contain the empathy, gwibber, etc packages, because it is required for the functionality of Ubuntu Desktop.

For more information, check out [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

P.S. There is no such thing as Ubuntu Workstation. I think you are refering to Ubuntu Desktop.

Anyhow, if the package *wine* is installed, it should pull in all its dependencies as well. 

Try something like
```

sudo apt-get --purge remove wine1.3 wine1.3-dbg wine1.3-dev wind1.3-gecko wine wine1.4 wine1.4-amd64 wine1.4-common wine1.4-dbg wine1.4-dev wine1.4-i386

sudo apt-get install wine.

```Also, you **should not be testing 12.04 if you are still a newbie.**

---

