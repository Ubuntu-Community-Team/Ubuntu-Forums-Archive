---
title: "deny hosts removing an Ip and checking tcpwrappers"
date: 2010-10-21
forum: Security
---

### Post by tapas_mishra on 2010-10-21
Hi,
I could not find any where the documentation the only best which I got was
[https://help.ubuntu.com/community/InstallingSecurityTools](https://help.ubuntu.com/community/InstallingSecurityTools)

My question is the following blog says to remove an IP from
/etc/hosts.deny which denyhost has blocked

[http://www.cyberciti.biz/faq/linux-unix-delete-remove-ip-address-that-denyhosts-blocked/](http://www.cyberciti.biz/faq/linux-unix-delete-remove-ip-address-that-denyhosts-blocked/)
you need to have a directory /usr/share/denyhosts/data
I do not find any such directory

Also when I tried to check  tcp wrapper configuration
as given here

[http://www.cyberciti.biz/faq/block-ssh-attacks-with-denyhosts/](http://www.cyberciti.biz/faq/block-ssh-attacks-with-denyhosts/)

tcpdchk -v
Cannot find your inetd.conf or tlid.conf file.
Please specify its location.

what does the above output mean?
How do I make sure denyhosts is doing its job?

---

### Post by FuturePilot on 2010-10-21
Follow this [http://denyhosts.sourceforge.net/faq.html#3_19]("http://denyhosts.sourceforge.net/faq.html#3_19")

WORK_DIR refers to /var/lib/denyhosts

---

### Post by tapas_mishra on 2010-10-22
Ok I did 
```

ps -el | grep `cat /var/run/denyhosts.pid`

```got some output seems 
```

5 S     0 24735     1  0  80   0 - 11550 poll_s ?        00:00:00 python 
```it is working with name python 
also I see the IPs logged in WORK_DIR/hosts file.
Did
>  sudo apt-get install xinetd then > tcpdchk -v  since
tcp_wrappers use two files
/etc/hosts.allow # for allow allow
/etc/hosts.deny # for deny host
```

aptitude install xinetd
Log started: 2010-10-22  16:58:28
Selecting previously deselected package xinetd.^M
(Reading database ... ^M(Reading database ... 5%^M(Reading database ...  10%^M(Reading database ... 15%^M(Reading database ... 20%^M(Reading  database ... 25%^M(Reading database ... 30%^M(Reading database ...  35%^M(Reading database ... 40%^M(Reading database ... 45%^M(Reading  database ... 50%^M(Reading database ... 55%^M(Reading database ...  60%^M(Reading database ... 65%^M(Reading database ... 70%^M(Reading  database ... 75%^M(Reading database ... 80%^M(Reading database ...  85%^M(Reading database ... 90%^M(Reading database ... 95%^M(Reading  database ... 100%^M(Reading database ... 165452 files and directories  currently installed.)^M
Unpacking xinetd (from .../xinetd_1%3a2.3.14-7ubuntu3_amd64.deb) ...^M
Processing triggers for ureadahead ...^M
ureadahead will be reprofiled on next reboot^M
Processing triggers for man-db ...^M
Setting up xinetd (1:2.3.14-7ubuntu3) ...^M
 * Stopping internet superserver xinetd       ^[[167G ^M^[[161G[ OK ]^M
 * Starting internet superserver xinetd       ^[[167G ^M^[[161G[ OK ]^M

```again
> tcpdchk -v Cannot find your inetd.conf or tlid.conf file. Please specify its location.Created inetd.conf file manually and then 
>  # touch /etc/inetd.conf # tcpdchk -vgives me 
```

tcpdchk -v
```Using network configuration file: /etc/inetd.conf                      
But tcpwrappers thing I am not getting what do I need to be able to make sure tcpwrappers are enabled.

---

