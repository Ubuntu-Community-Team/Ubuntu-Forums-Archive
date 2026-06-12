---
title: "ODBC client (isql) no longer working after system upgrade"
date: 2012-01-31
forum: Server Platforms
---

### Post by sverre76 on 2012-01-31
This friday I performed a system update on my companys Ubuntu server using "aptitude safe-upgrade". After the following system reboot I can no longer get isql working to communicate with the remote Pervasive SQL server.

I have done this a couple of times before so I believe this has nothing to do with environment variables not being set properly. But the error message returned when I try to run the client gives me very little information about what is going on.
```
psql@ubuntu1:~$ echo "select D1001, D1021 from PULAGER WHERE D18202='Y'" | isql -v -b -d\| hoistswe
bash: /usr/local/psql/bin/isql: No such file or directory
```

The file /usr/local/psql/bin/isql is there so there is propably another file that it is complaining about. How can I get information about which file it is actually missing? And how could that be missing after I just have been running a safe-upgrade?

my .bash_profile:
```
psql@ubuntu1:~$ cat .bash_profile
umask 022
PVSW_ROOT=/usr/local/psql
PATH=$PVSW_ROOT/bin:/bin:/usr/bin:/usr/lib
LD_LIBRARY_PATH=$PVSW_ROOT/lib:$PVSW_ROOT/lib64:$PVSW_ROOT/bin:/usr/lib
MANPATH=$PVSW_ROOT/man:$MANPATH
BREQ=$PVSW_ROOT/lib
export PVSW_ROOT PATH LD_LIBRARY_PATH MANPATH BREQ
```

I also found out something that looks a little weird, but I have no idea if it has been like this before the upgrade, but I guess that file should be executable:
```
root@ubuntu1:/usr/local/psql/lib# ldd odbcci.so 
        not a dynamic executable
```


Please let me know if you need more information to be able to help me out. Thanks!

---

### Post by sverre76 on 2012-01-31
I went through the aptitude log from the last update and reinstalled the packages I felt might be needed by the odbc client, and that made it work! 

So no help needed, but maybe someone else stumbles upon this in the future so I will post what packages I reinstalled.

```
aptitude install ia32-libs lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 libv4l-0 nspluginwrapper
```

---

