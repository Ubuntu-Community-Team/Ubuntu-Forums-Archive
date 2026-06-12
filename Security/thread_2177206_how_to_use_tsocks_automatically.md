---
title: "how to use tsocks automatically?"
date: 2013-09-27
forum: Security
---

### Post by joan_carles2 on 2013-09-27
I'm using a proxy socks through and SSH tunel.

Each time that I want to launch a software i must use the terminal adn type tsocks and then the name of what I want to launch. For example:

tsocks firefox

I just want to avoid that. So I introduced next code to teh archive .bashrc:

. tsocks -on

And now each time that I launch a software from the terminal i just don't need to write tsocks.

My problem is what I should do to run tsocks automatically launching an application from the menu. The idea is to don't the terminal to launch applications.

I've tried to intoduce . tsocks -on on the file .profile but doesn't work. How I could do it?

---

### Post by unspawn on 2013-09-27
Could try
```
echo /usr/lib/libtsocks.so >> /etc/ld.so.preload
```
but do see the caveats in 'man tsocks'.

---

### Post by joan_carles2 on 2013-09-28
what you propose works but cause me some problems. Problems that I have are next:

1- first you stablish the tunel and then in root mode you use the command that you proposed
echo /usr/lib/libtsocks.so >> /etc/ld.so.preload

Then all the program that you run are under the local proxy socks.

2- I restart the computer and when I restart the computer none of the of the programs works because the ssh tunel is not opened. When I try to stablish the tunel is completely imposible becasue I have next error:

19:18:19 libtsocks(3359): Error 111 attempting to connect to SOCKS server (Connection refused)
ssh: connect to host 32.32.32.32 port 22: Connection refused

I tried to stablish the tunel with my user and also with the root user. But the problem is not solved

3- Then to make it work again I must edit the archivo /etc/ld.so.preload and delete the line 
/usr/lib/libtsocks.so

4- Once this line is deleted then I stablish the tunel without any problem. Once the tunel is stablished then I have to introduce again 
echo /usr/lib/libtsocks.so >> /etc/ld.so.preload

Then all the program that you run are under the local proxy socks.

How can I avoid this complicated process?

---

### Post by unspawn on 2013-09-28
The problem here is the order of things and the tunnel requirement. Setting up a SSH tunnel requires pubkey auth (not good if it wouldn't), meaning ssh-agent should be running beforehand, meaning the user should be logged in beforehand, and all should be done before the environment enforces LD_SO_PRELOAD. So, as it is set system-wide, using /etc/ld.so.preload appears not be the option for you. Similarly, since the user is already logged in, it's too late to source /etc/profile.d/ scripts to LD_SO_PRELOAD something. One option, without giving thought to feasibility or practicality right now, could be to first enforce a firewall block for the user requiring SOCKS connections, then start SSH tunnel as a different user (also see *autossh* for keeping connections alive), then log in with the user requiring SOCKS connections (at this point a /etc/profile.d/ script should be sourced that sets LD_SO_PRELOAD), then remove the firewall block.

---

### Post by joan_carles2 on 2013-09-29
thks for your explanation. Finally I decided to give up tsocks. Finally I will use redsocks. I've tested and works fine. I observed that tsocks doesn't work with some software like chrome. With redsocks all the traffic goes to the tunnel easily

---

