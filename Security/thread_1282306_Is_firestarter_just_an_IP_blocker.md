---
title: "Is firestarter just an IP blocker"
date: 2009-10-04
forum: Security
---

### Post by brain frog on 2009-10-04
I am currently looking into firewalls and can someone clearly tell me if firestarter is simply an IP blocker?

My knowledge of IP blockers is limited i know of software like peerguardian that has lists of IP addresses that it blocks like bogon or spyware sites or known attackers, firestarter only seems to allow you to add one IP address at a time not a list or have i not found the option?

I have found this link [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183) would it be worth using grapgical IP blocker instead as it seems to allow lists of bad IP addresses?

As you can tell my knowledge of networking is not fantastic but i have heard that it is important to block the connection before it connects with your computer but some block it once its already accessed your computer can anyone clear this up for me please?

Thanks

---

### Post by Lars Noodén on 2009-10-04
fwbuilder does the same thing as firestarter, if it helps to compare two tools with the same goal.

Firestarter is a Graphical User Interface to IPTables.
IPTables is a packet filter (sometimes called a firewall)  
IPTables filters where and how often network packets come or go.  

[http://www.ibm.com/developerworks/linux/library/s-netip/](http://www.ibm.com/developerworks/linux/library/s-netip/)
[http://iptables-tutorial.frozentux.net/](http://iptables-tutorial.frozentux.net/)

You have/need three common packet types, ICMP, TCP, and UDP for basic network activities.  To over-generalize, ICMP is for status of the network.  TCP is for reliable, but slower, persistent connections.  UDP is for faster connections, but neither persistent nor guaranteed.  

If you are not running a server service, then generally there are no legitimate connections initiated from outside.  Thought there will be incoming connections in response to your outgoing requests, e.g. getting mail, web surfing, torrents, etc.  However, if you are not running a server service, there is nothing listening for a connection from the outside anyway so there is nothing to connect to.  

SE Linux might be more useful for locking down desktops.  However, if you are always adding or removing programs, then SE Linux might not be a joy to work with in its most battened down mode.

---

### Post by lovinglinux on 2009-10-04
> **brain frog said:**
> I am currently looking into firewalls and can someone clearly tell me if firestarter is simply an IP blocker?

Firestarter, UFW, fwbuilder, guarddog and others are all firewall managers. Their features varies, but in a nutshell they are all capable of creating rules to block IP, port or protocol, because the real firewall (iptables/netfilter) works in the background and provides that functionality. What firewall managers do is simply allow you to create the rules without writing the iptables commands yourself. 

> **brain frog said:**
> My knowledge of IP blockers is limited i know of software like peerguardian that has lists of IP addresses that it blocks like bogon or spyware sites or known attackers, firestarter only seems to allow you to add one IP address at a time not a list or have i not found the option?

You need to use Firestarter Policy settings. Depending on which Policy you choose, it will block any traffic or allow all traffic. Then you need create specific rules to respectively allow or block specific IP addresses, ports or protocols.

Firestarter does not have a method of blocking IP addresses based on blocking lists. Gufw, which is the recommended firewall manager these days has the ability to import IP blocklists, but this functionality is very slow. If you need an ipblocker like PeerGuardian, then I recommend [moblock](http://moblock-deb.sourceforge.net/) and [iplist](http://iplist.sourceforge.net/). What they do is essentially the same as any other firewall manager like Firestarter. They create rules for the real firewall (iptables/netfilter), but their rules are solely based on lists of IP addresses. Moblock also allow you to create regular firewall rules (to block protocols and ports), so it can completely replace Firestarter. Nevertheless, moblock's regular iptables rules are launched by scripts, so you need to write the rules yourself and thus need to know iptables commands, if you want to use it as firewall manager.

What most people who needs a regular firewall and an ip blocker do is to use a firewall manager like UFW in conjunction with moblock or iplist. In this case, they must be careful about the order of starting the firewall manager and the ipblocker, otherwise one application rules might disable the other application rules.

> **brain frog said:**
> I have found this link [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183) would it be worth using grapgical IP blocker instead as it seems to allow lists of bad IP addresses?

If you use BitTorrent, then yes. I do prefer [moblock](http://moblock-deb.sourceforge.net/) with [mobloquer](http://mobloquer.foutrelis.com/) GUI, but you might feel more comfortable with iplist.

> **Lars Noodén said:**
> If you are not running a server service, then generally there are no legitimate connections initiated from outside.  Thought there will be incoming connections in response to your outgoing requests, e.g. getting mail, web surfing, torrents, etc.  However, if you are not running a server service, there is nothing listening for a connection from the outside anyway so there is nothing to connect to. 

What does means is that you don't even need a firewall if you are not running a server, because all ports are already closed and thus any unrequested incoming connections (including hacking attempts) will be rejected.

---

### Post by sharma567 on 2009-10-06
If you have Firestarter configured to allow all IPs addresses to all ports or a particular port on your server, you can’t block a specific IP from accessing those ports using the GUI interface. However, Firestarter does allow you to manually specify IP Tables rules to either load up BEFORE or AFTER the Firestarter firewall rules by editing configuration files. On CentOS 5, the file to put the rules you want to load before Firestarter’s rules is /etc/firestarter/user-pre. For rules you want to load after Firestarter loads its firewall rules, edit the file /etc/firestarter/user-post. When you add your rules, instead of using the command “iptables” you need to use the variable name “$IPT” instead. To block an IP address from accessing any of your ports, you will need to add the IP Tables rule to the user-post file.
_____________________________________________
[business opportunity directory](http://www.giblink.com/site/Businesses/)  [humor blog](http://www.davepye.com)

---

