---
title: "no internet at boot"
date: 2010-06-01
forum: Server Platforms
---

### Post by spencerocks on 2010-06-01
I am running 10.4 and my eth0 used to be working perfectly. Last night i turned off the server. Today when samba and stuff wasn't working I found out that eth0 was not 'running'. The only way i can get internet working is "sudo dhclient eth0". Then it works but until reboot.
Thanks in advance.

---

### Post by arrrghhh on 2010-06-01
So does that mean your server is running on DHCP instead of a static IP?

I would recommend static, just because you don't want your server's IP changing.  It's not required tho, so let's work on the issue.

Can you post your /etc/networking/interfaces file?  Perhaps the entry for eth0 is missing or mangled.

---

### Post by spencerocks on 2010-06-01
See the weird thing is that i am using static

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address: 192.168.2.102
netmask: 255.255.255.0
gateway: 192.168.3.1

```

Thanks

---

### Post by arrrghhh on 2010-06-01
Well, I'm not sure how picky it is for syntax... but...

```
auto lo eth0
iface lo inet loopback

iface eth0 inet static
        address 192.168.0.99
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1
```

So try adding those fields that are missing, plus get rid of the colon's.  Restart the machine, or just restart networking and see what happens.  Also, if you're static why are you using 'sudo dhclient eth0'?  You should just do an ifup/down...

---

### Post by spencerocks on 2010-06-01
I fixed the syntax and stuff but Whenever i try and do a restart on the eth0 i get 'SIOCADDRT: No such process'

---

### Post by arrrghhh on 2010-06-01
> **spencerocks said:**
> I fixed the syntax and stuff but Whenever i try and do a restart on the eth0 i get 'SIOCADDRT: No such process'

How are you restarting eth0?  Can you reboot the machine?

---

### Post by spencerocks on 2010-06-01
i tried ```
sudo /etc/init.d/networking restart
``` and yes i am able to restart the machine and i did that too

---

### Post by spencerocks on 2010-06-01
Well i got it!
my ip address was 192.168.2.102 when it should of been 192.168.3.102

Thanks for all your help!

---

### Post by arrrghhh on 2010-06-01
> **spencerocks said:**
> Well i got it!
my ip address was 192.168.2.102 when it should of been 192.168.3.102

Thanks for all your help!

LOL glad you got it sorted.  Please MARK this thread as [SOLVED] by using the thread tools drop down!

---

### Post by xifer on 2010-06-02
that raises an interesting question.

static or dynamic IP for servers?

in the past i've also mostly avoided dhcp on servers - but is that a good thing really?

---

### Post by arrrghhh on 2010-06-02
> **xifer said:**
> that raises an interesting question.

static or dynamic IP for servers?

in the past i've also mostly avoided dhcp on servers - but is that a good thing really?

Well if you use DNS or avahi, then I guess DHCP would be fine.  I'd rather configure it static, because I know it's not going to change.

---

