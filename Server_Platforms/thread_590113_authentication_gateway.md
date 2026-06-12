---
title: "authentication gateway"
date: 2007-10-24
forum: Server Platforms
---

### Post by cdenley on 2007-10-24
I set up an authentication gateway for my samba domain. I did it using iptables scripts. Users who try using the internet are redirected to apache using DNAT. Since the hostname they are connecting to isn't configured as a vhost, it is sent to the default vhost, which is used for authentication. Once they authenticate, it runs an iptables script using sudo. If they are a predefined user, they can access anything. Everyone else can only access a few predefined domains. If they try to access a domain they are not allowed, the DNAT rule send them to my server. Assuming it is a web request, the php script sees they are already authenticated since their username is in the database, and prints an access denied message. The PDC logon script runs wget to request a php script from the web server which gets the client's IP, and deletes all the firewall rules for that machine, requiring the new user to authenticate before using the internet.

This setup seems to work perfectly, except occasionally, iptables seems to reset itself entirely, or delete rules it shouldn't. Also, I noticed that occasionally, even though the iptables scripts have finished running, if I try listing nat rules on the server, it hangs for a few seconds while listing the new rules. I don't think it's a scripting problem, since I run the same functions over and over, but only occasionally see a problem. Is iptables not meant to be changed frequently? Is there an easier way to go about this? Can I use squid to achieve the desired results? I would want to restrict all internet traffic, not just web traffic. If an authenticated user logs out from windows, the next user who logs in on that machine should be required to authenticate.

---

### Post by robert_pectol on 2007-10-24
> **cdenley said:**
> I set up an authentication gateway for my samba domain. I did it using iptables scripts. Users who try using the internet are redirected to apache using DNAT. Since the hostname they are connecting to isn't configured as a vhost, it is sent to the default vhost, which is used for authentication. Once they authenticate, it runs an iptables script using sudo. If they are a predefined user, they can access anything. Everyone else can only access a few predefined domains. If they try to access a domain they are not allowed, the DNAT rule send them to my server. Assuming it is a web request, the php script sees they are already authenticated since their username is in the database, and prints an access denied message. The PDC logon script runs wget to request a php script from the web server which gets the client's IP, and deletes all the firewall rules for that machine, requiring the new user to authenticate before using the internet.

Sounds like an effective captive portal you've got setup.  Very nice!

> **cdenley said:**
> This setup seems to work perfectly, except occasionally, iptables seems to reset itself entirely, or delete rules it shouldn't.

Perhaps a bug in one of your scripts?  The iptables tool itself is probably not the culprit as it's mature code with years of development and refinement behind it.  Go through your script code with a fine tooth comb and I bet you'll find it.

> **cdenley said:**
> Also, I noticed that occasionally, even though the iptables scripts have finished running, if I try listing nat rules on the server, it hangs for a few seconds while listing the new rules. I don't think it's a scripting problem, since I run the same functions over and over, but only occasionally see a problem.

Sounds like a name resolution issue.  Try listing the rules with, "-n" switch, which will list just the IP addresses and port numbers.  Quoting from the iptables man page:
> iptables manpage "...By default, the program will try to display them as host names, network names, or services (whenever applicable)."

> **cdenley said:**
> Is iptables not meant to be changed frequently? Is there an easier way to go about this?

Iptables is very capable of handling this without issue.  No, I don't think there is an easier or better way.

> **cdenley said:**
> Can I use squid to achieve the desired results? I would want to restrict all internet traffic, not just web traffic.

Dynamic packet filtering and redirection is pretty much it then.  I think your current approach is valid.  You just need to fix the applicable script(s).  Squid can provide a certain level of access control.  However, as you mentioned, you need to restrict all Internet traffic, not just Web traffic.  I'd stick with your current approach.  Good luck.

---

### Post by cdenley on 2007-10-24
Thanks for the tip on using the -n switch. I listed the rules in the script with an iptables command so I could find which rules needed to be deleted. I added the -n switch to this command in the script, and it works much faster. I have also been unable to reproduce my problem since that change, so I think that may have fixed it. I will keep testing, though.

---

