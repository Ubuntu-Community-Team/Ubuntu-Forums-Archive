---
title: "proftpd configuration issue"
date: 2008-02-26
forum: Server Platforms
---

### Post by girasquid on 2008-02-26
Hello, all.

I am currently trying to setup and configure proftpd on a fresh Ubuntu 7 Server install, using the "LAMP" and "SSH Server" options from the installer. This is my proftpd configuration file:
```

# To really apply changes reload proftpd after modifications.

# Includes DSO modules
Include /etc/proftpd/modules.conf

UseIPv6				off

ServerName			"Max"
ServerType			standalone
DeferWelcome			off

# turn off the painfully slow lookups
UseReverseDNS			off
IdentLookups			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DefaultRoot			~

Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

TransferLog /var/log/proftpd/xferlog
ExtendedLog /var/log/proftpd/extended.log
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
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
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

```

After setting up proftpd using this configuration file, it was working fine locally. I moved it to a co-lo closet, and now FTP does not work. This is what my FTP client's logs say:
```

220 ProFTPD 1.3.0 Server (Max) [192.168.1.25]
USER foo
331 Password required for foo.
PASS ********
230 User foo logged in.
SYST
215 UNIX Type: L8
PWD
257 "/" is current directory.
NOOP
200 NOOP command successful
FEAT
211-Features:
 MDTM
 REST STREAM
 SIZE
211 End
PASV
227 Entering Passive Mode (192,168,1,25,228,249).

```
Based on that output, I figured that proftpd thought it was still on the local IP of 192.168.1.25 - so I added a MasqueradeAddress directive to the proftpd.conf file. However, that only gives me this log:
```

220 ProFTPD 1.3.0 Server (Max) [xxx.xxx.x.xx]
USER foo
331 Password required for foo.
PASS ********
230 User foo logged in.
SYST
215 UNIX Type: L8
PWD
257 "/" is current directory.
NOOP
200 NOOP command successful
FEAT
211-Features:
 MDTM
 REST STREAM
 SIZE
211 End
PASV
227 Entering Passive Mode (xxx,xxx,x,xx,xxx,xx).

```

With the x's replaced with the server's actual IP address.

I know for certain that the IP I added as a MasqueradeAddress is the correct one - pinging the box returns that IP, and navigating to it on the internet gets me to the website it is supposed to be hosting. However, when I attempt to connect via FTP, the above is all the message I get.

This is what appears in /var/log/proftpd/proftpd.log:
```

Feb 26 18:57:15 Max proftpd[7304] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): FTP session opened.
Feb 26 18:57:15 Max proftpd[7304] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): USER foo: Login successful.
Feb 26 18:57:15 Max proftpd[7304] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): Preparing to chroot to directory '/home/foo'
Feb 26 18:57:15 Max proftpd[7304] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): mod_delay/0.5: delaying for 76 usecs
Feb 26 18:57:21 Max proftpd[7304] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): FTP session closed.
Feb 26 18:58:49 Max proftpd[7305] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): FTP session opened.
Feb 26 18:58:49 Max proftpd[7305] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): USER foo: Login successful.
Feb 26 18:58:49 Max proftpd[7305] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): Preparing to chroot to directory '/home/foo'
Feb 26 18:58:49 Max proftpd[7305] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): mod_delay/0.5: delaying for 73 usecs
Feb 26 18:58:52 Max proftpd[7305] Max (xx.xxx.xx.xxx[xx.xxx.xx.xxx]): FTP session closed.

```

With the x's being replaced with my home computer's IP address.

Does anyone know what I could have misconfigured? The only thing I can notice that looks out of the ordinary based on my proftpd log is that nothing happens after the chroot call.

Thanks,
Girasquid

---

### Post by faulkes on 2008-02-26
Without further information on the network, I would hazard a guess that this is a
standard passv issue.

Please see this thread: [http://ubuntuforums.org/showthread.php?t=692355](http://ubuntuforums.org/showthread.php?t=692355)

Although it deals with vsftpd, the symptoms (and likely resolution via the proftpd
man page) are similar.

Faulkes

---

### Post by girasquid on 2008-02-26
> **faulkes said:**
> Without further information on the network, I would hazard a guess that this is a
standard passv issue.



thanks for the link, but I don't think it's quite the same problem - my server("Max") is running off of a static IP.

I tried changing the MasqueradeAddress to what I received from [http://corz.org/ip](http://corz.org/ip), but the log is still the same:
```

220 ProFTPD 1.3.0 Server (Max) [xxx.xxx.xxx.xxx]
USER foo
331 Password required for foo.
PASS ********
230 User foo logged in.
SYST
215 UNIX Type: L8
PWD
257 "/" is current directory.
NOOP
200 NOOP command successful
FEAT
211-Features:
 MDTM
 REST STREAM
 SIZE
211 End
PASV
227 Entering Passive Mode (xxx.xxx.xxx.xxx,195,133).

```

If I try to connect via FileZilla, this is the log:
```

Status:	Resolving IP-Address for foo.com
Status:	Connecting to 66.51.123.60:21...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.0 Server (Max) [xxx.xxx.xxx.xxx]
Command:	USER foo
Response:	331 Password required for foo.
Command:	PASS ***
Response:	230 User foo logged in.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (xxx.xxx.xxx.xxx,210,177).
Command:	LIST

```

What other information do you need about my network?

---

### Post by faulkes on 2008-02-26
What exists between machine A and machine B, i.e. a router, a NAT firewall, etc..

A static IP would not make a difference if NAT is involved.

PASSV expects that the IP sent from the server to match the IP sent from the client, if
there is a device in betwen those two, a static IP would not make a difference.

Faulkes

---

### Post by smileypaul on 2008-02-26
Its an ugly problem, i too have the same issue. Apparently there is a resolution to the problem in the other thread, but i havent had a chance to give it a shot yet.. from the looks of it, it basically querying for an ip, updating, and then restarting proftpd every 10 minutes.. not much of a resolution..

to be honest, i have tried dozens of FTP clients, and the only one that worked all of the time with proftp, was FileZilla.. 

But because of this issue, just today, i've had to ditch my ISP, and move to a smaller ISP that was willing to offer me 5 static ip's..

If you do fin da solution, please post it..

Best of Luck

---

