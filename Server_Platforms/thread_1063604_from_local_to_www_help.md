---
title: "from local to www help"
date: 2009-02-08
forum: Server Platforms
---

### Post by userkiller on 2009-02-08
Hi i been using ubuntu for 2 days ;)
i manage to install it and set up some require softwares i install phpbb and it working. Now how can i turn it from local to www that every one can acess it am i have a domain name from godaddy.:p


Help if you want to be help:D

---

### Post by skunkbad on 2009-02-08
You need to point the nameservers of your domain to your server. You can do this in the domain control panel. Then you need to enable port forwarding of port 80 on your router. Direct this port to your server's LAN IP. I think that's it, but if I'm wrong, I know somebody else will help.

---

### Post by hyper_ch on 2009-02-08
as the previous poster said, you need to set nameserver. I don't know if godaddy offers customized nameserver entries. Do you have a static or dynamic ip? If you have a dynamic IP you need a tool that updates the ip with the nameserver.

I have good experience pointing to domain to the [http://www.everydns.com/](http://www.everydns.com/) nameservers and use their perl script to update the info.

Once, you got that, you need to forward port 80 from the router to your server's IP. The server should have a static IP in the lan.

Furthermore if you want to enable some email features with phpBB then I think you'd also need to setup a proper smtp server for it.

---

### Post by userkiller on 2009-02-08
> **hyper_ch said:**
> as the previous poster said, you need to set nameserver. I don't know if godaddy offers customized nameserver entries. Do you have a static or dynamic ip? If you have a dynamic IP you need a tool that updates the ip with the nameserver.

I have good experience pointing to domain to the [http://www.everydns.com/](http://www.everydns.com/) nameservers and use their perl script to update the info.

Once, you got that, you need to forward port 80 from the router to your server's IP. The server should have a static IP in the lan.

Furthermore if you want to enable some email features with phpBB then I think you'd also need to setup a proper smtp server for it.


yes i do have static ip

---

### Post by hyper_ch on 2009-02-08
then make at the registrar nameserver entries that point to your static IP :)

---

