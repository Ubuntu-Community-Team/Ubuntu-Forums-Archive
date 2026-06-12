---
title: "error on installing libmysqlclient-dev on ubuntu server 16.04"
date: 2017-04-13
forum: Server Platforms
---

### Post by janjaap77 on 2017-04-13
I try to install libmysqlclient-dev.
but when i do that the following error pops up, and i dont know how to solve that.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  rlwrap
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  libmysqlclient-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,160 kB of archives.
After this operation, 7,071 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 89063 files and directories currently installed.)
Preparing to unpack .../libmysqlclient-dev_5.7.17-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libmysqlclient-dev (5.7.17-0ubuntu0.16.04.2) ...
dpkg: error processing archive /var/cache/apt/archives/libmysqlclient-dev_5.7.17-0ubuntu0.16.04.2_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/mysql_config.1.gz', which is also in package libmysqlclient16-dev 5.1.73-rel14.12-624.precise
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libmysqlclient-dev_5.7.17-0ubuntu0.16.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```



in fact i thought it was installed on my server, but i cant find out if it is and more to say what version it is then. so thats why i dod this procedure.
However im now stuck with this error.

---

### Post by howefield on 2017-04-13
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by darkod on 2017-04-13
You check if any package is installed and the version in the repositories with:
```
apt-cache policy <packagename>
```

As for this error, not sure I can help much. But it is complaining on another similar package that has precise in it's name. Since you are running xenial (16.04), is there any chance there are precise related packages in there?

Something installed manually from source maybe? Was this an upgrade initially from precise?

---

### Post by janjaap77 on 2017-04-13
did the command above and this was the outcome.

```

apt-cache policy libmysqlclient-dev
libmysqlclient-dev:
  Installed: (none)
  Candidate: 5.7.17-0ubuntu0.16.04.2
  Version table:
     5.7.17-0ubuntu0.16.04.2 500
        500 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     5.7.17-0ubuntu0.16.04.1 500
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     5.7.11-0ubuntu6 500
        500 http://nl.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

i dont know about that other package to be honest.

so i did the same command to check it out and this was the outcome.

```
apt-cache policy libmysqlclient16-dev
libmysqlclient16-dev:
  Installed: 5.1.73-rel14.12-624.precise
  Candidate: 5.1.73-rel14.12-624.precise
  Version table:
 *** 5.1.73-rel14.12-624.precise 100
        100 /var/lib/dpkg/status

```

now the main answer is, why do i want to install libmysqlclient-dev.

that is because i have a program that i want to run, but when i run it it says.

```

Could not connect to MySQL database at 127.0.0.1: Client does not support authentication protocol requested by server; consider upgrading MySQL client
```

So i looked it up and they say they need libmysqlclient to run the program.

---

### Post by darkod on 2017-04-13
What you can do, is note down the exact name of that second package, and then remove it with sudo apt-get remove.

After that try again sudo apt-get install of the first package (the one you want installed).

Since that second package has precise in the name, and figures as installed, I would assume it is safe to remove it. The first package seems to be much newer version anyway...

If it turns out you do need that second package, you will have its full name to reinstall it again. But I doubt it, because of the precise word there...

---

### Post by janjaap77 on 2017-04-13
thanks darkod, i will try when i get at home after work to see if that fixes my problem.

gr.

---

### Post by janjaap77 on 2017-04-15
thanks, and sorry for the late reply that fixed my error indeed.

---

### Post by darkod on 2017-04-15
No problem, glad you got it fixed. Please mark the thread as solved, you can do that in Thread Tools above the first post.

---

