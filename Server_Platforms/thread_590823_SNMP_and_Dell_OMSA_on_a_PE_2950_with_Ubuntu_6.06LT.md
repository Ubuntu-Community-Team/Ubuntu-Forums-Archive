---
title: "SNMP and Dell OMSA on a PE 2950 with Ubuntu 6.06LTS server."
date: 2007-10-25
forum: Server Platforms
---

### Post by usaindp1776 on 2007-10-25
Hello everyone:

I am an Ubuntu/Linux newbie.  I have installed Ubuntu 6.06 LTS Server on a Dell PowerEdge 1855 Blade.  I have installed OMSA and SNMP on the server but I can't figure out how to configure it to send SNMP traps to our server monitoring software running on another server.

Can anyone give me some pointers?  Any help of greatly appreciated.

---

### Post by usaindp1776 on 2007-10-29
Ok.  I finally figured part of it out anyway.  I now have snmp up and running and sending alerts to our monitoring software.  I saw some comments out on the net saying you should install snmp before omsa, so I removed omsa and installed it again.

This resynched something up because now I get traps initiated by OMSA.  The only problem is that the contents of the traps are empty.

---

### Post by gtdaqua on 2007-11-17
I have installed OMSA on my PE2970 Gutsy 64-bit. Cant get the web server turned on! 
How did u get urs working?

---

### Post by usaindp1776 on 2007-12-05
I installed it on a Dell PE 1855 blade.  I changed the post, but the thread title for some reason hasn't changed to reflect that.

Anyway, I never got the web server running.  I wasn't really looking for that anyway.  My goal was to get SNMP Traps sent to my server monitoring software elsewhere on the network.  I haven't had time lately to work on it so I'm still stuck at the same place that I was -- no information in the SNMP traps.

If I get this working (or the web server) I will post.  I would appreciate any ideas anyone has on the subject.

Thanks.

---

### Post by btmspox on 2007-12-07
On my 1955 Blade I haven't gotten to the SNMP part, nor have totally gotten the webserver working (it's running, but I can't login) but I did get the utilities working which is probably a big step. I think I had to start "/etc/init.d/dsm_om_connsvc" to get the webserver going on port 1311 via https.

There's a number of helpful people on the [linux-poweredge]("http://lists.us.dell.com/mailman/listinfo/linux-poweredge") list.

I've got a lot of notes and links on my [blog here]("http://loftninjas.org/blog/2007/12/dell-omsa-for-sas-raid-on-debian-etch.html").

The sara.nl folks are on the above mailing list and have some newer packages for different arch's [available]("ftp://ftp.sara.nl/pub/outgoing/dell/").

Bryan

---

### Post by oneloveamaru on 2008-05-12
The web interface will start up with /etc/init.d/dsm_om_connsvc start

If you want it to start automatically when you boot up, run this line without the quotes.

"/usr/sbin/update-rc.d dsm_om_connsvc start 20 2 3 4 5 . stop 19 0 1 6 . >/dev/nullssh"

To enable snmp to work with OMSA, you need to enable it. Run "/etc/init.d/dataeng enablesnmp".
This will add a line at the bottom of your /etc/snmp/snmpd.conf so OMSA can connect to SNMP via smux.

This is the line it adds. "smuxpeer .1.3.6.1.4.1.674.10892.1"

You still need to configure your snmpd.conf to allow connections to read the snmp. Here is a sample. NOTE: public is always the default community. For added security, change it to something else.


rwcommunity public 127.0.0.1
rocommunity public 127.0.0.1
rwcommunity public servername
rocommunity public servername
trapcommunity public
trapsink servername public
trapsink servername public
syscontact Root <root@localhost>
syslocation corp

Trapsink sends traps to that server, with the community string. I do localhsot AND the servers monitoring it. ro and rwcommunity is pretty self explanatory.

NOTE: Check your /etc/default/snmpd file and remove 127.0.0.1 from the line it's on. That is extra security so only localhost can read your snmp traps. Obviously you want others to read it, so make sure to remove it. When you are done, the line should look like this:

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid' <-- don't copy and paste this in, just delete 127.0.0.1 out of that line. You need the back tics and the forum format may change them.

Now do: /etc/init.d/snmpd restart
then a /etc/init.d/dataeng restart

That should get you working for 32bit users.

64bit users, keep going.

If you cannot log in at [https://servername:1311](https://servername:1311) and you keep getting log in, incorrect(and it should if you are running a 64 bit distro), you need to copy some files, as OMSA 5 uses PAM and not it's own authentication anymore.

Change /lib/security path to /lib32 in /etc/pam.d/omauth 
This is what omauth will look like afterwards

auth       required     /lib32/pam_unix.so nullok
auth       required     /lib32/pam_nologin.so
account    required     /lib32/pam_unix.so nullok


and copy from a 32bit install (a server running a 32bit ubuntu/debian distro) theses files :

 /lib/libsepol.so.1
 /lib/libselinux.so.1
 /lib/security/pam_unix.so
 /lib/security/pam_nologin.so

copy into /lib32 on your amd64 servers.

I just run these lines on the 32bit server, to copy over to my amd64 server.

scp /lib/security/libse* root@server:/lib32/

scp /lib/security/pam_* root@server:/lib32/

then edit the /etc/pam.d/omauth as described above.

after a ldconfig (run ldconfig) you should be able to pam login to the web interface at [https://server:1311](https://server:1311)

For snmp to work, I would restart a few services.

Do a /etc/init.d/snmpd restart
then a /etc/init.d/dataeng restart

If you don't have a 32 bit install, PM me, I could zip the files up and send them to you.

That should do it.

Good luck.

---

### Post by gtdaqua on 2008-05-13
Even if 'dataeng' is running, you need this to have Dell OMSA send snmp status to your NMS:

> 
sudo /etc/init.d/dataeng enablesnmp


You need this to get the web server running:

> 
sudo /etc/init.d/dsm_om_connsvc start


---

### Post by oneloveamaru on 2008-06-04
gtdaqua, what are you replying to? Four lines down in my post I have /etc/init.d/dataeng enablesnmp and I even said what it does.

---

