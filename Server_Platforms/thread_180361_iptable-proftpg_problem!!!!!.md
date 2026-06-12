---
title: "iptable-proftpg problem!!!!!"
date: 2006-05-22
forum: Server Platforms
---

### Post by slapper on 2006-05-22
Hi all 

I am using ubuntu as a server for a couple of months and i am very satisfied!!!But i have a problem and i can not solve it.I am using this older tutorial([HTML]http://www.ubuntuforums.org/showthread.php?t=57111&highlight=iptables[/HTML]) and everything works great exept my proftpg server.I am running proftopd as anonymous and standalone in port 1980.Moreover i have made a folder for uploads.I modifyed the script from the tutorial above to fit in my configs for my proftpd.Here is what i have changed

#ftp (20,21)
if [ $allow_ftp -eq "1" ] ; then
	iptables -A INPUT -p tcp -m multiport --destination-ports ftp-data,ftp -j ACCEPT

to this :

#ftp (1980)
if [ $allow_ftp -eq "1" ] ; then
	iptables -A INPUT -p tcp -i --dport 1980 -j ACCEPT

I am only intend to filter the incoming trafic to my server.All the other services(ssh.apache2,mysql) run great with the tutorial above.


And here is my proftpd.conf!!!



> # This is a basic ProFTPD configuration file.
# It establishes a single server and a single anonymous login.
# It assumes that you have a user/group "nobody" and "ftp"
# for normal/anonymous operation.

ServerName                    "ProFTPD-slapper server"
ServerType                     standalone
DefaultServer                  on

# Port 21 is the standard FTP port.
Port                            1980
# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    10

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Restrict the range of ports from which the server will select when sent the
# PASV command from a client. Use IANA-registered ephemeral port range of
#65000 -65534
PassivePorts 65000 65534


# This next option is required for NIS or NIS+ to work properly:
#PersistentPasswd off

SystemLog                       /var/log/proftpd.log
TransferLog                     /var/log/xferlog
# Normally, we want files to be overwriteable.
<Directory /*>
  AllowOverwrite                on
</Directory>


---

