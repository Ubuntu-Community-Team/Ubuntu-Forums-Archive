---
title: "Beginner question about setting up a file server on ubuntu"
date: 2008-07-03
forum: Server Platforms
---

### Post by arandall on 2008-07-03
I am trying to setup a file server on an ubuntu machine that will have a mounted disk available for upload/download from outside of my home network. 

I have an external drive, but since it isn't bus powered, I want to just hook it up to a desktop I have laying around and be able to connect to it from my laptop anywhere I go. Is this possible? If so, how? Is Samba capable of doing something like this? 

Thanks for any help

---

### Post by Titan8990 on 2008-07-03
Your best best on something like this is looking into VPNs. I am not sure that it would be a good idea for security reasons to forward smb ports on your router to a file server.

Also you could look into hosting an FTP through apache.

---

### Post by amenszer on 2008-07-03
Yeah, for accessing your home network from anywhere, VPNs are the way to go.

---

### Post by arandall on 2008-07-03
Thanks for the replies - is there a nice guide somewhere for how to setup a VPN?

---

### Post by nix4me on 2008-07-03
I would setup a ssh server on it and use sftp to connect to it.

---

### Post by arandall on 2008-07-03
> **nix4me said:**
> I would setup a ssh server on it and use sftp to connect to it.

what's the benefit of doing it that way as opposed to the VPN? From what I understand, a VPN will make it that I can mount the server drive as a local network drive, which seems ideal for me...

Is it just not worth the hassle of having to setup a VPN?

---

### Post by hyper_ch on 2008-07-04
or instead of sftp maybe even sshfs

far simpler to setup ssh server than vpn - I think

---

### Post by Zack McCool on 2008-07-04
> **arandall said:**
> what's the benefit of doing it that way as opposed to the VPN? From what I understand, a VPN will make it that I can mount the server drive as a local network drive, which seems ideal for me...

Is it just not worth the hassle of having to setup a VPN?

That depends on how much you need in term of services.  Ssh functions as a bit of a VPN on it's own...   You can mount drives, forward ports, and the setup is a snap.

Using ssh, I am connected to my home machine from work.  I use freenx on top of ssh as a terminal server.  That gives me a full desktop.  If I want to copy files, I use WinSCP.  If I want to forward ports to defeat a firewall, I connect to the ssh server through putty, and forward the ports I need.

SSH is extremely flexible.

---

