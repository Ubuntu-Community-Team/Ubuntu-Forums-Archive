---
title: "Dictionary Attack; openvpn and openssh no longer work"
date: 2011-03-25
forum: Security
---

### Post by MMegaTron on 2011-03-25
Hi guys,

I work for a small company setting up their IT services.  I have been trying to setup OpenVPn for the past month.  The previous IT support person had set the server up, and had installed winSCP for users to connect.  Unfortunatley we had [permissions issues so I tried setting up OpenVPn to solve it.  He did not setup secure passwords for the root/admin accounts or certificatesd for the SSH.  

I had got OpenVPN  completely almost 100% working until now, but over the last couple of days openvpn AND ssh which  both previously wokrked have stopped working for all users working from home.  I  came in and tried investigating today and found the auth.log in  /etc/logs filled with messages about root attempting to connect and  being rejected and other users who do not exist, all of this being  repeatedly a couple of hundred times since early last Sunday morning.  It  is obvious this a dictionary attack from some malicious user  somewhere.  Anyway, the point is that neither openvpn nor ssh are  working now and I am pretty stumped because I don't know what has caused  this, whether the user actually got into the system and changed some  settings or whether it is simply sending so many requests that  legitimate users cant connect (i'm guiessing it's the former as the logs  arent showing any attempts now, but haven't seen on the logs that the  user has successfully been able to break in).  

Does anyone have any ideas  which might help?  I can post the log file if necessary.

Thanks,

Jack

---

### Post by CharlesA on 2011-03-25
Was there any successful logins?

If both services aren't working, and they worked before, the box could have been compromised since it wasn't secured properly.

Take the machine off the network while you try to track down what happened.

Are you able to ssh into the box by using ssh user@localhost?

---

### Post by bodhi.zazen on 2011-03-25
Could be any number of things, denyhosts or fail2ban (or similar) on the server. Could be your  server changed ip addresses or a problem with your router or network.

As far as dictionary attacks, they are common enough to be "normal".

IMO you simply need to use keys and disable passwords (for ssh). Should be fine with OpenVPN.

I agree, you need to look further server side.

---

### Post by MMegaTron on 2011-03-28
Hi guys,

Thanks very much for your replies.  It turns out that the ip address had changed, we have a dns name mapped to our local ip so it changing meant it was mapping to a non-existant address.  I remapped it to the right one and it is all working again now.  However I'm not certain what caused the ip change (any ideas anyone?).  I haven't tried getting in via localhost, but that sounds like a good suggestion and will try asap.  I think your right bodhi.zazen keys probably would be very wise! We're having the server checked over by a security specialist company now and hopefully we will find out if it has been comprimised or not. 

Thanks
Jack_****_[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

---

### Post by cariboo on 2011-03-28
If you use DHCP to set your server ip address, it could change on a reboot. To prevent that from happening, I always set a static ip address for the server.

---

