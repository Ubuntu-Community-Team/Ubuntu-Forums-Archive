---
title: "Samba over internet"
date: 2018-06-29
forum: Server Platforms
---

### Post by pecukevicius on 2018-06-29
Hello,

I have currently running Ubuntu Server, and configured Samba to use on local network, so we can share files.

Also today i have got Static IP address.
Would it be possible to configure Ubuntu and samba, to be able to connect to Samba shared folder from home?

If so, how to set it up?

Regards
Tomas

---

### Post by darkod on 2018-06-29
I wouldn't recommend sending samba traffic over internet. Consider installing openvpn server on your Ubuntu server, and connecting over VPN from remote locations. That will give you access to your server without risking security.

---

### Post by cmcanulty on 2018-06-29
Could you please post the specifics on how to do that

---

### Post by darkod on 2018-06-29
You have the ubuntu help pages on openvpn here: [https://help.ubuntu.com/lts/serverguide/openvpn.html.en-GB](https://help.ubuntu.com/lts/serverguide/openvpn.html.en-GB)

There are also many tutorials on the internet.

---

### Post by SeijiSensei on 2018-06-30
The simplest arrangement is a static-key tunnel as described in [http://openvpn.net/static.html](http://openvpn.net/static.html).  This sets up a point-to-point encrypted connection between two machines.  I have a cloud server that I connect to from my home network.  The remote machine is configured as the server, and the home machine as the client.  You will need to open a port in the remote's firewall to permit the traffic.  I usually choose a custom port above 10000.

On the server, my configuration file reads
```

dev tun
ifconfig 10.1.1.1 10.1.1.30
secret /path/to/my/keyfile
port 12345
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

```

```

dev tun
remote ip.addr.of.serv er
ifconfig 10.1.1.30 10.1.1.1
port 12345
secret /path/to/my/keyfile
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```

Notice that the ifconfig specifies the local and remote tunnel IPs.  The order is therefore reversed on the two machines.  You can generate a keyfile with the command "openvpn --genkey --secret /path/to/my/keyfile".  You can copy the key to the remote server with scp.

---

### Post by TheFu on 2018-06-30
While VPNs are good for many uses, there are easier, secure, remote file access methods available too.  There have been network performance issues using CIFS over a VPN. I don't know if those still remain, but they are still in the warnings for openvpn.

If you do go to the effort to setup openvpn, you might want to use the AES-256 cipher instead of the defaults.

An easier alternative ... ssh
if you setup ssh and get the port forwarding and security correct for ssh, then you can use sftp, scp, rsync, or sshfs from anywhere in the world, relatively securely.

Just don't use passwords.  Only allow ssh-keys or ssh-certs for authentication.

How to secure ssh and all related tools is a well-worn, well-understood thing.  Getting ssh working, securely to a home network is about 20x easier than setting up a VPN, IMHO.

I have both openvpn and remote ssh setup to home.  I barely use openvpn.  Remote ssh is a way of life for Unix people already.  ssh is the swiss-army-knife for system-to-system communications.
[http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html) shows a few things that ssh makes possible. Even long time Unix / ssh people will likely learn something new.

---

