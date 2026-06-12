---
title: "how to setup shorewall 4 to only allow ports 80 and 22"
date: 2011-02-21
forum: Server Platforms
---

### Post by Elias2816 on 2011-02-21
I am in the process of setting up my first web server and I was told to use shorewall for the firewall. I got it installed and copied the rules file over but now I cannot figure out how to deny all access except from ports 80 and 22. Do i add it under SECTION ESTABLISHED, SECTION RELATED or SECTION NEW. 

I was told to add

HTTP/ACCEPT   net   $FW
SSH/ACCEPT    net   $FW

above #LAST LINE however i have a newer version. I feel like im taking crazy pills... any help would be appreciated.

---

### Post by mciverza on 2011-02-22
> **Elias2816 said:**
> I am in the process of setting up my first web server and I was told to use shorewall for the firewall. I got it installed and copied the rules file over but now I cannot figure out how to deny all access except from ports 80 and 22. Do i add it under SECTION ESTABLISHED, SECTION RELATED or SECTION NEW. 

I was told to add

HTTP/ACCEPT   net   $FW
SSH/ACCEPT    net   $FW

above #LAST LINE however i have a newer version. I feel like im taking crazy pills... any help would be appreciated.

in /etc/shorewall/rules

add (notice that the gaps are TABs not spaces)
ACCEPT          net              $FW             tcp     80
ACCEPT          net              $FW             tcp     22


If you want to limit access to SSH, so that only your typical IP addresses can get to it 
you can modify the line so that it looks similar to the one below. BUT: make sure that your IP address info is correct, or you could lock yourself out.

ACCEPT          net:41.0.0.0/8              $FW             tcp     22
ACCEPT          net:196.0.0.0/8              $FW             tcp     22

That above example would be a generic allow all Africa to access SSH.

---

