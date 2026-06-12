---
title: "SSH known_hosts fingerprint(s)"
date: 2023-02-27
forum: Server Platforms
---

### Post by aljames2 on 2023-02-27
I've done a system reinstallation and when I run ssh-copy-id to push a .pub key to a server, it brings back an old ecdsa-sha2 fingerprint from somewhere.  It immediately creates a known_hosts.old file containing only my new host fingerprint, and also creates an active known_hosts file with an additional (presumable old) fingerprint.

I've tried deleting both known_hosts* , and recreating it, still the same returns.  Also, I purged ssh & configs and reinstalled ssh, still the same ghost from the past.

Possible culprit?  In additional to my successful ssh, I did do 1 sftp session to the server using the client's gui file manager. Could this sftp session have created another fingerprint.

SSH & sftp all works ok with keys.  I guess I'm a bit ocd over this .old file, at least in knowing what's creating it.

---

### Post by The Cog on 2023-02-28
Could your ssh be configured to do a double-hop to the destination - connecting through an intermediate ssh host to get there? Just a thought.

---

### Post by MAFoElffen on 2023-02-28
That seems weird.

On the file known_hosts.old, is created every time the known_hosts file is updated:
> 
Warning

The ssh-keygen manpage claims that the results of ssh-keygen -H are written to standard output, but this is not true. The command modifies your ~/.ssh/known_hosts file directly. It also stashes a copy of the old file in ~/.ssh/known_hosts.old for safety, but don’t depend on this: running ssh-keygen -H twice obliterates the safe copy.

RE: [https://www.oreilly.com/library/view/ssh-the-secure/0596008953/apas03.html](https://www.oreilly.com/library/view/ssh-the-secure/0596008953/apas03.html)

---

### Post by aljames2 on 2023-02-28
The client is Xubuntu 22.04, and the server is Ubuntu Server 20.04.  The Xubuntu is my kvm host with one VM on it right now.  Using a bridge (br0) network for VMs.  The server however, that I SSH into, is a separate physically connected box on the LAN.  No in-between hops.

---

### Post by aljames2 on 2023-03-01
When I use SSH -vvv I notice the process seems to be initiating a second ssh session after successful authentication using "publickey"

Not sure if this clues us in on anything...

```

.
.
.
Authenticated to 192.168.12.24 ([192.168.12.24]:364) using "publickey".
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting no-more-sessions@openssh.com
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: filesystem
debug3: receive packet: type 80
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug3: client_input_hostkeys: received RSA key SHA256:jp7wxxxxxxxxxx
debug3: client_input_hostkeys: received ECDSA key SHA256:EzFxxxxxxxxxx
debug3: client_input_hostkeys: received ED25519 key SHA256:/V65xxxxxxxxxx
debug3: put_host_port: [192.168.12.24]:364
debug1: client_input_hostkeys: searching /home/aljms/.ssh/known_hosts for [192.168.12.24]:364 / (none)
debug3: hostkeys_foreach: reading file "/home/aljms/.ssh/known_hosts"
debug3: hostkeys_find: found ssh-ed25519 key at /home/aljms/.ssh/known_hosts:1
debug3: hostkeys_find: found ecdsa-sha2-nistp256 key at /home/aljms/.ssh/known_hosts:2
debug1: client_input_hostkeys: searching /home/aljms/.ssh/known_hosts2 for [192.168.12.24]:364 / (none)
debug1: client_input_hostkeys: hostkeys file /home/aljms/.ssh/known_hosts2 does not exist
debug3: client_input_hostkeys: 3 server keys: 1 new, 1 retained, 1 incomplete match. 0 to remove
debug3: client_input_hostkeys: asking server to prove ownership for 1 keys

.
.
.

```

---

### Post by LHammonds on 2023-03-01
When you re-installed the VM, did you use the same configuration and just deleted the disks?  The reason I ask is that if you did, the host may see the same fingerprint as opposed to creating a new VM.

Also, when you say you deleted the known_hosts*, are you talking about only deleting them from the xubuntu system or also the ubuntu VM or the "physically connected box" on the LAN?

LHammonds

---

### Post by aljames2 on 2023-03-01
Thank LHammonds and everyone!

So, my VM data & xml config files was copied to my new NVMe and I used Virt-Manager to reload it.  I have not ever set up an SSH connection to this VM from anywhere.

I deleted the known_hosts & known_hosts.old from the xubuntu system only.  And then when I SSH again into the other box, these 2 files are recreated.  That extra ECDSA key is found from somehwere and adds the extra fingerprint.

---

### Post by aljames2 on 2023-03-01
I did try something new (for me) in setting up the xubuntu machine.  I turned off NetworkManager and enabled netword.  I use a yaml file for all the network settings.  Everything works, so I don't think removing NetworkManager would cause this..
```

aljms@xubtwodsk:~/.ssh$ systemctl status NetworkManager
&#9675; NetworkManager.service
     Loaded: masked (Reason: Unit NetworkManager.service is masked.)
     Active: inactive (dead)

```

---

### Post by aljames2 on 2023-03-01
Showing my xubuntu yaml in case something in the routing could be a cause.
```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces: [eno1]
      addresses: [192.168.12.30/24]
      routes:
      - to: default
        via: 192.168.12.1
        metric: 100
        on-link: true
      mtu: 1500
      nameservers:
        addresses: [192.168.12.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no

```

---

### Post by MAFoElffen on 2023-03-02
Been thinking about this. In the first post, you used 'ssh-copy-id' and you said it added an old ecdsa-sha2 fingerprint to the remote target.

In my mind and logic, the only source that it could have got it from is from the source machine where the 'ssh-copy-id' command was issued from...

When you issue the 'ssh-copy-id' command, it is usually in this format:
```

ssh-copy-id -i ~/.ssh/mykey user@host

```
If you rather do
```

ssh-copy user@host

```
...then it sends whatever it thinks the the default key for that machine is.

RE: [https://manpages.ubuntu.com/manpages/trusty/man1/ssh-copy-id.1.html](https://manpages.ubuntu.com/manpages/trusty/man1/ssh-copy-id.1.html)
> 
     **-i** _identity_file_
             Use only the key(s) contained in _identity_file_ (rather than looking for identities
             via [ssh-add]("https://manpages.ubuntu.com/manpages/trusty/man1/ssh-add.1.html")(1) or in the **default_ID_file**).  If the filename does not end in _.pub_
             this is added.  [COLOR=#ff0000]If the filename is omitted, the **default_ID_file** is used.[/COLOR]

             Note that this can be used to ensure that the keys copied have the comment one
             prefers and/or extra options applied, by ensuring that the key file has these set as
             preferred before the copy is attempted.

So... Going off of that... Look for the old ecdsa-sha2 fingerprint on the source machine via
```

ls ~/.ssh/*

```
...and see if that old key file is there. It might have thought that the old file was the keyfile named in the default_ID_file(?)
Then remember to include the '-i ~/.ssh/keyfilename.pub' flag in your command.

By the way, if you add a '-n' flag to the command, that will do a dry run test of the command and print out the filename of the key file it will try to transfer to the target machine.

Please try that to satisfy my own curiosities on this.

---

### Post by aljames2 on 2023-03-02
So I used the ssh-copy-id as shown above which is how I copy keys to  server machines.  I didn't know about the -n tag so I tried that and the  dry-run showed me exactly the key that would be copied.  I then  committed the command to copy the key over to the server.  Here is my  client computer (xubuntu) ~/.ssh directory:
```

aljms@xubtwodsk:~/.ssh$ tree
.
&#9500;&#9472;&#9472; config
&#9500;&#9472;&#9472; known_hosts
&#9500;&#9472;&#9472; known_hosts.old
&#9500;&#9472;&#9472; kvmHost_id_ed25519
&#9492;&#9472;&#9472; kvmHost_id_ed25519.pub

0 directories, 5 files

```

And here is my ls -l results showing the almost simultaneous creation of the known_hosts & known_hosts.old files.
```

aljms@xubtwodsk:~/.ssh$ ls -l
total 20
-rw------- 1 aljms aljms 133 Feb 25 16:34 config
-rw------- 1 aljms aljms 364 Mar  2 18:50 known_hosts
-rw-r--r-- 1 aljms aljms 142 Mar  2 18:50 known_hosts.old
-rw------- 1 aljms aljms 444 Feb 27 21:15 kvmHost_id_ed25519
-rw-r--r-- 1 aljms aljms  89 Feb 27 21:15 kvmHost_id_ed25519.pub

```

I  have a very simple setup right now.  freshly installed ssh on client  & server.  I have only the 1 keypair that I created here and no  other key pairs.  

The server machine I am ssh'ing into is a bit older.  It used to  be Ubuntu Server 18.04, then I upgraded to 20.04 about a year ago.  I  have had other clients with ssh access to this server in the past, but  now down to just this one right now.  To try to rule out the server  causing this, I purged ssh and reinstalled it to start clean.  So I  can't comprehend, what on my server, is sending this extra fingerprint.

---

### Post by TheFu on 2023-03-02
The network and ssh package aren't connected to this issue.

At sshd install time, there are keys created for the system. These are stored under /etc/.
When a user creates new ssh keys, those should go into a clean ~/.ssh/ directory for the user.  On both the client and server, remove your ~/.ssh/ directories and start over.
On the client, use **ssh-keygen**, then **ssh-copy-id**.  That will create a new known_hosts local and an authorized_keys on the remote system.  On both 20.04 and 22.04, ed25519 keys are well supported.

Over time, especially with systems that get dist-updates, old smelly ssh-keys are left over.  Sometimes it is good to purge them.  Just beware that you'll need to ssh-copy-id to all the systems the removed public keys were on again.  Maybe a better idea is to move the ~/.ssh/ directory rather than deleting it ... so you can put it back if bad things result.

BTW, removing the ssh package(s) doesn't remove the /etc/ssh/ directory or the old server keys.  Use **apt purge** for that.

---

### Post by aljames2 on 2023-03-03
I started over, purged ssh on both machines, removed ~/.ssh & /etc/ssh, & reinstalled ssh.  Same result.  I was able to track down the extra  fingerprint in my known_hosts file.  For some reason, this time, the known_hosts fingerprints  are not hashed (not sure why), so now I can clearly see the 2 entries which start off with the IP of the server followed by the ssh_host keys.  The extra entry is an ecdsa-sha2 entry that matches the contents of /etc/ssh/ssh_host_ecdsa_key.pub on my server.

So  it seems that my server is responding by first sending the fingerprint corresponding to the publickey I sent it via ssh-copy-id, but then immediately after, sent this extra fingerprint matching the server's ssh_host_ecdsa_key.pub

A mystery still.

---

### Post by TheFu on 2023-03-03
> **aljames2 said:**
> I started over, purged ssh on both machines, removed ~/.ssh & /etc/ssh, & reinstalled ssh.  Same result.  I was able to track down the extra  fingerprint in my known_hosts file.  For some reason, this time, the known_hosts fingerprints  are not hashed (not sure why), so now I can clearly see the 2 entries which start off with the IP of the server followed by the ssh_host keys.  The extra entry is an ecdsa-sha2 entry that matches the contents of /etc/ssh/ssh_host_ecdsa_key.pub on my server.

So  it seems that my server is responding by first sending the fingerprint corresponding to the publickey I sent it via ssh-copy-id, but then immediately after, sent this extra fingerprint matching the server's ssh_host_ecdsa_key.pub

A mystery still.

If you've cleaned the ssh directories off all the machines, then there aren't **any** known_hosts files left. Sorry if that wasn't clear.

---

### Post by aljames2 on 2023-03-03
I deleted all that first.  But, ssh-keygen then creates a new ~/.ssh directory, placing my new keypair there.  Then, ssh-copy-id adds the known_host file.

---

### Post by TheFu on 2023-03-03
The known_hosts is a client-side thing.  The public key(s) go into the authorized_keys file is on the sshserver.  So, if both client and server ~/.ssh/ start empty (or don't exist) AND /etc/ssh/ is empty or doesn't exist on both, 
Then you run 
```
sudo apt install ssh fail2ban
```
on both the local and remote consoles, that will generate new ssh_host keys in /etc/ssh/.
Next, run 
```
ssh-keygen -t ed25519
```
on the clients only.
Then on the clients, run 
```
ssh-copy-id userid@server
```
to create the ~/.ssh/authorized_keys file on the remote system.
Validate with an
```
ssh  userid@server
```
During that ssh connection (ssh-copy-id or ssh or sftp), the known_hosts is created with the remote server signature if the system-wide known_hosts doesn't already have the PKI signature.  The ssh manpage says this:
```
     ssh automatically maintains and checks a database containing identification
     for all hosts it has ever been used with.  Host keys are stored in
     ~/.ssh/known_hosts in the user's home directory.  Additionally, the file
     /etc/ssh/ssh_known_hosts is automatically checked for known hosts.  Any new
     hosts are automatically added to the user's file.  If a host's identifica&#8208;
     tion ever changes, ssh warns about this [B]and disables password authentica&#8208;
     tion to prevent server spoofing or man-in-the-middle attacks[/B], which could
     otherwise be used to circumvent the encryption.  The StrictHostKeyChecking
     option can be used to control logins to machines whose host key is not
     known or has changed.

```

I guess my assumptions about what you mean "I've done a system reinstallation" means, since when ssh-server is installed, new host keys are generated automatically.  I've seen cloud_init generate system keys too, the installers seem to change every few months, so I can't keep up with which release is involved.  

I know that some lxc container images used to install snap packages previously. But I've done a number of lxc 20.04 and 22.04 container installs the last few days and snapd hasn't been there (which is good). I don't remember when system ssh keys were generated.  Since I use rdiff-backup to "pull" backups to a backup server, locked down ssh is required.

---

### Post by aljames2 on 2023-03-04
May my burden save me again.  Noting what worked for me here, so I don't forget it next time...

Credit clues from above, and also a reading here:
[https://stackoverflow.com/questions/57760094/fingerpints-for-ssh-do-not-match-with-gitlab-com/57760278#57760278](https://stackoverflow.com/questions/57760094/fingerpints-for-ssh-do-not-match-with-gitlab-com/57760278#57760278)

Not  sure if this a awkward relationship thing between Ubuntu Server 20.04  & Xubuntu 22.04 desktop, but to remind you, ssh'ing from my Xubuntu  desktop client, into my Server worked fine, except the Server kept  writing 2 host fingerprints within my client side ~/.ssh/known_hosts  file.

Created ~/.ssh/config file:
```

Host server
    User aljms
    HostName 192.168.12.24
    Port 364
    HostKeyAlgorithms ssh-ed25519

```

Then created my keypair on my client,
```

ssh-keygen -t ed25519 -C "kvmhst"

saved & named here..

/home/aljms/.ssh/kvmhst_ed25519

```

Then sent the .pub key to my server,
```

ssh-copy-id -i kvmhst_ed25519.pub server

```

I  guess forcing my server host to use only the ed25519 algorithm for  sessions with my client set it straight, now it only sent 1 fingerprint  to my known_hosts file.

I rebooted both machines and tested ssh'ing again.  All work fine.  I then locked down ssh.

---

