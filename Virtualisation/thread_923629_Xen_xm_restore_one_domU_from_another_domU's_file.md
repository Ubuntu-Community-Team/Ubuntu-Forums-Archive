---
title: "Xen xm restore one domU from another domU's file?"
date: 2008-09-18
forum: Virtualisation
---

### Post by JamesGist on 2008-09-18
I have 3 virtual machines with the same setup.

Is this possible

xm save dom1
xm shutdown all three domains
xm restore all three domains from dom1's file?

---

### Post by andysmith3 on 2008-09-18
helloreplica.com  provides a wide array of [Replica Watches](http://www.helloreplica.com/) and professional customer sevrice, our goal is to make every customer 100% satsfied. We are more than ready to show our unique prowess and fortes to gain our footing. And we also provide fast delivery service, we guarantee our listing price is lower than other competitor. welcome to oursite  [Replica Rolex Watches](http://www.helloreplica.com/)  [Rolex Watches](http://www.rolex2u.com/)   [replica rolex watches](http://www.rolex2u.com/) [replica rolex](http://www.rolex2u.com/)

---

### Post by JinxAu on 2008-09-19
Not sure about the "xm save" method, but if your domUs are running from loopback images, you should just be able to over-write the current ones with your dom1 image.

For example, one of my domU disk config looks like this:
```

disk = ['file:/srv/xen/guest1/guest1-xen.ext3,sda1,w',
         'file:/srv/xen/guest1/guest1-xen.swp,sda2,w']

```

So, if I wanted to make a new DomU based on the above guest, I just:
- shutdown guest1
- copy the /srv/xen/guest1 directory to /srv/xen/guest2
- rename the two loopback images to guest2 and create another config file based on the guest1 config.
- Start the new guest2 DomU

Your configuration may be different, as I know some Xen setups utilise a database based configuration (so no /etc/xen config files). Found this in Fedora, as it seems to be utilising the configuration that XenSource uses.

Cya round
Jinx

---

