---
title: "[SOLVED] Installing SSH"
date: 2008-08-01
forum: Server Platforms
---

### Post by zdunham on 2008-08-01
Hi, I just installed SSH on Ubuntu Hardy, having a little trouble here's what I've done:

I ran:
```

sudo apt-get install openssh-server
sudo apt-get install ssh

```

Assume my IP was 192.168.2.1, this is what I did next:
```

ssh me@192.168.2.1

```
Then it asked for my password and everything is fine, and I also started the server obviously with

```

sudo /etc/init.d/ssh start

```

Now, I download PuTTY on a Windows machine also on the network and when I put in the IP and select SSH and port 22, it times out every time I try it. From what I've seen on the internet I don't think I've missed anything but maybe I have? Thanks for any help in advance!

---

### Post by jerome1232 on 2008-08-01
Have you established a firewall on the ssh server? (iptables is installed by default but not configured)

the following command will tell you if iptables has any policies setup.
```
sudo iptables -L
```

---

### Post by zdunham on 2008-08-01
I never installed any firewalls and there are no firewalls anywhere on the network in between the machine I installed SSH on and the machine I'm attempting to log in from, I'll go try what you just said give me 2 minutes.

---

### Post by zdunham on 2008-08-01
I ran the command you said here is what I got:

```

Chain INPUT (policy ACCEPT)
target   prot opt source     destination

Chain FORWARD (policy ACCEPT)
target   prot opt source     destination

Chain OUTPUT (policy ACCEPT)
target   prot opt source     destination

```

Don't know if that helps.

---

### Post by Vivaldi Gloria on 2008-08-01
Have you forwarded the necessary ports in your router?

---

### Post by zdunham on 2008-08-01
I'm kind of a newbie at this stuff, I'm connected to a switch so if I put in the switches IP in the browser I can connect to it as if it's a normal router?

---

### Post by WRDN on 2008-08-01
The easiest way to allow port 22 (default for SSH), is to install Firestarter (from repo's), and on the "Inbound Connections" Policy, add a rule to allow port 22. Personally, I would limit this to your network, rather than everyone.

---

### Post by rahmath on 2008-08-01
Can u ping from XP to Linux???

---

### Post by Vivaldi Gloria on 2008-08-01
> **zdunham said:**
> I'm kind of a newbie at this stuff, I'm connected to a switch so if I put in the switches IP in the browser I can connect to it as if it's a normal router?

There are different kind of switches. If yours can forward ports then, yes, the switch must forward port 22 to your ubuntu box. But that's not always enough. How does the switch connects to internet? Isn't there a modem? That should also not block port 22 and forward it.

The following site has info on how to port forward on different routers, switches. Have a look at it.

[http://portforward.com/](http://portforward.com/)

---

### Post by zdunham on 2008-08-01
I can ping the machine and it replies yes, I'll try the Firestarter idea as well.

---

### Post by Vivaldi Gloria on 2008-08-01
> **WRDN said:**
> The easiest way to allow port 22 (default for SSH), is to install Firestarter (from repo's), and on the "Inbound Connections" Policy, add a rule to allow port 22. Personally, I would limit this to your network, rather than everyone.

No, that's bad advice.

In default ubuntu install all ports are already open so his problem is not about opening ports in his ubuntu.

---

### Post by zdunham on 2008-08-01
I installed Firestarter anyways I might as well, I opened 80, 22, and 443, I have SSL working as well so I needed 443. Anything else I do with the machine still works after that but still no luck with SSH.

---

### Post by WRDN on 2008-08-01
> **Vivaldi Gloria said:**
> No, that's bad advice.

In default ubuntu install all ports are already open so his problem is not about opening ports in his ubuntu.

I had to edit the firewall settings using the method I described before SSH would work for me.
While it is true that all ports are open, no services are listening, so changes must be made to the firewall.

---

### Post by zdunham on 2008-08-01
I tried putting the IP address of the switch that the machine is connected to into the browser to see if I could check it's configuration, I want to see if port 22 is open on the switch, how can I do that?

---

### Post by jerome1232 on 2008-08-01
Well from the output of iptables -L we can see iptables is set to accept all connections from anywhere, so it's not a host based firewall, (all firestarter does is configure iptables which we know isn't the problem) I would try to telnet to the linux computer on port 22, if it gets through you'll get a response like this:
(I forget the exact syntax on windows I believe you add a colon to specify port)
```
telnet 192.168.2.1:22
SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
```

---

### Post by jerome1232 on 2008-08-01
> **zdunham said:**
> I ran the command you said here is what I got:

```

Chain INPUT (policy ACCEPT)
target   prot opt source     destination

Chain FORWARD (policy ACCEPT)
target   prot opt source     destination

Chain OUTPUT (policy ACCEPT)
target   prot opt source     destination

```

Don't know if that helps.

It's not his firewall, his firewall is set to accept all connections here. I agree firestarter will only hinder things atm.
This is either a putty setting or hardware firewall.

---

### Post by zdunham on 2008-08-01
I tried what you said from the command line and it tries port 23 anyways, then I tried PuTTY because you can use Telnet in there also and it just doesn't connect.

---

### Post by Vivaldi Gloria on 2008-08-01
> **zdunham said:**
> I installed Firestarter anyways I might as well, I opened 80, 22, and 443, I have SSL working as well so I needed 443. Anything else I do with the machine still works after that but still no luck with SSH.

You are writing the correct ip, right? If yes, then you have to be sure of two things.

(1) Port 22 reaches your machine.

(2) There isn't a setting in /etc/ssh/sshd_config which allows only local connections. For example edit that file and add 

```
ListenAddress *
```

See "man sshd_config" for more info. Also check the option called something like "AllowUsers".

I'll bet my money on option (1). Again, how does the ubuntu system connect to internet? A switch itself doesn't connect to internet. You must be connecting over a modem or router. Anything between you and the internet must forward port 22 to the ubuntu machine.

---

### Post by zdunham on 2008-08-01
Being an idiot, I can't figure out how to access the switch, I'm actually a computer science student interning at a place and this is some of my first REAL experience with network stuff. I put the switch's IP in the web browser and it says failed to open...

I'll try what you just said Gloria.

---

### Post by y@w on 2008-08-01
Are you on the same LAN?

---

### Post by zdunham on 2008-08-01
Alright in sshd_config it has Port 22 listed as the listening port, and it has setting about separating user priveleges which it has "yes" for.

And yes I'm on the same LAN.

---

### Post by y@w on 2008-08-01
You said that you opened up ports 80 and 443.. Do you have a web server running on that machine? If so, can you access it?

---

### Post by zdunham on 2008-08-01
Apache2/Subversion are on there and I can access my repositories via https and do whatever transactions I want.

I also added "AllowUsers * =" to the sshd_config and it restarted fine but didn't change anything.

---

### Post by jerome1232 on 2008-08-01
> **zdunham said:**
> I tried what you said from the command line and it tries port 23 anyways, then I tried PuTTY because you can use Telnet in there also and it just doesn't connect.

yes sorry, I just booted into windows that command should have been, ```
telnet 192.168.2.1 22
```

At any rate vivaldi gloria is correct. Either sshd isn't listening, or (I've never seen a switch with a firewall although I know they exist) that switch is blocking ports.
after you make changes to /etc/ssh/sshd_config
be sure to do this command for the changes to take affect.
```
sudo /etc/init.d/ssh restart
```

Do you have a make/model on the switch?

an afterthough:
Sometimes norton/mcafee have an outbound firewall, did you try disableing those on the windows box, or making sure they allow port 22 outbound

---

### Post by Vivaldi Gloria on 2008-08-01
I suggest you google the switch to learn how to reach its settings. No body knows there??

---

### Post by zdunham on 2008-08-01
It's Dell PowerConnect 2724, I have another one that I'm configuring that is just connected to a laptop with a crossover and I can access that one fine but this one I can't access, I feel dumb lol. And I'm "told" that there is no firewall in between these machines.

The second one I'm congifuring is the same exact model.

When I try telnet 192.168.2.1 22, it fails.

---

### Post by jerome1232 on 2008-08-01
according to [http://akamai.infoworld.com/Dell_PowerConnect_2724/product_58902.html?view=1&curNodeId=96](http://akamai.infoworld.com/Dell_PowerConnect_2724/product_58902.html?view=1&curNodeId=96) 
> For instance, these switches have no serial console capability. When powered up, they are completely inaccessible via IP, but by pressing the recessed "Management Mode" button on the front, the unit will reboot and enable the Web management with the default to a 192.168.2.1

---

### Post by y@w on 2008-08-01
Hmm. This has to be something simple :) What's the IP of the machine that you're trying to connect from?

---

### Post by zdunham on 2008-08-01
> **jerome1232 said:**
> according to [http://akamai.infoworld.com/Dell_PowerConnect_2724/product_58902.html?view=1&curNodeId=96](http://akamai.infoworld.com/Dell_PowerConnect_2724/product_58902.html?view=1&curNodeId=96)

It's in management mode and this one was set up before I worked here, I know about management mode and the settings from the identical one that I'm setting up. If only I could access this one the same way, still trying to access it.

---

### Post by zdunham on 2008-08-01
> **y@w said:**
> Hmm. This has to be something simple :) What's the IP of the machine that you're trying to connect from?


Why would you need to know that?

---

### Post by y@w on 2008-08-01
I wanted to verify that they were on the same subnet... 

Are you trying to SSH to the switch?? The only IP I see is 192.168.2.1, but you said they're on the same network.

---

### Post by zdunham on 2008-08-01
> **y@w said:**
> I wanted to verify that they were on the same subnet... 

Are you trying to SSH to the switch?? The only IP I see is 192.168.2.1, but you said they're on the same network.

I just used the IP for forum purposes thats not really it's IP, the IP's are 192.168.10.45 of the Ubuntu machine with SSH, and the Windows one is 192.168.21.50. Subnet 255.255.255.0 on both.

---

### Post by jerome1232 on 2008-08-01
Yeah I was about to say if that switch is in managment mode and that computer has an ip of 192.168.2.1 we have a conflict!

---

### Post by zdunham on 2008-08-01
> **jerome1232 said:**
> Yeah I was about to say if that switch is in managment mode and that computer has an ip of 192.168.2.1 we have a conflict!

Not necessarily, you can change the IP in management mode and it is actually 192.168.10.2

---

### Post by y@w on 2008-08-01
Ok, so are you trying to go through a NAT then?

---

### Post by zdunham on 2008-08-01
> **y@w said:**
> Ok, so are you trying to go through a NAT then?


NAT? I'm a newb.

---

### Post by y@w on 2008-08-01
Your machines are on different subnets.. Is there a router in between them? If so, my guess is you're missing a port forwarding rule.

---

### Post by Vivaldi Gloria on 2008-08-01
> **zdunham said:**
> NAT? I'm a newb.

[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

For our purposes, it's the thing in routers which assigns particular ports to particular IPs.

---

### Post by zdunham on 2008-08-01
I'll let you know in a few minutes when the firewall guru gets back from lunch, he said before that port 22 is open on all firewalls because they use SSH for other stuff but I'll make him check again, I don't have access. Shouldn't be long.

---

### Post by rahmath on 2008-08-01
run this command in your SSH server and paste the output here

$ netstat -ant

this will show you the listening ports in your SSH server. If 22 is listed there, then it is clear that SSH is running fine.

then why can;t try by setting up the IP address of both WIndows and Linux to a same subnet. like 192.168.2.50 --> windows, 192.168.2.51 --> Linux.

I guess this setting of IP, will solve your issue, if SSH is running there. And one more thing, is it was a clean installation of Ubuntu, and the SSH, then definetley you dont want to edit any setting of SSH.

hope this will help u

---

### Post by Vivaldi Gloria on 2008-08-01
> **zdunham said:**
> I also added "AllowUsers * =" to the sshd_config and it restarted fine but didn't change anything.

Why is there a "=" in that line. It should be

```
AllowUsers *
```

Also try

```
ListenAddress *
```

---

### Post by zdunham on 2008-08-01
Output for the netstat -ant:

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address   Foreign Address         State      
tcp        0      0 0.0.0.0:80      0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631   0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:443     0.0.0.0:*               LISTEN     
tcp6       0      0 :::22           :::*                    LISTEN

```

I'll have to get permission before I can change the subnet let me find out.

---

### Post by zdunham on 2008-08-01
> **Vivaldi Gloria said:**
> Why is there a "=" in that line. It should be

```
AllowUsers *
```

Also try

```
ListenAddress *
```

Tried those, didn't make a difference :(.

---

### Post by rahmath on 2008-08-01
Please dont get urself confused. Please do the following...

1 Remove SSH for your system.
$ sudo aptitude purge openssh-server


then install it again;
$ sudo aptitude install openssh-server

then run;

try from Windowz;

if not set the  IP address of both system to same subnet like 192.168.2.50 amd 192.168.2.51

then try...

this procedure should work...

---

### Post by Vivaldi Gloria on 2008-08-01
We already know that sshd works OK because you can ssh from the ubuntu box itself. You said so in the first post, right?

So this is an issue of reaching the machine remotely.

---

### Post by zdunham on 2008-08-01
> **Vivaldi Gloria said:**
> We already know that sshd works OK because you can ssh from the ubuntu box itself. You said so in the first post, right?

So this is an issue of reaching the machine remotely.


Yes I can access it from the ubuntu box itself.
I put "ssh me@192.168.10.45" or "ssh me@localhost" and it's fine.

---

### Post by y@w on 2008-08-01
> **Vivaldi Gloria said:**
> We already know that sshd works OK because you can ssh from the ubuntu box itself. You said so in the first post, right?

So this is an issue of reaching the machine remotely.

Agreed. I'd suggest either waiting for the person you mentioned to help with the firewall. Just "out of the box", SSH server on Ubuntu works just fine.

---

### Post by Vivaldi Gloria on 2008-08-01
Why doesn't the firewall guru help you?

---

### Post by zdunham on 2008-08-01
> **Vivaldi Gloria said:**
> Why doesn't the firewall guru help you?


He's at lunch still haha.

---

### Post by Vivaldi Gloria on 2008-08-01
y@w, welcome to the forums btw. ;)

---

### Post by zdunham on 2008-08-01
There isn't anything special I need on my Windows machine as far as software right? I mean I have PuTTY and the command prompt.

---

### Post by jerome1232 on 2008-08-01
Yup just putty

---

### Post by zdunham on 2008-08-01
Alright, firewall man just got back, according to him there is nothing blocking the way between these 2 machines, and nothing blocking port 22. He also said it doesn't matter what subnet we're on and showed me as he SSH'd to a different server on another subnet also within the network. So now I'm back to square one and have no idea what's wrong.

I'm just going to reinstall and try once more.

---

### Post by jerome1232 on 2008-08-01
> **zdunham said:**
> Alright, firewall man just got back, according to him there is nothing blocking the way between these 2 machines, and nothing blocking port 22. He also said it doesn't matter what subnet we're on and showed me as he SSH'd to a different server on another subnet also within the network. So now I'm back to square one and have no idea what's wrong.

I'm just going to reinstall and try once more.

Can you reach that other ssh server from this particular windows box?

Could that (the one the firwall man used) other machine reach your ssh server?

---

### Post by zdunham on 2008-08-01
> **jerome1232 said:**
> Can you reach that other ssh server from this particular windows box?

Could that (the one the firwall man used) other machine reach your ssh server?

His machine couldn't reach the Ubuntu box either, but it could reach the other server's ssh.

---

### Post by dannyboy79 on 2008-08-01
show us your /etc/ssh/sshd_config file or post it on pastebin.org and past link here. You aren't using any kind of authentification?

---

### Post by zdunham on 2008-08-01
Here is sshd_config

```

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
PermitRootLogin yes
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
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by jerome1232 on 2008-08-01
Just to ensure there's no firewalls (just in case since you did install firestarter)
I would run a few commands
this one will remove firestarter and it's config files
```
sudo apt-get remove --purge firestarter
```
since firestarter is a gui for iptables we need to clear iptables rules.
```
sudo iptables -F
```
and lets make sure defaults are set to accept
```
sudo -i
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -L   #it should look like this now
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
exit  #don't forget to run this so you aren't root anymore
```
if iptables looks like that ubuntu is not blocking the connection

When you reinstall ssh server make sure to remove it with the --purge option so when you install it you will have fresh config files.

If later you want to configure iptables properly I'd recommend UFW, it's installed by default and is very easy to use.

---

### Post by dannyboy79 on 2008-08-01
#PasswordAuthentication yes

this should be uncommented and changed to no  if you want to use RSA/DSA keys with the authorized_keys file. So did you use that putty program to convert your ssh key into a putty key?

also, please post the results of this command

netstat -pant | grep 22

from the machine that's running the ssh server.

you also have this in your config:
PermitRootLogin yes

which is a no no in my opinion.

---

### Post by zdunham on 2008-08-01
> **jerome1232 said:**
> Just to ensure there's no firewalls (just in case since you did install firestarter)
I would run a few commands
this one will remove firestarter and it's config files
```
sudo apt-get remove --purge firestarter
```
since firestarter is a gui for iptables we need to clear iptables rules.
```
sudo iptables -F
```
and lets make sure defaults are set to accept
```
sudo -i
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -L   #it should look like this now
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
exit  #don't forget to run this so you aren't root anymore
```
if iptables looks like that ubuntu is not blocking the connection

When you reinstall ssh server make sure to remove it with the --purge option so when you install it you will have fresh config files.

If later you want to configure iptables properly I'd recommend UFW, it's installed by default and is very easy to use.


Did all that, still nothing.

---

### Post by zdunham on 2008-08-01
> **dannyboy79 said:**
> #PasswordAuthentication yes

this should be uncommented and changed to no  if you want to use RSA/DSA keys with the authorized_keys file. So did you use that putty program to convert your ssh key into a putty key?

also, please post the results of this command

netstat -pant | grep 22

from the machine that's running the ssh server.

you also have this in your config:
PermitRootLogin yes

which is a no no in my opinion.

About to do this, get back to you in a few.

---

### Post by zdunham on 2008-08-01
Here is the output for the netstat:

```

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp6   0   0 :::22          :::*               LISTEN      -    

```

---

### Post by jerome1232 on 2008-08-01
It's gotta be something else blocking the port then, your machine is configured correctly as far as I can see.

With iptables clear nothing on ubuntu will block any port

When you install ssh-server with a default setup it will work out of the box.

If your on different subnet there has to be a router/NAT device letting the networks talk, and it's responsible for forwarding ports to correct machines, I think that is where the error lies.

Am I mistaken on any of this?

---

### Post by zdunham on 2008-08-01
> **jerome1232 said:**
> It's gotta be something else blocking the port then, your machine is configured correctly as far as I can see.

With iptables clear nothing on ubuntu will block any port

When you install ssh-server with a default setup it will work out of the box.

If your on different subnet there has to be a router/NAT device letting the networks talk, and it's responsible for forwarding ports to correct machines, I think that is where the error lies.

Am I mistaken on any of this?

Makes sense to me but my firewall guru (Sounds stupid) says otherwise, I haven't worked at this place long so I don't know the whole network structure but he says that nothing is blocking it.

---

### Post by y@w on 2008-08-01
Is there another machine on this network that you can try this from? You could always just plug your machine into the same network.. 

It may not be that there's anything blocking it, just that there's a route that's incorrect. I would try it while you're on the same subnet, on the same switch. That'll narrow down if it's a configuration problem on the machine or a networking issue.

---

### Post by zdunham on 2008-08-01
> **y@w said:**
> Is there another machine on this network that you can try this from? You could always just plug your machine into the same network.. 

It may not be that there's anything blocking it, just that there's a route that's incorrect. I would try it while you're on the same subnet, on the same switch. That'll narrow down if it's a configuration problem on the machine or a networking issue.


We tried from 2 other machines. Didn't work on either of them, it was the machines of the 2 other systems guys I work with.

---

### Post by dannyboy79 on 2008-08-01
what does the command

route 

return?

---

### Post by zdunham on 2008-08-01
> **dannyboy79 said:**
> what does the command

route 

return?


I'm guessing you mean on my regular Windows machine.

```

Manipulates network routing tables.

ROUTE [-f] [-p] [command [destination]
                  [MASK netmask]  [gateway] [METRIC metric]  [IF interface]

  -f           Clears the routing tables of all gateway entries.  If this is
               used in conjunction with one of the commands, the tables are
               cleared prior to running the command.
  -p           When used with the ADD command, makes a route persistent across
               boots of the system. By default, routes are not preserved
               when the system is restarted. Ignored for all other commands,
               which always affect the appropriate persistent routes. This
               option is not supported in Windows 95.
  command      One of these:
                 PRINT     Prints  a route
                 ADD       Adds    a route
                 DELETE    Deletes a route
                 CHANGE    Modifies an existing route
  destination  Specifies the host.
  MASK         Specifies that the next parameter is the 'netmask' value.
  netmask      Specifies a subnet mask value for this route entry.
               If not specified, it defaults to 255.255.255.255.
  gateway      Specifies gateway.
  interface    the interface number for the specified route.
  METRIC       specifies the metric, ie. cost for the destination.

All symbolic names used for destination are looked up in the network database
file NETWORKS. The symbolic names for gateway are looked up in the host name
database file HOSTS.

If the command is PRINT or DELETE. Destination or gateway can be a wildcard,
(wildcard is specified as a star '*'), or the gateway argument may be omitted.

If Dest contains a * or ?, it is treated as a shell pattern, and only
matching destination routes are printed. The '*' matches any string,
and '?' matches any one char. Examples: 157.*.1, 157.*, 127.*, *224*.
Diagnostic Notes:
    Invalid MASK generates an error, that is when (DEST & MASK) != DEST.
    Example> route ADD 157.0.0.0 MASK 155.0.0.0 157.55.80.1 IF 1
             The route addition failed: The specified mask parameter is invalid.
 (Destination & Mask) != Destination.

Examples:

    > route PRINT
    > route ADD 157.0.0.0 MASK 255.0.0.0  157.55.80.1 METRIC 3 IF 2
             destination^      ^mask      ^gateway     metric^    ^
                                                         Interface^
      If IF is not given, it tries to find the best interface for a given
      gateway.
    > route PRINT
    > route PRINT 157*          .... Only prints those matching 157*
    > route CHANGE 157.0.0.0 MASK 255.0.0.0 157.55.80.5 METRIC 2 IF 2

      CHANGE is used to modify gateway and/or metric only.
    > route PRINT
    > route DELETE 157.0.0.0
    > route PRINT


```

---

### Post by dannyboy79 on 2008-08-01
you never answered me about the RSA/DSA key conversion for putty?

and no, I was asking what the route command returned from your ssh server (ubuntu)

---

### Post by zdunham on 2008-08-01
> **dannyboy79 said:**
> you never answered me about the RSA/DSA key conversion for putty?


Ah yes I was going to ask you about that, how can I tell if PuTTY is doing that? I pretty much open it and then go to SSH and put the IP in and port 22.

I'll get the route for you.

---

### Post by zdunham on 2008-08-01
Here is route on Ubuntu machine:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

```

---

### Post by dannyboy79 on 2008-08-01
well according to your sshd_config, you're using public/private keys for securing your ubuntu ssh server. if putty doesn't know the public key, how's it going to connect. Let me see this log file after you have tried to connect a few times

cat /var/log/auth.log

---

### Post by zdunham on 2008-08-01
It's pretty huge from all of the stuff I've done today but here it is:

```

Aug  1 08:17:01 files-300 CRON[8863]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 08:17:01 files-300 CRON[8863]: pam_unix(cron:session): session closed for user root
Aug  1 09:17:01 files-300 CRON[8866]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 09:17:01 files-300 CRON[8866]: pam_unix(cron:session): session closed for user root
Aug  1 10:04:09 files-300 gdm[8870]: pam_unix(gdm:session): session opened for user zdunham by (uid=0)
Aug  1 10:04:09 files-300 gnome-keyring-daemon[8904]: adding removable location: volume_uuid_bdb9a55f_2dd5_4da3_8328_b8214937ab75 at /
Aug  1 10:04:09 files-300 gnome-keyring-daemon[8904]: location device 'FILE' already registered at: /
Aug  1 10:04:36 files-300 sudo: pam_unix(sudo:auth): authentication failure; logname=zdunham uid=0 euid=0 tty=/dev/pts/1 ruser= rhost=  user=zdunham
Aug  1 10:04:48 files-300 sudo: pam_unix(sudo:auth): conversation failed
Aug  1 10:04:49 files-300 sudo: pam_unix(sudo:auth): auth could not identify password for [zdunham]
Aug  1 10:04:49 files-300 sudo:  zdunham : pam_authenticate: Conversation error ; TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/vim /etc/apache2/sites-available/files-300.stellarfinancial.com
Aug  1 10:05:07 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/nautilus
Aug  1 10:05:07 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:05:07 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:06:12 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/apache2 restart
Aug  1 10:06:12 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:06:12 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:14:03 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem
Aug  1 10:14:04 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:14:04 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:16:52 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/apache2 restart
Aug  1 10:16:52 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:16:52 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:17:01 files-300 CRON[9524]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 10:17:01 files-300 CRON[9524]: pam_unix(cron:session): session closed for user root
Aug  1 10:22:15 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/svnadmin create /svn/work
Aug  1 10:22:15 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:22:15 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:23:00 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/apache2 restart
Aug  1 10:23:00 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:23:00 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:30:21 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/apt-get install ssh
Aug  1 10:30:21 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:30:21 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:30:35 files-300 useradd[9970]: new user: name=sshd, UID=112, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Aug  1 10:30:35 files-300 usermod[9971]: change user `sshd' password
Aug  1 10:30:35 files-300 chage[9972]: changed password expiry for sshd
Aug  1 10:30:35 files-300 sshd[10010]: Server listening on :: port 22.
Aug  1 10:30:35 files-300 sshd[10010]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 10:32:06 files-300 sshd[10038]: Accepted password for zdunham from 127.0.0.1 port 51223 ssh2
Aug  1 10:32:06 files-300 sshd[10049]: pam_unix(sshd:session): session opened for user zdunham by (uid=0)
Aug  1 10:52:30 files-300 sshd[10329]: Accepted password for zdunham from 127.0.0.1 port 33607 ssh2
Aug  1 10:52:30 files-300 sshd[10332]: pam_unix(sshd:session): session opened for user zdunham by (uid=0)
Aug  1 10:53:01 files-300 sudo:  zdunham : TTY=unknown ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/sbin/synaptic
Aug  1 10:53:01 files-300 sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug  1 10:53:01 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:53:48 files-300 sshd[10408]: Accepted password for zdunham from 127.0.0.1 port 57624 ssh2
Aug  1 10:53:48 files-300 sshd[10411]: pam_unix(sshd:session): session opened for user zdunham by (uid=0)
Aug  1 10:54:28 files-300 sudo:  zdunham : TTY=pts/5 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/apt-get install ssh
Aug  1 10:54:28 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 10:54:28 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 10:54:39 files-300 sshd[10483]: Accepted password for zdunham from 127.0.0.1 port 57625 ssh2
Aug  1 10:54:39 files-300 sshd[10486]: pam_unix(sshd:session): session opened for user zdunham by (uid=0)
Aug  1 11:01:37 files-300 sudo:  zdunham : TTY=pts/6 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/apt-get install openssh-server
Aug  1 11:01:37 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:01:37 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:02:06 files-300 sudo:  zdunham : TTY=pts/6 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh start
Aug  1 11:02:06 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:02:06 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:06:29 files-300 sudo:  zdunham : TTY=pts/6 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh restart
Aug  1 11:06:29 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:06:29 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:06:29 files-300 sshd[10010]: Received signal 15; terminating.
Aug  1 11:06:29 files-300 sshd[10736]: Server listening on :: port 22.
Aug  1 11:06:29 files-300 sshd[10736]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 11:09:00 files-300 sudo:  zdunham : TTY=pts/6 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh restart
Aug  1 11:09:00 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:09:00 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:09:00 files-300 sshd[10736]: Received signal 15; terminating.
Aug  1 11:09:00 files-300 sshd[10790]: Server listening on :: port 22.
Aug  1 11:09:00 files-300 sshd[10790]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 11:11:43 files-300 sudo:  zdunham : TTY=unknown ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/sbin/synaptic
Aug  1 11:11:43 files-300 sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug  1 11:11:43 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:14:10 files-300 sshd[10861]: Accepted password for zdunham from 192.168.10.45 port 52262 ssh2
Aug  1 11:14:11 files-300 sshd[10866]: pam_unix(sshd:session): session opened for user zdunham by (uid=0)
Aug  1 11:14:53 files-300 sudo:  zdunham : TTY=pts/7 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh restart
Aug  1 11:14:53 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:14:53 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:14:53 files-300 sshd[10790]: Received signal 15; terminating.
Aug  1 11:14:54 files-300 sshd[10914]: Server listening on :: port 22.
Aug  1 11:14:54 files-300 sshd[10914]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 11:15:11 files-300 sshd[10049]: pam_unix(sshd:session): session closed for user zdunham
Aug  1 11:15:11 files-300 sshd[10332]: pam_unix(sshd:session): session closed for user zdunham
Aug  1 11:15:12 files-300 sshd[10411]: pam_unix(sshd:session): session closed for user zdunham
Aug  1 11:15:12 files-300 sshd[10486]: pam_unix(sshd:session): session closed for user zdunham
Aug  1 11:15:12 files-300 sshd[10866]: pam_unix(sshd:session): session closed for user zdunham
Aug  1 11:17:01 files-300 CRON[10964]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 11:17:01 files-300 CRON[10964]: pam_unix(cron:session): session closed for user root
Aug  1 11:31:01 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/sbin/iptables -L
Aug  1 11:31:01 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:31:01 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:36:42 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/nautilus
Aug  1 11:36:42 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:36:42 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:48:35 files-300 polkit-grant-helper[11431]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 11402 [uid=1000] [auth=zdunham]
Aug  1 11:48:48 files-300 sshd[10914]: Received SIGHUP; restarting.
Aug  1 11:48:49 files-300 sshd[11533]: Server listening on :: port 22.
Aug  1 11:48:49 files-300 sshd[11533]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 11:49:16 files-300 sshd[11533]: Received SIGHUP; restarting.
Aug  1 11:49:16 files-300 sshd[11742]: Server listening on :: port 22.
Aug  1 11:49:16 files-300 sshd[11742]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 11:57:23 files-300 sudo:  zdunham : TTY=unknown ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/sbin/synaptic
Aug  1 11:57:23 files-300 sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug  1 11:57:23 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 11:58:52 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/sbin/firestarter
Aug  1 11:58:52 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 11:58:52 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 12:01:53 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/sbin/firestarter
Aug  1 12:01:53 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 12:01:53 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 12:17:01 files-300 CRON[12750]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 12:17:01 files-300 CRON[12750]: pam_unix(cron:session): session closed for user root
Aug  1 12:19:26 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/nautilus
Aug  1 12:19:26 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 12:19:26 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 12:25:45 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh restart
Aug  1 12:25:45 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 12:25:45 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 12:25:45 files-300 sshd[11742]: Received signal 15; terminating.
Aug  1 12:25:45 files-300 sshd[12912]: Server listening on :: port 22.
Aug  1 12:25:45 files-300 sshd[12912]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 13:06:59 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/bin/netstat -ant
Aug  1 13:06:59 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 13:06:59 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 13:10:29 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh restart
Aug  1 13:10:30 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 13:10:30 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 13:10:30 files-300 sshd[12912]: Received signal 15; terminating.
Aug  1 13:10:30 files-300 sshd[13480]: Server listening on :: port 22.
Aug  1 13:10:30 files-300 sshd[13480]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 13:17:01 files-300 CRON[13563]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 13:17:01 files-300 CRON[13563]: pam_unix(cron:session): session closed for user root
Aug  1 14:05:28 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/aptitude purge openssh-server
Aug  1 14:05:29 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:05:29 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:05:44 files-300 sshd[13480]: Received signal 15; terminating.
Aug  1 14:05:45 files-300 userdel[14215]: delete user `sshd' 
Aug  1 14:05:57 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/apt-get install openssh-server
Aug  1 14:05:57 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:05:57 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:06:03 files-300 useradd[14294]: new user: name=sshd, UID=112, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Aug  1 14:06:03 files-300 usermod[14295]: change user `sshd' password
Aug  1 14:06:04 files-300 chage[14296]: changed password expiry for sshd
Aug  1 14:06:04 files-300 sshd[14334]: Server listening on :: port 22.
Aug  1 14:06:04 files-300 sshd[14334]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 14:06:10 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh restart
Aug  1 14:06:10 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:06:10 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:06:10 files-300 sshd[14334]: Received signal 15; terminating.
Aug  1 14:06:10 files-300 sshd[14361]: Server listening on :: port 22.
Aug  1 14:06:10 files-300 sshd[14361]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 14:14:52 files-300 sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=zdunham
Aug  1 14:14:56 files-300 sudo:  zdunham : 1 incorrect password attempt ; TTY=unknown ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/sbin/firestarter
Aug  1 14:15:05 files-300 sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=zdunham
Aug  1 14:17:01 files-300 CRON[14523]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 14:17:01 files-300 CRON[14523]: pam_unix(cron:session): session closed for user root
Aug  1 14:17:04 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/nautilus
Aug  1 14:17:04 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:17:04 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:26:17 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge firestarter
Aug  1 14:26:17 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:26:18 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:26:43 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/sbin/iptables -F
Aug  1 14:26:43 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:26:43 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:26:47 files-300 sudo:  zdunham : TTY=pts/2 ; PWD=/home/zdunham ; USER=root ; COMMAND=/bin/bash
Aug  1 14:26:47 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:26:47 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:28:36 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge openssh-server
Aug  1 14:28:36 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:28:36 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:28:41 files-300 sshd[14361]: Received signal 15; terminating.
Aug  1 14:28:41 files-300 userdel[14792]: delete user `sshd' 
Aug  1 14:28:48 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/apt-get install openssh-server
Aug  1 14:28:48 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:28:48 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:28:56 files-300 useradd[14869]: new user: name=sshd, UID=112, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Aug  1 14:28:56 files-300 usermod[14870]: change user `sshd' password
Aug  1 14:28:56 files-300 chage[14871]: changed password expiry for sshd
Aug  1 14:28:56 files-300 sshd[14909]: Server listening on :: port 22.
Aug  1 14:28:56 files-300 sshd[14909]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 14:29:07 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh start
Aug  1 14:29:07 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:29:08 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:32:43 files-300 sudo:  zdunham : TTY=pts/3 ; PWD=/home/zdunham ; USER=root ; COMMAND=/usr/bin/nautilus
Aug  1 14:32:43 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:32:43 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:35:44 files-300 sudo:  zdunham : TTY=pts/1 ; PWD=/home/zdunham ; USER=root ; COMMAND=/etc/init.d/ssh restart
Aug  1 14:35:44 files-300 sudo: pam_unix(sudo:session): session opened for user root by zdunham(uid=0)
Aug  1 14:35:44 files-300 sudo: pam_unix(sudo:session): session closed for user root
Aug  1 14:35:44 files-300 sshd[14909]: Received signal 15; terminating.
Aug  1 14:35:44 files-300 sshd[15082]: Server listening on :: port 22.
Aug  1 14:35:44 files-300 sshd[15082]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 15:17:01 files-300 CRON[15583]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  1 15:17:01 files-300 CRON[15583]: pam_unix(cron:session): session closed for user root

```

---

### Post by zdunham on 2008-08-01
I'm going to be leaving work at 4 so anything else I'll have to try on Monday. Thanks for all the help by the way.

I saw something in there just now that might have said that port 22 was already being used. Maybe you can confirm that not sure thought. If that is the case, what else could be using it? Or maybe it is listed twice in a config file that it shouldn't be.

---

### Post by jerome1232 on 2008-08-01
> **dannyboy79 said:**
> well according to your sshd_config, you're using public/private keys for securing your ubuntu ssh server. if putty doesn't know the public key, how's it going to connect. Let me see this log file after you have tried to connect a few times

cat /var/log/auth.log

if telnet ip.address.stuff 22 timed out nothing is reaching his machine to attempt to auth so I'm not sure why looking at that auth log would help.

That 192.168.10.1 address in your route is probably the?/a? router.

btw my auth.log has those "port already in use" messages but ssh works flawless.

Even if his sshd_config is set to only allow rsa/dsa keys and putty tries to auth with no key, putty will pop an error that says something about an authentication method not availble.

---

### Post by zdunham on 2008-08-01
> **jerome1232 said:**
> if telnet ip.address.stuff 22 timed out nothing is reaching his machine to attempt to auth so I'm not sure why looking at that auth log would help.

That 192.168.10.1 address in your route is probably the?/a? router.

btw my auth.log has those "port already in use" messages but ssh works flawless.

Even if his sshd_config is set to only allow rsa/dsa keys and putty tries to auth with no key, putty will pop an error that says something about an authentication method not availble.


This is what I think is telling us something about the port:

```

Aug  1 14:28:56 files-300 sshd[14909]: Server listening on :: port 22.
Aug  1 14:28:56 files-300 sshd[14909]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.

```

---

### Post by jerome1232 on 2008-08-01
```
Aug  1 08:41:41 ubuntu sshd[5012]: Server listening on :: port 22.
Aug  1 08:41:41 ubuntu sshd[5012]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 08:42:19 ubuntu sshd[6246]: Server listening on :: port 22.
Aug  1 08:42:21 ubuntu sshd[6246]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 09:01:32 ubuntu sshd[5013]: Server listening on :: port 22.
Aug  1 09:01:32 ubuntu sshd[5013]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 09:02:08 ubuntu sshd[6065]: Server listening on :: port 22.
Aug  1 09:02:08 ubuntu sshd[6065]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 10:16:26 ubuntu sshd[5010]: Server listening on :: port 22.
Aug  1 10:16:27 ubuntu sshd[5010]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug  1 10:17:03 ubuntu sshd[6240]: Server listening on :: port 22.
Aug  1 10:17:04 ubuntu sshd[6240]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
```

Yeah mine does that too. Yet it works so I don't believe that to be a problem. If you did (while logged onto the ssh server:
```
ssh localhost
```
or if you did
```
telnet localhost 22
``` 
They will come back with responses. Those are just ways to see if it's listening like it should.
Plus the netstat commands you've run all show the ssh daemon to be listening on port 22.

---

### Post by dannyboy79 on 2008-08-01
do this instead

cat /var/log/auth.log | grep sshd

I see something in there that's weird but can't stand looking at all the other stuff.

i think your hosts file is screwed up, it shouldn't be  listening on 0.0.0.0.0. 

When I ssh into my ubuntu server with putty, I use public/private key pair, I can ssh in from work, then ssh into itself from itself and not receive the errors you guys are getting, "Server listening on :: port 22.
Aug  1 10:16:27 ubuntu sshd[5010]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use."

so I don't know what's up. If you're using rsa/dsa keys and your password auth is turned off, then why is it letting you enter a password? here's the line from your auth.log

```
Aug  1 10:32:06 files-300 sshd[10038]: Accepted password for zdunham from 127.0.0.1 port 51223 ssh2
Aug  1 10:32:06 files-300 sshd[10049]: pam_unix(sshd:session): session opened for user zdunham by (uid=0)
Aug  1 10:52:30 files-300 sshd[10329]: Accepted password for zdunham from 127.0.0.1 port 33607 ssh2
Aug  1 10:52:30 files-300 sshd[10332]: pam_unix(sshd:session): session opened for user zdunham by (uid=0)
```

---

### Post by dannyboy79 on 2008-08-01
> **jerome1232 said:**
> 
Even if his sshd_config is set to only allow rsa/dsa keys and putty tries to auth with no key, putty will pop an error that says something about an authentication method not availble.
that's why I suggested before that he uncomment the line
#PasswordAuthentication yes
and make it say
PasswordAuthentication no

that's why he's not getting errors from putty about not having the correct key.

---

### Post by jerome1232 on 2008-08-01
I did notice he deleted the sshd user and recreated it a few times, I'm guessing that's when he reinstalled ssh-server though.

---

### Post by zdunham on 2008-08-01
> **jerome1232 said:**
> I did notice he deleted the sshd user and recreated it a few times, I'm guessing that's when he reinstalled ssh-server though.

That is when I reinstalled it, I'll try all this out on Monday at post.

---

### Post by zdunham on 2008-08-04
> **dannyboy79 said:**
> 
i think your hosts file is screwed up, it shouldn't be  listening on 0.0.0.0.0. 


Where is the hosts file located?

---

### Post by jerome1232 on 2008-08-04
/etc/hosts 
     My ssh server listens on that 0.0.0.0 and works though, as a side note.

---

### Post by zdunham on 2008-08-04
Alright, I've finally come to the conclusion that there absolutely MUST be something going on that is not on that machine itself. If SSH is supposed to work right after install and it does work on the local machine, it just has to be something else. Someone here brought up the fact that it is timing out rather than giving a different error and that seems to me like it just can't even get TO the machine.

---

### Post by zdunham on 2008-08-04
We got it working, the big boss came back and made firewall guru check the settings and what do you know it had nothing to do with me, now it works, thanks for all your help you guys are amazing.

---

### Post by jerome1232 on 2008-08-04
I know this is late, Don't know why I didn't think of this sooner but this might be for future refrence I guess.

A good way to have figured out if it was your machine not configured right or a firwall out there on the network would be like so (I'll explain in the code)

```
sudo -i            # gives you root, we'll need root privilages alot here and I don't like typing sudo all the time
ufw default deny   # this sets iptables to reject all connections
ufw logging on     # this logs all rejected connections
ufw enable         # this actually turns the firewall on 
exit               # relinquish root
```

now try and hit the machine a few times (no don't smack it, just try and connect from other machines), If the packets are actually hitting the server, iptables will reject the packets and start logging all rejected packets. So lets see if the firewall got hit with packets.
The following commands sort through syslog for 'UFW' then creates a text file with the UFW entries called rejected.log
```
sudo grep UFW /var/log/syslog | cat >rejected.log
gedit rejected.log   # now we are opening our new file
```

If there are hits in here then something is missconfigured on your machine the packets do make it there, if nothing is here then the problem lay elsewhere. Now to undo that firewall

```
sudo ufw disable   # that turns off the firewall
```

---

### Post by zdunham on 2008-08-05
That is some good reference thanks for that.

---

