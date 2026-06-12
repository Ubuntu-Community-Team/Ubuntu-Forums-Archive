---
title: "Iptables and blocking ips"
date: 2012-04-21
forum: Security
---

### Post by tcsmith1978 on 2012-04-21
Hi,

Am okay with iptables but wondered if there was a way to dynamically add and remove ip addresses from a ban list. Ideally I would like to just be able to edit a DB of some description or a text file.

Thanks,

Tim

---

### Post by unspawn on 2012-04-21
The "recent" module nfo in 'man iptables' contains examples for addition and removal of IP addresses from /proc/net/ipt_recent/ lists. Doesn't get easier than that. Only caveat is it supports only IP addresses, not ranges.

---

### Post by wacky_sung on 2012-04-21
Do you ever think of ban it through host file and it make things much easy for you.

Check [this]("http://indrajeet-deshmukh.blogspot.co.uk/2011/04/18how-to-block-websites-using-hosts.html") out.

---

### Post by gradinaruvasile on 2012-04-21
This is just the first google hit if you search "iptables block ip"...:

[http://nixcraft.com/getting-started-tutorials/1427-iptables-block-ip-address.html](http://nixcraft.com/getting-started-tutorials/1427-iptables-block-ip-address.html)

---

### Post by SeijiSensei on 2012-04-22
I create my ruleset from a script where I can use for loops to iterate over a list of banned IPs like this:

```

BANNED=$(cat /usr/local/etc/banned_ip_list)

for addr in $BANNED
do
     /sbin/iptables -I INPUT -s $addr -j REJECT
done

```

The list is a plain text file with one IP address per line.

If this were part of a longer script, I'd probably use -A instead of -I.  However -I works either way since it puts the blocking rules above all the other rules in the set.

Removing banned IPs is a bit trickier.  Rather than attempt to delete the specific rule, I'd just remove the address from the list then rerun the script.

---

### Post by wacky_sung on 2012-04-22
> **SeijiSensei said:**
> I create my ruleset from a script where I can use for loops to iterate over a list of banned IPs like this:

```

BANNED=$(cat /usr/local/etc/banned_ip_list)

for addr in $BANNED
do
     /sbin/iptables -I INPUT -s $addr -j REJECT
done

```

The list is a plain text file with one IP address per line.

If this were part of a longer script, I'd probably use -A instead of -I.  However -I works either way since it puts the blocking rules above all the other rules in the set.

Removing banned IPs is a bit trickier.  Rather than attempt to delete the specific rule, I'd just remove the address from the list then rerun the script.

Do you have an auto update script using the ban list using the link from [blocklist]("http://www.iblocklist.com/lists.php")?
Try to use [Moblock]("http://moblock-deb.sourceforge.net/") but seem not working anymore.

---

### Post by unspawn on 2012-04-22
> **wacky_sung said:**
> Do you ever think of ban it through host file and it make things much easy for you.
That IMHO depends on the reason for blocking. The "recent" module 0) makes removing IP addresses as easy as 'echo -1.2.3.4 > /proc/net/xt_recent/NAME', 1) it doesn't depend on an application having its own implementation of or having been compiled with libwrap support, 2) doesn't expose the application to packets and 3) its blacklist resides in memory only and does not require an application to read any FS file like /etc/hosts.{deny,allow}. 
Nothing easier, efficient and more secure than that.


> **SeijiSensei said:**
> ```

     /sbin/iptables -I INPUT -s $addr -j REJECT
```
That'll work OK with a couple of addresses but rules are traversed linearly. If one loads a gazillion rules in the filter table INPUT chain it will be way slower compared to using the "recent" module or ipsets.

---

### Post by wacky_sung on 2012-04-22
> **unspawn said:**
> That IMHO depends on the reason for blocking. The "recent" module 0) makes removing IP addresses as easy as 'echo -1.2.3.4 > /proc/net/xt_recent/NAME', 1) it doesn't depend on an application having its own implementation of or having been compiled with libwrap support, 2) doesn't expose the application to packets and 3) its blacklist resides in memory only and does not require an application to read any FS file like /etc/hosts.{deny,allow}. 
Nothing easier, efficient and more secure than that.



That'll work OK with a couple of addresses but rules are traversed linearly. If one loads a gazillion rules in the filter table INPUT chain it will be way slower compared to using the "recent" module or ipsets.

Currently i have not tried out [IPSet]("http://ipset.netfilter.org/") because it work on Kernel 2.4.x and 2.6.x. Thus using the latest Ubuntu 12.04 with Kernel 3.2.x and i do not wish to test it if it is workable.

---

### Post by unspawn on 2012-04-22
//OT: both [http://git.netfilter.org/cgi-bin/gitweb.cgi?p=ipset.git;a=shortlog;h=HEAD](http://git.netfilter.org/cgi-bin/gitweb.cgi?p=ipset.git;a=shortlog;h=HEAD) and [http://blog.gmane.org/gmane.comp.security.firewalls.netfilter.general](http://blog.gmane.org/gmane.comp.security.firewalls.netfilter.general) show Linux-3.x work is progressing and [https://bugs.launchpad.net/ubuntu/+bug/979682](https://bugs.launchpad.net/ubuntu/+bug/979682) shows a fixed and approved package.

---

### Post by SeijiSensei on 2012-04-22
> **unspawn said:**
> That'll work OK with a couple of addresses but rules are traversed linearly. If one loads a gazillion rules in the filter table INPUT chain it will be way slower compared to using the "recent" module or ipsets.

Modern computers can traverse thousands of iptables rules in milliseconds.  My block lists contain a couple hundred entries and, even on older hardware, I saw no performance degradation by doing so.

How many addresses are we really talking about here?  I don't block thousands upon thousands of addresses by default.  Why would I?  On my mail/web servers I block addresses from repeated annoying spammers and IPs that repeatedly attempt to identify local accounts via POP3 requests or to connect to SSH.  I don't see much point in blocking thousands of addresses that will never attempt a connection.

---

