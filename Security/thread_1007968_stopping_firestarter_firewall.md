---
title: "stopping firestarter firewall"
date: 2008-12-11
forum: Security
---

### Post by homebuilder on 2008-12-11
Hi,
 I installed firestarter now I am having trouble accessingshared folders on my ubuntu machine from my other machines. I can manually stop it but it restarts everytime I reboot... how can I stop or delete firestarter? 


related, I installed a virus software program, now sure how to update, make sure its working... yeah, new to ubuntu

---

### Post by dragos_iliescu_2005 on 2008-12-11
You should open the correct port inside the firewall. Open Firestarter, navigate to Policy, click add and add your port to be openned or your service to be allowed.

---

### Post by homebuilder on 2008-12-11
Thanks, but I am not tryingto get a port open, trying to allow other computers on the network to share the directories. My xp machines can access when firestarter is turned off, but not when it is on. 

So... since I am not an expert, not sure how to make it work with it on... how do you turn it off completely so it doesnt reload when you restart?

---

### Post by cariboo on 2008-12-12
You could just use Synaptic to completely remove Firestarter, yuou would then need to clear the iptables rules you set. In a terminal type the following:

```
sudo iptables -F
```

and

```
sudo iptables -X
```

to check the iptables rules

```
sudo iptables -L
```

Jim

---

### Post by iponeverything on 2008-12-12
After removing firestarter, I would also purge anything it left behind:

```
sudo dpkg --purge firestarter
```

---

### Post by dragos_iliescu_2005 on 2008-12-12
> **homebuilder said:**
> Thanks, but I am not tryingto get a port open, trying to allow other computers on the network to share the directories. My xp machines can access when firestarter is turned off, but not when it is on. 

So... since I am not an expert, not sure how to make it work with it on... how do you turn it off completely so it doesnt reload when you restart?

You can refer to Firestarter as to a graphical interface. Using this interface you can manage the firewall rules (rules are stored in /etc/iptables.up.rules). For having supplementary informations, follow the link [http://www.fs-security.com/docs/persistence.php]("http://www.fs-security.com/docs/persistence.php")
**I am not recommended to stop the firewall,** but to edit the rules.

There are others interfaces too that you can use to manage the firewall rules, but Firestarter is by far the easiest one.
To allow others to access your resources, open Firestarter, navigate to Policy tab, select inbound traffic were you can:
-specify the ip's that you allow to access the resources or
-specify the ports or services to allow

In your case, specify the hosts to allow is your case.

---

### Post by pseudonym on 2008-12-12
> **homebuilder said:**
> related, I installed a virus software program, now sure how to update, make sure its working... yeah, new to ubuntu

If it's clamav you've installed, or clamtk (the gui version - 'Virus Scanner' in your 'System' menu), then it updates itself automatically, provided you're connected to the internet from boot-up onwards.

---

### Post by bodhi.zazen on 2008-12-12
If you are wanting to run a firewall, you will need to learn how to open the ports for samba.

I suggest you remove firestarter (purge) and if you wish to use a firewall take a look at UFW (gufw if you want a gui).

Antivirus is of very limited utility on Linux. If you are interested in learning security look at the stickies in the security section starting with:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

