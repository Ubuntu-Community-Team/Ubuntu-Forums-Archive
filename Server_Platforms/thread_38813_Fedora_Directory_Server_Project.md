---
title: "Fedora Directory Server Project"
date: 2005-06-02
forum: Server Platforms
---

### Post by nocturn on 2005-06-02
RedHat aquired Netscape Directory Server, it released it under the GPL resulting in the Fedora DS.

This would be cool to have on Ubuntu (as OpenLDAP is often rather painfull).

[http://directory.fedora.redhat.com](http://directory.fedora.redhat.com)

---

### Post by thomasmathiesen on 2005-06-07
Could someone write a how-to for fedora-directory-server <-> ubuntu client ?

---

### Post by defkewl on 2005-06-08
I think you should throw this idea to Ubuntu-dev mailing list :)

---

### Post by thomasmathiesen on 2005-06-29
Here's a script I made for hoary;

conf file (led-client-ubuntu.conf) :
#pam_ldap config related
host REPLACEME

#ldap database
base dc=REPLACEME,dc=REPLACEME
ldap_version 3
timelimit 10
pam_filter objectclass=posixAccount
pam_login_attribute uid
ssl no
#tls_checkpeer no
pam_password crypt

#pam config files related
account	sufficient	pam_ldap.so
account	required	pam_unix.so
auth	sufficient	pam_ldap.so
auth	required	pam_unix.so nullok_secure use_first_pass
session	required	pam_unix.so
session	required	pam_mkhomedir.so skel=/etc/skel/ umask=0077
password	required	pam_unix.so nullok obscure min=4 max=8 md5
password	required	pam_cracklib.so retry=3 minlen=6 difok=3

#User to test with
testuser	heidi


Script (led-client-ubuntu-hoary.sh) :
# RUN THIS AS ROOT like this:
# sh led-client-ubuntu-hoary.sh

#Setting up vars
logfile=/var/log/led-client-install.log


#Replacing /etc/apt/sources.list
echo "Copying /etc/apt/sources.list to sources.list.old and replacing it." >> $logfile
mv /etc/apt/sources.list /etc/apt/sources.list.old
touch /etc/apt/sources.list
echo "#Created by LinProfs Enterprise Directory client script" >> /etc/apt/sources.list
echo "#Your old sources.list is now called sources.list.old" >> /etc/apt/sources.list
echo "deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted" >> /etc/apt/sources.list
echo "deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted" >> /etc/apt/sources.list
echo "deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted" >> /etc/apt/sources.list
echo "deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted" >> /etc/apt/sources.list
echo "deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe" >> /etc/apt/sources.list
echo "deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe" >> /etc/apt/sources.list
echo "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted" >> /etc/apt/sources.list
echo "deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted" >> /etc/apt/sources.list
echo "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe" >> /etc/apt/sources.list
echo "deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe" >> /etc/apt/sources.list
echo "Updating your apt cache." >> $logfile
apt-get update 2>>$logfile
clear
echo "Installing software.." >> $logfile
apt-get install libnss-ldap libnss-db libpam-ldap nscd 2>>$logfile

#Shall we copy the old sources.list back to the original state?

echo "Editing /etc/nsswitch.conf" >> $logfile
sed 's/compat/ldap files/g' /etc/nsswitch.conf >> /tmp/led_nsswitch.conf
mv /etc/nsswitch.conf /etc/nsswitch.conf.old 2>>$logfile
mv /tmp/led_nsswitch.conf /etc/nsswitch.conf 2>>$logfile

echo "Editing /etc/pam_ldap.conf and removing not-useful ldap files" >> $logfile
rm -f /etc/ldap/ldap.conf /etc/libnss-ldap.conf 2>>$logfile
mv /etc/pam_ldap.conf /etc/pam_ldap.conf.old 2>>$logfile
touch /tmp/pam_ldap.conf 2>>$logfile
echo "#Created by LinProfs Enterprise Directory client script" >> /tmp/pam_ldap.conf
echo "#Your old pam_ldap.conf file has been renamed to /etc/pam_ldap.conf.old"
awk '/host/ { print }' ./led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/base dc=/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/ldap_version/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/timelimit/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/pam_filter/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/pam_login_attribute/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/ssl/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/tls_checkpeer/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
awk '/pam_password/ { print }' led-client-ubuntu.conf >> /tmp/pam_ldap.conf
mv /tmp/pam_ldap.conf /etc/pam_ldap.conf 2>>$logfile

#By some reason it needs both libnss-ldap.conf and pam_ldap.conf.
#These files are authentical, so we'll just copy pam_ldap.conf
cp /etc/pam_ldap.conf /etc/libnss-ldap.conf 2>>$logfile

echo "Editing and backing up pam files" >> $logfile
#Backup files
mv /etc/pam.d/common-account /etc/pam.d/old-common-account 2>>$logfile
mv /etc/pam.d/common-auth /etc/pam.d/old-common-auth 2>>$logfile
mv /etc/pam.d/common-session /etc/pam.d/old-common-session 2>>$logfile
mv /etc/pam.d/common-password /etc/pam.d/old-common-password 2>>$logfile

#Create temp files
touch /tmp/common-account 2>>$logfile
touch /tmp/common-auth 2>>$logfile
touch /tmp/common-session 2>>$logfile
touch /tmp/common-password 2>>$logfile

#Write header in temp files
echo "#Created by LinProfs Enterprise Directory client script" >> /tmp/common-account
echo "#Your old common-account file has been renamed to /etc/pam.d/old-common-account" >> /tmp/common-account
echo "#Created by LinProfs Enterprise Directory client script" >> /tmp/common-auth
echo "#Your old common-auth file has been renamed to /etc/pam.d/old-common-auth" >> /tmp/common-auth
echo "#Created by LinProfs Enterprise Directory client script" >> /tmp/common-session
echo "#Your old common-session file has been renamed to /etc/pam.d/old-common-session" >> /tmp/common-session
echo "#Created by LinProfs Enterprise Directory client script" >> /tmp/common-password
echo "#Your old common-password file has been renamed to /etc/pam.d/old-common-password" >> /tmp/common-password

#Write new config to pam files
awk '/account\t/ { print }' ./led-client-ubuntu.conf >> /tmp/common-account
awk '/auth\t/ { print }' ./led-client-ubuntu.conf >> /tmp/common-auth
awk '/session\t/ { print }' ./led-client-ubuntu.conf >> /tmp/common-session
awk '/password\t/ { print }' ./led-client-ubuntu.conf >> /tmp/common-password
mv /tmp/common-account /tmp/common-auth /tmp/common-session /tmp/common-password /etc/pam.d/ 2>>$logfile

clear

#This test is not being used..
echo "We are done." >> $logfile
echo "We are done.. and now I will run a test for you.."
echo "If you see an output below, it means that it could find the user in the ldap."
ledtest=$(awk '/testuser\t/ { print $2}' ./led-client-ubuntu.conf)
getent passwd $ledtest
echo "This test is not to trust 100%, so even though you do not see anything, it may"
echo "work. Just reboot your machine, and try to login to an account you have"
echo "created on your LED-Server. Remember that this user must have a posixAccount."
echo "Errors and information from the install-script can be found in $logfile"


Save these two files in the same folder and run the sh as root (sudo sh). This script is being used for our customers, so you may want to remove all the logging and output.

---

