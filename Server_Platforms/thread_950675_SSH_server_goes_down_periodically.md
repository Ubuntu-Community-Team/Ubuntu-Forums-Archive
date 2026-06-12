---
title: "SSH server goes down periodically"
date: 2008-10-17
forum: Server Platforms
---

### Post by rtsask on 2008-10-17
Hello all,

[B]I have a critical cvs server, which so many developers work with it 24 hours, SSH on this server is intermittent and goes down several times in week specially after midnight and this make our company to be behind of its tasks, could someone tell me if there is an script to restart ssh automatically if it is froze besides i would like to mention if we shutdown ssh server port 22 is still listening and it is so weird.
[/B]


Thanks  so much,

Rouzbeh :(

---

### Post by cariboo on 2008-10-17
Check to see if:

```
TCPKeepALive
```

is commented out or set to no in /etc/ssh/sshd_config

Jim

---

### Post by k_grdn on 2008-10-17
Hi,


Check your logs to see what processes are running/in error at the time ssh goes down.  Likely culprit maybe cron/syslog rotate, a daemon may need to restart to rotate its log, possibly this could hang your network/ssh connection.

If this is a critical service I suggest implementing monitoring software maybe Bigbro or nagios to alert you when ssh/network unreachable then kick it when its down.


Regards,

k_grdn

---

### Post by rtsask on 2008-10-17
There is no such a line in sshd_config at all.

-Rouzbeh

> **cariboo907 said:**
> Check to see if:

```
TCPKeepALive
```

is commented out or set to no in /etc/ssh/sshd_config

Jim

---

### Post by cariboo on 2008-10-17
Here is my /etc/ssh/sshd_config:

```
jimk@Willy:/etc/ssh$ cat sshd_config
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd yes
PrintLastLog yes
**TCPKeepAlive yes**
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
IgnoreUserKnownHosts no
PasswordAuthentication yes
DenyGroups deniedssh
```

Note the path /etc/ssh/sshd_config. I bolded the particular entry.

Jim

---

### Post by rcrcomputing on 2008-10-20
> **rtsask said:**
> Hello all,

[B]I have a critical cvs server, which so many developers work with it 24 hours, SSH on this server is intermittent and goes down several times in week specially after midnight and this make our company to be behind of its tasks, could someone tell me if there is an script to restart ssh automatically if it is froze besides i would like to mention if we shutdown ssh server port 22 is still listening and it is so weird.
[/B]


Thanks  so much,

Rouzbeh :(

#!/bin/bash

RESTART="/etc/init.d/ssh restart"

PGREP="/usr/bin/pgrep"

SERVICE="sshd"

$PGREP ${SERVICE}

if [ $? -ne 0 ]
then
    echo $SERVICE is down. Restarting..
    $RESTART
    else
    echo $SERVICE is running
fi

---

### Post by rcrcomputing on 2008-10-20
I guess it should tell you it did..  Now it emails you..


> #!/bin/bash

nameofscript=restart_service
admin=your@email.com
local_machine=home_server
RESTART="/etc/init.d/ssh restart"

PGREP="/usr/bin/pgrep"

watch_service="sshd"


***************************************
Should not have to edit below this line..

function alert_mail()

   {

cat << EOF > /tmp/$watch_service.error
script = $nameofscript
Running on host = $local_machine

$local_machine reports an error
I'm reporting that I had to restart the $watch_service service..
EOF

# Now let's mail the error to admin
mail -s "$local_machine Restarting $watch_service" $admin < /tmp/$watch_service.error



}

$PGREP ${watch_service}

if [ $? -ne 0 ]
then
    echo $watch_service is down. Restarting..
    $RESTART
    alert_mail
    else
    echo $watch_service is running
fi

---

### Post by rcrcomputing on 2008-10-20
I'm going to bed. It's late, and I just re-read your post. Seems this script is not what you need.  :(   

Since it's listening, there is still a pid.  Maybe monit is worth looking at. Sorry I was not more helpfull.

---

