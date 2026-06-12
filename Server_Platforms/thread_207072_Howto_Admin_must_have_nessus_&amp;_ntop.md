---
title: "Howto: Admin must have: nessus &amp; ntop"
date: 2006-07-01
forum: Server Platforms
---

### Post by alamba on 2006-07-01
Hi All,

Here’s a mini-howto on installing nessus and ntop - 2 tools I believe are a must have for any network admin. Nessus is a vulnerability assessment tool and a great way of checking open ports, uninstalled patches and older versions of software running on the end-user systems in a network. Ntop is a graphical network monitoring tool that can server a dual purpose - network overview on a daily basis and management reporting.

Nessus = Vulnerability Assessment Tool ([http://www.nessus.org/download/](http://www.nessus.org/download/))
Ntop = Network monitoring tool ([http://www.ntop.org/](http://www.ntop.org/))

Nessus Installation Steps:

On Ubuntu Dapper System (Nessus Server)
1	sudo apt-get install nessusd
2	nessus-mkcert
3	nessus-adduser
4	cd /etc/init.d
5	./nessusd start

A quick check can be done by running $nmap localhost and checking if port 1241 is being listened on by nessus.

On NessusWX (Windows) Client

Click on Communications>Connect
Enter the server name/IP address and the username/password for the user you created above
Click on connect

Click on Session>New
Add target host, subnet or addresses
Check and set the variables in the tabs as deemed necessary by you.

Double click the session name you created above and you’re off scanning.

PS: There’s a bit about registering your nessusd server with Tenable to get plugin’s which I have not covered here. Please check the nessus website to enable this.


Ntop Installation Steps:

1	sudo apt-get install ntop
2	cd /usr/sbin/
3	./ntop

Create the admin user and password.

4	cd /etc/init.d/
5	./ntop restart

A quick check can be done by running $nmap localhost and checking if port 3000 is being listened on by ntop. Fire up your web browser on any machine and navigate to the url: http://<servername/ip address>:3000 to view ntop.

---

### Post by alamba on 2006-07-09
Edit: Ntop installation step 3 should read as:
./ntop -u ntop
Post configuring it should run fine from the init scripts.

A

PS: Thanks Michael for pointing this out @ [www.ubuntuos.com](www.ubuntuos.com)

---

### Post by RShadow on 2006-07-09
The one thing I have never understood about nessus is does nessus have to be installed on the machine you are probing? (because that doesn't make alot of sense to me) but all information I've looked into suggest that it is.

---

### Post by alamba on 2006-07-10
Abolutely not buddy. Nessus server is installed on a 'central' server which then probes the targets in the network. The client that connects into the nessus server for starting the probe, configuration, etc. can be on the same machine as the nessus server or can be a seperate (e.g. IT Admin's) machine. 

A

---

### Post by hebetude on 2007-09-19
If you install ntop like listed above you will severely break it.  Then have to kill -9 ntop and reinstall it.   This will work (in feisty):  
sudo apt-get install ntop -y 
sudo ntop --set-admin-password  
sudo ntop -u ntop -d

---

### Post by alamba on 2007-09-20
Thanks mate. You solution does look more elegant. I'm not sure if this was available at the time the post was written. As for breaking the installation, I still have the same installation running since then with no problems whatsoever. Ofcourse, that might just be luck.

A

---

### Post by hebetude on 2007-09-20
Well I did it the way described and ntop couldn't access it's own files.  Even to the point that it couldn't set the admin-password so it was pretty fubar on my system.

The steps I listed are on the ubuntu wiki for ntop

---

### Post by jrichardson on 2007-11-29
Not sure what I am missing here. 

Originally installed using webmin Install Package from APT: ntop. Seemed to install fine but when I executed ntop I got: 


> ntop
Thu Nov 29 10:38:28 2007  NOTE: Interface merge enabled by default
Thu Nov 29 10:38:28 2007  Initializing gdbm databases
Thu Nov 29 10:38:28 2007  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: Can't be writer
Thu Nov 29 10:38:28 2007  Possible solution: please use '-P <directory>'
Thu Nov 29 10:38:28 2007  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Thu Nov 29 10:38:28 2007  CLEANUP[t3055457984]: ntop caught signal 2
Thu Nov 29 10:38:28 2007  THREADMGMT[t3055457984]: ntop RUNSTATE: SHUTDOWN(7)
Thu Nov 29 10:38:28 2007  CLEANUP[t3055457984] catching thread is MAIN
Thu Nov 29 10:38:28 2007  CLEANUP: Running threads
Thu Nov 29 10:38:28 2007  CLEANUP: Locking purge mutex (may block for a little while)
Thu Nov 29 10:38:28 2007  CLEANUP: Locked purge mutex, continuing shutdown
Thu Nov 29 10:38:28 2007  CLEANUP: Continues
Thu Nov 29 10:38:28 2007  PLUGIN_TERM: Unloading plugins (if any)
Thu Nov 29 10:38:28 2007  CLEANUP: Clean up complete
Thu Nov 29 10:38:28 2007  THREADMGMT[t3055457984]: ntop RUNSTATE: TERM(8)
Thu Nov 29 10:38:28 2007  ===================================
Thu Nov 29 10:38:28 2007          ntop is shutdown...        
Thu Nov 29 10:38:28 2007  ===================================


Made sure that /var/lib/ntop/prefsCache.db is writable
Made sure that /usr/local/var/ntop exists and is writable.

so then I uninstalled ntop and used the CLI command: sudo apt-get install ntop -y 

Seemed to install OK, no errors. When I try to run ntop I get the same errors.

any ideas? What is the use of the -P <directory>

---

### Post by stanz on 2007-12-19
"man ntop",  read and scroll...its a biggie. 
"-p | --protocols", is well doc'ed.

---

### Post by wormser on 2007-12-24
> **hebetude said:**
> If you install ntop like listed above you will severely break it.  Then have to kill -9 ntop and reinstall it.   This will work (in feisty):  
sudo apt-get install ntop -y 
sudo ntop --set-admin-password  
sudo ntop -u ntop -d

That worked for me.  The first post did not.

---

### Post by psytek7 on 2008-01-17
#to change interfaces edit:
/var/lib/ntop/init.cfg

#change
INTERFACES="eth1"

#to eth0, eth2, eth3.. etc.
#note ppp0 doesn't seem to work or at least kills my internet connection

---

