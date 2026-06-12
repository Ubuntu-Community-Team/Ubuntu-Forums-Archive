---
title: "MySQL does not start on boot..."
date: 2010-05-11
forum: Server Platforms
---

### Post by pezball on 2010-05-11
Ubuntu server 10.04 comes with a new event based startup system, and I wonder if that can be responsible for this problem. The server has been upgraded from 9.10...
 
On reboot mysql does not always manage to start... /var/log/mysql/error.log has info similar to this:
 
100511 19:05:00 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
100511 19:05:00 [ERROR] Do you already have another mysqld server running on port: 3306 ?
100511 19:05:00 [ERROR] Aborting
 
So apparently port 3306 is not 100% unused when mysql tries to open it... or somehow network connections are not ready... even if mysql start is supposed to wait for 'net-device-up' and 'local-filesystems' according to /etc/init/mysql.conf...
 
This does not happen on all reboots... I am supposed to be able to start it manually with command 'start mysql' but that does not seem to work also... when i try start it again, it says mysql is running.. but no databases can be reached and mysqld is not active... reboot and good luck is all that helps... :confused:
 
As far as I know there are no firewalls installed, at least none I have manually configured and it has worked with no problems on 9.10... so this new upstart thing seems responsible... it simply does not let mysql wait until it can start in good way... that also explains why it's a random problem... if all starts happen when and if there is free processor time, it does not always start things in the same order on every reboot...
 
The key here is port 3306, or whatever port mysql is configured to use... the upstart system simply needs delay the start until the port is 100% free and available for the system to use... I have no clue if that can be done in any easy way... 
 
I assume similar problems might occur for other processes which rely on certain ports to be free on startup... cos this new startup can probably not make sure certain ports are available before it lets a process start...
 
mysql simply starts long before its needed resources are free for use...
 
it's something worth thinking about in future development of the new startup... simply waiting for 'net-device-up' is obviously no guarantee for success, since there may be other processes which scans some ports on upstart and happen to be busy with the port when another process needs it... an alternative is to make mysql more patient and retry the port several times before giving up...

---

### Post by pezball on 2010-05-24
This issue is fixed!!! (i hope... fingers and toes crossed)  :P
 
I added IFACE=eth0 after net-device-up in start script for mysql... cos unlike default mysql install, my mysql talks outside localhost... so it requires a "real world" network contact... waiting for the network adapter should solve the problem... :)

---

