---
title: "init: ureadahead-other main process (672) terminated with status 4"
date: 2011-01-30
forum: Server Platforms
---

### Post by hoanggeneral on 2011-01-30
Hi all.
I'm having this problem on my Ubuntu Server 10.04 (32-bit) virtual machine. I am running the server in VMWare Workstation 7.
[IMG]http://picasaweb.google.com/mr.hoang1412/UbuntuServer1004StartUpError?feat=directlink[/IMG][IMG]http://picasaweb.google.com/mr.hoang1412/UbuntuServer1004StartUpError?feat=directlink[/IMG]
[http://picasaweb.google.com/mr.hoang1412/UbuntuServer1004StartUpError?feat=directlink](http://picasaweb.google.com/mr.hoang1412/UbuntuServer1004StartUpError?feat=directlink)

I just finished this exercise one day before the error arrives.
```
·         Create a new user using the useradd command. 
  (everything below can be done in one command!)
  1.       Add the user to the group "admin"
  2.       Create a home directory for this user with the same name as the login.
  3.       Verify the account was created by logging in as the new user. Use the login name as the first letter of your first name and your last name. For example:
          
                          Full Name:          John Smith
                          Login:                    jsmith
   
   
  Answer:
  sudo useradd –c “John Smith” –g “admin” –m –s “/bin/bash” –p “testpass” jsmith
  sudo passwd jsmith
   
   
  ·         In your home directory, create a hard link to /dev/null and call it blackhole.
  Is this possible? Why?
  Answer:
  It’s not possible because hard link cannot form across file system.
   
  ·      In your home directory, create a soft link to /dev/null and call it blackhole.
  Is this possible? Why?
  Answer:
          It’s possible because soft-link/symbolic-link can form across file system.
   
   
   
   
  ·         Configure your network interface.
  1.       open the file: /etc/network/interfaces
  2.       remove all ethernet entries and insert the following:
  auto eth0
  iface eth0 inet dhcp
  3.       restart your network interface with the following command:
  /etc/init.d/networking restart
   
  è Cannot access to the internet anymore after doing this!
  
```Now, I cannot boot into the system anymore.
Anyone has any idea please help me.
Thanks.

---

### Post by Bucic on 2011-02-17
It seems to be a harmless warning (informational) [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)

So I'm guessing the real problem is elsewhere.


**Everything about ureadahead**
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

### Post by Bucic on 2011-02-17
[http://ubuntuforums.org/showthread.php?t=1518110&page=2](http://ubuntuforums.org/showthread.php?t=1518110&page=2)
+it's a harmless message. The boot problem is probably caused by something else.

---

