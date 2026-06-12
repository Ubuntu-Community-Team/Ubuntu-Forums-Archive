---
title: "Cant access Server with OpenSSH remotely"
date: 2020-09-15
forum: Server Platforms
---

### Post by Sceiron on 2020-09-15
Hi,

I got two computers on my local network. One is running Ubuntu Server 20.04, the other Windows (with Putty).

I can access my Ubuntu server, using putty on the "windows-computer", when i use the Ubuntu-severs LAN-IP: 192.168........, and it is possible to log in.

When i try to access Ubuntu-server using the servers "External IP", i'm getting "Access denied" in putty, even thought the usern/pw is the same.

I have checked that UFW is enabled, and the SSH seems to be open in UFW.
I got a new router from ISP not so long ago, i believe i have added port forwarding in the router for Ubuntu-server IP/Port (tcp/udp).

When connecting on ssh with putty, i get contact with the Ubuntu server, because i can type the user-name, but the password does not seem to work. What am i missing here ?
Is there a problem connecting since both computers is behind the same "External-IP" ?

Tnx

---

### Post by TheFu on 2020-09-15
Try using the Win10 ssh command, not putty.  Use 
```
ssh -vvvv username@LAN-IP
```
Does that work?
If it doesn't, there is a different issue.

If it does, try 
```
ssh -vvvv username@WAN-IP
```
If that doesn't work, then the router setup or capabilities is the issue. Look there for the problems.

BTW, please don't use port 22/tcp on the WAN side.  This is asking to be hacked.
Also, please don't use passwords for any internet connections. Use ssh-keys only and prevent any connections that attempt to use passwords.  Passwords over the internet is asking to be hacked.

Some routers don't allow internal systems to access the WAN-IP can come back inside. This is a security setting. Some which do enable it have a setting to disable it. Sorry, I don't know that setting name.

So, after all the win10 ssh command methods work, then you'll be able to fight with putty to get that working.  I helped someone with Win10 use the built-in ssh command to setup keys a few weeks ago.  It worked just like on Linux, just with Windows paths. We used relative paths since ~/ doesn't work on Windows. Too bad.  Also, Windows doesn't have a ssh-copy-id command, so getting the public ssh-key onto the remote system wasn't trivial.  Win10 does have ssh and ssh-keygen commands, however. The key setup on Linux is easy:
```
$ ssh-keygen -t ed25519
$ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
$ ssh username@remote
```
That's it for that part of the setup.
On the ssh-server side, to prevent passwords from WAN IPs, 
```
   $ sudoedit /etc/ssh/sshd_config
```
     Change line with:
  PasswordAuthentication yes
   to 
  PasswordAuthentication **no**

After that line, add:
```
  Match Address 192.168.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes

```
Obviously, edit the IP subnets for your needs and restart the sshd to re-read the config file.

The ssh-copy-id tool, takes the public key, appends it to the ~/.ssh/authorized_keys file and ensures the directory and file permissions are correct. ssh is picky about the ~/.ssh/ directory being 700 and most files inside it have to be 600, except and public keys generated on-that-machine.  Public keys pushed to the machine go inside the authorized_keys file, not separate files.

---

### Post by Sceiron on 2020-09-17
Hi, and thanks.

So i changed the port to something else then 22, thats ok (Both in /etc/ssh/sshd_config and Port-Forwarding in my router).
I'm restricted to Putty as my windows computer is managed by my administrator, and openSSH client is not an option... (it is not buildt in to the win CLI it seems, atleast i get errors when trying to execute).

Also the windows computer has a firewall, which i cant turn off. However, in the past i have got this working from the office with putty, but not any longer. Any suggestions why?
I can ping my home comp from the office, but Putty get "Network erro: Connection timed out"

EDIT:
I also run the TNC command from Win-PowerShell, so i get that the ping is ok, but the "TcpTestSucceeded=false". Hm, must be something not correct in the router then.
The router configuration should be in "Port Forwarding", right ?

EDIT2: What parameters do i need to set and how, this is my router:
[https://portforward.com/inteno/eg400/](https://portforward.com/inteno/eg400/)

**Source Zone**; Do i need to set this? Or can i leave it blank? (it has options like MDGM, HID; SIP or something, i don't remember the abbreviations atm)
**Destination zone:** LAN
**Source IP address:** Is it relevant, as i can be random? ( I think this is to restrict only certain computers to be able to use the rule (?) )
**Dest. Device,: **I can select the devices connected to my router on local side, so choosing my server, provides the correct Dst. IP Address.
**Dest. IP Address,: ** My servers IP-adress (Local one: 192.168.......)
**Protocol:**  i think i set TCP/UDP, but that should be fine ?
**Source Port: ** not 22, but my newly configured one. What is this actually representing? The routers inbound port?
**Destination Port :**  not 22, but my newly configured one. (This is the actual port configured in /etc/ssh/sshd_Config on server/destination-Computer I assume)

---

### Post by Sceiron on 2020-09-21
Ok, so i finally configured my router to use "Bridged Mode" for the spesific port the server is running on, and now it works. Original post question is solved.

---

