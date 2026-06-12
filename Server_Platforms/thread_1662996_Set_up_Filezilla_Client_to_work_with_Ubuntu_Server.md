---
title: "Set up Filezilla Client to work with Ubuntu Server 10.04 on local intranet"
date: 2011-01-09
forum: Server Platforms
---

### Post by Ed_Ziffel on 2011-01-09
Need some help configuring Filezilla client and/or Server 10.04 for intranet

10.04 server installed on dedicated machine on local network set up static 

ip      192.168.77.30
subnet  255.255.255.0
gateway 192.168.77.1

Can ping back and forth on local machines and have internet access through router hooked up to cable modem :)

Can access default index.html from local machines by typing server ip 192.168.77.30 in browser address bar.

How do set up Filezilla to be able to FTP in from machines on local network?

Do I also need to make changes on the server to allow this?

---

### Post by Ceyx on 2011-01-09
I Filezilla from a different city to my Ubuntu computer all the time.  I don't know about Ubuntu Server though....mine is a peer computer.

If you get and install Firestarter it will open the ports ( 21 for FTP ) for you.  I had to install OpenSSH ( and its SFTP component ).  You have to use your account name ( Ubuntu login name / password ) in Filezilla in order to get into the destination computer.

Hope this is of some help.

---

### Post by Ed_Ziffel on 2011-01-09
Thanks Ceyx

Was guessing that an FTP server was needed.  Also thought about a peer to peer type scenario where just pasting in new files over old ones would work like having a lamp server installed on a local machine.  

This firestarter, does it have functionality to act like a DDNS or do you have a static IP from your IP provider or is there some other thing happening that lets you resolve your servers IP on the internet?  

The router has port forwarding functionality.  Was thinking to set up each needed machine for remote access that way.  Any ideas on that?

---

### Post by CharlesA on 2011-01-09
I use sftp to transfer files to/from my web server. It was easier to set up then a regular ftp server and is more secure as it is encrypted.

Firestarter is a frontend for iptables, which is no long under active development. I would suggest using UFW or GUFW if you want to run a firewall.

In any case, there is no firewall enabled by default on Ubuntu, so you don't have to worry about opening ports up.

You don't have to mess with any settings on the router if you are just dealing with local commuication.

---

### Post by Ceyx on 2011-01-09
Ed:

The idea behind a firewall was so that you could watch and see what is happening - or not happening - for trouble shooting purposes.

Firestarter is not a DDNS resolver.  I control both ends of the communication ( I get into the remote computer using VNC and fire up Filezilla on the remote to start the transfers ).  My ISP rarely changes my external IP, so I just discover my external IP using whatismyip dot com.

Port forwarding was required on my router pointing to the internal ip of the computer to be used for connections from the outside world, but not from within or behind the router.

I use Filezilla only because I transfer large files ( 20GB ) and it is the only program I found that would resume a transfer from a broken connection, as opposed to restarting it.  Otherwise, I would just use SFTP as CharlesA suggests.  I do use Rsync on occasion too.

Regards

---

### Post by CharlesA on 2011-01-09
I use sftp with Filezilla. :)

You don't need firestarter to see incoming/outgoing connections - you can use netstat or lsof for that.

---

### Post by Ed_Ziffel on 2011-01-10
Thanks Ceyx and CharlesA

I'm going to print this to a pdf file for further reference.  
Am going to start a new thread with respect to extablishing a stable methodolgy to resolve a connection to the LAN's external IP.  

Thanks again.

---

