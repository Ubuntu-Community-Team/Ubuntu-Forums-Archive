---
title: "Apache2 PHP5 Issues"
date: 2007-11-04
forum: Server Platforms
---

### Post by Awayne on 2007-11-04
I'm running Dapper as a private server, recently I installed and removed some extra servers including some apache2 modules, I reinstalled the one's I needed and tried to keep it running fine. Problem arises when I try to use PHP on it. Before it worked fine after apt-get, now it wont handle PHP pages even though PHP5 and the correct Apache module is installed. I hunted through config files and Google but can't seem to find a solution anywhere, anyone have any ideas? Thanks.

---

### Post by bsharp on 2007-11-04
I kinda had the same problem, I don't really know how I fixed it, but somewhere on this forum I read to do this:

```
sudo apt-get install php5-mysql
```

This may or may not be an answer, but I hope it helps.

---

### Post by Awayne on 2007-11-04
Thank you but I get the usual "it's installed":
> Reading package lists... Done
Building dependency tree... Done
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I'm not sure what's went wrong, I can't reinstall and I'm not sure about purging all the packages then reinstalling them all.

---

### Post by digitalzen on 2007-11-05
I think im in the same boat...except im running 7.10 gutsy. Everything works fine untill i tryed a test.php page, and instead of running the script, i prompts me to download the test.php file...

I also tryed the
 > sudo apt-get install php5-mysql
which installed, but have the same problem....

Anyone else?

---

### Post by conjur3r on 2007-11-06
Can both of you try the following command?

# ll /etc/apache2/mods-enabled/ | grep php

If nothing was returned, try enabling the php module for apache with:

# sudo a2enmod php5

---

### Post by digitalzen on 2007-11-06
> **conjur3r said:**
> Can both of you try the following command?

# ll /etc/apache2/mods-enabled/ | grep php

If nothing was returned, try enabling the php module for apache with:

# sudo a2enmod php5

Thanks conjur3r, I'll try this when I get home.

---

