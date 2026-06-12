---
title: "UFW performance with a large number of rules?"
date: 2012-12-01
forum: Security
---

### Post by Johan! on 2012-12-01
Because of spam, hack attempts, SSH brute force attacks, etc., I am trying to block all access from China.
I have a list of all IP ranges belonging to China in CIDR notation, and adding these to UFW will result in over 2500 new rules.

Will this large number of UFW rules have a big impact on my servers  performance?

---

### Post by chadk5utc on 2012-12-01
As your firewall grows it is possible for bandwidth to slow a bit depending on your setup and the number of services your filtering and the number of nodes on your network. Is this a stand alone firewall or more likely shared with a web server? I have a firewall setup, iptables with a large ruleset and have blocked more than 32000 CIDR addresses for China, Asia, Pakistan, Korea (more)Etc and I have not personally noticed any performance issues or network/bandwidth issues. Here is a link for reference with some guidelines on cpu throughput info and is intended to be a stand alone firewall.
[http://www.pfsense.org/index.php?option=com_content&task=view&id=52&Itemid=49](http://www.pfsense.org/index.php?option=com_content&task=view&id=52&Itemid=49)

 Chad

---

### Post by Ms. Daisy on 2012-12-01
I take it you're not behind a router?  

It helps to cut down on the brute force attacks if you run your ssh server on a random high port instead of 22. It isn't really a security measure, but more bots seem to scan & brute force the passwords on port 22 in my experience.

---

### Post by Johan! on 2012-12-02
> **Ms. Daisy said:**
> I take it you're not behind a router?  

It helps to cut down on the brute force attacks if you run your ssh server on a random high port instead of 22. It isn't really a security measure, but more bots seem to scan & brute force the passwords on port 22 in my experience.

It's not just SSH, I am more concerned about hacks against Wordpress, Drupal, a forum, the mail service and so on. And of course the blog and forum spam.

> **chadk5utc said:**
> As your firewall grows it is possible for bandwidth to slow a bit depending on your setup and the number of services your filtering and the number of nodes on your network. Is this a stand alone firewall or more likely shared with a web server? I have a firewall setup, iptables with a large ruleset and have blocked more than 32000 CIDR addresses for China, Asia, Pakistan, Korea (more)Etc and I have not personally noticed any performance issues or network/bandwidth issues. Here is a link for reference with some guidelines on cpu throughput info and is intended to be a stand alone firewall.
[http://www.pfsense.org/index.php?option=com_content&task=view&id=52&Itemid=49](http://www.pfsense.org/index.php?option=com_content&task=view&id=52&Itemid=49)

 Chad
Thanks!
It's a web server, so it runs Apache, a few databases, a few web sites and a mail server. I will try it first with a small set of rules and see what happens. If there's no noticable impact, I will add more blocks.

---

### Post by SeijiSensei on 2012-12-02
I block spam at the mail server itself rather than with iptables.  I do have some scripts that scan logs to see which IP addresses are sending lots of spam and then adds iptables rules to block those specific addresses.  I use sendmail rather than postfix, so I cannot tell you how to configure it to block Chinese senders.  In [sendmail]("http://www.sendmail.com/sm/open_source/docs/m4/anti_spam.html") you can add rules to /etc/mail/access that block SMTP senders by domain.  "Wrapping" the SMTP server in [xinetd]("http://www.xinetd.org/") and using /etc/hosts.[allow|deny] [rules]("http://linux.die.net/man/5/hosts_access") is another option.

You can also establish [access rules]("http://httpd.apache.org/docs/2.2/howto/access.html") in Apache.  You can block all hosts in the .cn domain like this:

```

<Directory "/var/www">
    [stuff]
    deny from .cn
</Directory>

```

Most server applications give you control over access.  If you have an especially balky one, there is always xinetd.

---

### Post by unspawn on 2012-12-02
> **Johan! said:**
> I have a list of all IP ranges belonging to China in CIDR notation, and adding these to UFW will result in over 2500 new rules. Will this large number of UFW rules have a big impact on my servers  performance?
If you're concerned about the impact of large rule sets there's no reason why you shouldn't be able to *test* it yourself (virtualization, Jperf), do think about rule placement (raw table, "-J NOTRACK"), regularly refresh ranges (assignments not static, they change over time) and have a look at *ipset*: because with ipset filtering your .cn TLD efficiently and maintenance-friendly *requires only one iptables rule*. 

More than that though...


> **Johan! said:**
> Because of spam, hack attempts, SSH brute force attacks, etc., I am trying to block all access from China.
Do question the validity of what you're doing in terms of (mis)perception and (in)efficiency. If you combine nfo on attacks you've seen in the past with insights from say Project Honeypot, Stop Forum Spam, Dancho Danchev and Arbor Networks you'll find China, the US and Russia remain top three TLDs but you may also see for instance a TLD like India moving up wrt spam only. And if you tally attack activity more specifically you may find that within a TLD some ASNs cause ninety nine per cent of the trouble and the same goes for ranges within a single ASN. By all means, block ranges if it makes you feel good, but *do focus on things that matter*. Ensure you have Linux admin knowledge: a web-based management panel is *not* a substitute. Invest in proper host and service hardening (which should include passing up on "security by obscurity" for using tools like fail2ban, checking SANS and OWASP checklists and knowing when to block hostile activity at the application level with say mod_security instead of using access rules and when to block attacks at the network level). Realize security, like maintenance, is a continuous process: don't run or allow access to what is not needed, update when updates are released, make regular backups, read reports and regularly audit the machine locally and from remote (as in OpenVAS or equivalent, not nmap). Should you have time to spare try to learn from Real Life compromises. 
Anticipate, remain vigilant and most of all *have fun*.

---

