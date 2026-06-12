---
title: "SSH Issue"
date: 2007-07-02
forum: Server Platforms
---

### Post by mtbosworth on 2007-07-02
I've been trying to setup Freenx recently, but have had problems with SSH, which ended up dealing with my configuration.  I now has SSH up and running fine now.  However, I cannot connect!  If I use nmap is can see that ssh is listening at port 22 of my machine.  When I try to connect it says, "Connection closed by UNKNOWN".  I have no idea where to go with this.  You're help is much appreciated.  My guess so far is that either SSH config stills needs tweaked or I have some sort of firewall issue (possibly iptables configuration)?  Thanks in advance.

---

### Post by meatpan on 2007-07-02
Here are some ideas:

o When debugging a problem like this, run 'ssh -vv' instead of 'ssh'.  This will cause detailed status messages to be written to the terminal.  In many cases you can see exactly which stage of the connection/authentication process is behaving unexpectedly.
o Make sure the ssh port (22) is opened.  The port can be blocked by firewalls on your machine, or a router, on the inbound or outbound locations.
o If neither of these suggestions work, take a look at the file /etc/ssh/ssh_config.  Perhaps there are some options disabled, or your user isnt on the access list.  Be very careful and understand what your are doing if you plan to make changes to this file.

---

### Post by mtbosworth on 2007-07-03
I tried what you said and here are my config settings and the log:

Configuration:

Host *
   ForwardAgent no
   ForwardX11 no
   ForwardX11Trusted yes
   RhostsRSAAuthentication no
   RSAAuthentication yes
   PasswordAuthentication yes
   HostbasedAuthentication no
   BatchMode no
   CheckHostIP yes
   AddressFamily any
   ConnectTimeout 0
   StrictHostKeyChecking ask
   IdentityFile ~/.ssh/identity
   IdentityFile ~/.ssh/id_rsa
   IdentityFile ~/.ssh/id_dsa
   Port 22
   Protocol 2,1
   Cipher 3des
   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
   EscapeChar ~
   Tunnel no
   TunnelDevice any:any
   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

log:
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.xxx [192.168.1.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/mtbosworth/.ssh/identity type -1
debug1: identity file /home/mtbosworth/.ssh/id_rsa type -1
debug1: identity file /home/mtbosworth/.ssh/id_dsa type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
Connection closed by UNKNOWN

---

### Post by meatpan on 2007-07-03
I don't have any more ideas off the top of my head.  A quick web search hinted that your problem might be related to files in the /tmp directory.  Verify that your /tmp dir is not full.

How and when did you install your ssh packages?  Were these manually build from source via config/make?

I appologize for not being a better help.  Hopefully someone else can pipe in here.

---

### Post by mtbosworth on 2007-07-03
I just installed it with apt-get from the ubuntu feisty terminal.

---

