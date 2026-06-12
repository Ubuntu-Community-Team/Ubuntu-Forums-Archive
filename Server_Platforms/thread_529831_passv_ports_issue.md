---
title: "passv ports issue"
date: 2007-08-19
forum: Server Platforms
---

### Post by guilly on 2007-08-19
Ive configured an ftp server using proftpd, i can connect to it fine inside my LAN using its private ip. However when it comes time to access it from the outside world i get a connection refused my firewall is disabled(firestarter). since i've made rules in firestarte does this mean my iptables can still be blocking incoming connections even if firestarter is disabled? One more thing worth mentionning for me to be able to connect internally to my ftp box i neeed to disable passv on my client but when i try to connect from the outside world i have to enable it just to be able to even reach the box. But i still can't connect

i'm not sure what else could be blocking it? Yes i have a linksys router but the proper ports are opened

thanks for the help. i can post my proftpd.conf file if needed

---

### Post by freebeer on 2007-08-19
I was never able to get the passive ports to work properly in my set-up.  It's possible that my router (el-cheapo model) doesn't properly handle it.  So my solution was to just log in using active, not passive mode.

As far as getting your ports forwarded, you might want to double-check your modem.  Some models are modem/routers (in bridge mode?).  If you have one of these, it might be blocking the ports.

---

### Post by guilly on 2007-08-20
Thanks for the advice freebeer, I believe i have it working. However when i get a friend to test my connection it doesn't seem to work at his end he says the connection just times out. But when i try to connect from home using my external ip it works fine, even though i'm connecting using my external ip is it possible that the packets don't even leave the home since the router is "smart" enough to recognize my external ip address so therefore it just re routes the request to my server without even allowing the packets to leave my gateway?

---

### Post by freebeer on 2007-08-20
I suppose that's possible.  When I was setting mine up, on the local LAN I had to use the local IP address of the ftp server whenever I wanted to log in... I've since learned of /etc/hosts file so now I don't have to do that.  It appears that your situation is the reverse of mine.  :)

You said that you're having trouble connecting from externally (internet) locations.  Are you using a domain name?  You might want to check your domain name setting and see if you can set it to accept wildcards.

I had to set this so that the server would get connections for both ftp.domain.com and [www.domain.com](www.domain.com), etc.

---

### Post by guilly on 2007-08-20
I am using a domain name provided by dyndns... but i can successfully connect with the domain name by doing the conection within my LAN but when the connection is done outside my LAN with the domain name or my external ip. Same results occur....

---

### Post by MJN on 2007-08-20
> **guilly said:**
> i'm not sure what else could be blocking it? Yes i have a linksys router but the proper ports are opened

Ah... but what exactly do you mean by 'the proper ports are opened'?

By definition, the usual mode of operation when running passive FTP is for the server to inform the client what port to make a data connection on. Unless you've fixed this in your config this port will change per-connection and hence your router will have no prior knowledge of which port is being used (unless it inspected the FTP stream, which it won't do). Hence, you can connect from the outside but as soon as you try anything which requires data transferred it'll fail because the router sees this incoming packet destined to a port that i) has not been explicitly forwarded by a rule, or ii) does not match any current NAT sessions in its table.

Check out [http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html) for quite a nice overview of the ins and outs of active/passive FTP. The bottom line is that FTP can be a right pain - when it comes to firewalls/NATs what's good for client configuration is often bad for server configuration and vice versa.

I've only had experience of VSFTPD however with that it was possible to narrow down the range of data ports to be used (e.g. 3000-3010) and then you can forward just these ports on the router/NAT. Furthermore, it was also necessary to ensure that VSFTPD advertised it's public/WAN address as opposed to its real (internal/LAN) address in order to uphold the security checks on what data is going to/from where.

Do you really need FTP to achieve what you're trying to do? Moving data over an SSH tunnel is often preferable if only due to the simple configuration, but with the obvious security benefits besides.

Mathew

---

### Post by freebeer on 2007-08-20
I'm using dyndns as well.  The default is to NOT have wildcards checked, so check your settings there.  (It's a check box, then save.)  :)

As MJN mentioned, the range of passive ports can be quite wide.  I tried to narrow it down (but perhaps not enough?) in my ftp config file, and I forwarded the same range of ports in my router, but I wasn't able to get it to work.  I figured it was either my router, or me that was to blame. :)

Active mode was the only way I could get it to work, and for my purposes it was acceptable.  I just tell myself it's a security measure - most ftp clients will default to passive and then get stuck.  :twisted:

---

### Post by guilly on 2007-08-20
mjn, the ports i have opened are 50000 - 52000 

i believe i may take free beers approach and just disable it all together since this ftp is really for personal use and for a few collegues. 

free beer, to  disable passv do i simply remove that piece of code in my proftpd.conf file and then just specify one specific port by adding the code port 21 lets say... then just simply open up that one port on my router?

thanks for the help

---

### Post by MJN on 2007-08-20
Opened, and **forwarded**? Presumably you've configured ProFTPD to only use that range for DATA?

Sorry if I'm two steps behind here, it's just that there's no reason you shouldn't be up and running with this so it's worth questioning even the basics just to make sure.

Does your router have a firewall log? It might also be worth running a packet sniffer at the client and server ends as you'll then be able to see at what stage the exchange is breaking.

Mathew

---

### Post by freebeer on 2007-08-20
Actually, there's nothing in the ftp config file that I changed... I just tell the clients to use active mode.  (They can set this up as a permanent mode in the client (for your server), so they only have to do it once.)

---

### Post by guilly on 2007-08-20
alright guy's/gals. thanks for the help i'm going to retest it may very well be an issue with my friends client cuz i really don't understand

and i did use a packet sniffer and then tried connecting from inside my LAN using my external ip as host and everything went smooth. That's why i'm thinking its related to my friends client

---

### Post by Clark_Bent on 2007-08-22
I am having a similar problem and would appreciate any assistance. So far:

1. Connect to the server via 127.0.0.1
2. Connect to the server via my LAN IP 192.168.2.xxx
3. Can't connect via my WAN IP 

I have a Linksys router. I have tried both passive ports and non. I have forwarded a large range, but it did nothing. I have DMZ enabled. I am unable to scan my public IP with Nmap either. But if I boot into windows, I can scan and see the typical windows ports open when my firewall is disabled.

Output from iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


I have guarddog firewall installed, but it is disabled.

My proftpd.conf file looks like so:

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 65534

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile                   off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayFirstChdir           .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>

---

