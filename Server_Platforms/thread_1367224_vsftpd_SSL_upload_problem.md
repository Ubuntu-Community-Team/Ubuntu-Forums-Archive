---
title: "vsftpd SSL upload problem"
date: 2009-12-29
forum: Server Platforms
---

### Post by alfredovera on 2009-12-29
Using FireFTP.

I am having trouble uploading anything to my server when using ssl. Here is my vsftpd.conf:


listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to blah FTP service.
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#
ssl_enable=YES
force_local_logins_ssl=YES
force_local_data_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

Using these settings when attempting to upload anything it just hangs. In the status log at the bottom of FireFTP I see the transfer being attempted but it does nothing. I eventually get this error.

"522 Data connections must be encrypted."

I can see the directory structure on the server side. If I try to delete anything on the server side I get.

"550 Delete operation failed."

If I comment out the last section of the vsftpd.conf (the last 6 lines with the ssl settings) I can upload just fine. Can anyone help me? What I'm doing wrong?

---

### Post by Lars Noodén on 2009-12-29
If your goal is a secure connection to upload and download from your server using normal software, then SFTP is what you want.  FTPS is, as you are finding out, difficult to set up and, as you might see from searching this forum, difficult to maintain.  

There is nothing wrong with the program vsftp, it's just that FTP itself is not secure, and FTP+SSL is only a little better but far more complicated.  

So consider taking a step back and checking your goals.  If you don't need read-only, Anonymous FTP for download-only transfers, then uninstall vsftp.  

The openssh-server package has a built-in sftp-server subsystem.  It uses the SFTP protocol, which is more secure than FTPS, and is **far** easier to install, configure and maintain.  Ensure that the package openssh-server is installed, then connect from the client using Filezilla,  Konqueror, Dolphin, Nautilus, Cyberduck, Fugu, or Fetch.  That's it.

---

