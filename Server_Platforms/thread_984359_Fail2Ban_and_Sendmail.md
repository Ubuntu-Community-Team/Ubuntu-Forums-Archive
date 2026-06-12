---
title: "Fail2Ban and Sendmail"
date: 2008-11-16
forum: Server Platforms
---

### Post by xefialtis on 2008-11-16
I have a server running Postfix with Dovecot, and I have Fail2Ban up and running...
I visited a site, the Fail2Ban WIKI ([http://www.fail2ban.org/wiki/index.php/FAQ_english](http://www.fail2ban.org/wiki/index.php/FAQ_english)) and copied the config for sendmail-whois.conf (my chosen setting) ...

My emails come with a Sender, NO SUBJECT, and NO FROM...only the TO is filled in...the body of the message looks like this:

> 
-en Subject: [Fail2Ban] ssh: banned 71.242.245.111
From: Fail2Ban <fail2ban>
To: root@localhost

Hi,

The IP 71.242.245.111 has just been banned by Fail2Ban after
3 attempts against ssh.


and the config looks like:

> 
actionban = echo -en "From:root <fail2ban>
            To: <dest>
            Subject: [Fail2Ban] <name>: banned <ip>
            Hi,\n
            The IP <ip> has just been banned by Fail2Ban after
            <failures> attempts against <name>.\n\n
            Here are more information about <ip>:\n
            `whois <ip>`\n
            Regards,\n
            Fail2Ban"|sendmail -f <sender> <dest>  


if the last line says 

> 
sendmail -t


as in the WIKI suggestion, It doesn't send anything...

Ideas?

---

### Post by Mongoose100 on 2009-02-11
I had this exact same problem. No subject and the same info appearing in the email. To fix it, I had to remove the "-en" after the echo command inside the sendmail-whois config files. Now the emails send fine.

---

