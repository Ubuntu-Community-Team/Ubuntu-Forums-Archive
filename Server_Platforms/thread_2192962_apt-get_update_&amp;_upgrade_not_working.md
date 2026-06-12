---
title: "apt-get update &amp; upgrade not working"
date: 2013-12-10
forum: Server Platforms
---

### Post by adam17 on 2013-12-10
Hi,

I recently installed a Ubuntu Server 12.04LTS and have been having fun setting it up. 

However on boot the system mentioned that it needed some updates and I was prompted to type. "sudo apt-get update" and "sudo apt-get upgrade" this all worked and all was fine it said all was completed.

But now when I try and use the "sudo apt-get install minidlna"command for example I get:

"Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/minidlna/minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/minidlna/minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb)  Temporary failure resolving ‘gb.archive.ubuntu.com’
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

I have read online that this can be to do with ISP however all worked fine until the "sudo apt-get upgrade" 

Does anyone know how to fix this? Can I downgrade the apt-get function back to what it was on the original install?

Regards.

Adam

---

### Post by wlraider70 on 2013-12-10
Sounds like a DNS problem. Check your /etc/resolv.conf file.
Can you ping 8.8.8.8 ?

---

### Post by adam17 on 2013-12-10
Hi,

Yeah i can ping 8.8.8.8

Adam

---

### Post by sandyd on 2013-12-11
> **adam17 said:**
> Hi,

Yeah i can ping 8.8.8.8

Adam

Can you post the output of
```

cat /etc/resolv.conf
```
Depending on your config, there are two things it can show.

Either, it will say it is managed by resolvconf, .etc .etc

In that case, add the line
```

dns-nameservers 8.8.8.8 8.8.4.4
``` to your main network interface in /etc/network/interfaces


If you are using DHCP and the file does have nameservers, but are incorrect, then this is a issue you should take up with the DHCP server that serves your network :)

Otherwise, if the file is blank, or has the wrong nameservers and you are using static interfaces, run
```

echo "nameserver 8.8.8.8" > /etc/resolv.conf
echo "nameserver 8.8.4.4" >> /etc/resolv.conf
```

---

### Post by muttsnutman on 2013-12-20
> **sandyd said:**
> Can you post the output of
```

cat /etc/resolv.conf
```
Depending on your config, there are two things it can show.

Either, it will say it is managed by resolvconf, .etc .etc

In that case, add the line
```

dns-nameservers 8.8.8.8 8.8.4.4
``` to your main network interface in /etc/network/interfaces


If you are using DHCP and the file does have nameservers, but are incorrect, then this is a issue you should take up with the DHCP server that serves your network :)

Otherwise, if the file is blank, or has the wrong nameservers and you are using static interfaces, run
```

echo "nameserver 8.8.8.8" > /etc/resolv.conf
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
```

Probably should be :

echo "nameserver 8.8.8.8" > /etc/resolv.conf
echo "nameserver 8.8.4.4" >> /etc/resolv.conf

to concatenate the second nameserver line... there is no point in entering the same nameserver address twice.

NickB

---

