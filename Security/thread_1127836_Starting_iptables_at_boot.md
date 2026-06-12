---
title: "Starting iptables at boot"
date: 2009-04-16
forum: Security
---

### Post by allaboutsam on 2009-04-16
I've just ditched firestarter and gone through the iptables howto at [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo). The instructions there seem unnecessarily complicated. Is there any reason not just to add 

/sbin/iptables-restore < /etc/iptables.rules

to /etc/rc.local? Are there any circumstances under which that wouldn't work?

I'm running 8.10 desktop on my laptop, and I do use Network Manager. So far all good with the above configuration, but I would like to know if there is some problem with it that I haven't anticipated.

---

### Post by lensman3 on 2009-04-16
That will work fine.  Redhat's core 10 use iptables-restore in its bash script.

Remember that rc.local runs as the last thing during boot.  So it is possible to have an open network between the time that the network is initialized and started and when the firewall is applied. So it is possible to get hacked/infected in that 15 to 30 second window before a firewall is set.

I would suggest leaving the default firewall to be installed as usual.  I think it is started before an IP address is setup.  Then at the end of the boot, have your new script delete the old firewall and then start the new firewall.

Hope this helps

---

### Post by allaboutsam on 2009-04-17
That would be what I was missing.

Is there a better place to put it, so that it will start earlier in the boot process?

By the default firewall, do you mean ufw? If so, that is off per "chkconfig --list | grep ufw". (Why is it off? I never turned it off; nor did I turn it on. Should it be on in addition to iptables?)

---

### Post by kevdog on 2009-04-18
You could put in earlier in the boot sequence if you wanted, however Im not sure in what order the network is brought up.  Things are booted in order from 1-99.  rc.local is run after 99 services.  I have no idea when the network is brought up.  This would be important since you would want to start iptables theoretically just behind the network service.

Just my opinion, but placing your script in rc.local is fine.  Do you really think you are exposing yourself to any type of real risk in the short seconds between bringing up the network and loading the iptables rules?  Seems like a theoretical risk to me.

---

### Post by Lars Noodén on 2009-04-19
It depends on your network setup and your rules.  If you alternate between wifi and ethernet, then make sure your rules are generic enough to tolerate that.

---

