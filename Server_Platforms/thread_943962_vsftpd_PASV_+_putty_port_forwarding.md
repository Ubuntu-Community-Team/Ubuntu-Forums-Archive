---
title: "vsftpd PASV + putty port forwarding"
date: 2008-10-10
forum: Server Platforms
---

### Post by Shwick2 on 2008-10-10
I'm trying to set up a secure ftp transfer between my linux machine and my internet gateway running ubuntu 8.04.

I have vsftpd installed but I can't get PASV connection to work with putty.  My ubuntu firewall blocks everything except ssh.  

From my windows XP machine I establish a connection with putty to my ubuntu machine.  I have putty forward local port 21(windows machine) to 127.0.0.1:21(ubuntu machine).

This works sort of.  I use the ftp client from windows command line to connect to 127.0.0.1 21, which forwards me to port 21 on the ubuntu machine and allows me to connect/login.

Then after I enter "quote PASV" and try a "dir" command it hangs.  In vsftpd.conf I had added lines pasv_max_port=21 and pasv_min_port=21 so that the ftp server would tell the windows ftp client to use port 21 for data transfers.

I then added "pasv_address=127.0.0.1" to vsftpd.conf, thinking vsftp was telling the windows ftp client to try and connect to something other than localhost, and vsftpd wouldn't start, it said I had to edit 2 files.

I already have sftp working with psftp.exe, but I'd like one entry point into my system and psftp doesn't load bash.bashrc, so I want ftp through ssh to work.

See this site for PASV ftp: [http://www.slacksite.com/other/ftp.html](http://www.slacksite.com/other/ftp.html)

---

### Post by lykwydchykyn on 2008-10-10
You may want to check your syslog or vsftpd's log (not sure of the exact file, it'd be in /var/log somewhere) for errors.  I don't *think* you can set the PASV port to 21, I believe it has to be a range of ports in the unprivileged range (>1023) and you may need two of them (maybe not though).

Try changing your pasv port range to just one port over 1023, and tunnel that port as well.  If that doesn't work, try a range of two ports and tunnel them both.

---

### Post by Shwick2 on 2008-10-14
Ok I decided to ditch the port forwarding and just get it working normally first.  I got it working by opening my local interface through iptables.

In vsftpd.conf I specified a port range of 55000 to 55100 for PASV ports, but vsftpd doesn't use that range.  

Using wireshark I captured ftp packets and saw vsftpd sent PASV ports 62237 and 58847 for two different ftp sessions.

Why is it not using the specified range?


Here is a non-commented copy of vsftpd.conf.

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
pasv_max_port=55000
pasv_min_port=55100
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
log_ftp_protocol=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

---

### Post by lykwydchykyn on 2008-10-15
It may be a bit confused by you specifying a min_port that is higher than the max_port, but that's just a guess.

---

### Post by Shwick2 on 2008-10-15
Thanks that's exactly what the problem was, it's working now.

---

