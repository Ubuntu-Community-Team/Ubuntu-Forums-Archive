---
title: "How to Install an FTP over SSL (FTPS) on Ubuntu Server 18.04 LTS"
date: 2019-09-11
forum: Tutorials
---

### Post by LHammonds on 2019-09-11
Greetings and salutations,

I hope this thread will be helpful to those who follow in my foot steps as well as getting any advice based on what I have done / documented.

Link to original post: [HammondsLegacy Forums]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=265") (best when viewed at original location due to custom formatting)

[SIZE=4]High-level overview[/SIZE]

This document will describe how to setup an FTP server which utilizes SSL (FTPS) encryption and local login IDs to allow users to login and upload files but cannot login to the console.

[SIZE=4]Tools utilized in this process[/SIZE]

[LIST]
[*][Ubuntu Server]("http://www.ubuntu.com/download/ubuntu/download") 18.04 LTS, 64-bit 
[*][Portable PuTTY]("http://portableapps.com/apps/internet/putty_portable") 0.72 
[*][vsftpd]("https://help.ubuntu.com/community/vsftpd") 3.0.3 
[/LIST]

[SIZE=4]Helpful links[/SIZE]

The list below are sources of information that helped me configure this system.

[LIST]
[*][Ubuntu Help - FTP Server]("https://help.ubuntu.com/18.04/serverguide/ftp-server.html") 
[*][Ubuntu Help - vsftpd.conf man page]("http://manpages.ubuntu.com/manpages/xenial/en/man5/vsftpd.conf.5.html") 
[*][vsftpd website (vsftp.conf)]("http://vsftpd.beasts.org/vsftpd_conf.html") 
[/LIST]

[SIZE=4]Assumptions[/SIZE]

This documentation will need to make use of some very-specific information that will most-likely be different for each person / location. This variable data will be noted in this section and highlighted in red throughout the document as a reminder that you should plug-in your own value rather than actually using these "place-holder" values.

Under no circumstance should you use the actual values listed below. They are place-holders for the real thing. This is just a checklist template you need to have answered before you start the install process.

Wherever you see [COLOR=red]RED[/COLOR] in this document, you need to substitute it for what your company uses.

[LIST]
[*]Minimum Passive Port: [COLOR=red]9000[/COLOR] 
[*]Maximum Passive Port: [COLOR=red]9020[/COLOR] 
[*]FTP User Account: [COLOR=red]myftp[/COLOR] 
[*]FTP User Password: [COLOR=red]mypass123[/COLOR] 
[/LIST]

---

### Post by LHammonds on 2019-09-11
[size=4]Install Ubuntu Server[/size]

The 1st thing to do is the installation of Ubuntu Server.  The following guide will describe how to setup a server for use in a production environment and this document assumes the guide was followed to setup Ubuntu.

The server install guide also contains an "Assumption" section with variables colored in RED, instead of using those values, this guide will instead use the following as replacements:

Ubuntu Server name: [color=red]srv-ftps[/color]
Ubuntu Server IP address: [color=red]192.168.107.28[/color]

[color=red]**IMPORTANT**[/color]: Keep in mind, these are typically different for each site/install.  Do not use these exact values yourself...make up your own that matches your environment, write them down and use them instead of the values in the guide.

NOTE: These are the sections you can skip in the server install guide which are not necessary for this server (however, you might want them...it is up to you):


[list]
[*]Configure Ubuntu for File Sharing (Samba)
[*]Configure Windows Server as a Remote Mount Point
[*]SSH Public and Private Keys
[/list]


Follow the [How to Install Ubuntu Server](https://ubuntuforums.org/showthread.php?t=2389846) guide and come back when finished.

---

### Post by LHammonds on 2019-09-11
[SIZE=4]Install FTP Service[/SIZE]
 
At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR])

At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password ([COLOR=red]myadminpass[/COLOR]).

Install vsftpd and make a backup of the original config file.
```

apt -y install vsftpd
cp /etc/vsftpd.conf /etc/vsftpd.bak

```


[SIZE=4]Generate an SSL Certificate[/SIZE]

Run these commands but make sure you substitute your values in place of the "My" values.
```

openssl req -x509 -nodes -days 1095 -newkey rsa:2048 -text -subj "/C=MyCountry/ST=MyState/L=MyCity/O=MyOrganization/OU=MyOrganizationalUnit/CN=MyCommonName" -keyout /etc/ssl/private/vsftpd.key -out /etc/ssl/private/vsftpd.pem
chown root:ftp /etc/ssl/private/vsftpd.*
chmod 644 /etc/ssl/private/vsftpd.*

```


[SIZE=4]Configure vsftpd[/SIZE]

Edit /etc/vsftpd.conf and find/uncomment following lines:
```

local_enable=YES
write_enable=YES
local_umask=022
ftpd_banner=Welcome to our FTP server.
chroot_local_user=YES

```

Find the following existing lines and change the values as follows:
```

anonymous_enable=NO
connect_from_port_20=NO
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.key

```

Add the following new lines (feel free to adjust values as desired):
```
listen_port=990

# Turn on SSL
ssl_enable=YES

# Allow anonymous users to use secured SSL connections
allow_anon_ssl=NO

# All non-anonymous logins are forced to use a secure SSL connection in order to
# send and receive data on data connections.
force_local_data_ssl=YES

# All non-anonymous logins are forced to use a secure SSL connection in order to send the password.
force_local_logins_ssl=YES

# Permit TLS v1 protocol connections. TLS v1 connections are preferred
ssl_tlsv1=YES

# Permit SSL v2 protocol connections. TLS v1 connections are preferred
ssl_sslv2=YES

# permit SSL v3 protocol connections. TLS v1 connections are preferred
ssl_sslv3=YES

# Hide the info about the owner (user and group) of the files.
hide_ids=YES

# Connection limit for each IP:
max_per_ip=50

# Maximum number of clients:
max_clients=50

# When port_enabled is YES, active mode connects are allowed.
port_enable=YES

# When pasv_enable is YES, passive mode connects are allowed.
pasv_enable=YES

# pasv_min_port specifies the lowest possible port sent to the FTP clients for passive mode connections. This setting is used to limit the port range so that firewall rules are easier to create. The value must not be lower than 1024.
pasv_min_port=9000

# pasv_max_port specifies the highest possible port sent to the FTP clients for passive mode connections. This setting is used to limit the port range so that firewall rules are easier to create. The value must not exceed 65535.
pasv_max_port=9020

# require_ssl_reuse, if YES, all SSL data connections are required to exhibit SSL session reuse.  Set to NO if your log shows failures to upload because of no session reuse.

require_ssl_reuse=NO

# Set to YES to get extra information in the logs if you are having issues connecting.
debug_ssl=NO

# This setting allows FileZilla to connect or you would see something like "handshake failed" otherwise.
ssl_ciphers=HIGH
```

[SIZE=4]Restart FTP Service[/SIZE]

The the following:
```
systemctl restart vsftpd
```

---

### Post by LHammonds on 2019-09-11
[SIZE=4]Firewall Rules[/SIZE]

Edit the firewall script that was created during the initial setup of the server (if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&page=2&p=13758735#post13758735")):
```
vi /var/scripts/prod/en-firewall.sh
```

Add (or enable) the following:

```
echo "Adding FTPS Server rules"
ufw allow proto tcp to any port 990 comment 'FTPS' 1>/dev/null 2>&1
ufw allow proto tcp to any port 9000:9020 comment 'FTP Passive' 1>/dev/null 2>&1

```

Run the updated rules:

```
/var/scripts/prod/en-firewall.sh
```

[SIZE=4]Restart Scripts[/SIZE]

Edit the service start script to include vsftpd service. (if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&p=13758730#post13758730"))

```
vi /var/scripts/prod/servicestart.sh
```

Add or enable the following:

```
systemctl start vsftpd
```

Edit the service stop scripts to include vsftpd service. (if you [followed my instructions]("https://ubuntuforums.org/showthread.php?t=2389846&p=13758730#post13758730"))

```
vi /var/scripts/prod/servicestop.sh
```

Add or enable the following:

```
systemctl stop vsftpd
```

---

### Post by LHammonds on 2019-09-11
[SIZE=4]Configure User Accounts[/SIZE]

At the login prompt, login with your administrator account ([COLOR=red]administrator[/COLOR] / [COLOR=red]myadminpass[/COLOR])

At the $ prompt, temporarily grant yourself super user privileges by typing **sudo su** [COLOR=green]{ENTER}[/COLOR] and then provide the administrator password ([COLOR=red]myadminpass[/COLOR]).

Add an ftpusers group.
```

addgroup ftpusers

```

Use the default ftp folder of /srv/ftp but move the home directory of the default "ftp" account underneath that folder.  The /srv/ftp folder will be become the base folder for all FTP user accounts but nobody will be able to access it directly.

```

mkdir -p /srv/ftp/ftp/public
usermod -d /srv/ftp/ftp ftp
chmod 555 /srv/ftp
chmod 555 /srv/ftp/ftp
chmod 755 /srv/ftp/ftp/public
chown -R ftp:ftpusers /srv/ftp/ftp

```

Type this to add /usr/sbin/nologin to /etc/shells (* This allows users to login via FTP which cannot login directly on the server *)
```

echo "/usr/sbin/nologin" >> /etc/shells

```

Now add a user called [COLOR=red]myftp[/COLOR] with a password of [COLOR=red]mypass123[/COLOR]

```
mkdir -p /srv/ftp/myftp/public
chmod 555 /srv/ftp/myftp
chmod 755 /srv/ftp/myftp/public
useradd -g ftpusers -d /srv/ftp/myftp -s /usr/sbin/nologin myftp
chown -R myftp:ftpusers /srv/ftp/myftp
passwd myftp
mypass123
```

---

### Post by LHammonds on 2019-09-11
[SIZE=4]Public / Private Key Management[/SIZE]

If you need to generate an SSH key with a passphrase in order to connect to another FTP server, it can be a tricky thing to automate scripts that push and pull files to that server since each time you connect, it will ask for the passphrase.

I've seen some recommend to avoid passphrases when scripting or include the passphrase in the script.  Either of these methods reduces the security by not having the key protected or by exposing the passphrase by having it on the file system.

My preferred solution is to use the passphrase but also not store it on the server anywhere so if the keys are ever compromised, the passphrases do not go with them.

An SSH agent is used to load the keys in memory and as long as the agent is loaded, the scripts will be able to work automatically in the background.

This still requires manually typing in the passphrase(s) but only after the server reboots.

Here is how it works:

ssh-add is used to load the various private keys you have into memory.  This loads a program called "ssh-agent" in memory.  In order for SSH programs to access these keys, two variables have to be set.  SSH_AUTH_SOCK and SSH_AGENT_PID and they have to be pointed to the lock file and process ID respectfully.

Let's assume you have two passphrase-protected private keys stored here:

```
/root/.ssh/ssh2rsa-company1-private.rsa
/root/.ssh/ssh2rsa-company2-private.rsa
```

When you reboot your server, you will need to manually run a script like the following which will initially load the ssh-agent and the keys:

/var/scripts/prod/load-ssh-keys.sh
```
#!/bin/bash
#############################################
## Name          : load-ssk-keys.sh
## Version       : 1.0
## Date          : 2017-02-16
## Author        : LHammonds
## Compatibility : Ubuntu Server 16.04 LTS - 18.04.3 LTS
## Requirements  : Run as root
## Purpose       : Load SSH keys into memory which will
##                 allow FTP login without prompts.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2017-02-16 LTH  Created script.
#############################################

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi
clear
ssh-add -l >/dev/null
if [ "$?" == 2 ]; then
  ## Agent not loaded, load it up.
  eval `ssh-agent -s`
fi
echo "Purging any existing keys from memory..."
ssh-add -D
echo "Enter the Company #1 SSH passphrase..."
ssh-add /root/.ssh/ssh2rsa-company1-private.rsa
echo "Enter the Company #2 SSH passphrase..."
ssh-add /root/.ssh/ssh2rsa-company1-private.rsa
echo "Listing all keys in memory..."
ssh-add -l
echo "Complete. Keys will remain in memory until the next reboot."
echo ""
read -p "Press [Enter] key to continue..."
```

If you logout or if a script runs in a different session (which will likely be the case), it will not be able to "see" the keys loaded in memory because the SSH_AUTH_SOCK and SSH_AGENT_PID variables will not be set in a new session.

To fix this, your scripts need to "find" the currently loaded SSH agent and set the variables correctly.

Example:
```

## Point the required variables to the loaded ssh-agent
export SSH_AUTH_SOCK=`find /tmp/ -type s -name agent.\* 2> /dev/null | grep '/tmp/ssh-.*/agent.*'`
export SSH_AGENT_PID=`ps aux | grep ssh-agent | grep -v "grep" | awk '{print $2}'`

if [ ${#SSH_AUTH_SOCK} -lt 1 ]; then
  ## Variable still empty.  Houston, we have a problem.
  echo "ERROR - ssh-agent not pre-loaded with authentication key." | tee -a ${LogFile}
  echo "You must load the SSH keys before running this script."
  exit 0
fi
```

Here is an example of a loaded ssh-agent:

```

root@srv-ftps:/# pgrep -u root ssh-agent
4421
root@srv-ftps:/# ls -l /tmp/ssh-jDCLupzf4420/
total 0
srw------- 1 root root 0 Apr  6 18:24 agent.4420

```

With the above information, the variables will need to be set as follows:
```

SSH_AGENT_PID=4421
SSH_AUTH_SOCK=/tmp/ssh-jDCLupzf4420/agent.4420

```

It might also be a good idea to remind anyone at the console that runs the reboot process to remind them that once the server comes back up, the keys must be loaded in memory.

Example:

/var/scripts/prod/reboot.sh
```
#!/bin/bash
#############################################
## Name          : reboot.sh
## Version       : 1.0
## Date          : 2013-01-08
## Author        : LHammonds
## Compatibility : Ubuntu Server 12.04.1 LTS - 18.04.3 LTS
## Requirements  : Run as root
## Purpose       : Stop services and reboot server.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2013-01-07 LTH  Created script.
#############################################

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi
clear
echo ""
echo "WARNING: Be sure to Load SSH Keys after reboot or scripts will fail"
echo ""
sleep 5
echo "Stopping FTP service..."
service vsftpd stop
echo "Rebooting..."
echo "3"
sleep 1
echo "2"
sleep 1
echo "1"
sleep 1
shutdown -r now
```

If you also want the variables set into the root profile, type the following (while as root):

```
vi /root/.profile
```
Add the following:
```

## Point the required variables to the loaded ssh-agent
export SSH_AUTH_SOCK=`find /tmp/ -type s -name agent.\* 2> /dev/null | grep '/tmp/ssh-.*/agent.*'`
export SSH_AGENT_PID=`ps aux | grep ssh-agent | grep -v "grep" | awk '{print $2}'`
echo "Loaded SSH Keys..."
ssh-add -l

```

Now when you are in your low-rights account and need to sudo into the root account, type the following:
```
sudo su --login
```The "--login" is important so it executes the code in .profile.  Once you are logged in as root, you should be able to list the keys loaded in memory with:
```
ssh-add -l
```

---

### Post by LHammonds on 2019-09-11
[SIZE=4]Command-Line FTP Clients for Automation[/SIZE]

**sftp** command comes with OpenSSH and should already be installed on your server.

Example:
```
echo "lcd /local/path" > /tmp/ftp.cmd
echo "cd /remote/path" >> /tmp/ftp.cmd
echo "mget *" >> /tmp/ftp.cmd
sftp -b /tmp/ftp.cmd ftpuser@192.168.1.21
```

NOTE: To use this, you might have to modify /etc/ssh/sshd_config and modify the "AllowUsers" and "PasswordAuthentication" lines.

**sshpass** - This utility allows non-interactive authentication to a keyboard-interactive site.  For example, you might need to access an FTP server that requires a password to be typed in interactively.  sshpass is used to automate such systems but it isn't without risk.  Rather than exposing the password to anyone that is watching the process list, we can export a variable with the password in it to help hide the password from other users on the system.  But the script has to be locked down so nobody but the process running it can see the contents of the script...which contains the password.

You have to install sshpass from the repository using the following command:

```
apt install ssh-pass
```

Example usage:
```
#!/bin/bash
echo "lcd /files/to/send/ > /tmp/ftp.cmd
echo "cd /upload/path" >> /tmp/ftp.cmd
echo "mput *" >> /tmp/ftp.cmd
export SSHPASS='ASuperSecretPassword'
sshpass -e sftp -oBatchMode=no -b /tmp/ftp.cmd ftpuser@192.168.1.21
```

**ftp-ssl** - You have to install ftp-ssl from the repository using the following command:

```
apt install ftp-ssl
```

**lftp** - is a file transfer program that allows sophisticated FTP, HTTP and other connections to other hosts. You have to install ftp-ssl from the repository using the following command:

```
apt install lftp
```

[SIZE=4]SSL-Aware FTP Clients for Windows[/SIZE]

[SmartFTP]("http://www.smartftp.com/")

[FileZilla]("https://portableapps.com/apps/internet/filezilla_portable")

FileZilla Settings (tested with 3.44.2):
Host: ?.?.?.?
Port: 990
Protocol: FTP - File Transfer Protocol
Encryption: Require explicit FTP over TLS
Login Type: Normal

[WinSCP]("https://portableapps.com/apps/internet/winscp_portable")

WinSCP Settings (tested with 5.13.4 and 5.15.3)
File protocol: FTP
Encryption: TLS/SSL Explicit Encryption
Host name: ?.?.?.?
Port number: 990

---

