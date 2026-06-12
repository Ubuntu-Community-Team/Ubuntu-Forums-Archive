---
title: "Restrict FTP access in vsftpd to users on a subnet"
date: 2012-09-18
forum: Server Platforms
---

### Post by alepila on 2012-09-18
Hello everyone, I have configured an FTP server with vsftpd. For safety reasons, I would make sure that some users with write permissions, can access the server only from a particular subnet denying access from any IP address. I emphasize that the restriction must be active on a single user and not on all. Thank you very much!

---

### Post by Habitual on 2012-09-18
it's not a dated article but it may help...
[http://www.tuxradar.com/answers/467](http://www.tuxradar.com/answers/467)

Pretty sure some iptables or /etc/hosts.{allow, deny} may also be involved.

Subscribed with interest...

---

### Post by alepila on 2012-09-18
Thanks for your answer. I know TCP wrapper but I don't know how to configure it to allow a connection from one host only under s specific subnet. Is Iptables easier to configure? Do you know other methods more easier? Thank you

---

### Post by Lars Noodén on 2012-09-18
xinetd might be easier, being more customizable.

---

### Post by alepila on 2012-09-19
> **Lars Noodén said:**
> xinetd might be easier, being more customizable.

Thank you, can you post an example of configuration? Thanks

---

### Post by Lars Noodén on 2012-09-19
First there is the [disabling of the upstart script](http://askubuntu.com/questions/19320/whats-the-recommended-way-to-enable-disable-services/20347#20347) so that vsftpd can get called by xinetd.  To do that comment out the line [font=Courier New]start on runlevel [2345] or net-device-up IFACE!=lo[/font]in the file [font=Courier New]/etc/init/vsftpd.conf[/font].  Then stop vstftp: [font=Courier New]sudo service vsftpd stop[/font] 

Then comment out the line [font=Courier New]listen=YES[/font] in [font=Courier New]/etc/vsftpd.conf[/font]

Then install xinetd and make a file [font=Courier New]/etc/xinetd.d/ftp[/font]:

```

service ftp
{
        disable         = no
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/sbin/vsftpd
        # server_args     =
        per_source      = UNLIMITED
        log_on_failure  = USERID HOST
        # log_on_success  = PID HOST DURATION TRAFFIC EXIT
        # instances       = 10
        # nice            = 10
        # bind            = 192.168.0.100
        # only_from       = 192.168.0.0
        # access_times    = 08:00-15:25
        # no_access       = 192.168.54.0
        # no_access       += 192.168.33.0
        # banner          = /etc/banner.inetd.connection.txt
        # banner_success  = /etc/banner.inetd.welcome.txt
        # banner_fail     = /etc/banner.inetd.takeahike.txt
}


```

Restart xinetd for the changes to take effect.

See the manual pages for [xinetd.conf](http://manpages.ubuntu.com/manpages/precise/en/man5/xinetd.conf.5.html) for all the details.

---

### Post by alepila on 2012-09-19
Thank you very much!

---

### Post by Lars Noodén on 2012-09-19
If you need to add multiple subnets, you can do it like this with the +=

```

only_from         = 192.168.100.0/24
only_from         += 192.168.101.0/24

```

---

