---
title: "Provider 1&amp;1/Telekom is SPYING !!! Protection ?"
date: 2018-04-01
forum: Security
---

### Post by michael488 on 2018-04-01
Suckers from my provider 1&1/Telekom access my system (Ubuntu 16044) and watching, what I am doing, block websites, limit the bandwidth (sometimes from 100MB down to 300KB).
 I catched them with netstat !
 What else do I have to do, to stop these suckers from accessing my system ?
 That is, what I already did:  
 1. Enabled firewall, block ports (in and out):  1, 22, 23, 25, 98, 111, 123, 177, 512,513,514, 540,543,544, 2111, 6000:6010, 10000
 2. create file ftpusers in /etc and put all users from passwd in it
 3. create file nologin in /etc and actvate it in pam-login
 4. lightdm.conf : [XDMCPServer] enabled=false ; [VNCServer] enabled=false ;  
 [Seat:*] greeter-show-remote-login=false and allow-guest=false
 5. removed nopasswdlogin from pam-lightdm
 6. Removed (purge) : openssh-client, telnet, vino, remmina, libfreerdp*, libwinpr*,
 cups-browsed, pptp-linux, libvncclient*, libssh*, libsmbclient*, libsnmp*, libnm-glib-vpn1
 7. login.defs : CONSOLE    console
 8. access.conf :  -:root:ALL EXCEPT LOCAL ; -:wheel:ALL EXCEPT LOCAL .win.tue.nl ;
 -:adm:ALL EXCEPT LOCAL ; -:ALL:ALL
 9. pam-login : auth   required  pam_nologin.so ; auth   required    pam_access.so
      auth   required    pam_deny.so ;  account    required    pam_nologin.so
      account    required       pam_access.so ;  account    required    pam_deny.so
      password   required   pam_access.so ; session   required    pam_access.so
 leave the rest as it was
 10. pam-other : set auth, account, password, session to pam_deny.so
 11. /etc/systemd/logind.conf : set NautoVTs  and ReserveVT   to 0
 12. create a new file: portmap in /etc/default  insert: OPTIONS="-i 127.0.0.1"  
 13. hosts.deny : ALL:ALL
 
 
 I think, that there is an other way to access the X-Server or the display-manager or something like that, that easily bypass firewall and all other things !?
 Thanks for your help.

---

### Post by QIII on 2018-04-01
Hello!

Can you describe exactly what you found with netstat that suggests that you are being attacked?

---

### Post by TheFu on 2018-04-04
How does removing client software help? 

If you don't want to be hacked, don't run plain FTP, VNC, or XDMCP.  Those are huge security risks.
Don't allow internet access using passwords for ssh, scp, sftp, rsync, or any other ssh-based connections. Also, blocking the world from ssh would be smart, while only allowing the specific IPs you come from and nowhere else. Plus using fail2ban can't hurt.

I'm not convinced that anyone has hacked into the system at this point.  netstat can easily be misinterpreted.  But both VNC and plain FTP are commonly hacked, so definitely remove those.  Best to post the netstat stuff you believe is showing the issue.

hosts.deny only works for tcp-wrapper enabled listeners.  It isn't universal across the OS.
If you want to secure an Ubuntu-based system, there are sticky threads in the *security* subforum for reference.

---

