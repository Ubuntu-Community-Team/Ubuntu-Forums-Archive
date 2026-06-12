---
title: "no A record found for dns"
date: 2010-08-02
forum: Server Platforms
---

### Post by mmanjrekar on 2010-08-02
i get the following dns error whenever i try to setup the zimbra mail server. it seems entries from /etc/resolve.conf are vanishing after restarting the dns or network service. after updating this file dig gives proper result but the mail server is not able to detect it.

---

### Post by mmanjrekar on 2010-08-02
if i keep the resolve.conf file open then everything works fine. i have been able to setup the mail server but as soon as i close the file the problem persists. i have a static ip reserved from a dns pool.

---

### Post by cdenley on 2010-08-02
You're trying to setup zimbra with the domain "chaos.moc"? I don't think that is a valid domain name. Is this server supposed to receive mail from other mail servers over the internet? Did you configure that domain on a DNS server? If so, what records did you create?

---

### Post by mmanjrekar on 2010-08-02
i know it is not a valid domain name because of its 'moc' extension. it is purely meant for internal use i.e. within my network.

---

### Post by mmanjrekar on 2010-08-02
my main proble here is that the entries from /etc/resolve.conf are vanishing after sometime. now even if i keep the file open in vi, the entried get modded.

---

### Post by cdenley on 2010-08-02
> **mmanjrekar said:**
> my main proble here is that the entries from /etc/resolve.conf are vanishing after sometime. now even if i keep the file open in vi, the entried get modded.

How are you configuring your network. Did you configure all your network interfaces in /etc/network/interfaces? If you use something else, like NetworkManager in the desktop configuration, then that will overwrite /etc/resolv.conf with its own DNS settings.

---

### Post by mmanjrekar on 2010-08-02
i have configured everything by hand. i do not have any such utility running.
and just out of curiosity ... 'moc' extension should not be a problem from intranet, right?

---

### Post by cdenley on 2010-08-02
> **mmanjrekar said:**
> i have configured everything by hand. i do not have any such utility running.
and just out of curiosity ... 'moc' extension should not be a problem from intranet, right?

I don't think it would be a problem. Something must be overwriting /etc/resolv.conf if the contents keep disappearing.

---

### Post by mmanjrekar on 2010-08-02
any clue as to how i can find out what is overwriting the file even when it is opened by the root user ?

---

### Post by cdenley on 2010-08-02
What version of ubuntu are you using? 8.04?
```

sudo ps -ef
ls /etc/cron.d
cat /etc/crontab
ls -l /etc/init.d
lsb_release -r

```

---

