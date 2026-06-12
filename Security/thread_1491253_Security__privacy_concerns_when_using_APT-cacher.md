---
title: "Security / privacy concerns when using APT-cacher"
date: 2010-05-23
forum: Security
---

### Post by mahela007 on 2010-05-23
I have two Ubuntu PCs at home and I found out about apt-cacher as a means of reducing internet usage for updates. (my connection speeds aren't that good).
When I install apt-cacher, is it possible for anyone on the internet to use my PC as a repository? If so, how can I allow only computers on my LAN to access the apt-cacher cache? Thanks

---

### Post by bodhi.zazen on 2010-05-23
> **mahela007 said:**
> I have two Ubuntu PCs at home and I found out about apt-cacher as a means of reducing internet usage for updates. (my connection speeds aren't that good).
When I install apt-cacher, is it possible for anyone on the internet to use my PC as a repository? If so, how can I allow only computers on my LAN to access the apt-cacher cache? Thanks

Do you have a router ? Are you using the built in firewall ? Have you forwarded ports ?

If you have not forwarded ports then no, one should not be able to connect to your computer from the internet.

If, however, you have no router/firewall, use iptables or ufw to limit connections to your server to your other computer.

sudo ufw allow from clinet_ip to server_ip port to 3142
sudo ufw deny port 3142

Just plug in your server and client IP , and change port 80 to the port you are using (I assume port 3142, it is the default, but I am not sure).

You can also set your "allowed hosts" in /etc/apt-cacher/apt-cacher.conf 

[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

---

### Post by mahela007 on 2010-05-24
I do use a router but I have forwarded the port used for SSH. I'm afraid I didn't understand how to use the commands you posted. The Ubuntu wiki link didn't look very reliable. It's full of stuff not working well and 'looks like' statements. I'll try the other link you posted.

---

### Post by bodhi.zazen on 2010-05-24
> **mahela007 said:**
> I do use a router but I have forwarded the port used for SSH. I'm afraid I didn't understand how to use the commands you posted. The Ubuntu wiki link didn't look very reliable. It's full of stuff not working well and 'looks like' statements. I'll try the other link you posted.

See:     

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by mahela007 on 2010-06-11
Sorry I took so long to reply... So, do I only have to set up firewall rules to ensure an acceptable level of security?

---

### Post by bodhi.zazen on 2010-06-11
> **mahela007 said:**
> Sorry I took so long to reply... So, do I only have to set up firewall rules to ensure an acceptable level of security?

Do you have a router ? Does your router have a firewall ?

If so, then you are fine. Just do not forward ports to your apt-cache server.

If not, then yes you need to configure a firewall on your apt-cache server to allow connections only from your LAN.

---

### Post by mahela007 on 2010-06-12
So just to confirm, I do have a router.. but I don't think it has a firewall and I haven't forwarded ports. Therefore, I am safe.. and do not need to configure the Ubuntu firewall.;-) (right?)
As for the SSH port, (see post #3) I'm using key based logins so that should be safe.

---

### Post by bodhi.zazen on 2010-06-13
> **mahela007 said:**
> So just to confirm, I do have a router.. but I don't think it has a firewall and I haven't forwarded ports. Therefore, I am safe.. and do not need to configure the Ubuntu firewall.;-) (right?)
As for the SSH port, (see post #3) I'm using key based logins so that should be safe.

Most routers also serve as a firewall, and if you have to forward port 22 then yes you should be fine with that.

My understanding from your post is that the only port you have forwarded is for ssh, 22 by default ?

If you are forwarding port 22 , use keys (so far so good). I also suggest you disable password logins. In addition I suggest you consider using a service such as denyhosts or fail2ban or you configure iptables to block brute force attempts to crack your ssh server.

---

### Post by mahela007 on 2010-06-13
Yes.. I've forwarded only the default ssh port and like you've recommended, I've disabled key based logins. (I believe I followed you advice on another thread.. ;-) )

---

### Post by bodhi.zazen on 2010-06-13
> **mahela007 said:**
> Yes.. I've forwarded only the default ssh port and like you've recommended, I've disabled key based logins. (I believe I followed you advice on another thread.. ;-) )

You should be good to go with that basic set up. If you have the time and interest you can look at iptables or denyhosts/fail2ban, but with keys only I am not sure those additional steps add much.

---

### Post by mahela007 on 2010-06-17
thanks a lot!

---

