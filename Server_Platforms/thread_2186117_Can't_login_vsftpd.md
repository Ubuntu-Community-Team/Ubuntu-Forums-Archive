---
title: "Can't login vsftpd"
date: 2013-11-05
forum: Server Platforms
---

### Post by thishalll on 2013-11-05
I recently installed Ubuntu server on a desktop.

After I installed it, I forwarded port 22 to the desktop's port 22 in my router setup to use remote ssh connection.
[COLOR=#000000][FONT=Lucida Grande]
Then I installed vsftpd and edited vsftpd.conf like this:
[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]listen=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]anonymous_enable=NO[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]local_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]write_enable=YES[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]dirmessage_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]use_localtime=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]xferlog_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]connect_from_port_20=YES[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]chroot_local_user=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]chroot_list_file=/etc/vsftpd.chroot_list[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]secure_chroot_dir=/var/run/vsftpd/empty[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]pam_service_name=vsftpd[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]rsa_cert_file=/etc/ssl/private/vsftpd.pem[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]tcp_wrappers=YES[/FONT][/COLOR]


And I saved it, added my account to 'chroot_list_file.'

But, when I try to connect my server, it gives error msg like:


[COLOR=#000000][FONT=Lucida Grande]220 Welcome to the server![/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]FEAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]211-Features:[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]EPRT[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]EPSV[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]MDTM[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PASV[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]REST STREAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]SIZE[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]TVFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]UTF8[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]211 End[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]USER [My account][/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]331 Please specify the password.[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]PASS ********[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]500 OOPS: [/FONT][/COLOR]


The thing is if I allow to connect for anonymous account, I can connect to my server.

[FONT=Lucida Grande, Trebuchet MS, Helvetica, Arial, sans-serif][COLOR=#000000]I think the way I added the user to my server could be a problem.

My server's firewall is off and I forwarded port 21 as well.

Please help me![/COLOR][/FONT]

---

### Post by Lars Noodén on 2013-11-06
If you are just looking for an easy, secure way to transfer files using SFTP, I would recommend using the package OpenSSH-server instead.  Uninstall vsftpd and install openssh-server and SFTP should then work with no further configuration.  That would be over port 22 as you intend.

However if you are really looking to provide anonymous downloads, then you really will need vsftpd.

---

### Post by houstonbofh on 2013-11-06
I think you have some confusion on ports. The ssh protocol is on 22 and FTP is on port 21, and depending on if you are active or passive, many more ports.

---

