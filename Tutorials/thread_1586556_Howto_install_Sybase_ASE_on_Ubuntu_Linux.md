---
title: "Howto install Sybase ASE on Ubuntu Linux"
date: 2010-10-02
forum: Tutorials
---

### Post by WitchCraft on 2010-10-02
Goto [http://www.sybase.com/linux](http://www.sybase.com/linux) 
and download the  ASE Developer&#8217;s Edition.

While it is downloading, install libaio1
```

apt-get install libaio1

```
because the install anywhere installer doesn't resolve dependencies.


Now, while it still is downloading, use the time and edit your
```

/etc/sysctl.conf 

```

and add or edit the following line:
```

kernel.shmmax = 300000000

```
for that it has at least 300 MB shared memory, and not just 30 as it is the default.

Then, load the setup
```

/sbin/sysctl -p

```

or change the current configuration like this:
```

echo "300000000" > /proc/sys/kernel/shmmax

```
for that we don't have to restart.

Now, unzip the downloaded file, and open a bash console.


Change to the download directory:
```

cd /home/username/Downloads/ase155_linuxx86

```


Now give the install anywhere-file execute permission:
```

chmod +x ./setup.bin

```


Execute with
```

./setup.bin

```

Enter the setup's info and run the installation.
If it fails, fix the errors. 
Monitoring server won't install in 15.5.

Once installed and restarted, you need to make a startup script:

Put it in /etc/init.d/sybase, edit the SERVER and SYBASE vars at the top, then do:

```

update-rc.d sybase defaults

```

Here's the script:

```

#!/bin/sh
#
# Startup script for Sybase ASE
# 
# description: Sybase Adaptive Server Enterprise
# is a SQL database server.
# processname: dataserver
  

SYBASE=/home/sybase
SERVER=HLAGH
  

# Source environment variables.
. $SYBASE/SYBASE.sh
  

# Find the name of the script
NAME=`basename $0`
  

# For SELinux we need to use 'runuser' not 'su'
if [ -x /sbin/runuser ]
then
	SU=runuser
else
	SU=su
fi
  

start() {
	SYBASE_START=$"Starting ${NAME} service: "
	$SU sybase -c ". $SYBASE/SYBASE.sh; $SYBASE/$SYBASE_ASE/install/startserver \
-f $SYBASE/$SYBASE_ASE/install/RUN_${SERVER} > /dev/null"
	ret=$? 
	if [ $ret -eq 0 ]
	then
		echo "$SYBASE_START Success."
	else
		echo "$SYBASE_START Failed!"
              exit 1
	fi
}
  

stop() {
	echo -n $"Stopping ${NAME} service: "
	$SU sybase -c ". $SYBASE/SYBASE.sh; isql -S $SERVER -U sa -P '' < \
$SYBASE/$SYBASE_ASE/upgrade/shutdown.sql > /dev/null"
	ret=$?
	if [ $ret -eq 0 ]
	then
		echo "Success."
	else
		echo "Failed!"
		exit 1
	fi
}
  

restart() {
	stop
	start
}
  

case "$1" in
  

	start)
		start
		;;
	stop)
		stop
		;;
	restart)
		restart
		;;
	*)
		echo $"Usage: $0 {start|stop|restart}"
		exit 1
esac
exit 0

```


Now you can start, stop, and restart the sybase db using this command:
```

/etc/init.d/sybase start
/etc/init.d/sybase stop
/etc/init.d/sybase restart

```

Now, once the db runs, you will want to have a way to access the GUI...

The GUI is located in:
```

/opt/sybase/shared/sybcentral600/

```


To start it, you need to do this:
```

export SYBROOT="/opt/sybase/"
export SYBASE_JRE6="/usr/lib/jvm/jdk1.6.0_20_-sun/jre/"

```

where /opt/sybase is the sybase installation directory, and SYBASE_JRE6 is the path to your java jre. The jre is not installed by default on Linux, you need to download it from java.com and execute the installer. Once it is installed, you can search the JRE directory by doing:
```

updatedb
locate jre

```


Then you can start the GUI with:
```

/opt/sybase/shared/sybcentral600/scjview.sh

```

And by the way, the servername is not the servername you enter at installation, it's actually the hostname, but without \servername...


The command line tool seems not to work, whatever.
(
> 
Using locale name "en_US.utf8" defined in environment variable LANG
Locale name "en_US.utf8" doesn't exist in your /opt/sybase/locales/locales.dat file
An error occurred when attempting to allocate localization-related structures.

)

---

### Post by WitchCraft on 2010-12-19
Horrya, installing Sybase just became "a lot easier" with Maverick:


Additional to the steps mentioned before, you need to do this:

Add a user called sybase, but with administrative privileges...:
```

useradd --non-unique --create-home --uid 0 --home /home/sybase --password YOURLONGPASSWORDHERE sybase  

```


Then you need to add sybase shared libraries to the library path:
```

gedit /etc/ld.so.conf.d/sybase.conf

```


```

# Sybase needs you
/opt/sybase/OCS-15_0/lib3p
/opt/sybase/ASE-15_0/lib

```

Afterwards, you have to update the paths:
```

/sbin/ldconfig

```

Note that if you install x64, you need /opt/sybase/OCS-15_0/lib3p64 instead of /opt/sybase/OCS-15_0/lib3p


And make sure your system's hostname doesn't contain a character not in a-Z or 1-9 or _ such as '-'...

And, because on maverick, this is the jre:
```

SYBASE_JRE6="/usr/lib/jvm/java-6-sun-1.6.0.22/jre"

```


It's better to use the symlink to the latest jre:
```

SYBASE_JRE6="/usr/lib/jvm/java-6-sun/jre"

```

---

### Post by WitchCraft on 2012-01-07
Addendum:

Works like a breeze in 11.10

To get ODBC working, you must add 
```
/opt/sybase/DataAccess64/ODBC/lib
```
to 
```
/etc/ld.so.conf.d/
```
(assuming you use the 64 bit version, else it's/opt/sybase/DataAccess)

Or you can copy its content to
```
/usr/lib/odbc
```

and add 
```
/usr/lib/odbc
```
to the library path, once and for all.




```
gedit /etc/ld.so.conf.d/sybaseodbc.conf
```

and add file-content
```
# ODBC libraries
/usr/lib/odbc
```

then do 
```
/sbin/ldconfig
```


The ASE driver entry in /etc/odbcinst.ini  is

```
[Adaptive Server Enterprise]
Description = Sybase ODBC Driver
;Driver = /opt/sybase/DataAccess/ODBC/lib/libsybdrvodb.so
Driver = /opt/sybase/DataAccess64/ODBC/lib/libsybdrvodb.so
Setup =
FileUsage = -1
CPTimeout =
CPReuse =

```

```

[Sybase_pubs2]
Description = Sybase ODBC Data Source
Driver = Adaptive Server Enterprise
UserID = YourUserName
Password = YourPassword
Server = YourHostName
Port = 5000
Database = pubs2
UseCursor = 1

```

You can then test the connection using isql (from package unixodbc)
```

isql Sybase_pubs2
SELECT * FROM authors

```

If you get a isql error message, use -v to get more information on the error.
You might get a 'driver file not found' error, although the driver file is there, with the proper permissions.


To find out what the problem is, you can use ldd to find out what's wrong
```

ldd /opt/sybase/DataAccess/ODBC/lib/libsybdrvodb.so
linux-gate.so.1 => (0x003b6000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x001f5000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x009e2000)
libstdc++-libc6.2-2.so.3 => not found
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00edc000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x001f9000)
/lib/ld-linux.so.2 (0x00e67000)

```

In this case libstdc++-libc6.2-2.so.3 is not present.
And you need to install the appropriate version of the libstdc++ runtime.
In this case:
```

apt-get install libstdc++6-4.6-dev

```

---

