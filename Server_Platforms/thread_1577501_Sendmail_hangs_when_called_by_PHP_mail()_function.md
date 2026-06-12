---
title: "Sendmail hangs when called by PHP mail() function"
date: 2010-09-18
forum: Server Platforms
---

### Post by Kethinov on 2010-09-18
Hi all,

This appears to be a common problem and after much googling I've uncovered many threads both here and elsewhere, but none seem to have had the answer I'm looking for.

I've got a PHP script which send email like this:

```
mail($email, $subject, $message, "From: noreply@$server_name", "-fnoreply@$server_name");
```

However, when the script executes, /var/log/mail.log says this:

```

Sep 18 20:02:55 myhostname sendmail[20381]: My unqualified host name (myhostname) unknown; sleeping for retry

```

After an agonizing 60 second delay, it gives up:

```

Sep 18 20:03:55 myhostname sendmail[20381]: unable to qualify my own domain name (myhostname) -- using short name

```

At which point it successfully sends the email.

Has anyone figured out how to kill this 60 second delay?

---

### Post by windependence on 2010-09-19
Install postfix. It is a drop in replacement for sendmail and configuring sendmail is hell. Then you can adjust your settings to either (1) get the mail working or (2) remove the delay.
 
The problem you are having is most likely related to DNS which needs to be correct to handle mail.
 
-Tim

---

### Post by Kethinov on 2010-12-22
Thanks - postfix did the trick.

A note to anyone who follows this advice... you will need to reboot your server after installing postfix and removing sendmail. For some reason, sendmail reserves port 25 indefinitely until you reboot and I couldn't figure out how to kill the process without rebooting.

---

### Post by swbca on 2012-12-31
SOLUTION: (found on FreeBSD forums)
 
edit the **/etc/hosts** file as shown below
 
hosts file **_before_** edit
---------------------------------------------------------------------------
127.0.0.1 localhost
127.0.1.1 MINT14
 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
---------------------------------------------------------------------------
 
hosts file **_after_** edit - added a fqdn (does not have to be a valid public DNS record)
---------------------------------------------------------------------------
127.0.0.1 localhost
**_127.0.1.1 mint14.christmaslake.net_**
 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
---------------------------------------------------------------------------

---

