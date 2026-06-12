---
title: "Permission error with mailman's command-line interface"
date: 2013-02-07
forum: Server Platforms
---

### Post by Conjacq on 2013-02-07
I've got an Ubuntu Server 12.04 and installed Mailman on the server. I want to control the mailinglists in Mailman from PHP via the command-line. If I run

```
/usr/lib/mailman/bin/list_lists
```

I get the following error:

```
Traceback (most recent call last):
  File "/usr/lib/mailman/bin/list_lists", line 122, in <module>
    main()
  File "/usr/lib/mailman/bin/list_lists", line 94, in main
    mlist = MailList.MailList(n, lock=0)
  File "/var/lib/mailman/Mailman/MailList.py", line 130, in __init__
    self.Load()
  File "/var/lib/mailman/Mailman/MailList.py", line 640, in Load
    dict, e = self.__load(file)
  File "/var/lib/mailman/Mailman/MailList.py", line 606, in __load
    fp = open(dbfile)
IOError: [Errno 13] Permission denied: '/var/lib/mailman/lists/mailman/config.pck'
```

The file [FONT="Courier New"]/var/lib/mailman/lists/mailman/config.pck[/FONT] is changed a couple times per day by Mailman automatically and the permissions then become:

```
-rw-rw---- 1 list list 3741 Feb  7 12:00 config.pck
```

So I can't change the permissions of that file, because it is automatically reverted to the permissions above.

The permissions of [FONT="Courier New"]/usr/lib/mailman/bin/list_lists[/FONT] are as follows:
```

-rwxr-xr-x 1 root list  3333 Jul 17  2012 list_lists
```

I tried to set the setgid as follows:
```

sudo chmod g+s /usr/lib/mailman/bin/list_lists
```

And the permissions will become:

```
-rwxr-sr-x 1 root list  3333 Jul 17  2012 list_lists
```

But I get the same errors. How can I set the permissions correctly?

---

### Post by linuxtechguy on 2013-02-07
Try running the check_perms script in the bin folder with the -f flag to fix all permissions.

---

### Post by Conjacq on 2013-02-27
> **linuxtechguy said:**
> Try running the check_perms script in the bin folder with the -f flag to fix all permissions.

I ran the following:

```
sudo /usr/lib/mailman/bin/check_perms -f
No problems found
```

So check_perms -f doesn't locate or solve the problem.

I found a solution, but I'm not sure whether it is a safe one. My php script is run by user www-data. I added www-data to the group of the config file:
```
sudo usermod -a -G list www-data
```

To test the code, I used to following commands in the terminal:
```
sudo su www-data
/usr/lib/mailman/bin/list_lists
```

---

