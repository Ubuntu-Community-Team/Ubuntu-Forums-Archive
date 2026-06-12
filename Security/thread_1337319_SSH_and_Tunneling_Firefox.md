---
title: "SSH and Tunneling Firefox"
date: 2009-11-25
forum: Security
---

### Post by Rayve on 2009-11-25
Okay, so I finally got my SSH working without passwords (only keys) between my netbook (client) and desktop (server), through port 2222 vice 22, my question now is how to tunnel my browsing through it.  I followed the guide here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=723025](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=723025)  but I keep getting a Firefox proxy error from my netbook.  Regarding the command it says to enter: 
ssh -D 9999 -C [EMAIL="me@ipaddress.com"]me@ipaddress.com[/EMAIL]
I enter that on my netbook, right, for the browser?  And I'm entering my netbook's IP address or my desktop's?  Do I then start Firefox from the browser, or...?

Here is my config files from the desktop, in case that matters (and to ensure I'm really doing this without passwords, only keys):

sshd_config
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 2222
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 192.168.1.102
ListenAddress 0.0.0.0
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
#AuthorizedKeysFile    %h/.ssh/authorized_keys

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
 PasswordAuthentication no

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
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM no

# added 16 Nov 2009 per http://ubuntuforums.org/showthread.php?t=768648
AllowUsers candice

```Both usernames are the same (candice) which is why I edited the above file...  I commented out the ListenAddress 192.... part above because I misunderstood what I read and when I had that up, it wouldn't connect (said Port 22 refused).  Is there a way to make it so it will only accept SSHs from certain computers (IP addresses, though I use dyndns) or do the keys take care of that?

Is there anything else I can do to make it more secure?  I'll be traveling over the holidays and would like to know I'm at least a bit more secure than the average bear.  :)  Thanks, all.

---

### Post by XCan on 2009-11-25
I think you've confused yourself, heck I am confused even. This is what I do when I run ff tunneling through my workstation.
```

ssh -D 1234 me@my.ip.com -p 2222

```

After that simply open firefox and go to Edit -> Preferences -> Advanced -> Network -> Settings -> Manual proxy config. -> SOCKS Host: localhost:1234 . That's it. Know though that your dns lookups are not going through the tunnel, but your traffic is.

---

### Post by BkkBonanza on 2009-11-25
You question details are a bit confusing but I'll try to clarify what should be happening.

You can start the ssh proxy at the command prompt as suggested. Also you may find it easier to use gSTM gui app to manage the proxy (available in Synaptics).

SSH will create a proxy on your machine at port 9999 (your choice) that connects to the remote server (me@ipaddress.com, assuming you replace that with a valid server address you have). If you are using your desktop server then you need to use a connectable address, eg. 192.168... on your LAN or the public dyndns one if out on the net.

Then in Firefox or any other local app you tell it to use SOCKS v.5 proxy at localhost port 9999. SSH creates the proxy on your machine at localhost. That proxy tunnels to your server at whatever ip, and then relays traffic out from there. 

So Firefox talks to localhost:9999 -> ssh talks to server -> server opens ports on it's machine -> that talk to your real destination.

Hope this helps.

---

### Post by BkkBonanza on 2009-11-25
Also note, just saw other post above, in both Firefox and Thunderbird there are advanced config options that allow you to route DNS lookups through the proxy. 

In many situations it doesn't matter but if you are worried about someone tracking down what sites you are connecting to then you must do that. Otherwise the local sys admin can easily see via DNS traffic (port 53) what sites you were viewing.

Try google for details on exactly what options need setting. I recall there being more than one in each app.

Regarding your question about "more secure", you could make it so that only certain ips can connect to your server. It may be marginally more secure I guess. Usually using a key is secure enough and restricting ip has real limitations if you don't know where you'll be connecting from when traveling and so is likely unworkable.

If you are traveling and lose your notebook (it gets stolen?) then you may think about having a backup of your key on a usb dongle. I do that and use KeepassX to store passwords and keys in encrypted form so that such loss won't lock me out of my systems that I admin.

---

### Post by Rayve on 2009-11-25
Yeah, I think I confused myself with reading so any posts last week, heh.  Working perfectly now, thanks!

---

### Post by Rayve on 2009-12-01
This is still working, just have a quick question - I log in, tunnel my firefox, but it seems to be timing out quite often.  Is there any way I can change that?

Also, when I first do the command (ssh -D 9999 etc), it opens my netbook's keyring and asks for a password.  Can/should I remove whatever password that is trying to get to?  It's just a really random password (which is good, I know) but difficult to remember each time, heh.

Thanks, all.

---

### Post by HermanAB on 2009-12-01
Install a pre-shared SSH key and then you won't get the annoying password prompts.  Read 'man ssh-keygen' for details.

---

### Post by bodhi.zazen on 2009-12-01
Or use ssh agent ;)

---

### Post by BkkBonanza on 2009-12-01
That's odd. For me, ssh-agent has always been running by default. I don't recall changing anything but when I use ssh (for proxy or other uses) on Ubuntu it always gets the keys automatically. I see in htop that gnome-session starts ssh-agent and gpg-agent.

---

### Post by Rayve on 2009-12-02
> **HermanAB said:**
> Install a pre-shared SSH key and then you won't get the annoying password prompts.  Read 'man ssh-keygen' for details.

I have the keys set up for the regular ssh and no longer enter a password there, but this isn't at the command line, it's the GUI keyring that pops up on my netbook (the client) only when I enter the tunnel command.

---

