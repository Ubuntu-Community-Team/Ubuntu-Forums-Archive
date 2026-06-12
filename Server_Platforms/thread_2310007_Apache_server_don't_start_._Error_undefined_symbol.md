---
title: "Apache server don't start . Error: undefined symbol: apr_table_getm"
date: 2016-01-15
forum: Server Platforms
---

### Post by DanSalles on 2016-01-15
Good afternoon everyone.


During the installation of Apache server, I came across the following error:
[FAIL] Restarting web server: apache2 failed!
[warn] The apache2 configtest failed. ... (Warning).
Output of config test was:
/ usr / sbin / apache2: symbol lookup error: / usr / sbin / apache2: undefined symbol: apr_table_get
Action 'configtest' failed.
The Apache error log may have more information.




I tried to find a solution on google but not getting results.
Thanks you for the collaboration.

---

### Post by SeijiSensei on 2016-01-15
That's an error coming from the Apache binary executable itself.  You shouldn't see anything like this on a normal installation. 

What version of Ubuntu are you running, and how did you install Apache?

As a general rule, you should stick to LTS versions of Ubuntu on servers, currently 14.04LTS.

---

### Post by DanSalles on 2016-01-15
The version is Ubuntu 14.04 LTS. The command that i used was: [COLOR=#2C001E][FONT=Ubuntu]apt-get install apache2[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-01-15
Hmm.  I've installed Apache a number of times on 14.04 and never had that problem.

I just installed it now on this 14.04 machine with apt-get and see this:

```

The following NEW packages will be installed:
  apache2 apache2-bin apache2-data [B]libapr1 libaprutil1 libaprutil1-dbd-sqlite3
  libaprutil1-ldap[/B]

```
That gave me these libraries:
```

/usr/lib/x86_64-linux-gnu/libapr-1.so.0
/usr/lib/x86_64-linux-gnu/libapr-1.so.0.5.1
/usr/lib/x86_64-linux-gnu/libaprutil-1.so.0
/usr/lib/x86_64-linux-gnu/libaprutil-1.so.0.5.3

```
Do you see those libraries with those version numbers on your system?

Did you run "sudo apt-get update" before installing?  If not, then try this:
```

sudo apt-get remove apache2
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apache2

```
Any better?

---

### Post by DanSalles on 2016-01-20
Yes, i ran the uptade.

Using ldd/sbin/apache2, i got this information:
[TABLE="width: 500"]
[TR]
[TD]linux-vdso.so.1 =>  (0x00007fffe4123000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f3a303b2000)
    libaprutil-1.so.0 => **/opt/pleora/ebus_sdk/Ubuntu-12.04_64/lib/libraprutil-1.so.0 **(0x00007f3a3018f000)
    libapr-1.so.0 => **/opt/pleora/ebus_sdk/Ubuntu-12.04_64/lib/libapr-1.so.0 **(0x00007f3a2ff59000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f3a2fd3c000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f3a2f9b9000)
    libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007f3a2f7b3000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f3a2f5ab000)
    libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007f3a2f372000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f3a2f16d000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f3a2ef44000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f3a3087d000)[/TD]
[/TR]
[/TABLE]

Also, i saw in the files that i have: **libaprutil-1.so.0 => /usr/lib/x86_64-linux-gnu/libaprutil-1.so.0** and **libapr-1.so.0 => /usr/lib/x86_64-linux-gnu/libapr-1.so.0**.. I think that this is the problem. I tried to find on the Internet how to change the directory but not been successful

---

### Post by DanSalles on 2016-01-25
Thank for you all the help. I fixed the problem. I uninstalled manually the old Libraries and the server pulled the correct directories.


I'll leave the steps to follow if someone has a similar problem.


cd mkdir libapr /opt/pleora/ebus_sdk/Ubuntu-12.04_64/lib/
cp -u /opt/pleora/ebus_sdk/Ubuntu-12.04_64/lib/ libapr * libapr
rm -i /opt/pleora/ebus_sdk/Ubuntu-12.04_64/lib/libapr*
rm: remove regular file `/usr/local/lib/libapr-1.a '? y
rm: remove regular file `/usr/local/lib/libapr-1.la '? y
rm: remove `symbolic link /usr/local/lib/libapr-1.so '? y
rm: remove `symbolic link /usr/local/lib/libapr-1.so.0 '? y
rm: remove regular file `/usr/local/lib/libapr-1.so.0.2.12 '? y
rm: remove regular file `/usr/local/lib/libaprutil-1.a '? y
rm: remove regular file `/usr/local/lib/libaprutil-1.la '? y
rm: remove `symbolic link /usr/local/lib/libaprutil-1.so '? y
rm: remove `symbolic link /usr/local/lib/libaprutil-1.so.0 '? y
rm: remove regular file `/usr/local/lib/libaprutil-1.so.0.2.12 '? y

---

