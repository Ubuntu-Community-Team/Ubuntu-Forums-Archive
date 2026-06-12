---
title: "Denyhosts blocking a phantom host"
date: 2010-06-16
forum: Security
---

### Post by ccaaee on 2010-06-16
Hello

I have a host with the address 192.168.1.11 which is continually denied from a server on my lan running the denyhosts deamon. This is a cause for some concern (is someone spoofing??). So I go to this server remove "sshd: 192.168.1.11" from /etc/hosts.deny and then run:
tcpdump host 192.168.1.11
and
tail -f /var/log/denyhosts
in two different terminals. Sure enough, after a few minutes /var/log/denyhosts reports the blocking of this host BUT, according to tcpdump, nothing has happened on the lan during this time. Anyone got any ideas???

Thanks, ccaaee

---

### Post by dino99 on 2010-06-16
[https://bugs.launchpad.net/ubuntu/+source/denyhosts/+bug/564476](https://bugs.launchpad.net/ubuntu/+source/denyhosts/+bug/564476)

you can use ipblock for more security

---

### Post by bodhi.zazen on 2010-06-16
> **ccaaee said:**
> Hello

I have a host with the address 192.168.1.11 which is continually denied from a server on my lan running the denyhosts deamon. This is a cause for some concern (is someone spoofing??). So I go to this server remove "sshd: 192.168.1.11" from /etc/hosts.deny and then run:
tcpdump host 192.168.1.11
and
tail -f /var/log/denyhosts
in two different terminals. Sure enough, after a few minutes /var/log/denyhosts reports the blocking of this host BUT, according to tcpdump, nothing has happened on the lan during this time. Anyone got any ideas???

Thanks, ccaaee

I think this link will clarify things for you ;

[http://www.cyberciti.biz/faq/linux-unix-delete-remove-ip-address-that-denyhosts-blocked/](http://www.cyberciti.biz/faq/linux-unix-delete-remove-ip-address-that-denyhosts-blocked/)

See also ;

[http://denyhosts.sourceforge.net/faq.html#3_19](http://denyhosts.sourceforge.net/faq.html#3_19)

---

### Post by ccaaee on 2010-06-21
Thanks a 10^6 folks, it worked

---

