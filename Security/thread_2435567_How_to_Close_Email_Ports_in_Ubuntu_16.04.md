---
title: "How to Close Email Ports in Ubuntu 16.04?"
date: 2020-01-22
forum: Security
---

### Post by johnsingam on 2020-01-22
Hi All,

For security purpose i want to close he Email Ports in my webserver ubuntu 16.04. Please send me the commands for close the email ports.

Thank You!

---

### Post by SeijiSensei on 2020-01-22
Unless you installed SMTP or IMAP software like Postfix or dovecot, there should be nothing listening on those ports, so there's no reason to close them specifically. Ubuntu ships with nothing listening on any port.

You can add iptables rules to block those ports, but they are extraneous:
```

sudo iptables -I INPUT -p tcp --dport 25  -j REJECT   # smtp
sudo iptables -I INPUT -p tcp --dport 465 -j REJECT   # ssmtp
sudo iptables -I INPUT -p tcp --dport 143 -j REJECT   # imap
sudo iptables -I INPUT -p tcp --dport 993 -j REJECT   # imaps
sudo iptables -I INPUT -p tcp --dport 110 -j REJECT   # pop3
sudo iptables -I INPUT -p tcp --dport 995 -j REJECT   # pop3s

```

---

### Post by johnsingam on 2020-01-23
> **SeijiSensei said:**
> Unless you installed SMTP or IMAP software like Postfix or dovecot, there should be nothing listening on those ports, so there's no reason to close them specifically. Ubuntu ships with nothing listening on any port.

You can add iptables rules to block those ports, but they are extraneous:
```

sudo iptables -I INPUT -p tcp --dport 25  -j REJECT   # smtp
sudo iptables -I INPUT -p tcp --dport 465 -j REJECT   # ssmtp
sudo iptables -I INPUT -p tcp --dport 143 -j REJECT   # imap
sudo iptables -I INPUT -p tcp --dport 993 -j REJECT   # imaps
sudo iptables -I INPUT -p tcp --dport 110 -j REJECT   # pop3
sudo iptables -I INPUT -p tcp --dport 995 -j REJECT   # pop3s

```

Thank You SeijiSensei. I will try it.

---

### Post by kevdog on 2020-01-23
The iptables method will definitely work unless you want to run the commands within ufw.  Just depends on your preference.

---

### Post by johnsingam on 2020-01-23
> **kevdog said:**
> The iptables method will definitely work unless you want to run the commands within ufw.  Just depends on your preference.

Yes, its working fine. All email functions got stop now. Thanks a lot.

---

