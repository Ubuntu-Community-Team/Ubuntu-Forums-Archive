---
title: "Denyhosts and libpam-shield  - SSHd"
date: 2013-09-12
forum: Security
---

### Post by rollyah on 2013-09-12
When it comes to protecting SShd which is better to use 
they both protect against attackers trying to guess or brute force their way into the box through ssh. 
is there any benefit of one over the other ?

---

### Post by unspawn on 2013-09-12
> **rollyah said:**
> When it comes to protecting SShd which is better to use 
 DenyHosts default method is blocking through tcp_wrappers (/etc/hosts.{deny,allow}) which means it can only work with applications that are compiled with libwrap ('ldd /path/to/binary|grep libwrap') but what's more tcp_wrappers enables *the application itself* to make the decision to block or not. And pam-shield goes even allowing the application to access the PAM stack. Since it makes sense to block these attacks as soon (as low in the network stack as possible) I'd say *neither*. Fail2ban uses iptables and that's exactly the right level. (Additionally it can be configured to use *ipset* which is even more efficient because it only requires one iptables rule and does not clog up the default table in use. As far as tables go BTW I suggest the "raw" and not the "filter" table.)

---

### Post by CharlesA on 2013-09-12
I just use iptables directly instead of relying on Fail2ban to block SSH attacks. They accomplish the same thing, though.

---

### Post by rollyah on 2013-09-13
That makes perfect sense, thank you for the explanation.
i'll research fail2ban, but since you're familiar with it i hope you can answer this question:
this box will be a gateway having shorewall,snort(as IDS) on it.
will fail2ban affect shorewall config, and at the same time does it make sense to install fail2ban given that snort is installed?


> **unspawn said:**
> DenyHosts default method is blocking through tcp_wrappers (/etc/hosts.{deny,allow}) which means it can only work with applications that are compiled with libwrap ('ldd /path/to/binary|grep libwrap') but what's more tcp_wrappers enables *the application itself* to make the decision to block or not. And pam-shield goes even allowing the application to access the PAM stack. Since it makes sense to block these attacks as soon (as low in the network stack as possible) I'd say *neither*. Fail2ban uses iptables and that's exactly the right level. (Additionally it can be configured to use *ipset* which is even more efficient because it only requires one iptables rule and does not clog up the default table in use. As far as tables go BTW I suggest the "raw" and not the "filter" table.)

---

### Post by CharlesA on 2013-09-13
I don't think it will affect anything as Fail2ban just looks thru your logs and blocks IP addresses with failed login attempts.

---

### Post by unspawn on 2013-09-14
> **rollyah said:**
> will fail2ban affect shorewall config, 
No as per reason given by CharlesA.


> **rollyah said:**
> does it make sense to install fail2ban given that snort is installed?
Fail2ban mostly is about *end point security* so it makes sense if you would allow SSH access to your gateway itself from the outside.

---

### Post by steve26 on 2014-06-28
> **unspawn said:**
> And pam-shield goes even allowing the application to access the PAM  stack. Since it makes sense to block these attacks as soon (as low in  the network stack as possible) I'd say *neither*. Fail2ban uses iptables and that's exactly the right level..

It's incredibly important to implement security in **Layers**. This means that just running Fail2Ban will simply** NOT** cut it. 

If you ***just*** rely on Fail2Ban, your Intrusion Detection System is inherently insecure, and has a gaping hole: *_**"the Single Point of Failure"**_*

*While Fail2Ban is a great tool*, it depends on an active running *service*, and monitors *log files*. this means that there are a large number of situations where Fail2Ban can actually cease to ban anything. moreover, you should **never** trust your local log files. you should only use them for general oversight, and basic Intrustion Detection System functionality.

 What is the service crashes? What if for some reason it fails to start at boot? what if the log files permissions get changed? what if this means the application can no longer log its authentication failures? what if the program in question is updated, and changes its logging location? what if the program in question changes the way it logs authentication failures, and the regex suddenly needs to be updated? what if the syslog service goes down? and so on, and so forth..

as you can see, there is far too many possibilities which can lead to Fail2Ban, **failing-to-ban**. 

Like I said at the beginning of this post... the number one prinicipal in computer security, taught for many years, is to **always implement security in Layers**.  There IS never, and will NEVER be a "One size fits all" solution to security.

there is **nothing** wrong with running Fail2Ban along side DenyHosts. Fail2Ban can do short bans, while DenyHosts can execute the longer bans (day long?)

 furthermore, libpam-shield is a **great** tool for defending against brute force attacks. it is designed to ban hosts on the **Routing Table** (by default), which is *more low level than IPTables and Fail2Ban...*! but can also be configured to optionally use your Firewall Chain if needed. not to mention it uses a fast-access database to store it's real time information, which can also persists across reboots.

 besides the fact that the PAM stack is ***By Design*** THE place where you should decide whether to ACCEPT or DENY a login; the only way to actually *trigger* fail2ban is to let the host through to the PAM Stack to begin with :) the difference is the pam-shield doesn't rely on untrustworthy log files, or services that can fail, but rather, it relies on the PAM Stack, which is something much more stable and secure.

not to mention the only time it really ever matters how low in the stack it is, is during a heavily distributed brute force attack, or denial of service. in this case, you will likely be getting your hosting provider to black hole the hosts responsible on the routing table anyways..

it's unfortunate that people think that it's either one, or the other... i'm not sure if it's cronyism, laziness, or misunderstanding.. but you simply should **never** depend on one solution to get the job done. while your at it, you might as well configure pam_tally2, and double check your /etc/ssh/sshd_config for MaxStartups and MaxAuthTries. **fall back's are always important!**

):P

---

### Post by CharlesA on 2014-06-28
Sounds like a bit of a soapbox rant there. :)

If for some reason the permissions on your log files change or are overwritten, what would be the logical conclusion - that your box was owned, or that an application decided to mess with them?

I'd say the box is owned.

With that being said, I don't think I've ever run into a problem where a service didn't start on boot unless I was out of disk space or something wasn't mounted.

Please note: I've been running [CSF]("http://www.configserver.com/cp/csf.html") for a while now and it does the same thing as DenyHosts or Fail2Ban, but it also does checksum matching and other stuff. Quite handy imo. It makes it way easier to deal with iptables too.

---

### Post by thnewguy on 2014-06-29
I'd like to point out that, contrary to what one of the above posters wrote, DenyHost does not rely soley on tcp_wrapper. DenyHost, by default, uses both the /etc/hosts.deny file (tcp_wrapper) AND works with the iptables firewall. While both are enabled out of the box, the firewall option can be disabled if you don't want it. See their website for details: [http://denyhost.sourceforge.net/news.php](http://denyhost.sourceforge.net/news.php)

Basically DenyHost and Fail2Ban do the same thing, so it's a bit of a toss up as to which you prefer.

---

### Post by bogstad on 2015-01-21
Continuing the trend of correcting errors, libpam-shield can also manipulates iptables (by default it uses null routes).   So don't use that as a reason to choose to choose between the various options.  One reason to use libpam-shield MIGHT be because it is directly in the path of logins and is not dependent on reading log files to notice attackers.   This MIGHT make it more reliable then other packages since it sees (and counts) every login attempt directly.

---

