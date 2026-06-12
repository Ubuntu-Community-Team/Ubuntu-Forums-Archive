---
title: "How to allow only one website from internet"
date: 2012-09-23
forum: Server Platforms
---

### Post by Xgamer on 2012-09-23
Hi, i have to solve this situation,customer wants to allow access to only one website from his lan. Router is ubuntu server machine so how could I do that? I think that proxy server is little overkill, maybe configure iptables somehow. Thanks for advices :)

---

### Post by Habitual on 2012-09-23
["deny from" in an .htaccess file]("http://serverfault.com/questions/246003/apache-httpd-how-can-i-deny-from-all-allow-from-subnet-but-deny-from-ip-withi")
is incorrect for this situation, sorry about that.

---

### Post by agillator on 2012-09-23
From what you said I assume you are not running the server the web site is on, but are using a browser to do get to it and this is what you want to block. You have a couple of choices depending upon your actual situation. IPTABLES can block access to everything except the ip (or ip range) the site is on. You will have to check the actual configuration of your router/firewall to get the actual values, but the command would be similar to 'iptables -I <chain, probably INPUT> -p tcp -i <interface facing the internet> -s <url of the web site to accept, e.g. ok.website.com> -j ACCEPT'. Make sure the policies are all DROP or else add a rule to follow this one (i.e. insert it first) to read something like iptables -I INPUT -p tcp -i <whatever> -j DROP. Make sure this rule it activated AFTER the other rule or you will drop everything. Note that using the url of the site lets iptables itself get the ip(s). You can list the ips instead if you wish. Doing so might allow iptbles to run faster. I'm not sure if iptables does its lookup everytime the rule is checked or just when it is initially loaded. Also be aware that most firewalls are set up to block almost everything except packets in response to or associated with a connection made by a user on the LAN. So, putting the rules in the OUTPUT chain is probably also a good idea - block the traffic in both directions. Specifics really do depend on the configuration of your router/firewall. Running a listing (iptables -L -v -n --line-numbers) will show you that.

Your other option, of course, blacklist everything except the site you want in the browser. How you do that differs from browser to browser and is not an all encompassing solution.

---

### Post by conradin on 2012-09-24
What is the site? Is it the entire site, or just one page?
You can modify hosts.deny to say
```
ALL EXCEPT SomeSite.com
```

[http://linux.about.com/od/commands/l/blcmdl5_hostsde.htm](http://linux.about.com/od/commands/l/blcmdl5_hostsde.htm)

Ive done some work where the client had a large lobby monitor and wanted to display Intranet web-pages. In that case I wrote a browser with QT. Users of my browser could click through the site, but had no option to navigate elsewhere.

---

### Post by SeijiSensei on 2012-09-26
> **Xgamer said:**
> Hi, i have to solve this situation,customer wants to allow access to only one website from his lan. Router is ubuntu server machine so how could I do that? I think that proxy server is little overkill, maybe configure iptables somehow. Thanks for advices :)

```

iptables -A INPUT -p tcp -d ip.of.permitted.site --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j REJECT

```

Add that to your existing set of iptables rules.

---

