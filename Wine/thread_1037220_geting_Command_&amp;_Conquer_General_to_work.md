---
title: "geting Command &amp; Conquer General to work"
date: 2009-01-11
forum: Wine
---

### Post by networm1230 on 2009-01-11
Dos anyone know how to get Command & Conquer Generals to work on Linux?. I have tried wine but no lock there.

some Help

---

### Post by s|fr on 2009-01-15
networm, what do you mean it doesnt work specifically? even though this is a wine question and you should post this somewhere wine related, but ill see if i could just resolve this in one post. I have generals running on my machine. The only problem I had after installing it was the mouse cursor, which is a problem for both generals and tiberium wars. in order to fix that you need to install an unofficial patch for wine. download the source, patch it, build and that should do the trick. I would suggest if u have more problems u can post a bug over at wine appdb and the mainter will have a look at it. I would also recommend reading the thoroughly written details on how to get it up and running at appdb.wine.

---

### Post by networm1230 on 2009-01-16
> **s|fr said:**
> networm, what do you mean it doesnt work specifically? even though this is a wine question and you should post this somewhere wine related, but ill see if i could just resolve this in one post. I have generals running on my machine. The only problem I had after installing it was the mouse cursor, which is a problem for both generals and tiberium wars. in order to fix that you need to install an unofficial patch for wine. download the source, patch it, build and that should do the trick. I would suggest if u have more problems u can post a bug over at wine appdb and the mainter will have a look at it. I would also recommend reading the thoroughly written details on how to get it up and running at appdb.wine.

thanks for the reply. I mean when I put the C&C game in to the cd drive. I install the game and when I try to run the game it starts up about twenty seconds and than it crashes. the process ended completely.

Do you mean: [http://appdb.winehq.org/appview.php?iVersionId=1717](http://appdb.winehq.org/appview.php?iVersionId=1717)

---

### Post by s|fr on 2009-01-17
Well you are at the right page however the patch is not listed there. Also, you need to resolve the crash first. The patch is only for getting animated cursors work without the patch the only problem you have is that you dont see the mouse pointers in the game.

So have you followed that how to and copied all the files and installed as it says it should and basically whatever else it asks you to do?

---

### Post by networm1230 on 2009-01-19
> **s|fr said:**
> Well you are at the right page however the patch is not listed there. Also, you need to resolve the crash first. The patch is only for getting animated cursors work without the patch the only problem you have is that you dont see the mouse pointers in the game.

So have you followed that how to and copied all the files and installed as it says it should and basically whatever else it asks you to do?

I have Download the msvcirt.dll and put it in the folder it told me to. but when I try to install the game it will not install it says access denied.

---

### Post by s|fr on 2009-01-20
Right, so its the installation that is failing. Could you post the output when you try to run wine setup.exe on the command line? Which version of wine are you using? are you copying the cds onto the disk first? I definitely had to do that.

---

