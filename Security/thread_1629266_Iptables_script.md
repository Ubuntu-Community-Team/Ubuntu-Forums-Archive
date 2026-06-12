---
title: "Iptables script"
date: 2010-11-23
forum: Security
---

### Post by Okami on 2010-11-23
Hello

I feel stupid for asking this, I downloaded an iptables script, but I really dont know how to use it. I have tried forever to understand iptables but it is impossible. After a lot of searching about how to use script I found and did the following, but I need to know if it was the right way to use iptables script.

1. I saved the text in a file which I called fw.sh Is it correct that it should be .sh in the end?
2. I opened a terminal and wrote chmod 700 fw.sh
3. Wrote ./fw.sh
4. And last I wrote something which I hope saved the new script to iptables: bash -c "iptables-save > /etc/iptables.rules"

The script is from here: [http://www.hermann-uwe.de/files/fw_laptop](http://www.hermann-uwe.de/files/fw_laptop)

Sorry for my bad English and thanks in advance! :oops:

---

### Post by brian_p on 2010-11-23
> **Okami said:**
> 

I feel stupid for asking this, I downloaded an iptables script, but I really dont know how to use it. I have tried forever to understand iptables but it is impossible. After a lot of searching about how to use script I found and did the following, but I need to know if it was the right way to use iptables script.

If you do not understand what the script does it is not very wise to run it. You may have different objectives from what the script aims to achieve which may not fit with what it offers.

> Sorry for my bad English and thanks in advance! :oops:

Your English is very good. I hope mine makes it clear your course of action is not the best.

---

### Post by cariboo on 2010-11-23
I have to agree with brian_p, you shouldn't use the script, if you don't understand what it does.

When setting up firewall rules, first write down what you want to accomplish with the rules, then you can go ahead and write the rules. For most people running the default:

```
sudo ufw enable
```

is enough to protect their system during day to day usage.

---

### Post by Okami on 2010-11-23
Thank you both. Perhaps I should continue to use ufw then :) I normally doesnt use anything I found on Internet, but I have been looking at that script for some time and thought it was what I was looking for by reading the description.

But was it the right steps to take when using iptables scripts?

---

### Post by cariboo on 2010-11-23
Personally if I were to setup firewall rules, I wouldn't rely on scripts to do the work. I don't use firewalls on systems on my internal network, as I'm behind a router. When I did use a fire wall I used [Arno's iptables firewall]("http://rocky.eld.leidenuniv.nl/joomla/index.php?option=com_content&view=article&id=46&Itemid=77") as a guide and reference, but created my own set of rules.

---

### Post by Okami on 2010-11-24
Thanks for the link to the website. I will try to learn how to setup iptables rules, but for now I will continue to use ufw.

---

### Post by bodhi.zazen on 2010-11-25
> **Okami said:**
> Thanks for the link to the website. I will try to learn how to setup iptables rules, but for now I will continue to use ufw.

IMO scripts for iptables make it mor ecomplicated then it needs to be.

I use iptables-save an iptables-restore (actually iptables-apply).

See:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

It takes a bit to understand the rules, and if you understand the syntax of ufw you are half way home.

---

### Post by Okami on 2010-11-26
Thank you bodhi.zazen.

Right now for ufw I have "default deny", denying incoming traffic if I understand it right.

Would it be the same to use iptables like this?

iptables -A INPUT -j DROP
iptables -A FORWARD -j ACCEPT
iptables -A OUTPUT -j ACCEPT

or is it only

iptables INPUT DROP
iptables FORWARD ACCEPT
iptables OUTPUT ACCEPT

---

### Post by bodhi.zazen on 2010-11-26
> **Okami said:**
> Thank you bodhi.zazen.

Right now for ufw I have "default deny", denying incoming traffic if I understand it right.

Would it be the same to use iptables like this?

iptables -A INPUT -j DROP
iptables -A FORWARD -j ACCEPT
iptables -A OUTPUT -j ACCEPT

or is it only

iptables INPUT DROP
iptables FORWARD ACCEPT
iptables OUTPUT ACCEPT

You need the flags. -A for append (to the end of the chain) vs -I (insert at a secific place in the chain) or -D (delete or remove).

You also need the -j which is "jump" or what action to take.

The -P flag is the Policy, or what action to take if no rule in a chain is matched.

I an not really sure there is much of a difference between having the last rule in the chain to drop all traffic

iptables -A INPUT -j DROP

vs the default policy of DROP

The problem with setting the default policy to DROP is that it is very easy to lock yourself out if you flush the rules

iptables -F

since you now have no rules, with a defualt policy of DROP you will no longer have access to the server or desktop from any kind of remote connection. You would then need physical access to log in and fix your defunct rules.

Does that make sense ?

If not, you need to do some more reading.

ufw is a configuration tool. If you list all the rules you will see it is more then simply setting the default policy.

```
sudo ufw enable
sudo iptables -L -v 
```

---

### Post by Okami on 2010-11-27
Thanks again. I am sorry but I will never understand this =) it is confusing. Thanks for taking your time to explain.

I guess it should be:

iptables -P INPUT DROP

if I want to block all incoming packets. I should read more carefully.

Edit: now iptables -L looks like this:

target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
DROP       all  --  anywhere             anywhere

I used "iptables -A INPUT -p tcp --dport 80 -j ACCEPT" and after that "iptables -A INPUT -j DROP" I thought this would allow web traffic but it does not.

---

### Post by bodhi.zazen on 2010-11-27
> **Okami said:**
> Thanks again. I am sorry but I will never understand this =) it is confusing. Thanks for taking your time to explain.

I guess it should be:

iptables -P INPUT DROP

if I want to block all incoming packets. I should read more carefully.

Edit: now iptables -L looks like this:

target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
DROP       all  --  anywhere             anywhere

I used "iptables -A INPUT -p tcp --dport 80 -j ACCEPT" and after that "iptables -A INPUT -j DROP" I thought this would allow web traffic but it does not.

It is confusing at first.

When you say "allow web traffic" what do you mean by that ? Are you running a web server ? Or are you running a client, ie firefox ?

I think what you are missing is the concept of a port. 

"Web traffic" connects to port 80 (http) or 443 (https) on the SERVER. I wold also include other servers such as ftp and DNS.

"Web traffic" is more then port 80.

The client uses a random higher port.

So, as a client, to allow all web traffic, you need to allow ports 80 and 443.

```
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -A INPUT -p udp --sport 53 -j ACCEPT
sudo iptables -A INPUT -p tcp --sport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --sport 443 -j ACCEPT
sudo iptables -A INPUT -j DROP
```

The middle 3 lines can be shortened with multiport

```
sudo iptables -A INPUT -p udp --sport 53 -j ACCEPT
sudo iptables -A INPUT -p tcp -m multiport --sports 80,443
sudo iptables -A INPUT -j DROP
```

---

### Post by Okami on 2010-11-28
Thank you very much, it worked. I thought it was only port 80 to use firefox. I am not running any servers so configure iptables like this should be enough?

---

### Post by bodhi.zazen on 2010-11-28
> **Okami said:**
> Thank you very much, it worked. I thought it was only port 80 to use firefox. I am not running any servers so configure iptables like this should be enough?

Enough for what ?

IMO most desktop users do not need to enable their firewall and those that do 

```
sudo ufw enable
``` is sufficient.

What is it youare trying to accomplish ?

Again, I think you should read up on iptables and ports.

---

### Post by Okami on 2010-11-28
I only wanted to accomplish the the same as ufw default deny, but with iptables only. Since script was not a good idea I decided to try and learn a little about iptables.

I dont really know what ufw deafult deny do, sounds like it should block all incoming traffic, but it does not because I dont need to open any ports to be able to use Internet. I probaply dont understand neither ufw or iptables and everything around it properly.

---

### Post by bodhi.zazen on 2010-11-28
> **Okami said:**
> I only wanted to accomplish the the same as ufw default deny, but with iptables only. Since script was not a good idea I decided to try and learn a little about iptables.

I dont really know what ufw deafult deny do, sounds like it should block all incoming traffic, but it does not because I dont need to open any ports to be able to use Internet. I probaply dont understand neither ufw or iptables and everything around it properly.

start ufw, list and understand the rules

```
sudo iptables -L -v -n
```

You need to understand ports, both on the client and server, as well as the TCP protocol.

ufw blocks all NEW incoming connections, but allows ESTABLISHED connections.

I suggest you read up on "basic" networking, once you understand networking protocols, iptables is very straight forward to use.

---

