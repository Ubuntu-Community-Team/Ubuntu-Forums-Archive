---
title: "ubuntu server, ssh, write failed: broken pipe"
date: 2010-11-17
forum: Server Platforms
---

### Post by hobbsc on 2010-11-17
I'm getting some bizarre behavior with Ubuntu Server 10.04 64bit on two of our new servers (both fresh installs).  I have ubuntu server (same version) deployed on 4-5 other servers without this issue.

Initially I cannot ssh into a fresh server install until I manually set the address that the ssh server is listening on in /etc/ssh/sshd_config.  Once I've connected, I seem to be kicked out at random intervals with the following error:

Write failed: Broken pipe

Using "ssh -vv" doesn't show any other information.  When I'm kicked out in this manner, I cannot reconnect for another seemingly random period of time.  Sometimes a few seconds, others a few minutes.  If I run "netstat -nap|grep :22", I can see that my connection still exists after the write failed error.  I can't seem to re-connect until that connection drops.

After one of these errors, if I hop onto the server from the console, ssh into another machine, and then attempt to ssh back into the server, everything works fine.

Using "-o TCPKeepAlive=yes" client side doesn't seem to effect anything.  I've disabled both iptables and ufw on the server.  AppArmor is not showing any enforced profiles and SELinux isn't installed.

Anyone have any thoughts?  :confused:

Thanks!

EDIT:  my logs aren't reporting any errors.

---

### Post by hobbsc on 2010-11-17
Note that when I try to get back in after the broken pipe error, this is the error I get:

ssh: connect to host 172.22.50.92 port 22: Connection refused

And nmap no longer shows port 22 as being open.

---

### Post by koenn on 2010-11-17
couple of guesses:

is there something in your sshd.conf that wouild limit a user to one concurrent connection ? could explain while you can't connect again after you were thrown out.

is there something specific you are doing in the ssh session that might fail or is it really randomly ?

the write error and broken pipe suggests ssh(d) is trying to send output to an other process, and fails. maybe it's trying to log through syslogd and fails -- is there something you customized about logging or so ? Or anything else out of the ordinary you can think of along the liners of 'sshd output to another program' ?

---

### Post by hobbsc on 2010-11-18
Nothing fancy going on in the ssh conf, with my logs, or any other setup.  This is a box stock install.  I'd be happy to paste the sshd_config and any logs if it'd help.

This same issue occurs if I use virt-manager locally to connect to one of these machines via ssh or if I use nautilus to view files via ssh (sftp?).

---

### Post by jpl888 on 2010-11-18
Sounds like a connectivity issue. I normally get broken pipe errors if I am in on a machine over the internet and the internet connection drops.

Try a different switch of something if you can.

---

### Post by CharlesA on 2010-11-18
Is there anything set to run when you connect via SSH?

---

### Post by hobbsc on 2010-11-18
Nothing is set to run on connect.  I've changed the cables out and checked the switchports (it's a Cisco stack).  The functioning servers are on the same switch.

I don't think the equipment in the middle is an issue.  When I run ubuntu server guests on those hosts, I don't have the same connectivity problems.  I can ssh into the guests without any timeout, I left one session open overnight and still had the same issue with the host.

I'll move them to a different switch and see if that fixes anything.

---

### Post by CharlesA on 2010-11-18
Does anything happen if you purge openssh-server and reinstall it?

---

### Post by hobbsc on 2010-11-19
Re-installing ssh didn't do anything.  I even built OpenSSH from source to no avail.

---

### Post by CharlesA on 2010-11-19
That's so strange. I've not run into that sort of thing before, but I kinda think that ssh isn't to blame.

Did a quick search and found this: [http://www.unix.com/unix-dummies-questions-answers/9832-broken-pipe.html](http://www.unix.com/unix-dummies-questions-answers/9832-broken-pipe.html)

Are you using the same client to connect to each machine via ssh?

---

### Post by hobbsc on 2010-11-19
I've used several different clients, but I generally use the same one.

Dell seems to think that we've got a bad motherboard in the server.  Having that replaced to see if it resolves the issue.

---

### Post by CharlesA on 2010-11-19
Keep us updated. Hope that fixes the problem. :)

---

### Post by Artyom7 on 2011-01-06
hi guys,
i have been facing a similar problem for the last 2 - 3 hours.
i keep getting disconnected from my server with that error message.

What i noticed is that this problem started occurring when i was messing around with iptables for internet connection sharing.

I would randomly lose connection to the server. when i tried to reconnect immediately, i got the same error ( connection refused on port 22 ). A minute later i was able to connect again.

i used this guide:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

the only iptables command i executed were these :
```

sudo iptables -A FORWARD -o eth0 -i eth1 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

```

Also, it coincides with me losing my internet connection on the same machine from which i ssh to the server..

maybe check your firewall?

---

### Post by flickerfly on 2011-02-03
I'm experiencing the same ssh problems with a virtual dell server. I'm very curious if the motherboard replacement worked for you.

---

### Post by ar-grig on 2011-09-26
I have the same issue. I can add, that after server restart I can connect. Then I get the same errors: broken pipe, connection refused. But I still can connect from different ip, the connection remains few minutes and then the same story with broken pipe and connection refused. It is not a hardware problem because the server was working pretty good before switching to ubuntu 10.04.
Have you any good news on the issue ?
Thank you.

---

### Post by archenroot on 2011-10-07
Hey, I am facing the same issue when connection from my notebook to server located in DMZ. I tried to add:
SSH client config file> /etc/ssh/ssh_config 
line> ServerAliveInterval 60
SSH daemon config file> /etc/ssh/sshd_config
line> ClientAliveInterval 60

Hope it will solve my problem as soon as I am not connected over internet, so I think this is not related to some broken communication on way of signal, but will see...

Ladislav

---

### Post by ar-grig on 2011-10-07
I can also add that the same system and configuration is installed on several servers with the same hardware and only one of them have the issue ..... System installation was done by cloning the working system .....  It seems to be a bit of magic here ....

---

### Post by FaceMuncher on 2011-12-29
I'm not using Ubuntu but see the same problem in Fedora 15.  I am currently looking for a fix since I want to move forward with NetworkManager instead of going back to my previous fix (on another system) but will post what I did on my last server in case it helps anyone:

Removed NetworkManager and reconfigured the old "network" config under chkconfig.  I had to create the /etc/sysconfig/network-scripts/ifcfg-eth0.  I know Ubuntu has a bit different configuration than RH/Fedora and do not know if Ubuntu uses NM.

Before the change I would experience what is described here (frequently and throughout the day) and after shooting NM in the head (which is better than it deserves IMO) the problem NEVER reoccurred.

---

### Post by CharlesA on 2011-12-29
Ubuntu uses network manager, but I mostly configure stuff via /etc/network/interfaces in Ubuntu and /etc/sysconfig/network-scripts/ifcfg-eth0 in CentOS/Fedora.

---

