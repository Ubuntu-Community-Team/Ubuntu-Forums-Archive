---
title: "iptables // xtables-addons // geoip issues"
date: 2012-04-03
forum: Server Platforms
---

### Post by geudrik on 2012-04-03
Hello all!

I've installed xtables-addons-* on my server 11.10 installation, but when I try to use the geoip module (everything else works fine) I get the following error...
```

$ sudo iptables -I INPUT -m geoip --src-cc CN -j DROP
Could not open /usr/share/xt_geoip/LE/CN.iv4: No such file or directory
iptables v1.4.10: Could not read geoip database

```

Any idea why?  I've looked for the file xt_geoip_dl but am unable to find it.. thoughts?  I would really like to get xtables working properly with geoip...

---

### Post by geudrik on 2012-04-04
Here's the solution...
```

sudo find / -name 'xt_geoip_dl' -print
cd into the directory
run xt_geoip_dl (youll need the "unzip" program
sudo ./xt_geoip_build -D /usr/share/xt_geoip *.csv     where /usr/share/xt_geoip is where iptables looks for the LE directory full of country codes

```

---

