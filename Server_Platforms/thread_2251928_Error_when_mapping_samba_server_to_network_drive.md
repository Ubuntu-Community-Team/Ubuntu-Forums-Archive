---
title: "Error when mapping samba server to network drive"
date: 2014-11-07
forum: Server Platforms
---

### Post by michael211 on 2014-11-07
Hi, I am fairly new to Samba and Ubuntu.  I am trying to map my remote samba share (server in the office) to a network drive (workstation at home).  When I map the drive to \\192.168.1.1\sharename where 192.168.1.1 is the actual external ip, I get an error that says:

```
file and print sharing resource (192.168.1.1) is online but isn't responding to connection attempts.
```

I turned off Windows Firewall to see what would happen and the same error comes up when attempting to connect.

Thanks in advance for your help!

---

### Post by Kimona on 2014-11-07
quick question did you verify your IP settings saved? Did you reboot the machine and validate you can ping it from a command prompt? No trying to insult your intelligence but I did that before!

---

### Post by michael211 on 2014-11-07
I am able to ping the external IP, but not with the port which is forwarded to the server appended on it.  I am however able to connect through FileZilla, Putty, and other SSH Clients through sftp.

---

### Post by bab1 on 2014-11-07
> **michael211 said:**
> I am able to ping the external IP, but not with the port which is forwarded to the server appended on it.  I am however able to connect through FileZilla, Putty, and other SSH Clients through sftp.

Unless you are using a VPN you won't be able to connect to a SMB/CIFS (Samba.Windows Sharing) server over a WAN (Internet) connection.  The technology does not use encryption all the time and the ports are typically blocked by most providers.  SMB/CIFS is for LAN's only.  On the other hand is SSH is always encrypted and is regularly used over the Internet.

---

### Post by michael211 on 2014-11-08
> **bab1 said:**
> Unless you are using a VPN you won't be able to connect to a SMB/CIFS (Samba.Windows Sharing) server over a WAN (Internet) connection.  The technology does not use encryption all the time and the ports are typically blocked by most providers.  SMB/CIFS is for LAN's only.  On the other hand is SSH is always encrypted and is regularly used over the Internet.

Is there a way to map the samba server to a network drive through SSH?  I did some research on setting up a VPN on ubuntu, and it seems like an undertaking I don't want to try right now.

I can access all my files just fine through SSH using FileZilla; however, there are two files I need to have actually mapped in order to use them.  These are my Quickbooks File and the operating files for a program called HomeTech.

They need their corresponding files on the local machine, or at least the local machine mapped to them.

---

### Post by SeijiSensei on 2014-11-08
You can mount remote shares over SSH by following this: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

I mount the share as root by running sshfs in /etc/rc.local, so I need to include the "allow_other" option to enable access by other users.

```
sshfs -o allow_other 10.10.10.10:/path/to/remote/share /path/to/local/mount/point
```

You'll need to set up [public keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") to have the mount happen transparently.

---

