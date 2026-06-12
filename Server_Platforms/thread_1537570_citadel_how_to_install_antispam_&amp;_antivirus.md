---
title: "citadel how to install antispam &amp; antivirus?"
date: 2010-07-23
forum: Server Platforms
---

### Post by gabak on 2010-07-23
i just installed citadel and everything is working great , but i m getting a lot spam.
i had a pc with email zimbra emails server but it died. zimbra had antispam built in.
so how can i do to do the same with citadel?
plz some step by step.

thank you all of you , in advance !!!!!!!!!

ps: i have ubuntu 10.04 32bit server.

---

### Post by gabak on 2010-08-02
here i found something but it still does nt help me but i m closer

[http://beginlinux.com/blog/2009/01/citadel-groupware-install/comment-page-1/#comment-1737](http://beginlinux.com/blog/2009/01/citadel-groupware-install/comment-page-1/#comment-1737)

Base install of required programs.

sudo apt-get install clamav clamav-milter spamassassin citadel-suite amavisd-new

Install and Start Spamassassin

vim  /etc/default/spamassassin

# Change to one to enable spamd
ENABLED=1

sudo /etc/init.d/spamassassin start

Spamassassin is listening on port 783.
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN

Citadel Configuration

Make sure all of your processes are running.
ps -eaf | grep cit 
root      5167     1  0 13:47 ?        00:00:00 /usr/sbin/citserver -d -x3 -lmail -t/dev/null
citadel   5168  5167  0 13:47 ?        00:00:01 /usr/sbin/citserver -d -x3 -lmail -t/dev/null
root      6052     1  0 13:47 ?        00:00:00 /usr/sbin/webcit -D/var/run/webcit/webcit.pid.8504 -p8504 127.0.0.1 504 -i0.0.0.0 -f -t/var/log/webcit//access.8504.log
root      6053  6052  0 13:47 ?        00:00:06 /usr/sbin/webcit -D/var/run/webcit/webcit.pid.8504 -p8504 127.0.0.1 504 -i0.0.0.0 -f -t/var/log/webcit//access.8504.log

Check Network Ports
# netstat -lnp 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:5666            0.0.0.0:*               LISTEN      5979/nrpe
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:2020            0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:5222            0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN      8057/spamd.pid
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      6510/apache2
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      6039/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      5077/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5840/cupsd
tcp        0      0 0.0.0.0:8504            0.0.0.0:*               LISTEN      6053/webcit
tcp        0      0 0.0.0.0:504             0.0.0.0:*               LISTEN      5168/citserver
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      5168/citserver
tcp6       0      0 :::22                   :::*                    LISTEN      5077/sshd
udp        0      0 0.0.0.0:35499           0.0.0.0:*                           5053/avahi-daemon:
udp        0      0 0.0.0.0:68              0.0.0.0:*                           4444/dhclient3
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5053/avahi-daemon:

Once the server is installed, login to the web interface with your server IP Address

---

