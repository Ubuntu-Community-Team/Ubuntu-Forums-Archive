---
title: "Need security advice on my setup"
date: 2012-07-15
forum: Security
---

### Post by MadsRC on 2012-07-15
I have the following setup in my home test/play-around lab:

1 x Firewall (pfSense)
1 x Wireless Access Point (DD-WRT)
1 x Storage Server (unRAID)
1 x Play-around/production server (Ubuntu Server 12.04)

I wanted to be able to access my files on the storage server from outside of my LAN, so what I decided to do is:
1: Mount all shares on the Ubuntu Server
2: Allow SSH Access to the Ubuntu Server (Using SSH Key's instead of password, and only allowing a certain user to SSH in)
3: Allow RDP Access to Ubuntu Server (Using 38 character, A-Z, a-z, special and numeric characters password)
4: Allow FTP or SFTP Access to Ubuntu Server

(I know I could also use VPN, which I'm in the process of setting up)
The idea behind this was that the fewer systems I can access from the outside, the fewer systems I have to be frantic about keeping updated. And with RDP I would have full graphical control of my LAN.

I've set up the first 3 steps, but I'm not sure about the fourth step. Since I've already got SSH set up, shouldn't I just use SFTP? It would have the advantage of being encrypted, which I understand FTP isn't?

For the RDP access, I set up xorg and fluxbox as a lightweight desktop and uses xRDP for the RDP session. Is this insecure? I'm mostly concerned wether or not the session is encrypted?

Last question. For SSH I use keys. From what I understand the server only needs the public key, as when I SSH in, I verify that I am me with my private key, and the server can then verify that with the public key? The session isn't encrypted by the keys, but only authenticated? The session encryption is done by OpenSSH itself right?

And for the record, I use different keys for different pc's that need to log on to the server.

---

### Post by CharlesA on 2012-07-15
If you have SSH access to the Ubuntu box, you have sftp access as well. No need to set up another FTP server.

As for remote desktop - I am assuming you are talking about connecting via the Ubuntu box to Windows machines. If that is not the case and you are using VNC, I would recommend tunneling it over SSH at the very least, even if you have a strong password.

On my setup at home, I have only SSH open to the internet, but have only a few IP addresses whitelisted. If I need to remote desktop to a Windows box, I just create an SSH tunnel to connect to that Windows box.

A VPN might be easier, but I don't feel like setting one up.

SSH Keys are used for authentication, An OpenSSH connection is encrypted from the start.

---

### Post by MadsRC on 2012-07-15
I have no windows machines on my lan. What I do is, I use RDP from my work machine (which sadly is a windows machine) when there are certain things I need to check from another IP than the one at the office. Also I use it for the unRAID  graphical and fiewall graphical webgui's that I don't want to expose to a WAN.

The package that I use to enable this is xRDP, but when it runs I know that some VNC processes are running too.

---

