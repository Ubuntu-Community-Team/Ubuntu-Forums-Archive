---
title: "Ubuntu 11.04, likewise open, samba share and active directory"
date: 2011-09-20
forum: Server Platforms
---

### Post by twalbers on 2011-09-20
[FONT=Verdana][SIZE=2]Ok I have installed likewise open and joined my server to the active directory domain.  I can login to SSH using domain credentials but I cannot get to samba shares using domain credentials. 

Here is what I have done so far:

 [/SIZE][/FONT][FONT=Verdana][SIZE=2]**Install Likewise Open:**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Sudo apt-get install likewise-open likewise-open-gui[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]**Avahi will interfear with the FQDN resolution so do the following:**[/SIZE][/FONT]
**[FONT=Verdana][SIZE=2]Stop avahi-daemon as it interfears with FQDN[/SIZE][/FONT]**
[FONT=Verdana][SIZE=2]                sudo /etc/init.d/avahi-daemon stop[/SIZE][/FONT]

**[FONT=Verdana][SIZE=2]Edit /etc/avahi/avahi-daemon.conf[/SIZE][/FONT]**
[FONT=Verdana][SIZE=2]                sudo vi /etc/avahi/avahi-daemon.conf[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]                **Uncomment out the #domain-name=local  and replace with domain-name=.alocal**[/SIZE][/FONT]
**[FONT=Verdana][SIZE=2]Start avahi-daemon [/SIZE][/FONT]**
[FONT=Verdana][SIZE=2]                sudo /etc/init.d/avahi-daemon start[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
  **[FONT=Verdana][SIZE=2]Join the domain:[/SIZE][/FONT]**
    [FONT=Verdana][SIZE=2]sudo domainjoin-cli join domain.local admin[/SIZE][/FONT]
  
[FONT=Verdana][SIZE=2]**Set the default domain:** 
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]         sudo lwconfig assumedefaultdomain true[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]    ** Now reboot the machine.**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]A
[/SIZE][/FONT]
  
**[FONT=Verdana][SIZE=2]Add Active directory group to the Sudoers file[/SIZE][/FONT]**
[FONT=Verdana][SIZE=2]     Sudo vi /etc/sudoers[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]                %ADGroupname  ALL=(ALL) ALL[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
**[FONT=Verdana][SIZE=2]Create a symlink for likewise open[/SIZE][/FONT]**
  
[FONT=Verdana][SIZE=2][FONT=&quot]sudo mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.orig[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]sudo ln -s /etc/samba/secrets.tdb /var/lib/samba[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2]  
 [/SIZE][/FONT]   **[FONT=Verdana][SIZE=2][FONT=&quot]Next, edit [/FONT][FONT=&quot]/etc/samba/smb.conf[/FONT][FONT=&quot] changing: [/FONT][/SIZE][/FONT]**
[FONT=Verdana][SIZE=2][FONT=&quot]   workgroup = DOMAIN[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]   ...[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]   security = ads[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]   realm = DOMAIN.local[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]   ...[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]   idmap backend = lwopen[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]   idmap uid = 50-9999999999[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]   idmap gid = 50-9999999999[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2]  
 [/SIZE][/FONT]**[FONT=Verdana][SIZE=2][FONT=&quot]Restart samba for the new settings to take effect: [/FONT][/SIZE][/FONT]**
[FONT=Verdana][SIZE=2][FONT=&quot]sudo restart smbd[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]sudo restart nmbd[/FONT][/SIZE][/FONT]


What am I missing? :confused:


Thanks.

---

### Post by HermanAB on 2011-09-21
Maybe see this: 
[http://www.aeronetworks.ca/howtos/LinuxActiveDirectory.html](http://www.aeronetworks.ca/howtos/LinuxActiveDirectory.html)

---

### Post by twalbers on 2011-09-21
I will create another vm to give this a try as it doesn't appear to use Likewise open at all and I don't want to mess up what I have. 

Is there any way to do what I want using Likewise open or is that a lost cause?

Thanks.

---

### Post by koenn on 2011-09-21
the function of likewiseopen is similar to that of winvindd in Herman's tut (they might be related at the source code level); both should work

Herman's tut (or this: [http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm) ) might help you understand, test, and troubleshoot your setup, but you're right that it's better not to mix them (too much)

consider raising the lower bound in idmap uid = 50-9999999999 and 
idmap gid = 50-9999999999 to something pretty high to avoid these mapped uids/gids overlapping with existing linux accounts

you probably need to focus on samba config as apparently you successfully joined the domain (-> permissions, references to domain name, user names, valid users/groups, ....) but you might want to double check that, eg by using something like 'getent' to see if you can list domain accounts

---

### Post by twalbers on 2011-09-21
Ok.  I am a noob on linux but I am learning.

getent passwd <user> returns a line similar to this  user:x:73557210:735576577:User name:/home/likewise-open/Domain/user:/bin/bash

lw-enum-users returns all the users in the Active Directory.

What would you suggest for the uid and gid 10000?

Not sure if winbind is working but if I do wbinfo -u I only get local linux users not the domain users.

---

### Post by koenn on 2011-09-21
try 'getent passwd' without <user>; I expect you get a passwd-like list of domain users, which is good; it shows linux gets domain accounts in a format it understands (i.e. as if the came from /etc/passwd) and we can assume linux apps such as ssh and samba can use them. 
I suppose lw-enum-users  does something similar.

So, probably, it's your smb.conf that needs work. 
yes, 10000 for lower uid/gid sounds right to me. 

also, try DOMAIN.LOCAL (for realm) in all caps, Kerberos seems to like caps

other than that, define a share with minimal config, try to access it, and see what samba complains about (in its logs).  Keep adding fixes until it stops complaining.

---

### Post by twalbers on 2011-09-21
Changed the realm to All caps and upped the uid/gid.  restarted smbd and nmbd.  No luck logging into a share.
Here is the log file for the machine I was trying to connect on:
[2011/09/21 20:37:28.379062,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/09/21 20:37:28.379183,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/09/21 20:37:41.141564,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/09/21 20:37:41.141763,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

---

### Post by twalbers on 2011-09-21
running getent passwd returns passwords but they don't look like domain accounts.

---

### Post by twalbers on 2011-09-21
Here is the contents of my samba smb.conf
[global]

   workgroup = domain.local
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = ADS
   realm = DOMAIN.LOCAL
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   idmap backend = lwopen
   idmap uid = 10000-9999999999
   idmap gid = 10000-9999999999
   usershare allow guests = yes


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /media/cdrom
   guest ok = yes

---

### Post by twalbers on 2011-09-21
Not sure if this has anything to do with it but here is what I get when I do wbinfo -t
could not obtain winbind interface details!
could not obtain winbind domain name!
checking the trust secret for domain (null) via RPC call failed
Could not check secret

---

### Post by twalbers on 2011-09-22
Any other thoughts on this?

---

### Post by twalbers on 2011-09-27
Ok I finally got this working.  All I had to do was follow the instructions from Likewise Open and also install the package from thier website.  The Ubuntu Distro was missing a very important tool called 'samba-interop-install.  

The final solution was to remove the computer from the domain and uninstall likewise open.  Then download the package from the Likewise website, install, join the domain, change the default shell to /bin/bash.  Now reboot, edit smb.conf then run samba-interop-install.  

Bingo now it works brilliantly.  The steps above are not inclusive but a very broad stroke.  If you are having the same issues just follow the Likewise help.

---

