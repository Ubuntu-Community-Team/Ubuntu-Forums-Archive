---
title: "Anyone use Firestarter?"
date: 2005-08-28
forum: Server Platforms
---

### Post by aquaboot on 2005-08-28
Hello,

I'm new to firestarter 1.01 and have a quick question. I'd like to control access to my server by turning ports off or on. For instance, I may want to allow ftp access from any external destination for a few hours and then be able to turn off access to port 22 completely. I can't seem to find a way to make policies for ports in this way. Am I just overlooking something?

Thanks Much,

---

### Post by scoon on 2005-08-28
Hey there, 

Firestarter is nothing more than a gui wrapper for iptables.  I don't know if rules like that could be wriiten.  It may be easier to set up a couple of cron jobs to turn your ftp daemon off and on at your desired times.  

regards, 

scoon

---

### Post by robert_pectol on 2005-08-29
Try Ubuntu-firewall!  It's a firewall script that gets called at boot time to automatically load and protect your system.  However, since it takes standard arguments (start, stop, status, reload, lockdown), you can invoke it or disable it from the command line very easily.  There's a config file that holds all the user's preferences.  Simply edit it to allow incoming traffic to your server and run "/etc/init.d/ubuntu-firewall.sh reload".  Then afterwards, re-edit the config file and reload the script with that same command.  Since it's command line driven, calling it from other scripts, etc., would be trivial.  It also supports NAT and port forwarding if you want your Ubuntu Box to be a gateway for another PC or local area network!  The Website for Ubuntu-firewall is:  [http://rob.pectol.com/content/view/2/1/](http://rob.pectol.com/content/view/2/1/)  Give it a try!

---

### Post by stoffe on 2005-08-29
[QUOTE=aquaboot]Hello,

I'm new to firestarter 1.01 and have a quick question. I'd like to control access to my server by turning ports off or on. For instance, I may want to allow ftp access from any external destination for a few hours and then be able to turn off access to port 22 completely. I can't seem to find a way to make policies for ports in this way. Am I just overlooking something?

Thanks Much,[/QUOTE]
 I don't have it installed at the moment, but I think you can go to the policy page and just "Allow Service" for FTP (or whatever). Then, when not needed anymore, remove the rule again. Or did you have something more complex in mind?

---

