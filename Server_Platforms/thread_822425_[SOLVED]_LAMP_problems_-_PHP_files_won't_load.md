---
title: "[SOLVED] LAMP problems - PHP files won't load"
date: 2008-06-08
forum: Server Platforms
---

### Post by messyhead on 2008-06-08
Hi folks. I've installed LAMP using ```
sudo tasksel install lamp-server
```

and it all worked fine. I installed phpmyadmin and I can create databases and tables without problem.

I created a new site and copied all the site files that I'm working on into the required folder. However when I try to access any of the php files in the folder I get the following errors;

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/tony/public_html/main_menu.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

I'm sure this is something simple, but I've not had experience in configuring a LAMP before so not sure what to do. I have previously installed on a laptop using the same method and everything worked first time, but this is now on my desktop.

Can anyone help with this?

thanks

Tony

---

### Post by quelx on 2008-06-08
Search the forums for **"Unknown on line 0"** (including the quotes). Many have had this problem and been able to solve it.  If you run into issues with the fixes let us know.

---

### Post by messyhead on 2008-06-08
Didn't think about searching for that. I've managed to fix it by setting the permissions using;

sudo chmod -R a+rwx /home/user/public_html

thanks

---

### Post by quelx on 2008-06-08
> **messyhead said:**
> Didn't think about searching for that. I've managed to fix it by setting the permissions using;

sudo chmod -R a+rwx /home/user/public_html

thanks
With that anyone with local access on the system can read and write anything in /home/user/public_html.

```

chmod -R a+r /home/user/public_html
chmod a+rx /home/user/public_html
```

would be sufficient and allow only **user** to change files.

---

### Post by messyhead on 2008-06-09
> **quelx said:**
> With that anyone with local access on the system can read and write anything in /home/user/public_html.

```

chmod -R a+r /home/user/public_html
chmod a+rx /home/user/public_html
```

would be sufficient and allow only **user** to change files.

Thanks, I'm the only one using the system so it won't be an issue, but I'll bear that in mind for the future.

---

