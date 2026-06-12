---
title: "/run/resolvconf/interface/eth0.*"
date: 2013-09-15
forum: Ubuntu Development Version
---

### Post by zika on 2013-09-15
Which files are &#8222;responsible&#8220; for generating following files:
/run/resolvconf/interface/eth0.dhclient
/run/resolvconf/interface/eth0.inet
...?
I have some relict dns-namesrvers which propagate into this files even though I've cleaned all the places I could think of...
Yes, I've made /etc/resolv.conf, for makeshift sake, static, not a symlink, in order to curcumvent this trouble, but I would like to learn how to remove these relicts from my machine...
Thank You in advance for any hint...

Update&#8321;: Simply erasure of files mentioned above through proper instutions of system (via resolvconf and couple of tweks in the meantime) did not propagate before/after reboot... Still having &#8222;static&#8220; resolv.conf, chasing atavisms that could come, even, from IP... We will see...

Update&#8322;: Now it is solved... Two solutions:
1. Proper configuring of dnsmasq (turn off uso of resolvconf in dnsmasq and put wanted nemservers directly in dnsmasq. I've been using this befor lar install and I can not remember why I gave it up to use resolvsonf...)...

and/or

2. ```
echo "manual" | sudo tee /etc/init/resolv.override
```

Update&#8323;: There is a third solution that I like most... Prevent only refresh of /etc/resolv.conf... My question about atavisms still stand but it will wait for better tims... Ergo:```
:~$ cat /etc/dhcp3/dhclient-enter-hooks.d/nodnsupdate 
#!/bin/sh
make_resolv_conf(){
    :
}
```[http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks/](http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks/)

---

