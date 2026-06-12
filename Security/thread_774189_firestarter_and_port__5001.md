---
title: "firestarter and port  5001"
date: 2008-04-29
forum: Security
---

### Post by paulcaseyjr on 2008-04-29
Hi,
I'm running firestarter on Ubuntu desktop (Hardy Heron - 8.04) and it's basically working fine - very well in fact! 

The only thing that seems to be a problem is the remote connection to a slingbox.  That used to work on the hardware firewall by setting up port forwarding for port 5001 to the correct internal address. 
In firestarter, I set up a policy and forwarding rule for inbound traffic for port 5001 and the correct internal address, but the connection never succeeds -- and there is nothing showing up in the Blocked connections message log. 

Any ideas?

Thanks, 

Paul

---

### Post by moonpup on 2008-04-29
Is the hardware router/firewall still allowing the traffic and forwarding it to the correct box?? Or did you remove that hardware and are using this linux box as the router/firewall?

To me it sounds like the hardware router/firewall (if still in place) is either not allowing the traffic or is forwarding it to the wrong computer.

---

### Post by paulcaseyjr on 2008-04-29
No -- I actually removed the hardware router and linux is now in charge.  Think I'm going to add some other ports to forward and see if it will work with them or if it's 5001 related.

---

### Post by moonpup on 2008-04-29
Hi,

In that case, have you restarted iptables or at least reloaded the configuration file? If you add rules to the config, they don't take effect until you do one the above. Try restarting iptables...

---

### Post by The Cog on 2008-04-29
If you can post the output of the command ```
sudo iptables-save -c
``` then we can have a look and see if that port should be gettting through.

Also from ```
netstat -lnt
``` to see if something is even listening on that port.

---

### Post by paulcaseyjr on 2008-04-30
Well, I think you may have been right about restarting.  I actually restarted the whole box and it started working.  I really don't think I changed anything else that would have affected it.  I think today's fun will be to add another forwarding rule and see when it takes effect.  Thanks for the feedback.

---

### Post by moonpup on 2008-04-30
Well I'm glad that worked for you. As I stated, when you add and remove rules to iptables you need to restart it. It's just the way it works and why it worked when you rebooted. So just remember when you make changes to iptables, restart the service. That doesn't mean reboot... just restart iptables.

---

