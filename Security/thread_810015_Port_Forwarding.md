---
title: "Port Forwarding"
date: 2008-05-27
forum: Security
---

### Post by nicnicman on 2008-05-27
Why am I having so much trouble port forwarding in Ubuntu?  I am obviously doing something wrong but I just can't seem to figure it out. 

 Under Windows I was successful port forwarding for uTorrent and I would like to do the same with Ubuntu.  Now it doesn't have to be uTorrent; I am open to any torrent app as long as it is efficient.  I've tried Transmission and uTorrent under Wine but failed.  

If anyone has any suggestions please let me know.

---

### Post by Dr Small on 2008-05-27
Are you behind a router, and attempting to forward the port to your system? Or are you directly connected to your modem, via ethernet?

---

### Post by hyper_ch on 2008-05-28
did you install firestarter?

---

### Post by nicnicman on 2008-05-28
Yes, I am behind a router which I have configured.  Its a Linksys WRT54G.

No, I don't believe I have activated any firewalls unless I did it accidentally.  

Thanks for the inquiries.

---

### Post by nicnicman on 2008-05-28
I am unable to connect to the router or the internet using the static IP.  

The same router settings work with the same static IP under Windows.

---

### Post by Oldsoldier2003 on 2008-05-28
> **nicnicman said:**
> Yes, I am behind a router which I have configured.  Its a Linksys WRT54G.

No, I don't believe I have activated any firewalls unless I did it accidentally.  

Thanks for the inquiries.

you will need to configure your torrent program to use the ports you have forwarded in your router. also you should be sure that the ports are actually being forwarded to your machine, since most routers do forwarding by IP address. (If you IP address doesn't match what is setup in your router you'll need to change the IP address on the ubuntu machine to match the routers settings in order for it to work.)

---

### Post by nicnicman on 2008-05-28
Is it possible that this is causing the problems

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/185854]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/185854")

---

### Post by Oldsoldier2003 on 2008-05-28
> **nicnicman said:**
> Is it possible that this is causing the problems

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/185854]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/185854")

very possible since i see you are having a problem connecting to your gateway (missed that post) have you added auto eth0 to /etc/network/interfaces?  It didn't click because when I set up my Hardy I manually edited /etc/network/interfaces as a matter of habit...

---

### Post by nicnicman on 2008-05-29
How do I add auto eth0?

---

### Post by kevdog on 2008-05-29
Manually edit the /etc/network/interfaces file (or simply most the contents of the file).

To edit

gksu gedit /etc/network/interfaces

---

### Post by nicnicman on 2008-05-29
So I add the line "# auto ethO" to the file?

---

### Post by kevdog on 2008-05-29
Dont preface the line with a # sign.  This implies a comment line and will be ignored.

---

### Post by nicnicman on 2008-05-29
Added the line but I still cannot connect to the gateway.:confused:

---

### Post by nicnicman on 2008-05-29
Actually after messing around with file a little it seems to be working.

Thanks for the help.

---

### Post by balagosa on 2008-05-31
i would like to revive this thread because i also want to do port forwarding.

so i already placed "auto eth0" on /etc/network/interfaces

and i accesses my router and i already placed in my address for port forwarding, with a specific application which is "ktorrent".

Question:
1) How do i know it is a successful port forwarding?
2) there is a field "start" and "end". can anyone explain me with these?
the numbers under these are "18768"

---

### Post by kevdog on 2008-05-31
Could you provide some screen shots b/c Im not sure what you are talking about?

---

### Post by balagosa on 2008-05-31
the start & end as i have found out is the ports enabled.

so, my last question, how do i know the forwarding worked.

can anyone also give me a good HowTo for Port Forwarding

---

### Post by kevdog on 2008-05-31
PortForwarding through a router? or from an Ubuntu box that has two NICs that will allow internet connection sharing?

---

### Post by balagosa on 2008-05-31
> **kevdog said:**
> PortForwarding through a router? or from an Ubuntu box that has two NICs that will allow internet connection sharing?

oh sorry.let me go into details.

Port Forwarding through a router which is "WRT54g Linksys Router". been in the family for years now, and my cousin only told me about port forwarding yesterday.

i got KTorrent as of now and Transmission. I tried to test the **Start to End** ports "above" and said they were close (for Transmission). I installed the UpNp plug-in for KTorrent and there were no devices found on the "Port Forwarding" page. so i guess something is still wrong :)

---

### Post by balagosa on 2008-06-01
errr....bump*

---

