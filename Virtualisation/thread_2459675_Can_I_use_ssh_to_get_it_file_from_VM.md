---
title: "Can I use ssh to get it file from VM?"
date: 2021-03-23
forum: Virtualisation
---

### Post by Swan_DB on 2021-03-23
Preface: may be a duplicate question of something, or similar, but I have a tbi and can't really manage to check all the "already posted" posts, please have mercy.


1) Can I connect from "Host" to the VM operating system, and download an image from there?
--1.a) Both desktop/host (is host the correct term here?) and the OS on the VM have Openssh installed.
--1.b) Would I use cURL to get it, or just a native ssh command, or maybe SFTP, or .... another command line tool?  Rather not use GUI stuff..
2) I don't know where else to ask this question; or how to accurately ask it as I'm a noob.


Any input or questions leading to input are greatly appreciated.
[HR][/HR]
PS. I won't use bad words #NoMoreJail, at least I'll try not to, can't promise because: Rock and roll!!!  :guitar:

Edit: of course I mess up the title...  It's suppose to say *a file* not it file...

---

### Post by TheFu on 2021-03-23
ssh is the main tool, but there are about 50 others that leverage it for all sorts of stuff. In general, if a client can ssh into a server, then all the other things can be setup to work and connectivity/authentication from the ssh setup will be reused.

So - there are many ways to transfer files between computers.
sftp, scp, rsync, sshfs all use ssh.
scp is a replacement for rcp. The commands/options are the same.
sftp is a replacement for ftp. The commands/options are the same.
rsync is rsync, but between different systems, ssh has been used by default for about 15 yrs. When you see *rsync -e ssh* .... that's probably a very old guide, a guide written by someone who didn't read the manpage or one of a highly specialized situations where the -e ssh is actually necessary.
sshfs is a way to mount a remote directory to your local machine.  There are some limitations and not all file system capabilities work, but most do.  All access happens through an ssh-tunnel, so the performance will reflect that added encryption.  In general, the times I use sshfs are:
a) to show someone else
b) when I have a complex scripting environment on 1 computer, but the data to be processed is on another and I don't have NFS access to the data (NFS is probably 20x faster than sshfs).

The question is fine.

For any lurkers, almost all linux GUI file managers support using sftp to access other Unix systems running ssh-servers.  Into the URL, just enter sftp://{hostname}/     # if DNS or /etc/hosts have the entry for {hostname}
sftp://{hostname}.local/  # if avahi is running
sftp://{IP address}/    # to use the IP address
sftp://{host alias from ~/.ssh/config file}/    # if that has been setup.

Sometimes the sftp has to be ssh:// or fish://  I don't understand why, since sftp is the correct protocol.

Is there a reason you didn't just try sftp user@host?  I'm confused.

If ssh isn't working between the client and the server, then sftp, scp, sshfs, rsync ... and the other 50 ssh-based tools won't work either.

BTW, will you try to attend SELF this year? It is virtual, not in Charlotte.  [https://southeastlinuxfest.org](https://southeastlinuxfest.org)

---

### Post by The Cog on 2021-03-23
As TheFu says, but a couple of points:
It depends on the networking setup between the host and the guest as to whether they can connect to each other. On a bridged connection I don't think there should be any problem. I have vague memories that maybe a NAT configuration might make connection between host and guest difficult. They need to be able to ping one another, in which case ssh should also be able to connect.
The machine accepting the ssh connection needs openssh-server installed and running. openssh is just the client and can only make outgoing calls.

---

### Post by ajgreeny on 2021-03-23
All my VMs use NAT connections and it is very easy to use ssh or sftp to connect from guest to host which is the only way I ever want to connect; once connected it's possible to move files in either direction, host to guest or guest to host.

What is not possible using NAT connections, (or if it is I do not know how), is to connect from host to guest, but as I say, it doesn't really matter as I can move files in either direction once connected guest to host.

---

### Post by Swan_DB on 2021-03-23
I cannot get it to work.  I've got the server running in the VM, pretty sure, and the client running on the same PC, just my desktop not in the VM, pretty sure, but I can't get the commands right, 
ie. I can't figure out `ssh` + ?,   where "?" is the host:username or username:host or user@host or IP address or ...  <----   I don't know this part, I can't make sense of the manual pages yet, all this is confusing, but I'm learning a little at a time:
```
NAME     ssh — OpenSSH remote login client


SYNOPSIS
     ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface] [-b bind_address] [-c cipher_spec]
         [-D [bind_address:]port] [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11]
         [-i identity_file] [-J destination] [-L address] [-l login_name] [-m mac_spec]
         [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address] [-S ctl_path]
         [-W host:port] [-w local_tun[:remote_tun]] destination [command]


DESCRIPTION
     ssh (SSH client) is a program for logging into a remote machine and for executing commands on
     a remote machine.  It is intended to provide secure encrypted communications between two un&#8208;
     trusted hosts over an insecure network.  X11 connections, arbitrary TCP ports and UNIX-domain
     sockets can also be forwarded over the secure channel.


     ssh connects and logs into the specified destination, which may be specified as either
     [user@]hostname or a URI of the form ssh://[user@]hostname[:port].  The user must prove
     his/her identity to the remote machine using one of several methods (see below).


     If a command is specified, it is executed on the remote host instead of a login shell.



``` **but I do have 2 more questions:**

1) Is host always the server?

2) Do I connect from server side to client first, or client side to server first?

**Edit:**  I'm pretty sure I need to set up the server first to accept the client, which I haven't done....  and it just registered in my brain that that's probably why it's not connecting.

[HR][/HR]

---

### Post by Swan_DB on 2021-03-24
On my host (VM running on my desktop acting as the server side) inside ~/.ssh/$  I have > moduli  sshd_config  ssh_host_ecdsa_key.pub  ssh_host_rsa_keyssh_config  sshd_config.d       ssh_host_ed25519_key  ssh_host_rsa_key.pub
 ssh_config.d  ssh_host_ecdsa_key  ssh_host_ed25519_key.pub  s sh_import_id can someone explain why I have "ssh" and "sshd", and how to use any of this in regards to my client, on my client (desktop, outside of VM), in ~/.ssh$, I have > id_ed25519  id_ed25519.pub  known_hosts  rsaKey  rsaKey.pub

, now I'm pretty sure I created the file "rsakey" manually, but only because I have no idea what I'm doing yet.  

Any input on these files would be appreciated, they all seem to store either a key, or multiple keys, depending on the file (I may be wrong on the multiple keys part, but I think the server side at least does have multiple keys per file, for some files at least).

I keep getting > ssh: Could not resolve hostname ubuntu: Temporary failure in name resolution, but when I put in ```
[FONT=Verdana]ssh [/FONT][COLOR=#0000cd][FONT=Verdana]user[/FONT][/COLOR][FONT=Verdana]@[/FONT][COLOR=#0000cd][FONT=Verdana]XXX.XXX.XXX.XXX[/FONT][/COLOR]
```, it just seems to stall for ~2 minutes then times out with > ssh: connect to host [COLOR=#0000cd]XXX.XXX.XXX.XXX[/COLOR] port 22: Connection timed out

Edit : I don't understand the files, neither client or server side, that are being used.

[HR][/HR]

---

### Post by Swan_DB on 2021-03-24
Are my keys stored in the wrong directory?

I do :  ```
~/.ssh ls
```, and it lists all the files I quoted above ^
but I'm seeing on the manual page for ```
man sshd_config
```  something about > sshd(8) reads configuration data from /etc/ssh/sshd_configand I don't understand why I have the keys in "~/.ssh", and the manual page says something about "/etc/ssh/sshd_config"?  

Any input on why there are two directory locations?

**Edit: I quit.  MODERATORS can delete this thread.  Marking as [SOLVED] **so I don't keep posting and inevitably start using bad words because I'm on ~15 hours of sleep for the past week, my brother passed away 2 months ago, I hate my life, have a brain injury and...  well

---

### Post by slickymaster on 2021-03-24
Please, check this thread: [https://stackoverflow.com/questions/5906441/how-to-ssh-to-a-virtualbox-guest-externally-through-a-host](https://stackoverflow.com/questions/5906441/how-to-ssh-to-a-virtualbox-guest-externally-through-a-host)

---

### Post by TheFu on 2021-03-24
Sorry, but everyone here is a volunteer. We have commitments outside answering questions in these forums.

First, install ssh on both the client and the server.
Install SSH and Fail2ban (ssh is a meta packages on Ubuntu w/  both the client and server stuff:
```
  $ sudo apt install ssh fail2ban
```
  # fail2ban defaults are preconfigured for ssh on 22/tcp.

On normal Ubuntu systems, that is sufficient for password-based ssh connections, assuming there aren't other network problems - like a firewall or NAT.  We don't know your network config - but if both computers can ping each other, then ssh should work between them, in general ( firewall/NAT issues not getting in the way ).

Next, you'll want to create an ssh key on the system you want to ssh FROM.  That could be 1 or both systems. IDK.  Up to you. The one where the ssh command is run is "the client" - always.  It connects to "the server", which is the other system that is running ssh-server or sshd.

Forum link which address ssh key creation (to find more, search for ssh-keygen or ssh-copy-id)
[https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)

Forum link which address security for ssh 
[https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278)
There are lots and lots of security techniques available for ssh that is going to be over the internet. On a LAN, I'd just setup the ssh-keys, since keys are both much more convenient AND 1,000,000x more secure than passwords.

Understand that when we write user@remote ---- that isn't literally what is needed. For me, it would be 
```
ssh thefu@hadar
```
"thefu@" is only necessary if the username on both sides isn't the same. If the username on both systems is the same, then:
```
ssh hadar
```
is fine.

In the last link above, I think it spells out setting up a ~/.ssh/config file.  That can also be used to force a different username.

If you don't get side-tracked and just do the things in this single post, in order, ssh will work.  Further, sftp, scp will work too. They are part of the ssh package that was installed.
If you want to use rsync, it may need to be installed, but it will use ssh as the tunnel by default. Same for sshfs.

Now, if you want to connect using sftp, then use:
```
sftp thefu@hadar
```
then do the normal put/mput and get/mget commands.  I hardly ever use sftp in a shell.  I use scp all the time and rsync 5 times a day. Some examples:
1 file:
```
scp ~/bin/some-script  hadar:bin/
```
Files in globbed pattern:
```
scp ~/bin/*pl  hadar:/tmp/thefu/
```
Note that I don't specify the name of the file, just the directory, for the target location.  We can "pull" the file by swapping terms.
```
scp hadar:~/bin/*pl  ~/bin/
```
Normal Unix file permissions rule, so I can't use my account to place files into system directories without some gymnastics in the commands. It is possible and easier to pull, IME. Part of the difficulty is to use the ssh-keys for the connection without escalation via sudo, but still use sudo when writing to the local system directory.  Almost always, I'll just push to somewhere under /tmp/ then move from there into a system location. Huge files - say for 40G virtual machines - I'd go to the effort to place them as root where needed. The location for VM storage files is dependent on the hypervisor being used.  VBox happily defaults to normal user's HOME for that. Enterprise hypervisors do not.

rsync has way, way, way too many options to get into them all.  The best advice for that is to google "rsync examples" and look for 50 of them.

The man page for ssh, sshd_config, ssh_config, rsync are works of art. They are long and full of features. These 2 tools are in my top 5 tools for computer knowledge.  ssh is like the biggest Swiss-Army Knife for system-to-system communications. If you need for 2 systems to communicate, ssh is probably the tunnel between them.

Sorry about your brother.

---

### Post by Swan_DB on 2021-03-24
> [COLOR=#000000]Sorry, but everyone here is a volunteer. We have commitments outside answering questions in these forums.[/COLOR]
Just wanted to append a thank you to all who tried here, I've got some info from slickymaster's link that helped.  I think by the time I get the ssh working, I'm going to know the entire linux file system and a big portion of VMWare Workstation...  I'm literally going through every file in my Ubuntu desktop's /etc and /usr and basically just / and looking at everything trying to find network stuff, then I'm also going through the VM's network settings, and also the network settings for xubuntu (guest OS on the VM) which I thought xubuntu and the VM were the same thing, didn't realize I need to account for the network of the VM *and* the guest OS, or maybe I don't, idk.  But I'm going through all the files and reading the man pages of more than I likely need to...  Win some, lose some, draw some.  Thanks again.

---

### Post by TheFu on 2021-03-24
It is hard to know, what we don't know. ;)

Think of VMs this way.  They present virtual hardware to each VM.  Inside the VM, the OS still must be configured just as though that hardware ware real. Some hypervisors let us pick the hardware to be emulated from a short list that is very well supported. For networking performance and efficiency, with Linux VMs, use the virtio versions for the network adapter and storage controller. These are optimized for VMs and Linux has supported them over a decade.  Windows may or may not support them, IDK.  With Windows, you can download extra drivers to have virtio supported but those will be a pain when their are boot problems, so I usually just pick an Intel PRO/1000 NIC and either SATA or SCSI disk controller. I haven't seen any performance difference with those choices - except when transferring data on the same physical machine.  The virtio NIC driver can get to 35Gbps and 25Gbps almost always.  Eventually, data needs to be written to disk, so all that speed isn't really too helpful 99% of the time.

There are 3 or 4 popular VM network setups.
* NAT
* Host-only
* Bridged
I'd hope that the VMware Player/Workstation documentation would explain those clearly.  The Virtualbox documentation does. Other hypervisors assume you already understand the terms or can look them up.

If you want your VMs to be on the same subnet, get DHCP addresses from your DHCP server (often your router), the use "bridged" VM networking. ssh works just like we expect, just like having 2 physical machines involved connected to the same router/switch would.

For my play, throw-away, desktop VMs, I'd select NAT.  This puts the new VM into a NAT subnet separate from the host and other systems. It can talk outbound, but nothing will come inbound without extra manual effort.

---

### Post by Swan_DB on 2021-03-25
**[SOLVED] **On the VM's guest operating system (my server, xubuntu 20.04) I ran ```
sudo ufw status
```&#8203; which showed : > Status: activeand then when I realized my firewall was active on the guest OS (on the VM), I ran ```
sudo ufw disable
``` which showed : > Firewall stopped and disabled on system startup

and then from my remote computer (my desktop, same computer, just outside of the VM) I ran ```
ssh [COLOR=#000080]serverUsername[/COLOR][COLOR=#000000]@[/COLOR][COLOR=#000080]rserverIPaddress[/COLOR]
``` and it worked.  I can now try to `sftp` the file I needed which started this whole thing. 

[HR][/HR]
 Not sure how to keep the firewall up and access via ssh yet, but it works :)

---

### Post by rsteinmetz70112 on 2021-03-25
Try

```
 sudo ufw allow ssh
```

---

### Post by TheFu on 2021-03-25
> **Swan_DB said:**
>  
 Not sure how to keep the firewall up and access via ssh yet, but it works :)

Post #9 has links. Inside those links is information.

---

