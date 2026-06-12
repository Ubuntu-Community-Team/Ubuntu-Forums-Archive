---
title: "vsftpd problems"
date: 2011-02-05
forum: Server Platforms
---

### Post by random_id on 2011-02-05
I am having some problems getting vsftpd up and running.  I use to have it working fine to do FTPS, but I can't get it work now.  I have installed it on a new home server running 10.10

The first issue is that I can't get the program started.  Despite my tweaking of the conf file, I am getting a return of "unable to bind to ipv4..." When I try to run it, and then it immediately closes.  I figured that I could try to remove and reinstall it, but now I can't remove it.  I am getting error codes when I attempt to remove it with apt-get or synaptic.

I guess my first question is how do I remove vsftpd if I can't do it with apt-get remove or synaptic.  My other question, does anyone know what the issue is with not starting do to the "bind with ipv4" problem.

In the end, I just need to get some sort of FTPS working so I can use a new Eye-Fi card to automatically upload via FTP to my home server.

Thanks for your help.

---

### Post by random_id on 2011-02-05
Well, I was able to figure some stuff out.  I messed around with apt-get, then I finally went a little crazy and started deleting every file I could find entitled vsftp*.  I then reinstalled and things are working.  
Once I got it working, I gradually built up the conf file little by little.  I was able to keep making modifications and restarting the service.  Each time I checked the status to ensure that it was still running.

Now I can log in with FTPS, but only with my admin username.  I did add some more users to the user file for vsftpd, but those logins fail.  
Is there something else I need to add users to the vsftpd? 
Thanks

---

### Post by random_id on 2011-02-08
I finally got everything up and running.  In case anyone cares, setting up vsftpd for Eye-Fi was a pain.  I assume it had nothing to do with vsftpd and everything to do with Eye-Fi ftp abilities. 
In case anyone cares, I am going to post some of my vsftpd.conf file that I needed to enable for the Eye-Fi to work.  This is not the complete conf file.  The rest of it was pretty default.  This was just the stuff I needed to get Eye-Fi and FTPES working.

```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
pasv_enable=YES
pasv_addr_resolve=YES
pasv_address=<ddns.ddns.xxx>
pasv_min_port=47000
pasv_max_port=47100
pasv_promiscuous=NO
port_enable=YES
port_promiscuous=NO
require_ssl_reuse=NO


```

---

### Post by pushdakota on 2012-08-17
Thank for your posting, helped me getting my vsftpd up on a 12.04 - 32 bit machine.

Some issues I ran into:
The default vsftpd.cong points to a SSL cert that didn't exist on my machine, I had to create one with openssl. I created one with 2048 bits that works for me:
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem

Second, 

My complete config file below (that is working with FTPS for Eye-fi, but currently NOT for Filezilla - not a problem for me as I only use the ftp to get photos from Eye-fi)


grep -v "#" vsftpd.conf

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
log_ftp_protocol=NO
connect_from_port_20=YES
chroot_local_user=YES
chroot_list_enable=NO
local_root=/home
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
debug_ssl=YES
listen_port=1121
force_dot_files=YES
pasv_enable=YES
pasv_addr_resolve=YES
pasv_address=my.own.dyndns.name.here
pasv_min_port=47000
pasv_max_port=48000
pasv_promiscuous=NO
port_enable=YES
port_promiscuous=NO
require_ssl_reuse=NO

---

