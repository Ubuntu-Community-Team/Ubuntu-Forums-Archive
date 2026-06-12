---
title: "shorewall allow ports for specific IP"
date: 2009-09-01
forum: Security
---

### Post by anonmars on 2009-09-01
Hello,

Is there any way to allow traffic over certain ports for a specific IP with a shorewall command (ie dynamically)? I don't want to have to edit the config file for specific rules.

I've tried sudo shorewall allow IPaddress, but the traffic still gets dropped -- I take it that has something to do with the interaction between rules and blacklists... (allow appears to adjust the blacklist, and this IP isn't blacklisted, but there is a rule that would prevent traffic on specific ports from it).

Any ideas?

Thanks.

---

### Post by sasho_zl on 2009-09-01
In /etc/shorewall you have a rules file. You have the add the rule and restart the firewall.

---

### Post by eylisian on 2009-09-01
The easiest way to setup shorewall imo is to change directories to /etc/shorewall and then copy the following into place (for a one-interface config)

cd /etc/shorewall
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/rules .
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/interfaces .
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/zones .
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/policy .

Check the interfaces file, if eth0 isn't your interface name, make the appropriate change.

Then change the 0 to 1 in /etc/default/shorewall and start it up.

sudo shorewall start

Note: By default the one-interface rules file is configured to DROP ping requests so the machine will look like a non-responder to other hosts.

To add a port

Open the rules file, by default it's letting all traffic out and blocking everything else. To add a service port to ACCEPT traffic on a given port add a line like this (example is for SSH);

ACCEPT          net             $FW             tcp     22

Don't add anything below the last line =)

When your changes are made, restart shorewall;

sudo shorewall clear
sudo shorewall restart

I hope this was helpful,

Regards.

---

