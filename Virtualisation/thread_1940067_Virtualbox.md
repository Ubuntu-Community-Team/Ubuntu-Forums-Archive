---
title: "Virtualbox"
date: 2012-03-12
forum: Virtualisation
---

### Post by tioti on 2012-03-12
I installed Oracle VM VirtualBox in my computer pc having Win 7 Ultimate OS and connected to a LAN. I then installed Ubuntu 11.04 desktop inside VirtualBox to allow file sharing using Samba. I followed steps/tutorial below from Ubuntu website to configure Samba,  however I cannot view this Ubuntu pc when I browse the nework .

What could be possibly went wrong ? I really need help on this.

This is the whole tutorial I tried to follow with no luck
 **[FONT=&quot]Setup Samba Server In Ubuntu[/FONT]**
  [FONT=&quot]This tutorial will I will be teaching you how to **setup Samba Server on Ubuntu**. Using a **Samba Server** to share files between your **Ubuntu** and Windows computers, this is one of the best and easiest ways to accomplish this. So lets get started and install the required packages by running the following command.[/FONT]
  [FONT=&quot]sudo apt-get **install samba**[/FONT]
  [FONT=&quot]This should install the required packages however we still need to **configure Samba Server** so lets open up smb.conf in gedit.[/FONT]
  [FONT=&quot]sudo gedit /etc/samba/smb.conf[/FONT]
  [FONT=&quot]Now lets change the following two values in the **Samba Server** config.[/FONT]
  [FONT=&quot]workgroup = WORKGROUP[/FONT]
  [FONT=&quot]At the bottom of the **Samba** Server config add this and modify it to your needs.[/FONT]
  [FONT=&quot][share]
comment = *Ubuntu* File Server Share
path = /srv/*samba*/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755[/FONT]
  [FONT=&quot]Now all thats left is to create the **Samba Server** directory and restart the *Samba* Services, simply go into an open Terminal and run the following commands.[/FONT]
  [FONT=&quot]sudo mkdir -p /srv/**samba**/share
sudo chown nobody.nogroup /srv/**samba**/share/
sudo restart smbd
sudo restart nmbd[/FONT]
  [FONT=&quot]Congrats! You now have a fully functional **Ubuntu Samba Server**![/FONT]

---

### Post by Cheesemill on 2012-03-13
I think you need to set up the network settings in VirtualBox to give your VM a Bridged network connection instead of NAT (which is the default).

---

### Post by haqking on 2012-03-13
> **Cheesemill said:**
> I think you need to set up the network settings in VirtualBox to give your VM a Bridged network connection instead of NAT (which is the default).

+1

You need to configure bridged networking so your VM is on your actual network either via DHCP or preferably a static IP valid for your LAN.

cheers

---

