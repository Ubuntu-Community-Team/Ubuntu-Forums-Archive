---
title: "FTP pam failed"
date: 2012-05-08
forum: Server Platforms
---

### Post by blmain on 2012-05-08
Hi

The FTP virtuual pam authentiication failed
I working on a AMD Athlon 64 with Linux Ubuntu Server 64bit

If I allow Local and anonymous, bothe can connect

/etc/vsftpd.conf
listen=YES
tcp_wrappers=YES
connect_from_port_20=YES
ftpd_banner= »Bienvenue sur le serveur FTP» 
anonymous_enable=YES
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
#anon_other_write_enable=YES
local_enable=YES
#guest_enable=YES
#guest_username=userftp11 
#guest_username=vsftpd
virtual_use_local_privs=YES
pam_service_name=vsftpd
#userlist_enable=YES
rsa_cert_file=/etc/ssl/private/vsftpd.pem
user_config_dir=/etc/vsftpd/vsftpd_user_conf

The pam file are not in /lib/security
bertrand@BLSERVER:/lib/security$ ls -l
total 96
-rw-r--r-- 1 root root 10296 févr. 25 17:23 pam_ck_connector.so
-rw-r--r-- 1 root root 14504 avril 18 18:11 pam_ecryptfs.so
-rw-r--r-- 1 root root 43480 avril 12 16:09 pam_gnome_keyring.so
-rw-r--r-- 1 root root 22616 oct.  17  2010 pam_pwdfile.so

They look to be in /lib/x86_64-linux-GNU/security
bertrand@BLSERVER:/lib/x86_64-linux-gnu/security$ ls
pam_access.so     pam_issue.so      pam_nologin.so     pam_tally2.so
pam_cap.so        pam_keyinit.so    pam_permit.so      pam_tally.so
pam_debug.so      pam_lastlog.so    pam_pwhistory.so   pam_time.so
pam_deny.so       pam_limits.so     pam_rhosts.so      pam_timestamp.so
pam_echo.so       pam_listfile.so   pam_rootok.so      pam_umask.so
pam_env.so        pam_localuser.so  pam_securetty.so   pam_unix.so
pam_exec.so       pam_loginuid.so   pam_selinux.so     pam_userdb.so
pam_faildelay.so  pam_mail.so       pam_sepermit.so    pam_warn.so
pam_filter.so     pam_mkhomedir.so  pam_shells.so      pam_wheel.so
pam_ftp.so        pam_motd.so       pam_stress.so      pam_winbind.so
pam_group.so      pam_namespace.so  pam_succeed_if.so  pam_xauth.so

So I try to setup the vsftpd pam file as
/etc/pam.d/vsftpd
# Standard behaviour for ftpd(8).
auth    required    pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required    pam_shells.so

#auth required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd/login
#auth required pam_userdb.so db=/etc/vsftpd/login
#account required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd/login
#account required pam_userdb.so db=/etc/vsftpd/login

#auth required /lib/security/pam_userdb.so db=/etc/vsftpd/login
#account required /lib/security/pam_userdb.so db=/etc/vsftpd/login

#auth required pam_pwdfile.so pwdfile /etc/ftpd.passwd
#account required pam_permit.so

#auth required /lib/x86_64-linux-gnu/security/pam_pwdfile.so pwdfile /etc/ftpd.passwd
#account required /lib/x86_64-linux-gnu/security/pam_permit.so

#%PAM-1.0 Local user
#auth required /lib/x86_64-linux-gnu/security/pam_listfile.so item=user #sense=deny file=/etc/vsftpd.ftpusers onerr=succeed
#auth required pam_stack.so service=system-auth
#auth required /lib/x86_64-linux-gnu/security/pam_shells.so
#account required pam_stack.so service=system-auth
#session required pam_stack.so service=system-auth

#%PAM222222-1.0 Virtual User
#auth required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd_login
#account required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd_login

with this pam setup, Local user can connect and Anonymous can connect.
Statut :    Connexion établie, attente du message d'accueil...
Réponse :    220 »Bienvenue sur le serveur FTP»
Commande :    USER bertrand
Réponse :    331 Please specify the password.
Commande :    PASS *********
Réponse :    230 Login successful.
Commande :    SYST
Réponse :    215 UNIX Type: L8
Commande :    FEAT
Réponse :    211-Features:
Réponse :     EPRT
Réponse :     EPSV
Réponse :     MDTM
Réponse :     PASV
Réponse :     REST STREAM
Réponse :     SIZE
Réponse :     TVFS
Réponse :     UTF8
Réponse :    211 End
Commande :    OPTS UTF8 ON
Réponse :    200 Always in UTF8 mode.
Statut :    Connecté
Statut :    Récupération du contenu du dossier...
Commande :    PWD
Réponse :    257 "/home/bertrand"
Commande :    TYPE I
Réponse :    200 Switching to Binary mode.
Commande :    PASV
Réponse :    227 Entering Passive Mode (192,168,5,10,104,145).
Commande :    LIST
Réponse :    150 Here comes the directory listing.
Réponse :    226 Directory send OK.
Statut :    Calcul du décalage horaire du serveur...
88888Commande :    MDTM datashared
Réponse :    213 20120407100031
Statut :    Décalage du fuseau horaire : Serveur : 0 secondes, Local : 7200 secondes. Différence : 7200 secondes.
Statut :    Contenu du dossier affiché avec succès

Anonymous can connect also
Statut :    Connexion établie, attente du message d'accueil...
Réponse :    220 »Bienvenue sur le serveur FTP»
Commande :    USER anonymous
Réponse :    331 Please specify the password.
Commande :    PASS **************
Réponse :    230 Login successful.
Commande :    SYST
Réponse :    215 UNIX Type: L8
Commande :    FEAT
Réponse :    211-Features:
Réponse :     EPRT
Réponse :     EPSV
Réponse :     MDTM
Réponse :     PASV
Réponse :     REST STREAM
Réponse :     SIZE
Réponse :     TVFS
Réponse :     UTF8
Réponse :    211 End
Commande :    OPTS UTF8 ON
Réponse :    200 Always in UTF8 mode.
Statut :    Connecté
Statut :    Récupération du contenu du dossier...
Commande :    PWD
Réponse :    257 "/"
Commande :    TYPE I
Réponse :    200 Switching to Binary mode.
Commande :    PASV
Réponse :    227 Entering Passive Mode (192,168,5,10,234,213).
Commande :    LIST
Réponse :    150 Here comes the directory listing.
Réponse :    226 Directory send OK.
Statut :    Contenu du dossier affiché avec succès


If I enable guest and so disable anonymous

/etc/vsftpd.conf
listen=YES
tcp_wrappers=YES
connect_from_port_20=YES
ftpd_banner= »Bienvenue sur le serveur FTP» 
#anonymous_enable=YES
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
#anon_other_write_enable=YES
local_enable=YES
guest_enable=YES
#guest_username=userftp11 
#guest_username=vsftpd
virtual_use_local_privs=YES
pam_service_name=vsftpd
#userlist_enable=YES
rsa_cert_file=/etc/ssl/private/vsftpd.pem
user_config_dir=/etc/vsftpd/vsftpd_user_conf

/etc/pam.d/vsftpd
# Standard behaviour for ftpd(8).
auth    required    pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

# Standard pam includes
@include common-account
@include common-session
@include common-auth
#auth    required    pam_shells.so

auth required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd/login
#auth required pam_userdb.so db=/etc/vsftpd/login
account required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd/login
#account required pam_userdb.so db=/etc/vsftpd/login

#auth required /lib/security/pam_userdb.so db=/etc/vsftpd/login
#account required /lib/security/pam_userdb.so db=/etc/vsftpd/login

#auth required pam_pwdfile.so pwdfile /etc/ftpd.passwd
#account required pam_permit.so

#auth required /lib/x86_64-linux-gnu/security/pam_pwdfile.so pwdfile /etc/ftpd.passwd
#account required /lib/x86_64-linux-gnu/security/pam_permit.so

#%PAM-1.0 Local user
#auth required /lib/x86_64-linux-gnu/security/pam_listfile.so item=user #sense=deny file=/etc/vsftpd.ftpusers onerr=succeed
#auth required pam_stack.so service=system-auth
#auth required /lib/x86_64-linux-gnu/security/pam_shells.so
#account required pam_stack.so service=system-auth
#session required pam_stack.so service=system-auth

#%PAM222222-1.0 Virtual User
#auth required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd_login
#account required /lib/x86_64-linux-gnu/security/pam_userdb.so db=/etc/vsftpd_login

I have created login.db
bertrand@BLSERVER:/etc/vsftpd$ ls -l
total 24
-rw-r--r-- 1 root root 12288 mai    5 08:27 login.db
-rw------- 1 root root    39 mai    5 08:22 login.txt
-rw------- 1 root root    39 mai    4 07:03 login.txt~
drwxr-xr-x 2 root root  4096 mai    5 08:25 vsftpd_user_conf

I restart vsftpd service
bertrand@BLSERVER:~$ sudo service vsftpd stop
[sudo] password for bertrand: 
vsftpd stop/waiting
bertrand@BLSERVER:~$ sudo service vsftpd start
vsftpd start/running, process 4678

But local and guest cannot connet
Local user
Statut :    Connexion établie, attente du message d'accueil...
Réponse :    220 »Bienvenue sur le serveur FTP»
Commande :    USER bertrand
Réponse :    331 Please specify the password.
Commande :    PASS *********
Réponse :    530 Login incorrect.
Erreur :    Erreur critique
Erreur :    Impossible d'établir une connexion au serveur

Guest / Virtual User cannot connect
Statut :    Connexion établie, attente du message d'accueil...
Réponse :    220 »Bienvenue sur le serveur FTP»
Commande :    USER gilles
Réponse :    331 Please specify the password.
Commande :    PASS *********
Réponse :    530 Login incorrect.
Erreur :    Erreur critique
Erreur :    Impossible d'établir une connexion au serveur

Thanks for your help

---

