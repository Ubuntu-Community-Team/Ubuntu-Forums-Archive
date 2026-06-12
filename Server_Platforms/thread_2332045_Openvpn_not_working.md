---
title: "Openvpn not working"
date: 2016-07-27
forum: Server Platforms
---

### Post by wildmanne39 on 2016-07-27
Openvpn will not connect, I can not configure it with network manager it will not use vpn connection will not stay checked.

---

### Post by CharlesA on 2016-07-27
Thanks Wild_Man. This will probably help.
[http://askubuntu.com/questions/450493/openvpn-cant-import-configurations-on-new-14-04-installation](http://askubuntu.com/questions/450493/openvpn-cant-import-configurations-on-new-14-04-installation)

Stupid Network-manager. :(

---

### Post by wildmanne39 on 2016-07-29
Thank you charlesA!:)

---

### Post by wildmanne39 on 2016-07-29
Openvpn now connects for about 5 minutes and works then fails on ubuntu 16.04 does anyone have any idea why?
Thanks

---

### Post by darkod on 2016-07-29
Are you configuring the server or the client end? Or both?

And why the GUI (Network Manager), are you so dependent on it? I have always used terminal and text files even on Ubuntu Desktop (which has GUI of course).

OpenVPN is fairly easy to set up, so you are probably making a mistake somewhere... Maybe it's NM fault...

PS. You might already know this, but: [https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

---

### Post by wildmanne39 on 2016-07-29
Thanks darkod! I will take a look at that link.

I was given a script to set openvpn up and there is a bug concerning 16.04 that makes it harder but I used network manager because it was suggested and yes I can use the terminal I do most of the time but I was in a hurry. 

I may have to purge everything and do it manually.

The server was setup by the company that owns it I just had to change a couple of settings.
I appreciate all the help I can get.

---

### Post by CharlesA on 2016-07-30
Found the problem. Apparently Ubuntu was being stupid with systemd...
[http://askubuntu.com/questions/747023/systemd-fails-to-start-openvpn-in-lxd-managed-16-04-container](http://askubuntu.com/questions/747023/systemd-fails-to-start-openvpn-in-lxd-managed-16-04-container)

So, it would try to start and failed. Commenting out the property in that AU link allowed openvpn to start.

---

### Post by darkod on 2016-07-30
I recently had to set up test openvpn server with the new 16.04 and didn't notice any difference except for this: The first time you try to start the service and test if it worked instead of 'sudo service openvpn start' now in 16.04 you need to use the name of the conf file you put in /etc/openvpn too (without the extension). For example, if you decided to use server.conf for the conf file, you manually start the service with 'sudo service openvpn-server start'.

But that is for the first time manually only. On reboot it starts automatically and I didn't notice any difference with earlier versions of ubuntu. So I think this is more of an issue when creating it with GUI, then an issue because of 16.04. It might be combination of both, but again, because of using the GUI...

---

