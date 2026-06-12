---
title: "best firewall"
date: 2011-04-28
forum: Security
---

### Post by cakka on 2011-04-28
hello,

ubuntu is new for me
i want to install a firewall for my ubuntu server (vps)
what the best firewall for ubuntu ?
my ram is 512 mb
how to install firewall from console ?

thanks

---

### Post by Jive Turkey on 2011-04-28
iptables is built in to the kernel and will have the smallest footprint on the VPS.  Some VPS vendors offer the ability to wipe the rules on your VPS if you lock yourself out (via web interface).  All of the other firewall options I know of are only front ends for iptables.  ufw might already be installed however it only offers some of the simpler features of iptables.  I use shorewall, it offers more of the features of iptables and has some great documentation on the shorewall project website.  Unless you're trying to do something really tricky, ufw should have you covered.

---

### Post by Rubi1200 on 2011-04-28
Here are some links to get you started:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall)
[http://www.shorewall.net/](http://www.shorewall.net/)

---

### Post by cakka on 2011-04-28
> **Jive Turkey said:**
> iptables is built in to the kernel and will have the smallest footprint on the VPS.  Some VPS vendors offer the ability to wipe the rules on your VPS if you lock yourself out (via web interface).  All of the other firewall options I know of are only front ends for iptables.  ufw might already be installed however it only offers some of the simpler features of iptables.  I use shorewall, it offers more of the features of iptables and has some great documentation on the shorewall project website.  Unless you're trying to do something really tricky, ufw should have you covered.

> **Rubi1200 said:**
> Here are some links to get you started:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall)
[http://www.shorewall.net/](http://www.shorewall.net/)


i will check it 
thanks

---

### Post by sj1410 on 2011-04-28
[http://www.pisces.net.in/p/effortless-linux-based-firewall.html](http://www.pisces.net.in/p/effortless-linux-based-firewall.html)

---

### Post by nec207 on 2011-04-28
>  
iptables is built in to the kernel and will have the smallest footprint on the VPS. Some VPS vendors offer the ability to wipe the rules on your VPS if you lock yourself out (via web interface). All of the other firewall options I know of are only front ends for iptables. ufw might already be installed however it only offers some of the simpler features of iptables. I use shorewall, it offers more of the features of iptables and has some great documentation on the shorewall project website. Unless you're trying to do something really tricky, ufw should have you covered. 

I think he is looking for a firewall that will close any open ports and monitor port scanning .

---

### Post by bodhi.zazen on 2011-04-28
On a VPS I would use iptables + psad + fwsnort

---

### Post by cakka on 2011-05-01
> **nec207 said:**
> I think he is looking for a firewall that will close any open ports and monitor port scanning .

yes, right...
ubuntu is new for me
i am confuse how to setting up security on ubuntu

i must learn from zero :confused:

---

### Post by Pluxii on 2011-05-02
I have personally used [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter) and have been pleased with it. 
It's worth a look at at least, good easy to use GUI.

---

### Post by bodhi.zazen on 2011-05-02
> **Pluxii said:**
> I have personally used [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter) and have been pleased with it. 
It's worth a look at at least, good easy to use GUI.

By default Ubuntu uses ufw.

To enable it, use

```
sudo ufw enable
```

If you want a graphical interface, use gufw.

Firestarter is "OK", but it is no longer maintained and ifyou have a problem with it, unless you patch the code, no fix.

---

### Post by Pluxii on 2011-05-02
> **bodhi.zazen said:**
> By default Ubuntu uses ufw.
 
To enable it, use
 
```
sudo ufw enable
```
 
If you want a graphical interface, use gufw.
 
Firestarter is "OK", but it is no longer maintained and ifyou have a problem with it, unless you patch the code, no fix.
 
Hmm I was completely unaware that it was no longer maintained, thanks for telling me. Seems it's time for me to move on to other options as well.
 
After really taking some time to read that security sticky that really answers all my firewall concerns as well. OP if you haven't yet I really suggest you read that sticky, great info there.

---

### Post by cakka on 2011-05-02
> **Pluxii said:**
> I have personally used [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter) and have been pleased with it. 
It's worth a look at at least, good easy to use GUI.

> **bodhi.zazen said:**
> By default Ubuntu uses ufw.

To enable it, use

```
sudo ufw enable
```If you want a graphical interface, use gufw.

Firestarter is "OK", but it is no longer maintained and ifyou have a problem with it, unless you patch the code, no fix.

thank you for the information

can you give me a link, where i can learn about ufw ?
thanks

---

### Post by bodhi.zazen on 2011-05-03
[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by cakka on 2011-05-19
> **bodhi.zazen said:**
> [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)


is it was no longer maintained ?

---

### Post by bodhi.zazen on 2011-05-19
> **cakka said:**
> is it was no longer maintained ?

is what no longer maintained ?

---

### Post by Soul-Sing on 2011-05-19
> **cakka said:**
> is it was no longer maintained ?

> I have personally used [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter) and have been pleased with it.
It's worth a look at at least, good easy to use GUI.

indeed firestarter is not maintained for years now.

---

### Post by cakka on 2011-05-20
> **leoquant said:**
> indeed firestarter is not maintained for years now.

so, any other alternatives ?

---

### Post by Soul-Sing on 2011-05-20
> **cakka said:**
> so, any other alternatives ?

post# 13

---

### Post by Soul-Sing on 2011-05-20
> **leoquant said:**
> post# 13

or firewall hardware?: firewall distributions?
([https://secure.wikimedia.org/wikipedia/en/wiki/List_of_router_or_firewall_distributions](https://secure.wikimedia.org/wikipedia/en/wiki/List_of_router_or_firewall_distributions))

---

