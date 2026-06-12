---
title: "Networking before login"
date: 2009-12-28
forum: Server Platforms
---

### Post by Velbright on 2009-12-28
Hi,
I am trying to make a machine work via SSH from boot, and I need it to have networking and SSH working before login, I have disabled GDM so that I can run without a screen, How can I make it so that it connects to the network and starts SSH as soon as it boots without login, so that I can login via SSH, it is for a media-server machine,
Thanks :)

---

### Post by CharlesA on 2009-12-28
It should start sshd automatically on startup regardless if it has a gui or not.

Networking is the same way, it'll grab an address from DHCP (your router more then likely) and you can connect with SSH from that address.

---

### Post by slakkie on 2009-12-28
[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

One you have network, the sshd process should be able to accept incoming connections.

---

### Post by koenn on 2009-12-28
> **slakkie said:**
> [https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

One you have network, the sshd process should be able to accept incoming connections.

... if you have openssh-server installed

---

### Post by Velbright on 2009-12-28
> **CharlesA said:**
> It should start sshd automatically on startup regardless if it has a gui or not.

Networking is the same way, it'll grab an address from DHCP (your router more then likely) and you can connect with SSH from that address.

I always get an error saying No route to host, I believe this is because of the computer not connecting :S

---

### Post by Velbright on 2009-12-28
Oh. Didnt see other messages :)
Thanks.

---

### Post by Velbright on 2009-12-28
> **koenn said:**
> ... if you have openssh-server installed

What is the syntax for SSHD? presumably it needs running on boot?

---

### Post by doas777 on 2009-12-28
well, the tried and true method is to configure your /etc/network/interfaces file
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

or I'm told that if you config an connection in network manager, and you check teh box that says "Available to All Users", it will start your network earlier in the boot process and won't require a login prior to net connect.

---

### Post by Velbright on 2009-12-28
> **doas777 said:**
> well, the tried and true method is to configure your /etc/network/interfaces file
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

or I'm told that if you config an connection in network manager, and you check teh box that says "Available to All Users", it will start your network earlier in the boot process and won't require a login prior to net connect.

Will that work pre-login without GDM though?

---

### Post by doas777 on 2009-12-28
> **Velbright said:**
> Will that work pre-login without GDM though?

yes. the interfaces file config will work without X or gnome for that matter. 
not as sure about network-manager, but it should work as long as gdm is loaded. if you are ditching gdm, then the interfaces file is the best choice

---

### Post by CharlesA on 2009-12-28
> **Velbright said:**
> I always get an error saying No route to host, I believe this is because of the computer not connecting :S

[http://www.cyberciti.biz/tips/no-route-to-host-error-and-solution.html](http://www.cyberciti.biz/tips/no-route-to-host-error-and-solution.html)

> **Velbright said:**
> What is the syntax for SSHD? presumably it needs running on boot?

sshd is the daemon that listens for ssh connections. It should start automatically when the machine books, GUI or no GUI.

---

### Post by Velbright on 2009-12-28
> **doas777 said:**
> yes. the interfaces file config will work without X or gnome for that matter. 
not as sure about network-manager, but it should work as long as gdm is loaded. if you are ditching gdm, then the interfaces file is the best choice

So my config file should say what interface i am using (eth0 i think) and my IP, Subnet Mask, DNS etc?

---

### Post by doas777 on 2009-12-28
> **CharlesA said:**
> [http://www.cyberciti.biz/tips/no-route-to-host-error-and-solution.html](http://www.cyberciti.biz/tips/no-route-to-host-error-and-solution.html)



sshd is the daemon that listens for ssh connections. It should start automatically when the machine books, GUI or no GUI. that of course assumes that at least one nic is up at service load. otherwise you will find a service failure in dmesg.

---

### Post by doas777 on 2009-12-28
> **Velbright said:**
> So my config file should say what interface i am using (eth0 i think) and my IP, Subnet Mask, DNS etc?

yup

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.X
netmask 255.255.255.0
gateway 192.168.0.1 

```and for dns the /etc/resolv.conf is most standard. add lines like this:
```

nameserver 4.2.2.1
nameserver 4.2.2.2

```then when you are done, 
run
```
sudo /etc/init.d/networking restart
```

---

### Post by Velbright on 2009-12-28
sudo /etc/init.d/network restart didnt work. :S
Would a reboot do the job?

---

### Post by koenn on 2009-12-28
> **Velbright said:**
> So my config file should say what interface i am using (eth0 i think) and **my **IP, Subnet Mask, DNS etc?

the IP address, mask, ...,  for *that machine*, more accurately.

---

### Post by koenn on 2009-12-28
> **Velbright said:**
> sudo /etc/init.d/network restart didnt work. :S
Would a reboot do the job?

post the actual commands you run, and their actual output. 

saying "sudo /etc/init.d/network restart didnt work" is like calling a doctor, say "I'm ill" and expect him to come up with a cure instantly.

---

### Post by gradinaruvasile on 2009-12-28
> **Velbright said:**
> sudo /etc/init.d/network restart didnt work. :S
Would a reboot do the job?
The correct syntax is:

sudo service networking restart


And remove network-manager altogether, there is no need for it if you do not use wireless/mobile broadband.

---

### Post by doas777 on 2009-12-28
> **gradinaruvasile said:**
> The correct syntax is:

sudo service networking restart


And remove network-manager altogether, there is no need for it if you do not use wireless/mobile broadband.

thats the new way to do it. since we're still in transition, i'm sticking with the pre-karmic way, but either should still work. 

yes a reboot will suffice nicely.

---

### Post by doas777 on 2009-12-28
> **Velbright said:**
> sudo /etc/init.d/network restart didnt work. :S
Would a reboot do the job?

my bad. it should be 'networking'
```
sudo /etc/init.d/networking restart
```

sorry bout that

---

### Post by Velbright on 2009-12-28
What about Server Edition?
Do you know anything about that, I might use that, because the idea was a media and apache server...

I am guessing you could log in remotely on server? If you know please will you tell me 
Thanks :P

---

### Post by doas777 on 2009-12-28
well, your interfaces file is the same with either edition (and i would presume the only option on the server side, since the server doesn't come with a desktop environment like gnome), if that is what you are asking. 

there are numerous ways to remotely login to a server. what kind of tasks would you like to perform on it remotely?

---

### Post by Velbright on 2009-12-28
> **doas777 said:**
> well, your interfaces file is the same with either edition (and i would presume the only option on the server side, since the server doesn't come with a desktop environment like gnome), if that is what you are asking. 

there are numerous ways to remotely login to a server. what kind of tasks would you like to perform on it remotely?

UL & DL Files, Change FTP Stuff, But mainly SSH

---

### Post by doas777 on 2009-12-28
> **Velbright said:**
> UL & DL Files, Change FTP Stuff, But mainly SSH

for ssh, just install openssh-server and you should be good (edit sshd_config to set 'PermitRootLogin = no', and restart sshd).

the ul/dl can be done via scp, which is part of ssh. from windows connect with winscp, or from ubu, just open nautilus, and in the address bar, enter 'ssh://<serverName/IP>'.

many people swear by a managment frontend called webmin. never tried it myself, but you'll find many people who can help out with it.

---

