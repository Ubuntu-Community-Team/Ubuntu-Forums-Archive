---
title: "SSH Just stopped working..."
date: 2012-03-16
forum: Server Platforms
---

### Post by garfonzo on 2012-03-16
Here's the setup:

- Linux box in garage with SSH running nicely. 
- Windows box in office, connecting to Linux box via putty with non-standard port. 
- Windows and Linux machines on the same LAN
- this setup has been working for, oh, 8 months

Here's what happened:

- during the night (no SSH connections) there was a huge storm which knocked out our power. After the UPS was depleted, the Linux box lost its power and turned off (not a clean power down, a "pull the plug" type power down).
- once the power was restored to our house, I turned on the Linux box and my Windows machine and tried to SSH into the Linux box -- no luck. 

Now my Linux box refuses all SSH connection attempts from any computer. The weird thing is that I can still access the Samba shares on the Linux box from my Windows machine. I can ping the Linux box so I know it's online. I can even connect to it through Filezilla (for FTP transfers). However, I just can't SSH into it. 

I've tried upgrading via apt-get upgrade, rebooting, restarting SSHD, all with no changes. I'm still locked out. 

Any ideas what's going on?

---

### Post by superbike on 2012-03-16
hmmmm....

a funny idea, just try this:

$service ssh stop
$update-rc.d ssh defaults
$service ssh (re)start

there is no logic even to me:lolflag:

---

### Post by garfonzo on 2012-03-16
I don't want to restore defaults since I have some custom keys settings that I need for other stuff (I do remote backups from another server). 

I'm noticing in the /var/log/syslog that ssh is throwing this error:

"respawning too fast, stopped". 

Which, to me, indicates that SSH is not even running. After a large amount of Googling, it seems to be a bug, but I can't figure out how to resolve it.

---

### Post by garfonzo on 2012-03-16
So I found [this patch]("https://launchpadlibrarian.net/61361398/lucid.debdiff") from [this bug]("https://bugs.launchpad.net/ubuntu/lucid/+source/openssh/+bug/687535"). 

I have no clue how to use this patch. Anyone know how to apply this patch?

---

### Post by robgr85 on 2012-03-16
Check if the ssh is really not running and listening:

> 
ps aux | grep ssh


> 
netstat -ntlp


If it seems that sshd is up, try to check selinux settings/rules. What about iptables?

from other box:
> 
nmap -p SSHCUSTOMPORT LINUX_BOX_IP


If selinux is blocking ssh port, try this

> 
/usr/sbin/semanage port -a -t ssh_port_t -p tcp NEW_PORT


---

### Post by superbike on 2012-03-16
just another idea
stop the ssh server (whoops its not working!he he!)
temporarily move sshd.pid from /var/run
and then start the server

---

### Post by garfonzo on 2012-03-16
@robgr85: Running the commands show SSH is not running

---

### Post by Holdolin on 2012-03-16
I would also consider data corruption from an unclean shutdown.  Bad things can happen in a "pull the plug" type of shutdown, up to and including damage to your HDD (the heads my drop onto the platters instead of returning to their rest palce as they do during normal shutdowns.)

---

### Post by hawkmage on 2012-03-16
What happens if you run:
```
sudo service ssh start
```
If things are OK this should start sshd.  If it doesn't start are there any errors displayed when you run the command or in the log fines in /var/log like daemon.log or messages?

---

### Post by garfonzo on 2012-03-16
> **Holdolin said:**
> I would also consider data corruption from an unclean shutdown.  Bad things can happen in a "pull the plug" type of shutdown, up to and including damage to your HDD (the heads my drop onto the platters instead of returning to their rest palce as they do during normal shutdowns.)

Is it possible for data corruption to affect ONLY the SSH service? Everything else on the system works as expected -- is that possible?

---

### Post by Holdolin on 2012-03-16
Data corruption can do all sorts of wierd things.  An error could have occurded becuase the ssh deamon was not proply shut down (just becuase there were no connections, the daemon is always running, listening for a connection request, unless you manually stop it.)

---

### Post by garfonzo on 2012-03-16
> **Holdolin said:**
> Data corruption can do all sorts of wierd things.  An error could have occurded becuase the ssh deamon was not proply shut down (just becuase there were no connections, the daemon is always running, listening for a connection request, unless you manually stop it.)

Good to know (about random errors arising from hard shutdowns). 

I decided to backup my sshd_config and reinstall the openssh-server package and it seems to be working again. I can ssh into the box with the default config file. I wonder if my adjustments to sshd_config caused problems with any updates that completed during the forced reboot. Possibly...

now to slowly change the new default sshd_config file to my version. 

Thanks for the help folks.

---

### Post by garfonzo on 2012-03-16
OK -- it's fixed (I believe). 

It turns out that my syntax was bad (though I didn't change the syntax from before the power outage). I suppose that when the system went down and restarted, some upgrades which were waiting for a reboot, completed their update. Possibly one of those updates was sshd and this new version didn't like my syntax. That's my theory.

In any event, for anyone else who comes across this thread, here's what I did to fix the problem. 

I applied [this]("https://launchpadlibrarian.net/61361398/lucid.debdiff") bug patch by doing this:

```

sudo wget https://launchpadlibrarian.net/61361398/lucid.debdiff
sudo patch -p0 < /home/garfonzo/lucid.debdiff

```

However, that returned some errors so I'm not sure it did anything (I'm just giving a full account of what I did). 

Next I ran this command:
```

/usr/sbin/sshd

```
Which came back and told me that line 38 had a syntax error. Line 38 looked liked this:
```

IdentityFile ~/.ssh/id_rsa

```
I commented that out, restarted ssh and it worked. No more respawning to death.

So, it's solved. Thanks for your help folks.

---

### Post by hawkmage on 2012-03-16
Did it complain about the file /etc/ssh/ssh_config  or /etc/ssh/sshd_config?  

The /etc/ssh/ssh_config is for the ssh client and /etc/ssh/sshd_config is for the server.  

The directive you mention belongs in the ssh client /etc/ssh/ssh_config file not the config file for the sshd daemon.

---

### Post by superbike on 2012-03-16
oh well! all's well that ends well:guitar:

---

