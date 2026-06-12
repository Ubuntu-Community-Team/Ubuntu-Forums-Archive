---
title: "Warcraft III - Any body else getting memory errors with the new 1.23 patch?"
date: 2009-03-20
forum: Wine
---

### Post by hotweiss on 2009-03-20
Is any body else getting memory error's with the new 1.23 patch?

---

### Post by hikaricore on 2009-03-20
> **hotweiss said:**
> Is any body else getting memory error's with the new 1.23 patch?

Ummm..  what game might you be talking about?  These little details help.

---

### Post by no1wantdthisname on 2009-03-20
Sounds like Warcraft III.  I'm getting the same problem.

---

### Post by goldfish2 on 2009-03-20
Yeah me too.  They often happen right at loggin, but I did manage to play a full game just now.  It has only happened so far when the news page is about to load.  It hasn't happened in game or when in browsing for games.  And it doesn't always happen.

---

### Post by hotweiss on 2009-03-20
> **hikaricore said:**
> Ummm..  what game might you be talking about?  These little details help.

LOL sorry. Yes, I am talking about Warcraft III Frozen Throne.

---

### Post by Kosimo on 2009-03-21
Hey guys, I used to play Warcraft III with WINE 1.1.17 and everything used to work perfectly but after this latest update (1.23) I get FATAL errors and crashes all the time. Anyone else is having this issue?

---

### Post by Kosimo on 2009-03-21
Exactly the same problems with Warcraft III ROC....

Do we may need some specific .dll ?

---

### Post by goldfish2 on 2009-03-21
Yup, everyone it seems... haven't found any solutions yet.

[http://ubuntuforums.org/showthread.php?t=1101818](http://ubuntuforums.org/showthread.php?t=1101818)

"They often happen right at loggin, but I did manage to play a full game just now. It has only happened so far when the news page is about to load. It hasn't happened in game or when in browsing for games. And it doesn't always happen."

Thats all I've figured out.

---

### Post by Kosimo on 2009-03-21
> **goldfish2 said:**
> Yup, everyone it seems... haven't found any solutions yet.

[http://ubuntuforums.org/showthread.php?t=1101818](http://ubuntuforums.org/showthread.php?t=1101818)

"They often happen right at loggin, but I did manage to play a full game just now. It has only happened so far when the news page is about to load. It hasn't happened in game or when in browsing for games. And it doesn't always happen."

Thats all I've figured out.

 We should open a bug in wine's webpage a friend of mine which I use to play with in battle-net using wine is having the same issue.

---

### Post by goldfish2 on 2009-03-21
From
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

Looks like the new banner system is the problem. That would be consistent with my experience.

Maybe some of the ads that are loaded crash wine and some don't.

Perhaps instead of a wine fix there is a way to disable the banner system?  Perhaps there is some web addresses that can be blocked to prevent the banners from coming in?


Edit: One commenter notes that Ghost++ works without having issues, perhaps this is a workaround.

---

### Post by binbash on 2009-03-21
I can't connect to battle net after 1.23 :/

---

### Post by goldfish2 on 2009-03-21
bug report:
[http://bugs.winehq.org/show_bug.cgi?id=17809](http://bugs.winehq.org/show_bug.cgi?id=17809)

---

### Post by hotweiss on 2009-03-22
> **goldfish2 said:**
> bug report:
[http://bugs.winehq.org/show_bug.cgi?id=17809](http://bugs.winehq.org/show_bug.cgi?id=17809)

Thanks. I voted for the bug...

---

### Post by Kosimo on 2009-03-23
> **hotweiss said:**
> Thanks. I voted for the bug...

Me too ;)

---

### Post by hotweiss on 2009-03-23
I don't seem to have this problem any more...

---

### Post by panaut0lordv on 2009-03-29
How have you resolved it?

---

### Post by gr00by on 2009-03-29
I've solved this problem installing older version of Wine (1.1.4)

---

### Post by djungelmums on 2009-03-29
I've got the same problem!

---

### Post by panaut0lordv on 2009-03-29
I was trying to patch it myself and replace custom bins with .deb installed ones (1.1.18), now I'm trying solution from [http://bugs.winehq.org/show_bug.cgi?id=17809#c26](http://bugs.winehq.org/show_bug.cgi?id=17809#c26)

---

### Post by Troll_the_Great on 2009-03-31
> **gr00by said:**
> I've solved this problem installing older version of Wine (1.1.4)

Wine 1.1.4 works for me too! I hope though the next version of wine will fix this bug...

---

### Post by Anaithnid on 2009-04-08
If you know who you are going to play with (friends) you might want to give Lancraft a try.  Seems to run fine on Wine 1.1.4 which I just tested it on.


[http://lancraft.blogspot.com/search/label/Downloads](http://lancraft.blogspot.com/search/label/Downloads)


Battle.net still crashes on my machine after a few minutes in the menus even using 1.1.4.

---

### Post by Mandraix on 2009-04-10
I get a fatal error when running WC3 on BattleNet whether I'm in the custom games list or a chat channel. But once I'm in a game it runs fine with no errors.

---

### Post by no1wantdthisname on 2009-04-11
This git repo fixes the crashing: [http://repo.or.cz/w/wine/warcraft3.git](http://repo.or.cz/w/wine/warcraft3.git)

From: [http://bugs.winehq.org/show_bug.cgi?id=17809#c27](http://bugs.winehq.org/show_bug.cgi?id=17809#c27)

You still need the focus patch though.

---

### Post by Kosimo on 2009-04-11
Does the latest Wine version 1.1.19 have the fixes for this bug?

---

### Post by Kosimo on 2009-04-13
So now 1.1.19 is already available in Ubuntu's Wine PPA.

Anyone has been having issues with this particular version?

---

### Post by muscl3s on 2009-04-13
> **no1wantdthisname said:**
> This git repo fixes the crashing: [http://repo.or.cz/w/wine/warcraft3.git](http://repo.or.cz/w/wine/warcraft3.git)

From: [http://bugs.winehq.org/show_bug.cgi?id=17809#c27](http://bugs.winehq.org/show_bug.cgi?id=17809#c27)

You still need the focus patch though.

How do I install this git repo?  I'm having the crash problem.

---

### Post by Mokoma on 2009-04-14
there still releasing patches for warcraft 3?

---

### Post by mr.niceguy&lt; on 2009-05-08
oh men dat hurts..... they say that the latest patch is still not finished!!! :( better keep it watch out....:confused:

---

