---
title: "vsftpd listing directory does not show seconds"
date: 2016-03-08
forum: Server Platforms
---

### Post by Mikhail_Batkalin on 2016-03-08
Hello Guys,

I setup a Ubuntu Server on an EC2 instance, which is used for running / displaying data via vsftpd. Everything is working as it should, and it is being updated every 5 seconds. But, my directory is not showing the exact time that it's been last updated, only the latest minute(which I know it does update every 5 seconds - I've tested by removing the file). Is there a way to have the timestamp display seconds? See SS below:


[ATTACH=CONFIG]267710[/ATTACH]

Thanks for any help provided
-Mikhail

---

### Post by nerdtron on 2016-03-08
Is that the file view via web browser? I don't think there is an option to see the "seconds" for this.
But the ls command with the --time-style option can give you timestamp showing seconds, or even your own date format:
```


       --time-style=STYLE
              with -l, show times using style STYLE: full-iso, long-iso, iso, locale, or +FORMAT; FORMAT  is
              interpreted  like  in  'date';  if  FORMAT is FORMAT1<newline>FORMAT2, then FORMAT1 applies to
              non-recent files and FORMAT2 to recent files; if STYLE is prefixed with 'posix-', STYLE  takes
              effect only outside the POSIX locale


```

Sample:
```

[root@goddard ~]# ls -lh --time-style=+%T
total 15M
-rw-r--r-- 1 root root  23K 15:44:00 history
-rw-r--r-- 1 root root 7.4M 22:20:33 Joomla_3.4.3-Stable-Full_Package.tar.gz
-rw-r--r-- 1 root root 6.8M 07:45:45 latest.tar.gz
-rw-r--r-- 1 root root   98 08:55:39 test


```

---

