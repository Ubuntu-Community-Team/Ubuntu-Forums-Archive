---
title: "SSH and OpenVPN"
date: 2013-05-07
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2013-05-07
Hello, 

I'm trying to SSH into my server which is using OpenVPN from an external location. SSH via Putty works when the Server is not on the VPN. 

When I connect to my router's IP I get an error, "Server unexpectedly closed network connection" and wont let me login just a blank screen.

When I connect to the external IP my server thinks it has (the VPN IP), I get a login prompt but I can't get any further. I tried logging in normally, as root and also using my VPN account details. 

I can't find any documentation on how to SSH with a VPN connection. Could someone please explain what I need to do?

Thank you.

---

### Post by corsairetc on 2013-05-07
Do you have ping from your openvpn virtual IP address.

---

### Post by darkod on 2013-05-07
Hold on, the explanation is confusing.
So, is your server running the openvpn server or it connects to it as a client? You say "when the server is not on the vpn", does that mean it's a client?

You also say "when I connect to the external IP my server THINKS it has". It can't think anything, not yet anyway. :) It either has some IP or not. And ranges used for vpn are not external, not public.

You need to understand first how you have your system connected. Just follow the traffic. Imagine it going from your machine to the server. Where does it need to pass, imagine the whole route?

---

### Post by AmbiguousOutlier on 2013-05-07
Pinging works.

OK, I'm new to networking so I'll try to explain better: I have a home server (physically in my house) which which I can connect to via SSH using putty from my work computer (physically in my office). 

I then enable openVPN on my server in my house and connect to someones server in another country, then I SSH to my home server from my laptop connected to my home network and run this code;

wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'

I then goto my office and try to putty in with the same settings except I use the above IP address. 

Does that make sense, diagrams might be clearer. :)

---

### Post by darkod on 2013-05-07
So, you connect your server as a vpn client to another server running vpn? If that remote server has the vpn configuration set to become the gateway for all vpn clients, then your home server as a client starts using the remote server as gateway to the internet as soon as the vpn tunnel is established. So, when you check the public IP you actually get the public IP of the remote server location. Makes sense?

So, when trying to ssh into that IP you are actually trying to ssh into the remote server, not your home server. And hence you are getting declined.

That's what I think is happening.

Under the assumption the above is true, you can try this:
Find out your home server private IP after it connects to the vpn (you can still ssh to it from your home, right?). It will have a private IP on the tun0 interface it opens for the vpn. Or similar...
Then at work, connect your computer to the same remote vpn server. That will put you into the same vpn network.
After that you should be able to ssh into your home server using the private IP, since your work machine will have an IP in the same range too, being a client connected to the same vpn.

Does that make sense?

---

### Post by AmbiguousOutlier on 2013-05-08
That makes sense Darko. 

So are you basically saying I need to connect both my work pc and my home server as clients to the same vpn server? This way, they'll appear to be on the same local network and then I can connect as I do when I'm physically at home. 

However at work we have a proxy server and IT restrictions wont let me install any "proxy avoidance" software. 

Why am I not able to connect to my router's external IP address and just let that forward me to my home server?

---

### Post by darkod on 2013-05-08
Usually vpn clients are proxy aware. I wouldn't say any vpn client is proxy avoidance software although it might be considered as such since vpn will allow you to go out to the internet using a different route than your proxy.

When trying to access your server from outside, you have to take two important things in account:
1. Make sure you have the correct public IP. After you conenct your home server to the remote vpn its public IP might change since it might be routed through the vpn server. So, do not connect your home server to any vpn, and check the public IP. Or check it directly on the router.
2. Make sure in the router configuration you have port 22 (or which ever port you use for SSH if you changed the default one) forwarded to the server private IP. Also make sure the router firewall is allowing incoming traffic on port 22. Sometimes forwarding a port creates the necessary firewall rule, sometimes not. So it's best to double check it.

Also note that making your SSH publicly available will open your server to attacks. Expect people to start trying to enter your server immediately. Make sure you close SSH good. It's best to use key authentication, and in any case disable root SSH login.

Also, if your office has a fixed public IP, make the port forwarding/firewall accept traffic on your SSH port originating only from your office IP. That will help block most of the attacks.

---

### Post by AmbiguousOutlier on 2013-05-08
So I have the public IP of my router. I also have the public IP of my server once it's connected to the VPN. 

The router and has port 22 forwarded to the Private IP of my home server. DHCP is disabled and a static IP has been created. Firewall on my router has the rules set up on port 22 and TCP. (although it's temporarily disabled until I understand how this all works) 

I have also disabled root and had keys set up but I've enabled password authentication (again until I understand how it all works).

So If I connect to the public IP on my router using PuTTY and port 22 I get an error after about a minute, saying "Server unexpectedly closed network connection"

---

### Post by darkod on 2013-05-08
It should work, if all is set correctly. Double check everything. You are running sh on the default port 22 right?

---

### Post by AmbiguousOutlier on 2013-05-08
This is /etc/ssh/sshd_config

```

# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
#PasswordAuthentication no

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

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```

Does this look correct to you?

I've double checked everything else, and I restarted SSH, now back to work to see if it still doesn't let me login.

EDIT: Still doesn't work.

---

### Post by darkod on 2013-05-08
I really don't know what to say, it looks ok. There is small chance that your internet provider is blocking port 22, but that would be strange. They usually block web server and mail server ports to block people running servers at home, but I don't see why would they block 22.

Since you now have port forwarding in place, and a service listening on 22, check if the port is seen as open from the internet:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Note that if the port forwarding and firewall are set only to your office IP, you will need to allow it for all IPs temporarily so that the port check tool can be accepted. Otherwise the firewall/forwarding will block it.

PS. You said you have a proxy. Can it be your company is blocking port 22 traffic? They might not be letting you go out on port 22.

---

### Post by AmbiguousOutlier on 2013-05-08
Ok, I quickly went home and disabled openvpn. Came back to work and I can SSH in just fine. I've then tried to remotely start openvpn, at the point it makes the connection, my session freezes and I'm unable to start a new one. 

So I assume no ones blocking port 22.

I have followed this guide, I'm wanted to make my server a little more secure. Admittedly I don't fully understand everything in the guide, but I figured it would be safer to have most of it enabled. So there could be some conflicts, could you have a look please?

[http://www.thefanclub.co.za/node/50](http://www.thefanclub.co.za/node/50)


Thank you.

---

### Post by darkod on 2013-05-08
I thought we agreed to disconnect the vpn and then try the ssh from work. :) I wrote that many posts ago. When the server is connected to a vpn network it's a whole different ballgame.

OK, I'll take a look into that link and come back.

Meanwhile, i still fail to see why do you have your server into a vpn network. If you could elaborate on that, maybe we can come up with a recommendation. What do you expect to achieve with your server being into that vpn network?

---

### Post by darkod on 2013-05-08
I don't see anything wrong in that tutorial. Of course, some of the things are "too paranoid" but all of it should work out good.

I think the issue is only that you had the home server connected to the vpn and that it changes the default gateway when it's connected. Once you disconnected it, you could open the ssh session from work.

---

### Post by AmbiguousOutlier on 2013-05-08
Whoopsie, I must have crashed. :) 

I want to use a VPN as I want to download torrents and don't want ISP to know. [-X

---

### Post by darkod on 2013-05-08
That's fine but by connecting your server to a vpn network you have to understand few things:
1. The speed of the traffic might be much slower than your internet at home. And it will also depend on the vpn server connection on the other end.
2. The vpn server on the other hand will likely "impose" it's rules onto your server which from the vpn point of view is only a simple client. It might force it to use it's gateway, public IP, etc.

That might be the reason why ssh from outside doesn't work any more after you connect it to the vpn. They might be imposing restrictions which are not compatible with the ssh session from work.

---

### Post by AmbiguousOutlier on 2013-05-08
Speeds are actually fairly similar, I have an advertised line of 8mbps and frequently get close to 10mbps both when the VPN is connected and not. So I'm not complaining on that part. 

And I was assured by the Torguard VPN people that SSH is compatible, I guess I should ask their support team.

---

### Post by darkod on 2013-05-08
It might be, but in that case ask how should you access it. Maybe they have a changed port? It's easy to do port forwarding with different ports. For example, you have your ssh server listening on 22 on your server, but they want you to access Torguard IP : port 2222 and they do the translation between 2222 to 22 automatically. That's just an example.

Either send them an email, or look through their FAQs if there is some basic info there. Maybe they need to open a firewall for you?

---

### Post by darkod on 2013-05-08
I am looking into this Torguard VPN website and I can't find anything specific about ssh in the FAQ or Knowledge base. Further more, thinking about it, I believe many users use the same public IP vpn server. That would make sense, they won't make separate vpn server for each user.

If that's true, using ssh might not be as simple as you think. Imagine this, what if more users have ssh on their machine and they all have the same public IP vpn server. When you try to access that public IP with putty, where should it direct you, to which server? How does it know which user is trying to enter by ssh?

See if you can contact them to give you explanation/info about ssh but I don't see it clearly.

---

### Post by AmbiguousOutlier on 2013-05-08
Thanks for your help on this Darko, I've sent them an email asking your questions, I'll let you know what they say.

---

### Post by AmbiguousOutlier on 2013-05-13
Apparently everyone gets a different virtual public IP address, what they have done is created a static virtual private IP for my client. And then forwarded a port I specified in the region of 4xxxx to that virtual private IP. I've then forwarded on that port to my actual private IP address. 

So now if I log on to my virtual public IP address using that specified port I should get forwarded all the way to my server. In theory anyway, it still doesn't work, so will have to double check with them that they forwarded on the correct server. 

Does the theory make sense?

---

### Post by darkod on 2013-05-13
In general yes, but I'm confused with this part of your post:
> [COLOR=#000000] I've then forwarded on that port to my actual private IP address.[/COLOR]

Do you mean you are forwarding 4xxx on your home router to your private IP? You don't need to forward anything on your home router/machine in order to ssh into your hosted server. The provider needs to make sure they forward the correct port to your VM, and it seems they are doing that.

So, you should be able to ssh into your VM with the virtual public IP you have on the 4xxx port.

Unless they also have firewall activated blocking ssh or ssh is not running on the VMs at all. I don't recall, is this a VM you are controlling or the provider is controlling it? If you are controlling it, you can install ssh even if it's not installed right now, but if they are controlling the machines and offer only a set of features, you need to confirm ssh is one of them (sorry I don't recall if this was mentioned in the thread so far).

Now that you have a static public IP and a port number to work with, if the provider hasn't activated a firewall blocking ssh on that 4xxx port and if ssh service is running on the VM, you should be able to access it without any issues.

---

