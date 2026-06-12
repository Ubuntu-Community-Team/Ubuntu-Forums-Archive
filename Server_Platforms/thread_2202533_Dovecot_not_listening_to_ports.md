---
title: "Dovecot not listening to ports"
date: 2014-01-29
forum: Server Platforms
---

### Post by esben2 on 2014-01-29
Hello. I've followed this tutorial [https://www.digitalocean.com/community/articles/how-to-set-up-a-postfix-e-mail-server-with-dovecot](https://www.digitalocean.com/community/articles/how-to-set-up-a-postfix-e-mail-server-with-dovecot) trying to setup a dovecot/postfix mail server on my droplet mail.traede.com. I successfully send a mail using mailutil, but cannot connect through Mozilla Thunderbird.


SSL certification is installed and is working fine, but for some reason dovecot is not listening on port 143 or 587.


This is my /etc/dovecot/dovecot.conf [http://pastebin.com/YnhP95QU](http://pastebin.com/YnhP95QU)
This is my /etc/postfix/main.cf [http://pastebin.com/EAuYppP3](http://pastebin.com/EAuYppP3)
This is my /etc/postfix/master.cf [http://pastebin.com/400pmiXr](http://pastebin.com/400pmiXr)


sudo netstat -taupen returns [http://pastebin.com/YazYquru](http://pastebin.com/YazYquru)


telnet localhost 143 returns
Trying 95.85.60.223...
telnet: Unable to connect to remote host: Connection refused


Any help is much appreciated!! And please let me know if further information is needed.

---

### Post by CharlesA on 2014-01-29
What OS are you installing this on?

Dovecot 2.x splits the configuration into multiple files instead of just dovecot.conf.

I used this tutorial to get my mail server setup:
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

---

### Post by esben2 on 2014-01-29
I'm running Ubuntu 12.04.3 x64 and looks like Dovecot is 2.0.19.

The tutorial did say that the config file was split out which is why the entire thing was erased before adding the parameters.

Just got a mail from the host saying:
"[COLOR=#666666][FONT=helvetica neue]PORT STATE SERVICE [/FONT][/COLOR][COLOR=#666666][FONT=helvetica neue]22/tcp open ssh 
25/tcp open smtp 
80/tcp open http 
443/tcp open https 
587/tcp open submission[/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue]With that said I would double check to make sure all services impad etc are running. Also, I would double check any possible blocks (ex: iptables etc).[/FONT][/COLOR]
[COLOR=#666666][FONT=helvetica neue]If you should still have issues, please provide an excerpt of your error log so we can attempt to assist you in ascertaining the issue."

Could anyone help in this regard? I'm at a amateur level of Unix and do not know how to deal with these suggestions :-)

/var/log/mail.log and /var/log/mail.err are empty.[/FONT][/COLOR]

---

### Post by CharlesA on 2014-01-29
Well, you could check to see if anything is actually listening on those ports.

Run this:

```
sudo netstat -nlp | more
```

Check to see if dovecot is listing on anything.

You can also check /var/log/syslog and /var/log/mail.log to see if there are any errors in there.

---

### Post by SeijiSensei on 2014-01-30
Dovecot is broken up into many separate components.  Did you install dovecot-imapd?  With dovecot-imapd and dovecot-core installed, I can start the server and connect to port 143 on all interfaces.

---

