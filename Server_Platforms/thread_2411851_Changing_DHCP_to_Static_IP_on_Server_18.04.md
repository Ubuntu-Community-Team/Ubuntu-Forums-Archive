---
title: "Changing DHCP to Static IP on Server 18.04"
date: 2019-02-04
forum: Server Platforms
---

### Post by jbesedic on 2019-02-04
I am having a heck of a time trying to get the server to accept a static ip address.  I have read a bunch of forums and watch Youtube videos and I am still getting error on getting the server to have a static ip.

This is what the server has now.
[IMG]http://www.beachtourism.com/ubuntu/capture.JPG[/IMG]

I did create a file 99-disable-network-config.cfg  and placed it in the correct directory.  I did use nano to modify the file 

[IMG]http://www.beachtourism.com/ubuntu/capture3.JPG[/IMG]

I then renamed the 50-cloud-init.yaml  to 50-cloud-init.yamlbk

Now I created a new yaml file called 01-netcfg.yaml and typed in the following

[IMG]http://www.beachtourism.com/ubuntu/capture1.JPG[/IMG]

After creating the file and and typing in   netplan apply    I get the following error.

[IMG]http://www.beachtourism.com/ubuntu/capture2.JPG[/IMG]

Can someone help me out to get this fixed so that I can use this awesome server.

---

### Post by barroncm on 2019-02-04
Just edit the current config similar to this:
```

# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp3s0:
            addresses: ['10.10.2.100/16']
            gateway4: 10.10.2.1
            nameservers:
                addresses: [8.8.8.8,8.8.4.4]
    version: 2
~
~

```
Netplan requires the tab spacing
see the following for more info:
[https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux)

---

### Post by barroncm on 2019-02-04
Looks like the forum kills the tab spacing, the link I added is what I used to get mine configured
also get rid of [COLOR=#000000] /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg
[/COLOR]Just edit the existing file.[COLOR=#000000][/COLOR]

---

### Post by Irihapeti on 2019-02-04
> **barroncm said:**
> Looks like the forum kills the tab spacing, ...

Place any text of that nature between code tags, or select the text and click on the # icon, and it will preserve the spacing.

---

