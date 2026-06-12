---
title: "Exclude file from Checkout/import/export"
date: 2007-05-24
forum: Server Platforms
---

### Post by Naatan on 2007-05-24
Hi, my repository has a config file, but I do not want this file to be comitted, as it is different for every user.

Is there some way to prevent the file from being comitted, eg. the file is not in the repository to begin with, but can be added inside a checkout folder.

Thanks in advance.

---

### Post by Jussi Kukkonen on 2007-05-24
Sure there is, two ways actually. See the manual: [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/) and search for "Ignoring Unversioned Items".


EDIT: Ahh, apologies. I assumed the config file isn't in the repo originally, but that isn't the case -- my advice might not apply here.

---

### Post by Naatan on 2007-05-24
No thats ok, the config file doesnt have to be in the repository.. I'll make a config.php.example instead :) 

Thanks for the link :) I'll try it out tonight

---

