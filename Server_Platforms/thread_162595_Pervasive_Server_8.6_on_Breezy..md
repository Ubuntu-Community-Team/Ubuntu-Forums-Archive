---
title: "Pervasive Server 8.6 on Breezy."
date: 2006-04-19
forum: Server Platforms
---

### Post by PaLoBo on 2006-04-19
Hi all,

Has anybody successfuly managed to install pervasive server 8.6 or any other on ubuntu. I went through all the steps that the pervasive install guide mentions but I get quite a few script errors. (See them below.)

```

+++++ Setting up group and admgroup...
Creating group pvsw...
Creating group pvsw-adm...

+++++ Setting up user psql...
Creating user psql, this may take a while...

+++++ Setting up the environment...

+++++ Setting up symbolic links for libraries...

+++++ Making user psql owner of all files in /usr/local/psql...

+++++ Setting up entries in /etc/services...
The following line added to /etc/services:
btrieve 3351/tcp # Pervasive.SQL V8 MKDE daemon
The following line added to /etc/services:
sqlmgr 1583/tcp # Pervasive.SQL V8 SQL Manager daemon

+++++ Setting up the PCOM libraries...
/usr/local/psql/lib/libpseucjp.so.1 registered successfully
/usr/local/psql/lib/libpscp932.so.1 registered successfully
/usr/local/psql/lib/libcnstring.so.8 registered successfully
/usr/local/psql/lib/libmkc.so.8 registered successfully
/usr/local/psql/lib/libexp010.so.8 registered successfully
/usr/local/psql/lib/liblicmgrrb.so.8 registered successfully
/usr/local/psql/lib/liblegacylm.so.8 registered successfully
/usr/local/psql/lib/libmkderb.so.8 registered successfully
/usr/local/psql/lib/libpctlgrb.so.8 registered successfully
/usr/local/psql/lib/libpceurop.so.1 registered successfully
/usr/local/psql/lib/libpssax.so.1 registered successfully
/usr/local/psql/lib/libpsutilrb.so.1 registered successfully
/usr/local/psql/lib/libclientrb.so.8 registered successfully
/usr/local/psql/lib/libupiapirb.so.8 registered successfully
/usr/local/psql/lib/libpvmsgrb.so.8 registered successfully
/usr/local/psql/lib/libpsqlcsm.so.8 registered successfully
/usr/local/psql/lib/libpsqlcsp.so.8 registered successfully
/usr/local/psql/lib/libdbcsipxy.so.8 registered successfully
/usr/local/psql/lib/libdcm100.so.8 registered successfully
/usr/local/psql/lib/libcsi100.so.8 registered successfully
chown: cannot access `/tmp/PS*': No such file or directory

+++++ Setting up the startup file /etc/rc.d/init.d/psql ...
/usr/local/psql/etc/postinstall.sh: line 350: /etc/rc.d/init.d/psql: No such file or directory
chown: cannot access `/etc/rc.d/init.d/psql': No such file or directory
chmod: cannot access `/etc/rc.d/init.d/psql': No such file or directory

/usr/local/psql/etc/postinstall.sh: line 527: /etc/rc.d/init.d/psqlforce: No such file or directory
chown: cannot access `/etc/rc.d/init.d/psqlforce': No such file or directory
chmod: cannot access `/etc/rc.d/init.d/psqlforce': No such file or directory

+++++ Setting up the init script links...
/usr/local/psql/etc/postinstall.sh: line 637: cd: /etc/rc.d/rc0.d: No such file or directory
/usr/local/psql/etc/postinstall.sh: line 638: cd: /etc/rc.d/rc1.d: No such file or directory
/usr/local/psql/etc/postinstall.sh: line 639: cd: /etc/rc.d/rc2.d: No such file or directory
/usr/local/psql/etc/postinstall.sh: line 640: cd: /etc/rc.d/rc3.d: No such file or directory
/usr/local/psql/etc/postinstall.sh: line 641: cd: /etc/rc.d/rc4.d: No such file or directory
/usr/local/psql/etc/postinstall.sh: line 642: cd: /etc/rc.d/rc5.d: No such file or directory
/usr/local/psql/etc/postinstall.sh: line 643: cd: /etc/rc.d/rc6.d: No such file or directory
The Pervasive.SQL engines can be controlled by /etc/rc.d/init.d/psql:
/etc/rc.d/init.d/psql {start|stop|force|restart}

+++++ Setting up support for PAM authentication...
Copying PAM files...
Configuring PAM file...
Configuring PAM directory...

+++++ Stopping the Pervasive.SQL daemons...
/usr/local/psql/etc/postinstall.sh: line 693: /etc/rc.d/init.d/psql: No such file or directory
+++++ Setting up user licenses...
One license was applied.

chown: cannot access `/tmp/PS*': No such file or directory

+++++ Starting the Pervasive.SQL daemons...
/usr/local/psql/etc/postinstall.sh: line 712: /etc/rc.d/init.d/psql: No such file or directory
+++++ Setting up the DEMODATA database name...
Creating the database name DEMODATA...
Failed to Create database "DEMODATA".
Error code : 2307 (Cannot open DBNAMES.CFG file. Check if 'mkded' is running.)
No named databases found

+++++ Setting up the DEMODATA DSN in /usr/local/psql/etc/odbc.ini...
Creating the DSN DEMODATA...

/usr/local/psql/etc/odbc.ini created
/usr/local/psql/etc/postinstall.sh: line 773: /etc/rc.d/init.d/psql: No such file or directory
++++ Searching for and restoring configuration from previous install...
dbnames.cfg.rpmsave
bti.ini.rpmsave
odbc.ini.rpmsave
btpasswd.rpmsave

/usr/local/psql/etc/postinstall.sh: line 806: /etc/rc.d/init.d/psql: No such file or directory
+++++ Setting up the DefaultDB database name...
Creating the database name DEFAULTDB...
Failed to Create database "DEFAULTDB".
Error code : 2307 (Cannot open DBNAMES.CFG file. Check if 'mkded' is running.)
No named databases found

+++++ Setting up the DefaultDB DSN in /usr/local/psql/etc/odbc.ini...
Creating the DSN DefaultDB...

The original file /usr/local/psql/etc/odbc.ini is saved as /usr/local/psql/etc/odbc.ini.bak
The file /usr/local/psql/etc/odbc.ini updated

+++++ Setting up the Samba shares...
Creating the Samba share PSQLDATA for data...
Restarting smbd for the changes to take effect...

/usr/local/psql/etc/postinstall.sh: line 928: /etc/rc.d/init.d/psql: No such file or directory
chown: cannot access `/tmp/PS*': No such file or directory
+++++ Restarting the Pervasive.SQL daemons...
/usr/local/psql/etc/postinstall.sh: line 935: /etc/rc.d/init.d/psql: No such file or directory
Please read the license agreement in file /usr/local/psql/LICENSE.
Using this product indicates that you agree with all terms and
conditions stated therein. If you do not agree, you must uninstall
the product now.

View the README and documentation for this product at:
file:/usr/local/psql/doc/html/index.html

Register your Pervasive.SQL product at:
http://www.pervasive.com/registration

Install has successfully completed.

```

What went wrong? How can I check to see if all is ok?

Any help would be great. Cheers,
P.

---

### Post by jazzmuzik on 2006-04-19
> chmod: cannot access `/etc/rc.d/init.d/psql': No such file or directory

Ubuntu has directories /etc/rc.d/ and /etc/init.d/ but it doesn't have a directory named /etc/rc.d/init.d/ . That looks more like a RedHat/Fedora naming convention.

Are you sure you are installing a version of pervasive server for Debian/Ubuntu? Or perhaps the setup program has options to specify alternate locations for files?

---

### Post by PaLoBo on 2006-04-20
Hi again.

I've been tweaking (or trying anyway...) the install script and have managed to thusfar fixed the location of /etc/rc.d/init.d/psql.

The output of the install script looks like this now (I left out the parts with no errors.)

```

+++++ Setting up user licenses...
7112: License is already installed.

chown: cannot access `/tmp/PS*': No such file or directory

+++++ Starting the Pervasive.SQL daemons...
Starting Pervasive services:
mkded
sqlmgr
touch: cannot touch `/var/state/psql': No such file or directory

+++++ Setting up the DEMODATA database name...
Creating the database name DEMODATA...
Database DEMODATA has been successfully added
Database Maintenance Utility v8.60.192.030 for Unix
Database list:
DEMODATA

+++++ Setting up the DEMODATA DSN in /usr/local/psql/etc/odbc.ini...
An existing DSN DEMODATA was found.
Shutting down Pervasive services:
sqlmgr
stopping SQLManager...
mkded

Clearing Pervasive shared memory:
Cleaning shared memory region #0... OK
Cleaning IPC semaphores ... OK
Clearing semaphores:

++++ Searching for and restoring configuration from previous install...
dbnames.cfg.rpmsave
bti.ini.rpmsave
odbc.ini.rpmsave
btpasswd.rpmsave

Starting Pervasive services:
mkded
sqlmgr
touch: cannot touch `/var/state/psql': No such file or directory

+++++ Setting up the DefaultDB database name...
Creating the database name DEFAULTDB...
Database DEFAULTDB has been successfully added
Database Maintenance Utility v8.60.192.030 for Unix
Database list:
DEFAULTDB
DEMODATA

+++++ Setting up the DefaultDB DSN in /usr/local/psql/etc/odbc.ini...
An existing DSN DefaultDB was found.

+++++ Setting up the Samba shares...
An existing Samba share PSQLDATA was found.

Shutting down Pervasive services:
sqlmgr
stopping SQLManager...
mkded

chown: cannot access `/tmp/PS*': No such file or directory
+++++ Restarting the Pervasive.SQL daemons...
Starting Pervasive services:
mkded
sqlmgr
touch: cannot touch `/var/state/psql': No such file or directory

```

With regards to /tmp/PS*, should I manually create the foder? Also, being new to linux and it's directory structure, where would I find /var/state/psql. I searched /var and it has no /state. Should I also create those manually?

Thanks for all and any help

Cheers,
P.

---

### Post by jazzmuzik on 2006-04-20
If you are new to Liinux, I would look for a Pervasive Server package made for Ubuntu/Debian. Otherwise I think you are trying to installing a package that doesn't understand the Ubuntu directories/system. You may successfully tweak the install  only to find later that something else doesn't work.

You might also ask for help in the programming forum.

---

### Post by jazzmuzik on 2006-04-20
Another thought: see if your pervasive server package has an install option where you can tell it the directories to install to. Sometimes you can run something like this:

./programName --help

or

./configure --help

and it gives you a list of installation options.

---

### Post by PaLoBo on 2006-04-20
[QUOTE=jazzmuzik]If you are new to Liinux, I would look for a Pervasive Server package made for Ubuntu/Debian. Otherwise I think you are trying to installing a package that doesn't understand the Ubuntu directories/system. You may successfully tweak the install  only to find later that something else doesn't work.

You might also ask for help in the programming forum.[/QUOTE]
 Sniff...sniff. You are right. All seemed to go well but when I tried to run the application to input our key I got an error message stating that a certain library was missing, but when I checked for it, it was there. It seems that it didn't link to well. If there is anybody knowledgeable about scripts and ubuntu directory structure that would like to help me out, I could post the intall script here.

Apart from... I guess I'm just going to keep on tinkering. (I have backups of everything and dapper should have a final release soon, so if i break my system, then I have a good escuse to start all over. ;) )

Cheers and keep those sugestions coming because they are very much welcome.

P.

---

### Post by PaLoBo on 2006-04-20
This is driving me mad (just a little more than I already was :D )

I uninstalled and reinstalled. All seemed to go well. I then try and run sudo /usr/local/psql/bin/clilcadm, and get the following error:

```

/usr/local/psql/bin/clilcadm: error while loading shared libraries: libpscl.so.1: cannot open shared object file: No such file or directory

```

When I look, both the symlink libpscl.so.1 and the library to which it is linked (libpscl.so.1.50.192) are present in /usr/local/psql/lib.

Any thoughts?

As of yet, I am unable to find a pervasive that seems suitable for ubuntu.

I will keep trying...!!! ](*,)

---

### Post by PaLoBo on 2006-04-21
Finally managed to get this thing working. Even though I still can't rn the app to insert our key, I did some digging in the install script and found where they placed the trial kay, substituted it with ours and violá. As for the other errors, I had to manually create the directories /var/state and /tmp/PS*, and remove the various ocorrunces of /etc/rc.d/init.d/ and replace it with /etc/init.d.

Now all I need is a few weeks of testing to be sure and I can then install it on our server.

Cheers,
P.

---

### Post by jazzmuzik on 2006-04-21
That's great. Good luck during the testing.

---

