---
title: "Unable to run an IPTables command"
date: 2016-01-05
forum: Server Platforms
---

### Post by alfirdaous on 2016-01-05
Hello everyone,

I would like to run this command using php:

```

$cmd = '/sbin/iptables -A INPUT -s 41.100.123.100 -j DROP';
echo $cmd.'<br />';
        $run = exec($cmd .' 2>&1');
        echo 'run '.$run.'<br />';
```

The result is:

```

/sbin/iptables -A INPUT -s 41.100.123.100 -j DROP

**run Perhaps**** iptables or your kernel needs to be upgraded.**

```

Thanks in advance

---

### Post by matt_symes on 2016-01-05
Hi

The error message may be a red herring as iptables requires elevated privileges to run.

You don't want to run php on a webserver as root and you don't really want to use php to alter your firewall.

Why are you trying to do this and what are you trying to achieve ?

Kind regards

---

### Post by alfirdaous on 2016-01-05
The aim to do this, is that I have a PHP script scanning uploaded files, if any malware detected, it should ban a person using IPTables

---

### Post by SeijiSensei on 2016-01-06
If the script is running outside the web service, like from crontab, have it run as root.

If not, then write the IP address to a file, and write a script to run from crontab as root each minute that checks the file and adds the iptables rule.

---

### Post by alfirdaous on 2016-01-06
Well thank you very much SeijiSensei

---

