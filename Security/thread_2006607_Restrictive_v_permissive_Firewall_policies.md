---
title: "Restrictive v permissive Firewall policies"
date: 2012-06-19
forum: Security
---

### Post by Loerie on 2012-06-19
Firestarter has 2 options:
Restrictive by default
Permissive by default

Let's assume one selects 'restrictive' and whitelists port 80 (example).

Let's assume I don't want a connection with ip address 111.222.211.112 (example) which legitimate could use port 80.

How can one blacklist this ip address in a 'whitelist traffic' mode?

Thanks

---

### Post by Soul-Sing on 2012-06-19
ufw is the default firewall for Ubuntu. Or gufw.
restrict access on ip level is done via:
```
sudo ufw deny from -ip- to any
```
```
sudo ufw deny out to -ip-
```

> How can one blacklist this ip address in a 'whitelist traffic' mode?

Do not understand.

---

### Post by Loerie on 2012-06-19
Thanks leoquant.
I am using Firestarter as a GUI to configure my firewall and have selected the 'restrictive by default, whitelist traffic' option under 'policy' in Firestarter.

This allows ALL traffic through port 80.

The problem is that I do not see an option to simultaneously  BLOCK unwanted traffic through port 80 from a specific ip address when having selected the 'restrictive by default, whitelist traffic' option under 'policy' in Firestarter.

In short, as an example, I want to whitelist port 80 but at the same time blacklist a specific ip address using firestarter when having selected the 'restrictive by default, whitelist traffic' option under 'policy' in Firestarter.
Thanks!

---

### Post by Ms. Daisy on 2012-06-22
From the [Firestarter community documentation]("https://help.ubuntu.com/community/Firestarter"):
> Although Firstarter is fully functional, active development ended in 2005 with version 1.0.3.  What that means for you is fewer and fewer people use Firestarter, they're using UFW, iptables, or one of the other active alternatives instead.  Thus you'll probably have trouble finding someone that can answer your question.

---

### Post by Loerie on 2012-06-23
Thank you Ms. Daisy.

As a 'non-geek' I like the simplicity of FS and the ability to monitor my connections, traffic and 'hits'.

If using GUFW, how can I monitor in a simple, user friendly way whom/what I am connected to in realtime?

---

### Post by Ms. Daisy on 2012-06-23
I guess that depends on how well you understand internet traffic.  I find it fairly simple to look at the ufw logs to monitor things.   

For real time information you can use ```
sudo watch netstat -anlpe
``` which refreshes every 2 seconds and gives you a list of active connecitons.

---

