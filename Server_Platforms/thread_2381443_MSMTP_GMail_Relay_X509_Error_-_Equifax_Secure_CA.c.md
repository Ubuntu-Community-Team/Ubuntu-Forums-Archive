---
title: "MSMTP GMail Relay X509 Error - Equifax_Secure_CA.crt"
date: 2017-12-31
forum: Server Platforms
---

### Post by ghanson59 on 2017-12-31
Ubuntu Server 16.04.03
I had msmtp set up to send some server diagnostic reports and then suspended it back in September. I just restarted it and get an error that the Equifax certificate cannot be set. My understanding from reading is that Equifax is no longer a trusted source (go figure!) and I do notice that the Equifax_Secure_* certs have been removed from /usr/share/ca-certificates/mozilla. 
How do I update/correct this so I can connect with GMail again?

Here is my msmtp account settings file:
```
# msmtp config file for srvr
# https://www.emanueletessore.com/how-to-configure-msmtp-as-a-gmail-relay-on-ubuntu-server/
#
# 2017-12-31
# define the settings that can be useful for every account
defaults
        logfile /var/log/msmtp/general.log
# settings for srvr account
account srvr
        protocol smtp
        host smtp.gmail.com
        tls on
#       tls_trust_file /usr/share/ca-certificates/mozilla/Geotrust_Global_CA.crt
        tls_trust_file /usr/share/ca-certificates/mozilla/Equifax_Secure_CA.crt
        port 587
        auth login
        user emailRelay@gmail.com
        password **********
        from emailRelay@gmail.com
        logfile /var/log/msmtp/srvr.log
account default: srvr

```

Here is the error message:
```
gregh@srvr:~$ echo -e "Subject: Test Email\r\n\r\nTest email from srvr" | msmtp --from=default -t email_name@gmail.com --file=/etc/msmtp/srvr01
msmtp: cannot set X509 trust file /usr/share/ca-certificates/mozilla/Equifax_Secure_CA.crt for TLS session: Error while reading file.
msmtp: could not send mail (account default from /etc/msmtp/srvr01)

```

I can run telnet and reach GMail's servers on port 587 so it isn't a firewall issue. (I also tried pointing to Geotrust_Global_CA.crt but no luck.)
Thanks!

---

### Post by howefield on 2017-12-31
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by richard26 on 2018-12-28
I am having the same problem since posts recommending  Equifax_Secure_CA.crt are still out there. Was a solution found?

---

