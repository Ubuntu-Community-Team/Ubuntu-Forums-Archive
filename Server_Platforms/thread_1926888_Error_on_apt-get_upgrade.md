---
title: "Error on apt-get upgrade"
date: 2012-02-17
forum: Server Platforms
---

### Post by Hyli on 2012-02-17
Hi,
apt-get upgrade on Ubuntu server 10.04 stopped working today.
update logs in english ;

```

administrateur@digihost:~$ sudo su - -c 'LANG=C apt-get upgrade'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common firefox-locale-en
  firefox-locale-fr libpng12-0 libvorbis0a libvorbisenc2 libvorbisfile3 python-lazr.restfulclient
  update-manager-core update-manager-kde
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4705kB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? 
tar: ./md5sums: Cannot open: Invalid argument
tar: ./postinst: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/apache2_2.2.14-5ubuntu8.8_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
tar: ./md5sums: Cannot open: Invalid argument
tar: ./postinst: Cannot open: Invalid argument
tar: ./preinst: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: ./prerm: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/apache2-mpm-prefork_2.2.14-5ubuntu8.8_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
tar: ./conffiles: Cannot open: Invalid argument
tar: ./postrm: Cannot open: Invalid argument
tar: ./md5sums: Cannot open: Invalid argument
tar: ./postinst: Cannot open: Invalid argument
tar: ./preinst: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/apache2.2-common_2.2.14-5ubuntu8.8_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
tar: ./md5sums: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/apache2.2-bin_2.2.14-5ubuntu8.8_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              tar: ./md5sums: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/apache2-utils_2.2.14-5ubuntu8.8_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              tar: ./md5sums: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/firefox-locale-en_10.0.2+build1-0ubuntu0.10.04.1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              tar: ./md5sums: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/firefox-locale-fr_10.0.2+build1-0ubuntu0.10.04.1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              tar: ./shlibs: Cannot open: Invalid argument
tar: ./postinst: Cannot open: Invalid argument
tar: ./postrm: Cannot open: Invalid argument
tar: ./md5sums: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libpng12-0_1.2.42-1ubuntu2.3_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              tar: ./postrm: Cannot open: Invalid argument
tar: ./md5sums: Cannot open: Invalid argument
tar: ./shlibs: Cannot open: Invalid argument
tar: ./postinst: Cannot open: Invalid argument
tar: ./symbols: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libvorbis0a_1.2.3-3ubuntu1.1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              tar: ./postrm: Cannot open: Invalid argument
tar: ./md5sums: Cannot open: Invalid argument
tar: ./shlibs: Cannot open: Invalid argument
tar: ./postinst: Cannot open: Invalid argument
tar: ./symbols: Cannot open: Invalid argument
tar: ./control: Cannot open: Invalid argument
tar: Exiting with failure status due to previous errors


```

Sorry my logs are in french.

```
administrateur@digihost:~$ sudo apt-get upgrade 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront mis à jour*:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common libpng12-0 update-manager-core update-manager-kde
8 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/3'644ko dans les archives.
Après cette opération, 4'096o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? 
tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./postinst : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/apache2_2.2.14-5ubuntu8.8_amd64.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./postinst : la fonction open a échoué: Argument invalide
tar: ./preinst : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: ./prerm : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/apache2-mpm-prefork_2.2.14-5ubuntu8.8_amd64.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
tar: ./conffiles : la fonction open a échoué: Argument invalide
tar: ./postrm : la fonction open a échoué: Argument invalide
tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./postinst : la fonction open a échoué: Argument invalide
tar: ./preinst : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/apache2.2-common_2.2.14-5ubuntu8.8_amd64.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/apache2.2-bin_2.2.14-5ubuntu8.8_amd64.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
Aucun rapport «*apport*» écrit car MaxReports a déjà été atteint
                                                                tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/apache2-utils_2.2.14-5ubuntu8.8_amd64.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
Aucun rapport «*apport*» écrit car MaxReports a déjà été atteint
                                                                tar: ./shlibs : la fonction open a échoué: Argument invalide
tar: ./postinst : la fonction open a échoué: Argument invalide
tar: ./postrm : la fonction open a échoué: Argument invalide
tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/libpng12-0_1.2.42-1ubuntu2.3_amd64.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
Aucun rapport «*apport*» écrit car MaxReports a déjà été atteint
                                                                tar: ./postinst : la fonction open a échoué: Argument invalide
tar: ./preinst : la fonction open a échoué: Argument invalide
tar: ./prerm : la fonction open a échoué: Argument invalide
tar: ./conffiles : la fonction open a échoué: Argument invalide
tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/update-manager-core_1%3a0.134.11.2_amd64.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
Aucun rapport «*apport*» écrit car MaxReports a déjà été atteint
                                                                tar: ./postinst : la fonction open a échoué: Argument invalide
tar: ./preinst : la fonction open a échoué: Argument invalide
tar: ./prerm : la fonction open a échoué: Argument invalide
tar: ./md5sums : la fonction open a échoué: Argument invalide
tar: ./control : la fonction open a échoué: Argument invalide
tar: Arrêt avec code d'échec à cause des erreurs précédentes
dpkg-deb: le sous-processus tar a retourné une erreur de sortie d'état 2
dpkg*: erreur de traitement de /var/cache/apt/archives/update-manager-kde_1%3a0.134.11.2_all.deb (--unpack)*:
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
Aucun rapport «*apport*» écrit car MaxReports a déjà été atteint
                                                                dpkg: impossible d'ouvrir «*/var/lib/dpkg/status*» pour écrire les informations de status: Argument invalide
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
Any idea?
Thanks

---

### Post by Bevlar on 2012-02-17
Hi I googled the error message: /usr/bin/dpkg returned an error code (2)

and it appears to be the same issue as this:

[http://askubuntu.com/questions/98157/getting-error-message-package-operation-failed](http://askubuntu.com/questions/98157/getting-error-message-package-operation-failed)

Hope this helps.

Please bear in mind I am no expert on anything Linux.
I won't be offended if you wait for a response from somebody more experienced : D

---

### Post by Hyli on 2012-02-17
Sorry but it doesnt looks like it the same issue.

---

### Post by ajgreeny on 2012-02-17
Sorry, my French is very poor, but it looks as though the md5sum of at least one apache package that apt has downloaded may be corrupt.

I suggest you run ```
sudo apt-get clean
``` to clear the cache of downloaded packages, or if bandwidth is important, just delete the .deb files of the apache packages that seem to be the faulty ones from /var/cache/apt/archives, then try updating and upgrading again.  Even if I am wrong it will not be a major problem for the system as the newly downloaded corrupt packages will simply report the same errors, leaving you exactly where you are now.

---

### Post by Hyli on 2012-02-17
No i already tried to clean.
It looks like tar or another installed program needed in the upgrade process is corrupted

---

### Post by Hyli on 2012-02-20
I replaced tar and dpkg-deb executables with ones from another server but error is still here. Any idea?

---

### Post by Hyli on 2012-02-21
In the cron daily there is another error (for the same reason i think)

```

/etc/cron.daily/apt:
Traceback (most recent call last):
 File "/usr/bin/unattended-upgrade", line 519, in <module>
   main()
 File "/usr/bin/unattended-upgrade", line 446, in main
   fd = os.open(logfile_dpkg, os.O_RDWR|os.O_CREAT, 0644)
OSError: [Errno 22] Invalid argument: '/var/log/unattended-upgrades/unattended-upgrades-dpkg_2012-02-21_06:31:53.510019.log'
/etc/cron.daily/aptitude:
cp: cannot create regular file `aptitude.pkgstates': Invalid argument
touch: setting times of `aptitude.pkgstates': No such file or directory
savelog: could not touch aptitude.pkgstates
run-parts: /etc/cron.daily/aptitude exited with return code 4
/etc/cron.daily/dpkg:
cp: cannot create regular file `dpkg.status': Invalid argument
touch: setting times of `dpkg.status': No such file or directory
savelog: could not touch dpkg.status
run-parts: /etc/cron.daily/dpkg exited with return code 4
/etc/cron.daily/logrotate:
error: error creating output file /var/log/syslog.1.gz: Invalid argument
run-parts: /etc/cron.daily/logrotate exited with return code 1
/etc/cron.daily/man-db:
fopen: Invalid argument
run-parts: /etc/cron.daily/man-db exited with return code 2
/etc/cron.daily/standard:
cp: cannot create regular file `dpkg.status': Invalid argument
touch: setting times of `dpkg.status': No such file or directory
savelog: could not touch dpkg.status

```

---

### Post by Hyli on 2012-02-23
I added logs in english on the 1st post

---

