---
title: "HOWTO: Install Oracle Database 11gR2 (86_64) on Ubuntu 11.10 (64-bit)"
date: 2012-04-19
forum: Tutorials
---

### Post by mehrdad_v on 2012-04-19
Hello,

Here is a quick guide to installing Oracle Database 11gR2 (64-bit) on Ubuntu 11.10 (64-bit):

**Install the required  software packages:**

```
sudo apt-get install libaio1
sudo apt-get install libaio-dev
sudo apt-get install unixODBC
sudo apt-get install unixODBC-dev
sudo apt-get install expat
sudo apt-get install sysstat
sudo apt-get install libelf-dev
sudo apt-get install elfutils
sudo apt-get install lsb-cxx
sudo apt-get install pdksh
sudo apt-get install libstdc++5
sudo apt-get install ia32-libs
sudo apt-get install ksh
sudo apt-get install lesstif2
sudo apt-get install alien
sudo apt-get install gcc
sudo apt-get install gawk
sudo apt-get install binutils
sudo apt-get install gawk
sudo apt-get install x11-utils
sudo apt-get install rpm
sudo apt-get install alien
sudo apt-get install lsb-rpm
sudo apt-get install libmotif3
sudo apt-get install lesstif2
sudo apt-get install openssh-server
```The Oracle installation expects certain utilities and libraries in different locations:

```
sudo ln -s /usr/bin/basename /bin/basename
sudo ln -sf /bin/bash /bin/sh
sudo ln -s /usr/bin/rpm /bin/rpm
sudo ln -s /usr/bin/awk /bin/awk
sudo ln -s /usr/lib/x86_64-linux-gnu/libc_nonshared.a /usr/lib64/ 
sudo ln -s /usr/lib/x86_64-linux-gnu/libpthread_nonshared.a /usr/lib64/ 
sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /usr/lib64/ 
sudo ln -s /lib/x86_64-linux-gnu/libgcc_s.so.1 /lib64
sudo ln -s /usr/lib/i386-linux-gnu/libpthread_nonshared.a /usr/lib/libpthread_nonshared.a
```[B]

Create a kernel parameter file:[/B]

```
sudo cat - >> /etc/sysctl.d/60-oracle.conf
```(then cut & paste the following)
 
```
# Oracle 11gR2 kernel parameters
fs.aio-max-nr=1048576
fs.file-max=6815744
net.ipv4.ip_local_port_range=9000 65500
net.core.rmem_default=262144
net.core.rmem_max=4194304
net.core.wmem_default=262144
net.core.wmem_max=1048586
kernel.sem=250 32000 100 128
kernel.shmmax=2147483648
```(then press Ctrl-d to write the file)
 
*Note: kernel.shmmax = max possible value, e.g. size of physical RAM.*

Verify: 

```
sudo cat /etc/sysctl.d/60-oracle.conf
```Load new kernel parameters: 
 
```
sudo service procps start
```Verify: 

```
sudo sysctl -q fs.aio-max-nr
-> fs.aio-max-nr = 1048576
```[B]

Oracle Account and Directories[/B]:

```
sudo groupadd oinstall
sudo groupadd dba
sudo useradd -m -g oinstall -G dba oracle
sudo usermod -s /bin/bash oracle
sudo passwd oracle
sudo groupadd nobody
sudo usermod -g nobody nobody
```Verify: 

```
sudo id oracle
-> uid=1001(oracle) gid=1001(oinstall) groups=1001(oinstall),1002(dba)
```Create Oracle Directories, i.e.: /u01/app for Oracle software and /u02/oradata for database files:

```
sudo mkdir -p /u01/app/oracle
sudo mkdir -p /u01/app/oraInventory
sudo mkdir -p /u02/oradata
sudo chown oracle:oinstall /u01/app/oracle
sudo chown oracle:oinstall /u01/app/oraInventory
sudo chown oracle:oinstall /u02/oradata
sudo chmod 750 /u01/app/oracle
sudo chmod 750 /u01/app/oraInventory
sudo chmod 750 /u02/oradata
sudo -s
mkdir /etc/rc.d
for i in 0 1 2 3 4 5 6 S ; do ln -s /etc/rc$i.d /etc/rc.d/rc$i.d ; done
exit
```Allow the Oracle user to use the "sudo" command:

```
sudo usermod -G admin oracle
```[B]

Modify Oracle account shell limits:[/B]

Make a backup of the original file:

```
sudo cp /etc/security/limits.conf /etc/security/limits.conf.origina
``````
sudo cat - >> /etc/security/limits.conf
```(then cut & paste the following)

```
#Oracle 11gR2 shell limits:
oracle soft nproc 2048
oracle hard nproc 16384
oracle soft nofile 1024
oracle hard nofile 65536
```(then press Ctrl-d to write the file)

Verify: 

```
sudo cat /etc/security/limits.conf
```**Add the following line to the /etc/pam.d/login file:**

```
session required pam_limits.so
```Use an editor like vi or gedit and add the following to /etc/profile:

```
if [ "$USER" = oracle ]; then
   if [ $SHELL = "/bin/ksh" ]; then
      ulimit -p 16384
      ulimit -n 65536
   else
      ulimit -u 16384 -n 65536
   fi
fi
```[B]

ORA-00845: MEMORY_TARGET[/B]

[I]Oracle 11gR2 under Ubuntu 11.10 will result in "ORA-00845: MEMORY_TARGET not support on this system" either at Oracle database startup or during the initial installation. Ubuntu 11.10 uses a new version of the "systemd" system and session manager and has migrated away from /dev/shm and other common directories in favor of /run.

There are several ways how to address the problem. You can either enable /dev/shm shared memory, or change the default memory management of Oracle 11g from AMM (Automatic Memory Management) to ASMM (Automatic Shared Memory Management) as it was in used the previous 10g version. Since AMM is one of the new features of 11g, the following will show you how to make to make AMM work.[/I]

Login as root:

```
sudo su -
```Cut & paste the following into the command prompt (not a text editor):

```
cat > /etc/init.d/oracle-shm <<-EOF
#! /bin/sh
# /etc/init.d/oracle-shm
#
#
case "\$1" in
  start)
    echo "Starting script /etc/init.d/oracle-shm"
    # Run only once at system startup
    if [ -e /dev/shm/.oracle-shm ]; then
      echo "/dev/shm is already mounted, nothing to do"
    else
      rm -f /dev/shm
      mkdir /dev/shm
      mount -B /run/shm /dev/shm
      touch /dev/shm/.oracle-shm
    fi
    ;;
  stop)
    echo "Stopping script /etc/init.d/oracle-shm"
    echo "Nothing to do"
    ;;
  *)
    echo "Usage: /etc/init.d/oracle-shm {start|stop}"
    exit 1
    ;;
esac
#
### BEGIN INIT INFO
# Provides:          oracle-shm
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6 
# Short-Description: Bind /run/shm to /dev/shm at system startup.
# Description:       Fix to allow Oracle 11g use AMM.
### END INIT INFO
EOF
```Install the oracle-shm init script:

```
chmod 755 /etc/init.d/oracle-shm
update-rc.d oracle-shm defaults 01 99
```Restart the system and verify the success:

```
sudo cat /etc/mtab | grep shm
->none /run/shm tmpfs rw,nosuid,nodev 0 0
->/run/shm /dev/shm none rw,bind 0 0
```**The Oracle Universal Installer (OUI) requires X-windows. There are two fundamentally different ways to open a GUI application: **
[I]
- Remote Session
- Server Console

VNC/Remote Desktop: 
- Shares the screen of the Server Console.
- Applications are using the X-server on the server.

SSH with X-forwarding:
- Applications use the the X-server running on your client's desktop. 
[/I]
Using SSH with X-Forwarding:

```
ssh -X oracle@*your_server_ip_address*
```Or use VNC using an SSH tunnel:

```
ssh -A -L 5902:localhost:5902 oracle@your_server_ip_address
```Then open a VNC session to localhost:5902.

**Intiates Oracle 11gR2 installation:**

```
./runInstaller -ignoreSysPrereqs
```[B]

Errors during installation:
[/B]3 Errors will occur during installation ( at the linking process ), in order to make them correct below changes must be done on various make files and then click on retry:

vi $ORACLE_HOME/sysman/lib/ins_emagent.mk:

```
LDFLAGS=-Wl,--copy-dt-needed-entries -o $@ $(LDPATHFLAG)$(LIBHOME) $(LDPATHFLAG)$(PRODLIBHOME) $(LDPATHFLAG)$(LIBHOME)stubs/ $(LDFLAGS_ARCH) $(LDARCH_FLAGS)

replace:

$(SYSMANBIN)emdctl:
        $(MK_EMAGENT_NMECTL)
with:

$(SYSMANBIN)emdctl:
        $(MK_EMAGENT_NMECTL) -lnnz11
```vi $ORACLE_HOME/rdbms/lib/env_rdbms.mk

```
ORACLE_LINKER=$(ADE_DEL_FILE_CMD) $(PURECMDS) gcc -Wl,--no-as-needed $(OLAPPRELINKOPTS) $(LDFLAGS) $(COMPSOBJS)
replace:

KFED_LINKLINE=$(LINK) $(S0MAIN) $(SSKFEDED) $(SKFEDPT)  \
with:

KFED_LINKLINE=$(LINK) $(S0MAIN) -Wl,--no-as-needed $(SSKFEDED) $(SKFEDPT)  \

replace:

KFOD_LINKLINE=$(LINK) $(S0MAIN) $(SSKFODED) $(SKFODPT) $(KFODOBJ) \
with:

KFOD_LINKLINE=$(LINK) $(S0MAIN) -Wl,--no-as-needed $(SSKFODED) $(SKFODPT) \

replace:

KFNDG_LINKLINE=$(LINK) $(S0MAIN) $(SSKFNDGED) $(SKFNDGPT) $(KFNDGOBJ) \
with:

KFNDG_LINKLINE=$(LINK) $(S0MAIN) -Wl,--no-as-needed $(SSKFNDGED) $(SKFNDGPT) $(KFNDGOBJ) \

replace:

AMDU_LINKLINE=$(LINK) $(S0MAIN) $(SSKFMUED) $(SKFMUPT) \
with:

AMDU_LINKLINE=$(LINK) $(S0MAIN) -Wl,--no-as-needed $(SSKFMUED) $(SKFMUPT) \

replace

ORACLE_KERNEL_LIBS=$(LLIBSKGTR) $(LLIBPERFSRV) $(NAETTOBJS) $(CONFIG)\
         $(SPOBJS) $(LLIBSERVER) $(LLIBODM) $(LLIBSAGE) \
with

ORACLE_KERNEL_LIBS=$(LLIBSKGTR) $(LLIBPERFSRV) $(NAETTOBJS) $(CONFIG)\
        $(SPOBJS) -Wl,--no-as-needed $(LLIBSERVER) $(LLIBODM) $(LLIBSAGE) \
```vi $ORACLE_HOME/bin/genorasdksh

```
LD="gcc -Wl,--no-as-needed -shared -Wl,-relax ${LDOBJSZ} -L$OLIB -L$OLIB/stubs"

replace

$LD $LD_RUNTIME $LD_OPT $LD_OUT $LD_SELF_CONTAINED $BASE_LIB \

with 

$LD $LD_RUNTIME -Wl,--no-as-needed $LD_OPT $LD_OUT $LD_SELF_CONTAINED $BASE_LIB \
```vi $ORACLE_HOME/srvm/lib/env_srvm.mk
Insert at line 90:

```
PRODUCT=srvm
```vi $ORACLE_HOME/srvm/lib/ins_srvm.mk

```
GETCRSHOME_LINKLINE=$(LINK) $(LDPATHFLAG)$(RDBMSLIB) $(CDEBUG) $(OPT) $(GETCRSHOME_OBJ1) \
        -Wl,--start-group $(OCRLIBS_DEFAULT) -Wl,--end-group $(OCRLIBS_DEFAULT) $(LLIBCLNTSH) $(LINKLDLIBS)
```vi $ORACLE_HOME/network/lib/env_network.mk

```
TNSLSNR_LINKLINE=$(LINK) $(TNSLSNR_OFILES) $(LINKTTLIBS) -Wl,--no-as-needed $(LLIBONS) \
                 $(LOCALNETLIBS) $(MATHLIB) $(TNSLSNR_THREADLIB)
```[I]Or you can simply download my files from link below and replace the files:

[https://rapidshare.com/files/1834029122/Oracle_Make_Files.tar.gz](https://rapidshare.com/files/1834029122/Oracle_Make_Files.tar.gz) [/I]
[B]
Creating startup/init script:[/B]

Update the following script in /etc/init.d/oracledb:

```
#!/bin/bash
#
# /etc/init.d/oracledb
#
# Run-level Startup script for the Oracle Listener and Instances
# It relies on the information on /etc/oratab

export ORACLE_BASE=/u01/app/oracle
export ORACLE_HOME=/u01/app/oracle/product/11.2.0/dbhome_1
export ORACLE_OWNR=oracle
export PATH=$PATH:$ORACLE_HOME/bin

if [ ! -f $ORACLE_HOME/bin/dbstart -o ! -d $ORACLE_HOME ]
then
echo "Oracle startup: cannot start"
exit 1
fi

case "$1" in
start)
# Oracle listener and instance startup
echo -n "Starting Oracle: "
su $ORACLE_OWNR -c "$ORACLE_HOME/bin/lsnrctl start"
su $ORACLE_OWNR -c "$ORACLE_HOME/bin/dbstart $ORACLE_HOME"
su $ORACLE_OWNR -c "$ORACLE_HOME/bin/emctl start dbconsole"
touch /var/lock/oracle
echo "OK"
;;
stop)
# Oracle listener and instance shutdown
echo -n "Shutdown Oracle: "
su $ORACLE_OWNR -c "$ORACLE_HOME/bin/emctl stop dbconsole"
su $ORACLE_OWNR -c "$ORACLE_HOME/bin/lsnrctl stop"
su $ORACLE_OWNR -c "$ORACLE_HOME/bin/dbshut $ORACLE_HOME"
rm -f /var/lock/oracle
echo "OK"
;;
reload|restart)
$0 stop
$0 start
;;
*)
echo "Usage: `basename $0` start|stop|restart|reload"
exit 1
esac

exit 0
```Run the following commands as a root:

```
chmod a+x /etc/init.d/oracledb
update-rc.d oracledb defaults 99
```To make the Oracle start at the system boot in /etc/oratab change the 'N' on orcl line to Y as follows:

```
orcl:/home/mehrdad/oracle/product/11.2.0/dbhome_1:Y
```I hope it could help you through installation steps :)

Many thanks to:

[https://forums.oracle.com/forums/thread.jspa?messageID=9596361](https://forums.oracle.com/forums/thread.jspa?messageID=9596361)
[http://blog.craigpoma.com/2010/07/installing-oracle-11gr2-on-fedora-13.html](http://blog.craigpoma.com/2010/07/installing-oracle-11gr2-on-fedora-13.html)
[http://lesscode.blogspot.co.uk/2010/04/install-oracle-11g-r2-on-ubuntu-104.html](http://lesscode.blogspot.co.uk/2010/04/install-oracle-11g-r2-on-ubuntu-104.html)
[http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex/](http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex/)
[http://blog.arkzoyd.com/2011/11/oracle-database-11g-and-ubuntu-1110.html](http://blog.arkzoyd.com/2011/11/oracle-database-11g-and-ubuntu-1110.html)
[http://whoisroot.wordpress.com/2012/03/15/instalando-o-oracle-11g-release-2-no-ubuntu-11-10/](http://whoisroot.wordpress.com/2012/03/15/instalando-o-oracle-11g-release-2-no-ubuntu-11-10/)

---

### Post by hma.istsupport on 2012-07-22
Hi All,

I am trying the installation on 12.04. At the start I am getting the pre-reqs failed window as attached.  I checked the packages and all of them seemed to be a higher version than the expected. Still the errors are thrown.

When I ignore and proceed I get around 10 make file linking errors. Has this something to do with the incompatible packages ?

Thanks in advice guys..

adarsh

---

### Post by bonebreaker on 2012-08-09
Hello mehrdad_v,

If you copy and paste information you should have at least the courtesy to give credit and name the source.

[https://forums.oracle.com/forums/thread.jspa?threadID=2301639](https://forums.oracle.com/forums/thread.jspa?threadID=2301639)

Regards.

---

### Post by techexpert666 on 2012-08-22
That was quite useful. Googling about it showed up another good link. But it is for Red Hat.

[http://www.expertslogin.com/linux-administration/oracle-11gr2-installation-on-redhat-linux-5/](http://www.expertslogin.com/linux-administration/oracle-11gr2-installation-on-redhat-linux-5/)

---

### Post by MordicusEtCubitus on 2012-09-05
Hi,

If this can help you will find here a [howto install Oracle 11g on ubuntu]("http://www.makina-corpus.org/blog/howto-install-oracle-11g-ubuntu-linux-1204-precise-pangolin-64bits") 12.04 (64 bits) which works also for 11.10 describing a lot of possible issues and their work around.

Best regards,

---

### Post by mehrdad_v on 2013-01-17
> **bonebreaker said:**
> Hello mehrdad_v,

If you copy and paste information you should have at least the courtesy to give credit and name the source.

[https://forums.oracle.com/forums/thread.jspa?threadID=2301639](https://forums.oracle.com/forums/thread.jspa?threadID=2301639)

Regards.
Hey Bonebreaker,

You are right, my fault. But I didn't mean it that way, just wanted to share it with people.
Anyway, I have gathered these from different blogs and here is the links to all of them:

[HTML]http://thripal.blogspot.com/2011/07/oracle-11g-r2-on-ubuntu-1104.htm
http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex
http://lesscode.blogspot.com/2010/04/install-oracle-11g-r2-on-ubuntu-104.html
http://mikesmithers.wordpress.com/2010/03/14/installing-oracle-11gr2-on-ubuntu-9-10[/HTML]

---

### Post by pagotisrinivas on 2013-12-25
hi

i am unable to install following packages in my ubuntu 13.10---- 64 bit 

sudo apt-get install ia32-libs
sudo apt-get install lesstif2
sudo apt-get install lsb-rpm
sudo apt-get install lesstif2

please find the error screenshots and suggest me 

thanks in advance ...

---

### Post by mohamed5 on 2014-04-23
> **pagotisrinivas said:**
> hi

i am unable to install following packages in my ubuntu 13.10---- 64 bit 

sudo apt-get install ia32-libs
sudo apt-get install lesstif2
sudo apt-get install lsb-rpm
sudo apt-get install lesstif2

please find the error screenshots and suggest me 

thanks in advance ...

same here :(
any help??

---

