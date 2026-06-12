---
title: "Copying files you don't have permission to with rsync"
date: 2018-10-10
forum: Server Platforms
---

### Post by bigmonmulgrew on 2018-10-10
Hi Guys

I am trying to copy some files from serverA to serverB

On serverB I am running rsync

```
sudo rsync -au -e "ssh -i /home/myuser/.ssh/id_rsa"  myuser@serverAIP:/my/user/files/ /my/user/files
```

This is fine with files I have access to. But I want to be able to copy another users files /other/user/files.

This obviously creates a permission denied error.

After some googling I have found suggestions to use

```
--rsync-path="sudo rsync"
```

but doing this results in an error.

```
protocol version mismatch -- is your shell clean?
(see the rsync man page for an explanation)
rsync error: protocol incompatibility (code 2) at compat.c(178) [Receiver=3.1.2]
```

So how can I copy files I dont have access to. I can use sudo on both servers.

---

### Post by TheFu on 2018-10-10
Updated below:

```
sudo rsync  -avz root@serverA-IP:/my/user/files/ /my/user/files/
```

Get the trailing / correct. It is important.  But if you are pulling frils from your HOME, then all of those should be owned by the userid you have.

Setup ssh keys from root on the local machine to root on serverA.  Use **sudo ssh-copy-id root@serverAIP**. Might need to setup root with ssh-keys on the local machine and push those over.  

I haven't used -e in about 2 decades. ssh is used by default for rsync between 2 systems.  And if you use the default key files, then you don't need to specify those.

---

### Post by bigmonmulgrew on 2018-10-10
Thank you. I now have it working.

Not sure why I was using -e to be honest. I followed a lot of guides before I came here. At one point it wasnt picking up the key file.

Should I be worried about security concernes with this? Anyhting I shoudl be doing as well to make sure this is secure.

---

### Post by SeijiSensei on 2018-10-10
It's using SSH.  The only additional layer of security I would suggest is limiting which IPs can connect to the sshd server.  I do this through iptables, but you can also control access in /etc/sshd_config.

---

### Post by SeijiSensei on 2018-10-10
It's using SSH.  The only additional layer of security I would suggest is limiting which IPs can connect to the sshd server.  I do this through iptables, but you can also control access in /etc/sshd_config.

I run all my connections to remote servers over point-to-point OpenVPN tunnels.  You might consider that.  Take a look at [http://openvpn.net/static.html](http://openvpn.net/static.html) for details.

---

### Post by TheFu on 2018-10-10
> **SeijiSensei said:**
> It's using SSH.  The only additional layer of security I would suggest is limiting which IPs can connect to the sshd server.  I do this through iptables, but you can also control access in /etc/sshd_config.

This.  Keys help a bunch, but if only root from A should be allowed, then only accept  root from A. There are multiple different ways, but tcp-wrappers has been part of sshd for awhile, so I'd use that in the sshd_config as SeijiSensei is suggesting.  Limiting all ssh access as much as possible with firewall rules is smart too.  If nobody in Argentina will ever ssh into the machine, don't allow them to even attempt it.  If only LAN ssh access is intended, then block all public IPs.

---

