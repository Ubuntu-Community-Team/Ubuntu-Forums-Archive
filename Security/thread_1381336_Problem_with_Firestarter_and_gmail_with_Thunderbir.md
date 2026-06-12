---
title: "Problem with Firestarter and gmail with Thunderbird"
date: 2010-01-14
forum: Security
---

### Post by seancyril on 2010-01-14
Hi everyone, I have just installed firestarter and since adopting a restrictive policy  have been unable to access  my gmail account  through thunderbird. I have gone to the Allow Service box and  enabled all the usual POP3 and SMTP ports plus the ones that Thunderbird uses (995 for POP and 587 for SMTP) but when I try and connect to my mail with thunderbird it tells me that the connection to the gmail server was blocked. 
When I disable the firewall then there is no problem and I can receive my mail. I don't know what else to do as I have already allowed these ports to be used so why is the firewall still blocking them?

Any suggestions welcome

Sean

---

### Post by running_rabbit07 on 2010-01-14
Get rid of Firestarter and use ufw (UncomplicatedFireWall)

Start the firewall with this command, ```
sudo ufw enable
``` You don't have to install it because it is already there. I use Thunderbird w/Gmail and I have had no problems with connecting. If you want a GUI for ufw install GUFW with, ```
sudo apt-get install gufw
``` for info on configuring it, please go to this link written by the UF Moderator bodhi.zazen. [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

---

### Post by seancyril on 2010-01-16
Thanks for the advice. I'll give it a go

---

