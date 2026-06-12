---
title: "XAMPP on Intrepid Ibex  Failed to open string"
date: 2008-12-09
forum: Server Platforms
---

### Post by firespydr on 2008-12-09
This is the message I received when opening localhost

```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/opt/lampp/htdocs/xampp/index.php' (include_path='.:/opt/lampp/lib/php') in Unknown on line 0

```

I am running Ubuntu 8.10, Xampp 1.6.8.a. Just installed then setup security by running.  ```
sudo /opt/lampp security
``` 

I then tested and was asked for the username and password which it accepted. I then copied my backup htdocs folder to the /opt/lampp folder. I could not access the files, received a 403. Thinking it might be the xampp security settings, I deleted the opt/lampp folder. I then ran the command:

```
sudo tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt
```to reinstall xampp. The process ran without error. This time I did not change the security settings. I ran the command ```
sudo /opt/lampp start
``` to start the server and received the all clear

Starting XAMPP 1.6.1...
LAMPP: Starting Apache...
LAMPP: Starting MySQL...
LAMPP started.

I tested by typing in localhost in the browser (Firefox) got the xampp pages to show up. I then again copied my files from my mounted external hdd and now I get a:

```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/opt/lampp/htdocs/xampp/index.php' (include_path='.:/opt/lampp/lib/php') in Unknown on line 0

```

Any help would be appreciated.

---

### Post by cdenley on 2008-12-09
I never used XAMPP before (what's wrong with ubuntu's LAMP configuration?), but that sounds like a permissions problem to me.

```

ls -l /opt/lampp/htdocs/xampp/index.php

```

---

### Post by firespydr on 2008-12-09
Same idea, I'm just kinda used to the Xampp flavor that's all. ANd anyway, i figured that out and now I'm getting a 403 forbidden on any page in the directory. Maybe I should leave the root of the installation folder alone and just use more folders to add more sites, I'll try this and post back.

---

### Post by petkor on 2009-06-12
I had the same problem and i solved it.
Just change permissions on your folder in htdocs

chmod -R 777 name_of_directory

If you are concerned about security you should type in
appropriate mode instead 777

---

