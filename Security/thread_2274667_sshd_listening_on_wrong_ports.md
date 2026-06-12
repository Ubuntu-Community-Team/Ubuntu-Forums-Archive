---
title: "sshd listening on wrong ports"
date: 2015-04-21
forum: Security
---

### Post by anon9815 on 2015-04-21
using the soon to be officially released Ubuntu 15.04  though i have specified in /etc/ssh/sshd_config to listen on port 32 and told xinetd to run sshd listening on port 32  various scans confirm it is listening on both port 22 and port 32 i have tried restarting sshd and xinetd and have also tried rebooting but it hasn't changed.    the contents of my /etc/ssh/sshd_config is  ```
 # Package generated configuration file # See the sshd_config(5) manpage for details  # What ports, IPs and protocols we listen for Port 32 # Use these options to restrict which interfaces/protocols sshd will bind to #ListenAddress :: #ListenAddress 0.0.0.0 Protocol 2 # HostKeys for protocol version 2 HostKey /etc/ssh/ssh_host_rsa_key HostKey /etc/ssh/ssh_host_dsa_key HostKey /etc/ssh/ssh_host_ecdsa_key HostKey /etc/ssh/ssh_host_ed25519_key #Privilege Separation is turned on for security UsePrivilegeSeparation yes  # Lifetime and size of ephemeral version 1 server key KeyRegenerationInterval 3600 ServerKeyBits 1024  # Logging SyslogFacility AUTH LogLevel INFO  # Authentication: LoginGraceTime 120 PermitRootLogin without-password StrictModes yes  RSAAuthentication yes PubkeyAuthentication yes #AuthorizedKeysFile	%h/.ssh/authorized_keys  # Don't read the user's ~/.rhosts and ~/.shosts files IgnoreRhosts yes # For this to work you will also need host keys in /etc/ssh_known_hosts RhostsRSAAuthentication no # similar for protocol version 2 HostbasedAuthentication no # Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication #IgnoreUserKnownHosts yes  # To enable empty passwords, change to yes (NOT RECOMMENDED) PermitEmptyPasswords no  # Change to yes to enable challenge-response passwords (beware issues with # some PAM modules and threads) ChallengeResponseAuthentication no  # Change to no to disable tunnelled clear text passwords #PasswordAuthentication yes  # Kerberos options #KerberosAuthentication no #KerberosGetAFSToken no #KerberosOrLocalPasswd yes #KerberosTicketCleanup yes  # GSSAPI options #GSSAPIAuthentication no #GSSAPICleanupCredentials yes  X11Forwarding yes X11DisplayOffset 10 PrintMotd no PrintLastLog yes TCPKeepAlive yes #UseLogin no  #MaxStartups 10:30:60 #Banner /etc/issue.net  # Allow client to pass locale environment variables AcceptEnv LANG LC_*  Subsystem sftp /usr/lib/openssh/sftp-server  # Set this to 'yes' to enable PAM authentication, account processing, # and session processing. If this is enabled, PAM authentication will # be allowed through the ChallengeResponseAuthentication and # PasswordAuthentication.  Depending on your PAM configuration, # PAM authentication via ChallengeResponseAuthentication may bypass # the setting of "PermitRootLogin without-password". # If you just want the PAM account and session checks to run without # PAM authentication, then enable this but set PasswordAuthentication # and ChallengeResponseAuthentication to 'no'. UsePAM yes 
```  the contents of /etc/xinetd.d/ssh is  ```
 service ssh { socket_type = stream protocol = tcp wait = no user = root server = /usr/sbin/sshd server_args = -i -p 32 } 
```

---

### Post by TheFu on 2015-04-22
Haven't touched xinitd recently.  openssh-server conf is the only place I know to modify to move the ssh port (assuming nothing odd like a reverse proxy or trying to share port 443/tcp with different webservers.  Generally, I just have the edge router handle the port translation from 64022 --> 22 on the internal LAN server port.  That way, from inside, it is port 22 the default and from outside it is 64022 (to keep the log files shorter).

Your sshd_config file is appearing as 1 line above. It needs to have UNIX newlines. It is probably just a posting error, but ...

---

### Post by The Cog on 2015-04-22
I suspect that xinetd is listening on port 32 and sshd is listening on port 22. You should not need to use xinetd at all for sshd - I recommend that you remove the xinetd configuration again.

As TheFu says, the sshd_config line you posted appears as just one line. I wonder if an editor you are using has damaged the line endings of the config file - perhaps sshd is running on default settings because it cannot find any other settings in sshd_config?

---

