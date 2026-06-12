---
title: "LTSP - New client not booting"
date: 2006-02-27
forum: Server Platforms
---

### Post by redjim on 2006-02-27
I have an edubuntu server that has been working just great for weeks.  I have about 6 dell clients connected to it.   Now I am setting up some "new" compaq en 266 64mb computers in our lan
with 3com cards 905c-txm.
These are the same cards that boot perfectly off of dell optiplex gx1 350mhz.
They seem to boot until they get to the part where I think they hook up to dhcp

IP-Config: eth0 hardware address 00:08:c7:ea:3a:0e mtu dhcp RARP

They get here then freeze.
Does anyone know where I can get some help?
This is the same problem as http://www.nabble.com/Re:-I've-got-a-problem-with-ltsp-p1618200.html
Thanks for any help.

---

### Post by laramik on 2007-09-15
Are all of your clients and hardware all working with the same architechture.  64bit?  If not, you will continue to run into probelm after problem and just when you fix this error you will start to have another.  If you are running the 32 bit version across a 64 bit environment, or vice versa, you will have nothing but problems.  Just disable 64 bit if at all possible on your clients.

---

