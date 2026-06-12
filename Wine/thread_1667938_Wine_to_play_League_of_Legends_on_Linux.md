---
title: "Wine to play League of Legends on Linux"
date: 2011-01-15
forum: Wine
---

### Post by DCarrollUSMC on 2011-01-15
Please excuse my ignorance of any posts that might have already been made on the topic.  I was curious if anyone had any information for a beginner user of ubuntu (Installed yesterday for the first time.  I have heard that it is possible and even seen a few but nothing that I was capable of understanding.  Any chance someone can dumb down the process of using Wine to play League of Legends on Ubuntu 10.10 64Bit Desktop version.?

---

### Post by ronnielsen1 on 2011-01-15
Beta version

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18035](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18035)

Version 1

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141)

Winehq is the place to search for windows software in wine. Just follow the directions
It's rated gold I believe so it should run

> [SIZE=3]League of Legends currently does not run out of the box with Wine. It is using some unimplemented or broken API in Wine which make the launcher and the game crash and needs some native Windows libraries or programs. The following patches should be applied to the latest development version of Wine. Using an older version is not usefull for games, because the support for APIs used by games is constantly improving. 
[/SIZE]
   [SIZE=3]There are currently 1 known problems that can be fixed by applying a patch to Wine:       [/SIZE]

---

### Post by ronnielsen1 on 2011-01-15
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

**Adding the WineHQ PPA Repository:**

  Open the Software Sources menu by going to **Applications->Ubuntu Software  Center**, then selecting **Edit->Software Sources**. Choose the **Other  Software** tab and click **Add**.


Then, **copy and paste the line below**.
  [I]ppa:ubuntu-wine/ppa

[/I]This will automatically update wine if you allow it

---

### Post by DCarrollUSMC on 2011-01-19
> **ronnielsen1 said:**
> 

Winehq is the place to search for windows software in wine. Just follow the directions
It's rated gold I believe so it should run

This is where I run into problems.  I have zero experience with Linux systems and so I guess I need someone to hold my hand through the steps.  I get caught up on the first step of applying the patches.  I'm not sure what I'm doing wrong but I don't know how to even patch wine for League of Legends.

---

### Post by DCarrollUSMC on 2011-01-19
> **ronnielsen1 said:**
> 

Winehq is the place to search for windows software in wine. Just follow the directions
It's rated gold I believe so it should run

This is where I run into problems.  I have zero experience with Linux systems and so I guess I need someone to hold my hand through the steps.  I get caught up on the first step of applying the patches.  I'm not sure what I'm doing wrong but I don't know how to even patch wine for League of Legends.

---

