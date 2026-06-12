---
title: "iptables ip ranges?"
date: 2008-07-16
forum: Security
---

### Post by EMCGFX on 2008-07-16
What is the proper way to block ip ranges in iptables using this method: [http://www.cyberciti.biz/tips/howto-block-ipaddress-with-iptables-firewall.html]("http://www.cyberciti.biz/tips/howto-block-ipaddress-with-iptables-firewall.html")

There is example "202.54.20.1/24" But whats the diference between 8 and 24 when using this method.

for example if I want to block whole A ip range "192.0.0.0/24" do I need to use 8 as in "192.0.0.0/8" or 24 ? etc..

How to block A ip range ?

How to block B ip range ?

How to block C ip range ?

How to block D ip range ?

Please only reply if you personally know. Thanks.

:popcorn: Here is some popcorn for helping me.

---

### Post by kevdog on 2008-07-16
The 8,24 numbers you are refering to are known as Classless Inter Domain Routing (CIDR) notation.  It represents the netmask.  You can use CIDR notation or netmask notation so hence:

192.0.0.0/24  or
192.0.0.0/255.255.255.0

They both mean the same thing.  Again 24 is chosen since you are working with a class C network, where the first 3 octets or first 24 bits are used to describe the network.

[http://infocenter.guardiandigital.com/manuals/IDDS/node9.html](http://infocenter.guardiandigital.com/manuals/IDDS/node9.html)

---

### Post by EMCGFX on 2008-07-16
Thank you kevdog, this explains it ;-) But can you include some examples on how I use this [http://www.cyberciti.biz/tips/howto-block-ipaddress-with-iptables-firewall.html](http://www.cyberciti.biz/tips/howto-block-ipaddress-with-iptables-firewall.html) and add this ip ranges to ip.blocked list.

example from article:
202.54.20.22
202.54.20.1/24

But what about A/B/C/D ranges...

For example If I want to block all ips from range A, do I use 192.0.0.0/24 ?

and if I want to block all ips from range B, do I use 192.168.0.0/24

By looking at the page you told me, I figured that this:
/24 	255.255.255.0 	256

blocks all 256 ips in D range right?


Note I need to be able to use ip.blocked list with following bash code in my iptables firewall rules.

BLOCKDB=&#8221;/root/ip.blocked&#8221;
IPS=$(grep -Ev "^#" $BLOCKDB)
for i in $IPS
do
iptables -A INPUT -s $i -j DROP
iptables -A OUTPUT -d $i -j DROP
done

So in ip.blocked list, I need to use something like this to block all ip ranges:
192.0.0.0/24          # Block A ip range
192.168.0.0/24        # Block B ip range
192.168.110.0/24      # Block C ip range
192.168.110.100/24    # Block D ip range  < or do I use 8 instead...

would this be correct? Please, correct me if I am wrong =D

thanks.

---

### Post by EMCGFX on 2008-07-16
I found this on another forum, is this right ? Can some one confurm it please...

84.56.0.0/24 for every thing in the last digit
84.56.0.0/16 for everything in the last two digits
84.0.0.0/8 for everything in the last three digits.

---

### Post by kevdog on 2008-07-17
Yes your /8, /16, /24 explanation for CNS addresses blocking ranges of ip addresses of specific octets is correct.

---

### Post by gastur on 2008-07-17
If you need classfull masking:

class A 0 - 127 in first octet (except 0.0.0.0 and 127.etc), CIDR /8, mask 255.0.0.0

class B 128 - 191 in first octet, CIDR /16, mask 255.255.0.0

class C 192-223 in first octet, CIDR /24, mask 255.255.255.0

class D 224 - 239 in first octet, classfull masks -I don't know :)

If you want to learn more about IP addressing and using masks - not only classfull, but also classless variable length network addresses blocks and masks - try to fint Todd Lammle's CCNA study guide - the questions of addressing are thoroughly dealt with in chapters 2 and 3. Easy to read - and once read, hard to forget.

---

### Post by EMCGFX on 2008-07-27
@kevdog, can you maybe show me examples?

@gastur, can you tell me exact title of the book and maybe link on amazon?

---

### Post by kevdog on 2008-07-27
Examples of what?

---

