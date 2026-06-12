---
title: "Apache2 Problem."
date: 2006-06-22
forum: Server Platforms
---

### Post by SteffJay on 2006-06-22
I have been attempting to get a DC Hub server (Verlihub) to auto-boot and have now managed to do so. (see thread: [http://www.ubuntuforums.org/showthread.php?t=200443](http://www.ubuntuforums.org/showthread.php?t=200443) ). After succeding in my quest, i now find that Apache2 will not auto-boot  :-?  I have tried entering /etc/init.d/apache2 into the sessions startup sequence but to no avail. The strange thing is, if i log out and go into root, it runs !! but when i log out of root and back into my own session, it don't !!  :confused:   Any advice gladly received.  ;)

---

### Post by lamego on 2006-06-22
If you have installed apache2 using apt it does autoboot.
Also it doesn't make any sence that it would be running with root unless you have explicitely added an apache2 start command the root users profile which is very unlikely.

---

### Post by SteffJay on 2006-06-22
The problem is, it **was** autobooting untill i made the adjustments for the hub server !!!!   :mad:

---

### Post by henriquemaia on 2006-06-22
[quote=SteffJay]The problem is, it **was** autobooting untill i made the adjustments for the hub server !!!!   :mad:[/quote]

What do you mean by autobooting?

---

### Post by lamego on 2006-06-22
I guess it means the service starting during boot.

---

### Post by SteffJay on 2006-06-22
Correct !!!!

---

### Post by henriquemaia on 2006-06-22
[quote=SteffJay]Correct !!!![/quote] Oh, ok, thanks. Have you chmoded the apache2 to +x?

```
 sudo chmod +x /etc/init.d/apache2
```

---

### Post by herald on 2006-06-23
Erm, I'm not sure what the hub thingy is, but you might check the sequence number in the rc.2 or rc.3 directories...I forget exactly which it is...Anyway my thinking is this:  If it worked before, and does not now, maybe the hub thingy is taking too long during the boot, and the Apache daemon is getting stomped on.    Try having the Apache daemon load sooner or later than it is.  This is all assuming you're not trying to run the daemon out of the inetd or xinetd mechanism...if you are, stop and change it to run standalone from an inet.d script!!!

One thing I don't get....if the service is supposed to auto kick, what difference does it make who you login as?  It should be running before you're even prompted for a login (again, assuming you're running it as an init script)

My 2 cents.

---

### Post by SteffJay on 2006-06-23
I am a total **noob** when it comes to this so if you can give me an idea as to what to do, i might be able to sort it out.  :-? I have done the > sudo chmod +x /etc/init.d/apache2 thingy but still no joy......  :-?

---

### Post by henriquemaia on 2006-06-23
[quote=SteffJay]I am a total **noob** when it comes to this so if you can give me an idea as to what to do, i might be able to sort it out.  :-? I have done the  thingy but still no joy......  :-?[/quote]

Do you have BUM  (Boot-Up Manager) installed?

Try it. It's a gui for configuring the startup services. Check on bum if apache2 is set to run.

---

### Post by SteffJay on 2006-06-23
It say's it is but only if i start it manually !!! The Apache2 was set for 91 in BUM and reset it to 50 (like most of the others). Rebooted and still don't auto-start.   :-?

---

### Post by henriquemaia on 2006-06-23
[quote=SteffJay]It say's it is but only if i start it manually !!! The Apache2 was set for 91 in BUM and reset it to 50 (like most of the others). Rebooted and still don't auto-start.   :-?[/quote] 
When you start it manually, do you get any error message? Maybe you have some problem with permissions, that explaining why apache would run under root.

ps: how do you start it manually?

---

### Post by SteffJay on 2006-06-23
There are no error messages when i start it in Root Terminal. All i do is, **/etc/init.d/apache2 start** and away it goes !!!!   weird !!! This only started happening when i coded the script for Verlihub >  [http://www.ubuntuforums.org/showthread.php?t=200443](http://www.ubuntuforums.org/showthread.php?t=200443)  Since then it has never auto-started. As i said, if i log out of my session into Root, it auto-starts there  :-? but not when i log back into my session !!

---

### Post by henriquemaia on 2006-06-23
[quote=SteffJay]There are no error messages when i start it in Root Terminal. All i do is, **/etc/init.d/apache2 start** and away it goes !!!!   weird !!! This only started happening when i coded the script for Verlihub >  [http://www.ubuntuforums.org/showthread.php?t=200443]("http://www.ubuntuforums.org/showthread.php?t=200443")  Since then it has never auto-started. As i said, if i log out of my session into Root, it auto-starts there  :-? but not when i log back into my session !![/quote]

And what are the results of

```
cat /var/log/apache2/error.log


```

---

### Post by SteffJay on 2006-06-23
Hello **henriquemaia**. Thanks for helping me out here, i appreciate it greatly.....  ;)   The list is VERY long but i have copied "todays" extract here for you to look at......

  [Fri Jun 23 08:48:29 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Fri Jun 23 08:48:48 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:48:48 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:48:48 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:48:49 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:48:49 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:48:49 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:48:59 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 08:52:08 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:52:08 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:52:08 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:52:09 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:52:09 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:52:09 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:52:23 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 08:54:35 2006] [error] [client 86.131.37.94] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:54:35 2006] [error] [client 86.131.37.94] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:54:35 2006] [error] [client 86.131.37.94] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:54:35 2006] [error] [client 86.131.37.94] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:54:36 2006] [error] [client 86.131.37.94] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:54:36 2006] [error] [client 86.131.37.94] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 08:54:52 2006] [error] [client 86.131.37.94] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 09:03:10 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 09:03:10 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:03:10 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:03:10 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 09:03:10 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:03:10 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:03:10 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:03:10 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:03:23 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 09:03:30 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 09:04:36 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:04:36 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:04:36 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:04:39 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:04:39 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:04:39 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 09:04:48 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 11:12:43 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:12:43 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:12:43 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:12:44 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:12:44 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:12:44 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:13:05 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 11:31:09 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 11:40:32 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 11:41:07 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:41:07 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:41:07 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:41:07 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:41:07 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:41:08 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:41:15 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 11:47:00 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:47:00 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:47:00 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:47:01 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:47:01 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:47:01 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 11:47:10 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 12:22:16 2006] [error] [client 211.98.88.125] File does not exist: /var/www/a1b2c3d4e5f6g7h8i9
[Fri Jun 23 12:22:17 2006] [error] [client 211.98.88.125] script '/var/www/adxmlrpc.php' not found or unable to stat
[Fri Jun 23 12:22:22 2006] [error] [client 211.98.88.125] File does not exist: /var/www/adserver
[Fri Jun 23 12:35:42 2006] [notice] caught SIGTERM, shutting down
[Fri Jun 23 12:45:33 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Fri Jun 23 12:48:12 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:48:12 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:48:12 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:48:12 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:48:12 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:48:13 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:48:20 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 12:58:52 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:58:53 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:58:53 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 12:59:05 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 14:30:11 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 14:30:11 2006] [error] [client 83.129.24.45] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 14:30:17 2006] [notice] caught SIGTERM, shutting down
[Fri Jun 23 14:34:56 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Fri Jun 23 14:35:02 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:02 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:02 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:19 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:20 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:20 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:20 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:20 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:20 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:35:28 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 14:36:18 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:18 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:18 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:18 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:18 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:18 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:41 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:41 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:36:41 2006] [error] [client 82.33.202.40] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 14:49:42 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 16:14:44 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 16:14:44 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 16:14:44 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 16:14:44 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 16:14:44 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 16:14:44 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 16:14:55 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/closeMod.swf
[Fri Jun 23 17:00:21 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 17:00:21 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 17:00:21 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 17:00:21 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 17:00:21 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf
[Fri Jun 23 17:00:22 2006] [error] [client 194.200.144.99] File does not exist: /var/www/chat/cache.swf

As you can see, the **/var/www/chat/cache.swf**, **/var/www/a1b2c3d4e5f6g7h8i9**, **/var/www/adxmlrpc.php** and the **/var/www/chat/closeMod.swf** do not exist. That is correct, they don't. I don't even know why it is looking for them :confused: Any ideas ???

---

### Post by henriquemaia on 2006-06-25
[Fri Jun 23 14:30:17 2006] [notice] caught SIGTERM, shutting down

These messages don't look good. You have to test if these messages occur after boot process. 


You have one occuring at Fri Jun 23 12:35:42 2006 and then an Apache startup message 10 minutes later ( [Fri Jun 23 12:45:33 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations). 
On the second one, the time between them is +-4 min. This may indicate that apache is SIGTERMing at boot process if the time of startup coincide with your manually apache startup. Try to check that. At least you'll know that apache is aborting at startup during boot.

---

### Post by SteffJay on 2006-06-25
Hello **Henriquemaia**. Thanks for your reply. I will check that out and get back to you.  ;)

---

### Post by herald on 2006-06-26
swf files are related to MacroMedia's Flash if I remember correctly.  Those error messages are looking for "web content" files.  That should have absolutely nothing to do with whether or not your daemon runs.  The reason it only starts in root, it seems, is that unpriviliged users are not allowed to start/stop/reload processes.  Root has full access to the init scripts in /etc/init.d, while non-privileged users do not.
I have two questions...As Henrieque asked, how are you trying to "autostart" the process, and second, was Apache ever installed on this server before?  The fact that you're getting file not found messages leads me to believe that either there is already a somewhat functional website configured in Apache, or that after some sort of reinstall, the Apache config files are trying to load various portions of a formerly built website that is no longer in existence.  My personal opinion is that the messages coming to you in the error.log file are due to user browsing activities rather than Apache daemon errors.

I'm not familiar with BUM, but what I would recommend is a complete uninstall of the Apache2 package, and a complete reinstall.  That should properly re-create any of the init scripts, and properly reference them in the initd.conf file (which is (indirectly) where most stand alone daemons are started up when the system boots)

---

### Post by SteffJay on 2006-06-26
Hello **Herald**. Thanks for the reply. This fiasco first started when i made an auto-start script for a hub server called Verlihub. This would not start using the conventional methods in the session handler. Apache2 was already installed and auto-starting prior to that. The files that are being searched for are (probably) the Macromedia Flash Server i have installed, which is working in conjunction with a chatroom. I have already done a complete uninstall/reinstall of the Apache2 server but it was worse after that than before !!! I have since reinstalled a backup i made (thank God) of the entire Operating System which leaves me with the same problem of Apache2 not auto-starting when the OS boots up ](*,) . I have to start it manually. I hope this makes sence to you because it sure as hell does'nt to me !!! I don't like Windowzzzz but i will give it credit as to how things are installed and how things are auto-started or not !!!  :-|

---

### Post by henriquemaia on 2006-06-26
[quote=SteffJay]Hello **Herald**. Thanks for the reply. This fiasco first started when i made an auto-start script for a hub server called Verlihub. This would not start using the conventional methods in the session handler. Apache2 was already installed and auto-starting prior to that. The files that are being searched for are (probably) the Macromedia Flash Server i have installed, which is working in conjunction with a chatroom. I have already done a complete uninstall/reinstall of the Apache2 server but it was worse after that than before !!! I have since reinstalled a backup i made (thank God) of the entire Operating System which leaves me with the same problem of Apache2 not auto-starting when the OS boots up ](*,) . I have to start it manually. I hope this makes sence to you because it sure as hell does'nt to me !!! I don't like Windowzzzz but i will give it credit as to how things are installed and how things are auto-started or not !!!  :-|[/quote] 
Don't panic*. Most situations like this start with some trivial error, like mistaken privileges or something. 

Start with a new installation of Apache2. Begin by making a backup of your /etc/apache2 directory.

```
cp -r /etc/apache2 /home/your_user_name/Desktop/apache2backup
```

note: remember to change **your_user_name** to your actual username.

Uninstall the apache2 packages, using the option **Mark for Complete Removal** on synaptic.

Double-check that everything was really removed, making a:

```
sudo rm -r /etc/apache2
``` 
Note: you don't have to worry on this one, since you made a backup earlier.

Now install apache2 again through synaptic. Everything should be ok for now with apache, since it's using its default configuration provided by the package. 

If still want to go with the verlihub installation, do it step by step checking if everything is still ok with apache. You have to do a wise troubleshooting on this one.

*Cool. I made an unintentional [[SIZE=2]Hitchhiker's Guide to the Galaxy[/SIZE]]("http://en.wikipedia.org/wiki/The_Hitchhiker%27s_Guide_to_the_Galaxy") quote, :)[URL="http://en.wikipedia.org/wiki/The_Hitchhiker%27s_Guide_to_the_Galaxy"]
[/URL]

---

### Post by herald on 2006-06-29
OK, first thing to do is to look in /etc/rc2.d/ and look for something that says apache2.  It will probably be in the form of S##apache2 where the ## are some arbitrary number.  What you're looking at is the start script that "init" runs at that runlevel during bootup of your computer.  The ones that start with S are start scripts.  The ones (if any) that start with K are stop scripts.  The number is the sequence in which init runs the script, I.E. starts the process.  The lowest numbers are started first, the higher numbers are started last.  The apache daemon is supposed to spawn during runlevel 2.  If you do not have an init script in rc2.d that starts with S and has apache in the name, then init is NOT starting apache automatically.  This is a good place to start to see whether or not your computer is even set to auto launch Apache.  If the script is there, and you are not seeing the apache daemon when you do a "ps -ef |grep apache" then the next thing to check is the log files.  look in either the /var/log/dmesg file or the /var/log/messages file.  Look for any error relating to Apache.  Let us know what you find!

---

### Post by SteffJay on 2006-06-30
Ok **Herald**, thanks for the reply..... I tried the other method but ended up with a cursor the size of the screen..  :(   So, i had to reinstall everything as i did'nt know how to (or could'nt) get into the folders to change the backup file to the normal script again !!. I will give this a try and let you know the result. Ok.......

There is an item in /etc/rc2d/S99apache2

After doing the "ps -ef |grep apache" i get......  

root      5603     1  0 Jun28 ?        00:00:00 /usr/sbin/apache2 -k start -DSSLwww-data 29886  5603  0 Jun29 ?        00:01:41 /usr/sbin/apache2 -k start -DSSLwww-data 23315  5603  0 Jun30 ?        00:00:43 /usr/sbin/apache2 -k start -DSSLwww-data  3675  5603  0 Jun30 ?        00:00:17 /usr/sbin/apache2 -k start -DSSLwww-data  6823  5603  0 Jun30 ?        00:00:12 /usr/sbin/apache2 -k start -DSSLwww-data  6830  5603  0 Jun30 ?        00:00:12 /usr/sbin/apache2 -k start -DSSLwww-data  7487  5603  0 Jun30 ?        00:00:07 /usr/sbin/apache2 -k start -DSSLwww-data  7488  5603  0 Jun30 ?        00:00:07 /usr/sbin/apache2 -k start -DSSLwww-data 11211  5603  0 09:18 ?        00:00:02 /usr/sbin/apache2 -k start -DSSLwww-data 11212  5603  0 09:18 ?        00:00:02 /usr/sbin/apache2 -k start -DSSLwww-data 11213  5603  0 09:18 ?        00:00:03 /usr/sbin/apache2 -k start -DSSLroot     12105 11936  0 09:57 pts/0    00:00:00 grep apache

After checking the two log files, the "dmesg" file does not show any problems with Apache2 only the hardware sequence from start up and the "messages" file shows the in/out of the ethernet card I.E. un 22 07:36:47 localhost kernel: [17210591.500000] Inbound IN=eth0 OUT= MAC=00:e0:4c:ea:42:bf:00:13:10:4d:94:8a:08:00 SRC=76.0.233.215 DST=192.168.1.103 LEN=125 TOS=0x00 PREC=0x00 TTL=111 ID=51704 PROTO=UDP SPT=19545 DPT=8533 LEN=105

No trace of any error for Apache2 anywhere !!!!

---

### Post by herald on 2006-07-01
Hmmm, looks to me the only apache daemon that's kicking off is the SSL side of things...
Just to make sure I understand your setup, you've got some sort of VerliHUB software, apache2, apache2SSL, and a flash server that's running a Web Chat app.
Because you don't show any non secure http listen sockets, I'd go over the apache config files with a fine toothed comb to make sure every option in there is set correctly.  Pay special attention to the sites configured in sites-available and the sites-enabled directories.  The lack of messages in the standard system boot logs means that the process is kicking off fine.  The next place to look is in your apache error logs, but you said that all you were getting in those was missing file warnings for the flash files...look again and make sure.

---

### Post by SteffJay on 2006-07-02
After rebooting the pc this morning (Sunday 02-07-06) and looking into the Apache error log, this is the readout:

[B][Sun Jul 02 08:02:50 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf, referer: 26thregra-asc.hopto.org/chat/chatui.swf
[Sun Jul 02 08:02:50 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf, referer: 26thregra-asc.hopto.org/chat/chatui.swf
[Sun Jul 02 08:02:51 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf, referer: 26thregra-asc.hopto.org/chat/chatui.swf
[Sun Jul 02 08:02:51 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/cache.swf, referer: 26thregra-asc.hopto.org/chat/chatui.swf
[Sun Jul 02 08:03:01 2006] [error] [client 10.10.10.10] File does not exist: /var/www/chat/closeMod.swf, referer: 26thregra-asc.hopto.org/chat/chatui.swf
[Sun Jul 02 09:13:44 2006] [notice] caught SIGTERM, shutting down[/B]

The strange thing is, the **chatui.swf** does exist but the **closeMod.swf and cache.swf** does'nt but it is still reporting that nothing exists at all !!, but i still dont see why it is looking for them anyway   8-[

Also (refering to your advisory: **Pay special attention to the sites configured in sites-available and the sites-enabled directories**, The only thing in the **sites available** is a **default** and the only thing in **sites enabled** is **000-default**. Make any sence to you ?

It looks exceedingly more likely that i am going to have to wipe the whole thing and start all over again, not that i am willing to do so as there's about three days work in doing all of that. **NOT**  a healthy prospect !!!

---

### Post by SteffJay on 2006-07-02
Ok...  i have found the remedy !!!  go here [http://linuxhelp.blogspot.com/2006/04/enabling-and-disabling-services-during_01.html](http://linuxhelp.blogspot.com/2006/04/enabling-and-disabling-services-during_01.html) (you need the Debian Method) and do as instructed. I firstly, uninstalled the startup-sequences for Apache2 then setup the default as instructed and rebooted. Hey presto ....  Auto-starting !! I'm now a happy bunny !!  :p  Thanks to everyone who has had an input on this. All very much appreciated.

---

### Post by faultyCPU on 2006-07-03
how these files look in your system ? look at permissions
root@S:/var/log# cd /etc/init.d/

root@S:/etc/init.d# ls -l apache2
-rwxr-xr-x  1 root root 4430 Jan  7 19:21 apache2

root@S:/etc/init.d# cd /etc/rc2.d/

root@S:/etc/rc2.d# ls -l | grep -i apache
lrwxrwxrwx  1 root root 17 Jun  6 03:53 S91apache2 -> ../init.d/apache2

---

