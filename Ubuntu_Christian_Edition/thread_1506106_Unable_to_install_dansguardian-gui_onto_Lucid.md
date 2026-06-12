---
title: "Unable to install dansguardian-gui onto Lucid"
date: 2010-06-10
forum: Ubuntu Christian Edition
---

### Post by smandoli on 2010-06-10
Found 2-week-old post from David_KT requesting for testing:  **Ubuntu CE Lucid Repository is ready** ... Hope this helps.  

Note I am trying to install dansguardian-gui but _not_ Ubuntu CE, for although I love the Bible and the local church, I find most of the CE packages don't appeal to me.  

Install Lucid Lynx on desktop PC using CD
Run all updates from Update Manager
Run:  
```
sudo wget http://ubuntuce.com/
repos/Ubuntu_CE/apt/sources.list.d/lucid_i386.list 
-O /etc/apt/sources.list.d/ubuntuce.list; 
sudo apt-get update && sudo apt-get install dansguardian-gui
```
OUTPUT FROM TERMINAL: (There is more, this seemed like the most interesting part)
```
Setting up dansguardian (2.10.1.1-1really2.9.9.7-2ubuntu1) ...
Warning: The home dir /var/log/dansguardian you specified already exists.
Adding system user `dansguardian' (UID 116) ...
Adding new group `dansguardian' (GID 124) ...
Adding new user `dansguardian' (UID 116) with group `dansguardian' ...
The home directory `/var/log/dansguardian' already exists.  
   Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/log/dansguardian' does not belong to the user you are currently creating.
update-rc.d: warning: dansguardian start runlevel arguments (2 3 4 5) 
   do not match LSB Default-Start values (2 3 5)
update-rc.d: warning: dansguardian stop runlevel arguments (0 1 6) 
   do not match LSB Default-Stop values (0 6)
   DansGuardian has not been configured!  Please edit 
   /etc/dansguardian/dansguardian.conf manually then 
   rerun this script.
Setting up tinyproxy (1.8.1-3) ...
Starting tinyproxy: tinyproxy.
Setting up dhcp3-server (3.1.3-2ubuntu3) ...
Generating /etc/default/dhcp3-server...
 * Starting DHCP server dhcpd3                                                                    
 * check syslog for diagnotics    [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.
Setting up dansguardian-gui (2.5) ...
 Adding system startup for /etc/init.d/ubuntu_ce_firewall ...
   /etc/rc0.d/K91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc1.d/K91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc6.d/K91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc2.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc3.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc4.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc5.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```
[COLOR="Purple"]OPEN dansguardian-gui[/COLOR]
[LIST]
[*]transp. proxy OFF
[*]TInyproxy ON
[*]DG OFF 
[*]Inet Sharing OFF
[*]Firefox proxy is unlocked
[/LIST]
[COLOR="Purple"]Run Autoconfigure/Reset
Run Start Dansguardian[/COLOR]
"tinyproxy is already enabled, please file a bug if it is disabled on boot."
"Starting dansguardian ..."
"dansguardian is already enabled, please file a bug if it is disabled on boot."
Now unable to browse Internet.  "Connecting to ...", eventual time-out
[COLOR="Purple"]Run Stop Dansguardian[/COLOR]
Now Internet is available again.  
In conclusion, I am not able to run dansguardian at this point.  
I note that tinyproxt.conf is located /etc/ instead of /etc/tinyproxy/.
Can you suggest anything to enable me to use DG-gui?  Trouble shooting steps?

---

### Post by david_kt on 2010-06-10
> **smandoli said:**
> 
[COLOR="Purple"]Run Stop Dansguardian[/COLOR]
Now Internet is available again.  
In conclusion, I am not able to run dansguardian at this point.  
I note that tinyproxt.conf is located /etc/ instead of /etc/tinyproxy/.
Can you suggest anything to enable me to use DG-gui?  Trouble shooting steps?

Could try to run "Start Dasnguardian" and then see whether # transp. proxy, TInyproxy and DG all ON now.

DK

---

### Post by smandoli on 2010-06-10
Gee, David ... it works now.   Start Dansguardian ... no funny errors ... pages refresh fine, [test page]("http://sites.google.com/site/stupidicus/test") is blocked.
 * transp. proxy ON
 * TInyproxy ON
 * DG ON
 * Inet Sharing OFF
 * Firefox proxy is unlocked (will try locking next I guess)
I dunno why the improvement, but thanks much.  I'm very grateful for DG and your installer.  
----------------------------------

---

