---
title: "Please help secure my vsftp server"
date: 2011-04-21
forum: Security
---

### Post by Tolein on 2011-04-21
I have setup vsftpd and I would like to secure it with using ssl/tls. I have searched all over google but I can't seem to come up with a good walkthrough. I create my key with this command.
[root@vps] openssl req -x509 -nodes -days 365 -newkey rsa:1024 \  -keyout /etc/ssl/private/vsftpd.pem \  -out /etc/ssl/private/vsftpd.pem

After creating my key I add this to the end of the vsftpd.conf file.
When I try to restart the service I get an message that says unknown instance.
I'm hoping to get this working with FireFTP. Can any of you vsftpd experts that
have set this up before please help me. I can't seem to find a clear solution and
it is frustrating. Thanks in advance.

ssl_enable=YES  allow_anon_ssl=NO  force_local_data_ssl=NO  force_local_logins_ssl=NO  ssl_tlsv1=YES  ssl_sslv2=NO  ssl_sslv3=NO  rsa_cert_file=/etc/ssl/private/vsftpd.pem

---

### Post by Lars Noodén on 2011-04-22
[FTPS is not SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS)

If you have OpenSSH already installed then you already have SFTP access and don't need to fiddle with vsftp.  vsftp is a fine program but it is still FTP.  FTP is a tried and proven technology which  just turned 40 years old last week.  However, it is inherently insecure and wrapping it in SSL/TLS is hard.  

Another advantage of SFTP is that you can use [regular clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) for upload and download.

---

