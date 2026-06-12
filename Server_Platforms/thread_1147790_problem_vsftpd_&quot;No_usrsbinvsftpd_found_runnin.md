---
title: "problem vsftpd &quot;No /usr/sbin/vsftpd found running; none killed&quot;"
date: 2009-05-03
forum: Server Platforms
---

### Post by ahmedbj on 2009-05-03
Hello
when i tried to restart my vsftpd server i've got this error 
* Stopping FTP server: vsftpd   
  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd                              [ OK ] 

and this is what in my vsftpd.conf:
> 
#Pour configurer vsFTPd à écouter en mode StandAlone
listen = YES

# Pour autoriser les connexions annonymes
anonymous_enable = YES
    #Pour ne pas autoriser les users anon à écrir dans le dir FTP
        anon_mkdir_write_enable = NO
    #Spécifier le dossier FTP des user anon
        anon_root = /etc/ftp
    #Interdir aux users anon d'envoyer des fichiers
        anon_upload_enable = NO
    #Autoriser les users anon de télécharger les fichier du dossier anon_root
        anon_world_readable_only = YES
    #o_O
        ftp_username = ftp
    #Pour que les anon ne saisissent pas de mot de passe
        no_anon_passwd = NO
    #o_O  give anonymously uploaded files permissions
        anon_umask=022
    #Pour question de sécuriter en interdit toute opération d'écriture
        write_enable=NO
        anon_other_write_enable=NO


ftp_banner = "Bienvenu dans le serveur FTP de ahmed"

#Pour autoriser la connexion des utilisateur locaux
local_enable = YES
    #Autoriser les cmd FTP SITE CHMOD pour les local users
        chmod_enable = YES
    #Pour chrooter les local user dans leurs dossiers perso
        chroot_local_user = YES
    #o_O
        local_umask = 000

#Pour visioner la liste des dir
dirlist_enable = YES

#Téléchargement des fichiers autorisés
download_enable = YES

#Pour avoir un monitoring ( les user connecté )
setproctitle_enable = YES

####################
# Option numérique #
###################

#Spécifie la durée donnée à un client utilisant une connexion passive pour se connecter
accept_timeout = 60

#Spécifie le taux de transfert de données maximal, exprimé en octets par seconde, pour les utilisateurs anonymes
anon_max_rate = 0

#Spécifie la durée maximale exprimée en secondes, donnée à un client utilisant un mode actif pour répondre à une connexion de données.
CONNECT_TIMEOUT = 60

#Spécifie la durée maximale exprimée en secondes, pendant laquelle les transferts de données peuvent s'arrêter. 
#Une fois cette durée écoulée, la connexion au client distant est fermée.
data_connection_timeout = 60

# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES

#Spécifie le port sur lequel vsftpd doit être à l'écoute de connexions réseau. 
listen_port = 21

#Spécifie le nombre maximal de clients autorisés à se connecter simultanément au serveur lorsqu'il tourne en mode autonome.
#Toute connexion client supplémentaire provoquerait un message d'erreur.
max_clients = 20

#Spécifie le nombre maximal de clients autorisés à se connecter depuis l'adresse IP source. 
max_per_ip = 2

   ##########################
  #configurer vsftp pour   #
 #les connection internet #
##########################

#Activer le mode passive
pasv_enable = YES

#Vérifier que la machine qui a demandé la connexion au serveur est bien la même que celle qui demande
#à recvoir les données
pasv_promicious = No 

#Spécifie le port le plus bas possible qui est envoyé au client FTP pour des connexions en mode passif.
pasv_min_port = 40000

#Spécifie le port le plus max possible qui est envoyé au client FTP pour des connexions en mode passif.
pasv_min_port = 40100

#@ ip ou domaine.com avec pasv_addr_resolve = YES
pasv_adress = 192.168.0.222


port_promicious = NO


# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#


# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#

# You may fully customise the login banner string:
ftpd_banner=Welcome to ahmed FTP service.

# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
#rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


use_localtime=YES

# SSL options

ssl_enable=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
#allow_anon_ssl=NO
#force_local_data_ssl=YES
force_local_logins_ssl=YES

# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/certs/vsftpd.pem
rsa_cert_file=/etc/ssl/certs/vsftpd.pem


and when i try to connect to ftp server i got this error : ftp: connect: Connection refused
can someone help me
thank you

---

### Post by ahmedbj on 2009-05-04
can any one help me please

---

### Post by LiQuidAiR on 2009-05-10
Try using sudo vsftpd

This usually will tell you if there is an error with the vsftpd.conf file.

You can always check to see if vsftpd started correctly by using netstat -ano.  This will show all active sockets.  If you see 0.0.0.0:21 and its status is set to listening than you're half way home.

---

