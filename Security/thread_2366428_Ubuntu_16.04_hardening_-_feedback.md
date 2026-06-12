---
title: "Ubuntu 16.04 hardening - feedback"
date: 2017-07-17
forum: Security
---

### Post by Drenriza on 2017-07-17
Hey all

Recently i've been working on a hardening procedure for Ubuntu 16.04, gathering what i can from different sources,
and i was hoping for some feedback / advice or suggestions for improvement to learn from.

The hardening procedure is thought to be for public accessible servers, which can also be accessed physically.

Thanks to all in advance.

[FONT=Calibri]> added[/FONT]
  [FONT=Calibri]< removed[/FONT]
  [FONT=Calibri]$ command executed[/FONT]
  [FONT=Calibri]# comment
[/FONT]

**update and upgrade**
$ sudo apt-get update && sudo apt-get upgrade -y

**Configure user history and timestamp**
[FONT=Calibri]$ vim ~/.bashrc[/FONT]
  [FONT=Calibri]> HISTSIZE=10000
[/FONT]
  [FONT=Calibri]> HISTFILESIZE=20000[/FONT]
  [FONT=Calibri] 
[/FONT]
  [FONT=Calibri]$ echo 'export HISTTIMEFORMAT="%d/%m/%y %T "' >> ~/.bashrc[/FONT]
  [FONT=Calibri]$ source ~/.bashrc

**Disable reboot by ctrl+alt+delete**
[/FONT]
[FONT=Calibri]$ sudo systemctl mask ctrl-alt-del.target
[/FONT]
  [FONT=Calibri]$ sudo systemctl daemon-reload

**Set shell user timeout**
[/FONT]
[FONT=Calibri]$ vim ~/.bashrc[/FONT]
  [FONT=Calibri]> TMOUT=300 # 5 minutes[/FONT]
  [FONT=Calibri]> readonly TMOUT
[/FONT]
  [FONT=Calibri]> export TMOUT[/FONT]
  
  [FONT=Calibri]$ source ~/.bashrc

**Disable system users, console login**
Add "nologin" no all system users like tomcat,samba ect.

Example: luis2:x:1001:1001:Luis prueba,,,:/home/luis2:/bin/nologin

**Reconfigure timezone (update correct time)**
$ dpkg-reconfigure tzdata

[B]Shared memory
[/B]Information:  for servers and desktop installations there is no benefit to mounting /run/shm read/write
$ vim /etc/fstab
> none /run/shm tmpfs defaults,ro 0 0

**Disable file execution in /dev/shm, /tmp**
$ vim /etc/fstab
> tmpfs     /dev/shm    tmpfs     ro,noexec,nosuid        0       0
> tmpfs     /tmp             tmpfs     rw,noexec,nosuid,size=2G       0       0

**Secure network**
[/FONT]
[FONT=Calibri]$ vim /etc/sysctl.conf[/FONT]
  
  [FONT=Calibri]# Disable source packet routing[/FONT]
  [FONT=Calibri]> net.ipv4.conf.default.accept_source_route = 0[/FONT]
  [FONT=Calibri] 
[/FONT]
  [FONT=Calibri]# Ignore send redirects
[/FONT]
  [FONT=Calibri]> net.ipv4.conf.default.send_redirects = 0[/FONT]
  [FONT=Calibri] 
[/FONT]
  [FONT=Calibri]# Ignore ICMP redirects[/FONT]
  [FONT=Calibri]> net.ipv4.conf.default.accept_redirects = 0 
[/FONT]
  
  [FONT=Calibri]# Ignore Directed pings[/FONT]
  [FONT=Calibri]> net.ipv4.icmp_echo_ignore_all = 1 [/FONT]
  [FONT=Calibri] 
# log martians
[/FONT]
[FONT=Calibri]> net.ipv4.conf.all.log_martians=1 [/FONT]
  [FONT=Calibri]> net.ipv4.conf.default.log_martians=1

**Disable IPv6**
[/FONT]
[FONT=Calibri]$ vim /etc/sysctl.conf

[/FONT]
  [FONT=Calibri]> net.ipv6.conf.all.disable_ipv6 = 1[/FONT]
  [FONT=Calibri]> net.ipv6.conf.default.disable_ipv6 = 1
[/FONT]
  > net.ipv6.conf.lo.disable_ipv6 = 1[FONT=Calibri]
[SIZE=5][B]Configure SSH
[/B][/SIZE][B]Generate SSH RSA key for password less login, step 1/2 (client)
[/B][/FONT]
[FONT=Calibri]$ cd ~/.ssh/[/FONT]
  [FONT=Calibri]$ ssh-keygen -t rsa -b [encryption level] -C [comment] -f [output file name][/FONT]
  
  [FONT=Calibri]# Transfer key from local host to server[/FONT]
  [FONT=Calibri]$ ssh-copy-id -i [file.pub] [username]@[ip-address]

[/FONT]
[FONT=Calibri][B][B]Create SSH config file to use password less login, step 2/2 (client)
[/B][/B][/FONT]
[FONT=Calibri]$ vim ~/.ssh/config[/FONT]
  [FONT=Calibri]# Host [IP/hostname][/FONT]
  [FONT=Calibri]# IdentifyFile /home/[user]/.ssh/[keyfile]

[B]Create group for allowing specific users to ssh to server
[/B][/FONT]
[FONT=Calibri]$ sudo groupadd sshlogin[/FONT]
    [FONT=Calibri]$ usermod -a -G sshlogin [user]

[/FONT]
[FONT=Calibri]**Disable password and root login (server)**[/FONT]
  [FONT=Calibri]$ vim /etc/ssh/sshd_config[/FONT]
  [FONT=Calibri]> PermitRootLogin no[/FONT]
  [FONT=Calibri]> PasswordAuthentication no[/FONT]
  [FONT=Calibri]> UsePAM no[/FONT]
  [FONT=Calibri]> UseLogin no

[B]Basic hardening SSH
[/B][/FONT]
[FONT=Calibri]$ vim /etc/ssh/sshd_config[/FONT]
    [FONT=Calibri]> LoginGraceTime 30     
 [/FONT]
[FONT=Calibri]> AddressFamily inet[/FONT]
  [FONT=Calibri]> X11Forwarding no
## Does this make sense with RSA login?
[/FONT]
  [FONT=Calibri]> MaxAuthTries 2
[/FONT]
  [FONT=Calibri]> Banner /etc/issue.net
[/FONT]
    [FONT=Calibri]## Terminate 'ghost' sessions[/FONT]
  [FONT=Calibri]> TCPKeepAlive no[/FONT]
  [FONT=Calibri]## Logout the client after 600 seconds have passed with no activity.[/FONT]
  [FONT=Calibri]> ClientAliveInterval 600[/FONT]
  [FONT=Calibri]> ClientAliveCountMax 0[/FONT]
  [FONT=Calibri]## Only allow users of the group below to be able to ssh to the machine.[/FONT]
  [FONT=Calibri]> AllowGroups sshlogin
[/FONT]
  [FONT=Calibri]## checks to ensure that your ssh files and directories have the proper permissions and ownerships before allowing an SSH session to open up[/FONT]
  [FONT=Calibri]> StrcitModes yes
[/FONT]

---

### Post by TheFu on 2017-07-17
[https://www.amazon.com/Real-World-Linux-Security-2nd/dp/0130464562](https://www.amazon.com/Real-World-Linux-Security-2nd/dp/0130464562)

Plus review the "sticky" threads in this forum (security).

---

