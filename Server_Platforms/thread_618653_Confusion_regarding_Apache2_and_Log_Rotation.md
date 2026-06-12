---
title: "Confusion regarding Apache2 and Log Rotation"
date: 2007-11-20
forum: Server Platforms
---

### Post by meatpan on 2007-11-20
Hello All,

I've been trying to determine why my apache2 service is being halted every week.  As it turns out the logrotation process is restarting the server.  The apache2 installation is using SSL with an encrypted key, so when the server restarts, it prompts for a password.

The apache2 logrotation file looks like this (unmodified from installation):

```

/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}

```

First of all, why would the logging subsystem need to completely restart the server?   Does anyone know how I would go about starting a server that requires a password (when there is no terminal attached to the process)?

---

### Post by MJN on 2007-11-20
The Apache service needs to be restarted in order to free up the 'old' logfile for rotation before opening a 'new' set. Not doing so could cause some events to be lost, or the server to  balk because it cannot write to the logfile (which may not exist at the instance of rotation).

To cope with this your only real option (bar disabling the rotation of the logs) is to remove the passphrase from the private key - see [http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase) for details. Note the warning about setting permissions on the key/certificate (root read-only would suffice).

Mathew

---

### Post by p_quarles on 2007-11-20
It restarts because otherwise it won't be able to find the newly created log files. 

Normally it should not ask for a password when it does this, because it's runner as the apache user. It sounds like what's happening is that it's asking for ad admin password or a passkey to open the encrypted key. </snip>
EDIT: After reading MJN's link, I see that the suggestion I've just removed was a bad idea.

---

### Post by MJN on 2007-11-20
You were pretty much along the right lines though - however it's the encrypted private key that's the issue and so the password is related to the (de)encryption as opposed to the access permissions of the key itself.

As the link says removing the encryption is removing a *layer* of security but this is not the *only* layer - maintaining root read only permissions on the key should still provide the necessary level of protection required. (If someone gains root access they can steal the key and use it to impersonate your machine - but if they've got that far chances are this is merely one of many equally serious concerns that you'd have)

Mathew

---

