---
title: "Rsyslog cannot log to file"
date: 2013-06-05
forum: Server Platforms
---

### Post by termvrl on 2013-06-05
Hi All,
I have setup rsyslog to collect log from deivces such router, fwall.
I use syslog udp 514.

On my rsyslog.conf

# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514

On my 50-default.conf

# This one is the template to generate the log filename dynamically, depending on the client's IP address.
$template FILENAME,"/var/log/%fromhost-ip%/syslog.log"

# Log all messages to the dynamically formed file. Now each clients log (192.168.1.2, 192.168.1.3,etc...), will be under a separate directory which is formed by the template FILENAME.
*.* ?FILENAME

And I received this error:-

Jun  5 08:07:57 ubuntu rsyslogd-3000: Could not open dynamic file '/var/log/192.168.0.111/syslog.log' [state -3000] - discarding message [try [http://www.rsyslog.com/e/3000](http://www.rsyslog.com/e/3000) ]


Any idea?

Thanks.

---

### Post by slickymaster on 2013-06-05
That's probably due to permissions. You just have to edit your **/etc/rsyslog.conf** file and everything should work as you expect.
Open a terminal and run:```
gksu geany /etc/rsyslog.conf
```then edit the line:```
$PrivDropToGroup syslog
``` to ```
$PrivDropToGroup adm
```This simply changes the privileges to all users within the group adm.

---

### Post by termvrl on 2013-06-05
Hi slickymaster,

After i edit the conf file:-[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1753126")

$PrivDropToUser adm
$PrivDropToGroup adm

its work.

Thank you!

---

### Post by slickymaster on 2013-06-05
Glad you got it working.
Don't forget to mark the thread as SOLVED. See the link on my signature if you don't know how to do it.

---

