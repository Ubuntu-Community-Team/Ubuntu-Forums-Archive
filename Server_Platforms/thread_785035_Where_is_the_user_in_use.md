---
title: "Where is the user in use?"
date: 2008-05-07
forum: Server Platforms
---

### Post by t_ras on 2008-05-07
Ubuntu8.04,AMD64
I added a user with the right email address but wrong username. I deleted it, also emptied recycle bin.
The user is not in any table I could find in the MySQL server, it does not have a folder, or que in \var\mail, there also isn't such a user in the users list for linux.
Even though when trying to add it again I get "The username is already in use."

WHERE THE HELL IS IT IN USE?!!!!!

---

### Post by windependence on 2008-05-07
> **t_ras said:**
> Ubuntu8.04,AMD64
I added a user with the right email address but wrong username. I deleted it, also emptied recycle bin.
The user is not in any table I could find in the MySQL server, it does not have a folder, or que in \var\mail, there also isn't such a user in the users list for linux.
Even though when trying to add it again I get "The username is already in use."

WHERE THE HELL IS IT IN USE?!!!!!


Ummmm can you be a bit more specific? Where did you add the user? In the OS? In MySQL? Your post is confusing. I can help you if I know where you are trying to add the user.

-Tim

---

### Post by t_ras on 2008-05-07
I did all through ISPConfig.
I now notices I had omitted it....
And ISPConfig is giving the errors -I can add the user easily though Linux.

---

### Post by t_ras on 2008-05-07
OK, I hacked ispconfig_isp_user.lib.php to not check is users exists and it worked. lets hoep it doesn't mean any  troubles...

---

