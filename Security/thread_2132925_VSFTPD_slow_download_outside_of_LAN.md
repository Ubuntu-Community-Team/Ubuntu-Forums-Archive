---
title: "VSFTPD slow download outside of LAN"
date: 2013-04-06
forum: Security
---

### Post by mantas1 on 2013-04-06
Hello all. I have VSFTP up and ruining on ubuntu 10.04. It works great inside LAN, however when it comes to using it outside i have some problems. If i try to connect from filezila i get the listing and if i try to download it shows it will take forever to receive a file which is larger then 1mb, if one is less its ok. When i try to download from explorer i get time out error. I use passive mode, here is my vsftpd.conf:
[FONT=arial]listen=YES[/FONT]
[FONT=arial]anonymous_enable=no[/FONT]
[FONT=arial]local_enable=YES[/FONT]
[FONT=arial]write_enable=YES[/FONT]
[FONT=arial]local_umask=022[/FONT]
[FONT=arial]dirmessage_enable=YES[/FONT]
[FONT=arial]xferlog_enable=YES[/FONT]
[FONT=arial]log_ftp_protocol=yes[/FONT]
[FONT=arial]pasv_enable=YES[/FONT]
[FONT=arial]virtual_use_local_privs=YES[/FONT]
[FONT=arial]pasv_min_port=2000[/FONT]
[FONT=arial]pasv_max_port=2010[/FONT]
[FONT=arial]connect_from_port_20=NO[/FONT]
[FONT=arial]chroot_local_user=YES[/FONT]
[FONT=arial]secure_chroot_dir=/var/run/[/FONT][FONT=arial]vsf[/FONT][FONT=arial]tpd[/FONT]
[FONT=arial]pam_service_name=vsftpd-[/FONT][FONT=arial]virtua[/FONT][FONT=arial]l[/FONT]
[FONT=arial]rsa_cert_file=/etc/ssl/certs/[/FONT][FONT=arial]s[/FONT][FONT=arial]sl-cert-snakeoil.pem[/FONT]
[FONT=arial]rsa_private_key_file=/etc/ssl/[/FONT][FONT=arial]private/ssl-cert-snakeoil.key[/FONT]
[FONT=arial]hide_ids=YES[/FONT]
[FONT=arial]user_config_dir=/etc/vsftp/[/FONT][FONT=arial]vsf[/FONT][FONT=arial]tpd_user_conf[/FONT]
[FONT=arial]dual_log_enable=YES[/FONT]
[FONT=arial]guest_enable=YES[/FONT]
[FONT=arial]guest_username=ftp[/FONT]
[FONT=arial]local_root=/var/vsftp[/FONT]
If i switch to active mode it does work with filzilla, but then i cant login wia explorer. Maybe somebody has any ideas?

---

