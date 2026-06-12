---
title: "LTSP Local Apps Name Resolution"
date: 2009-07-21
forum: Server Platforms
---

### Post by cuschu on 2009-07-21
I have got an Ubuntu 9.04 LTSP server up and going, however I have run into one problem that I can't seem to fix. I need firefox and the flash plugin to run as a local app, since this lab will be used mostly for web search, which includes alot of youtube and the like. I got Firefox to launch locally, but I can not get it to use dns. I can get around the Internet browsing by IP, which tells me that the NAT and masquerading are working. If I open the version of Firefox (on the clients) that is run off of the server I can get anywhere on the Internet using DNS just fine. I have trien numerous solutions that I could find by Googling, but I haven't come up with one that fixes this particular problem. When I launch xterm as a local app here is some of the network information I get...

cat /etc/resolv.conf
cat: /etc/resolv.conf: Permission denied

route -n
bash: route: command not found

I tried a couple of ideas on how to change the permissions of the resolv.conf, but I can't get it to really change the permissions (or hold the change, whichever one)

Any ideas?

Thanks,
Curtis

---

