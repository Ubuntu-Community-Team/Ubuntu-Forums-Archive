---
title: "Reconfiguring internal firewall"
date: 2009-06-04
forum: Security
---

### Post by LucaGiudice on 2009-06-04
Hello everyone, I'm new here and also new to Ubuntu so sorry if dumb questions in wrong place.

Let's start with my problem:
Years ago a colleague of mine setted up an internal Ubuntu firewall to do prerouting and postrouting duty from-to our static IP address.

Now, several years later, that person does not work here anymore and we changed our internet provider. 
That means we changed our static IP and it's name. We also changed domain.

I started reconfiguring our firewall and I'm lost at one point:
I changed host name in both \etc\hosts  and \etc\hostname (I needed to do this because I need the firewall name to match the static IP name) but from now then when I reboot it won't manage to execute \etc\rc.local but the file is in it's place with all it's attributes set in the right place and so on. I can VI it and see it's contents, no problems. It just does not manage to see it at startup level.
The message I get is: 
/etc/rc2.d/S99rc.local:  29:  /etc/rc.local: not found

the file /etc/rc2.d/S99rc.local is untouched so should still be correct...

What am I missing?

---

### Post by iponeverything on 2009-06-04
two things:

-- what's the first line in the file /etc/rc.local
-- what's the output of "ls -l /etc/rc.local"

---

### Post by LucaGiudice on 2009-06-04
My rc.local

#!/bcn/sh -e
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#Subversion
iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 443 -j DNAT --to 196.100.0.17:8443

#Teleassistenza
iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 5901 -j DNAT --to 196.100.0.17:5901
iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 5900 -j DNAT --to 196.100.0.17:5900
iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 5800 -j DNAT --to 196.100.0.17:5800
iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 5500 -j DNAT --to 196.100.0.17:5500
iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 5501 -j DNAT --to 196.100.0.17:5501

#PC Exenet
iptables -t nat -A PREROUTING -p tcp -d lantek.ns0.it --dport 5555 -j DNAT --to 196.100.0.101:5555
iptables -t nat -A PREROUTING -p tcp -d lantek.ns0.it --dport 5556 -j DNAT --to 196.100.0.101:3389

# vnc per Viviana
#iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 5400 -j DNAT --to 196.100.0.5:5400


#Desktop remoto sul server da fuori ufficio
iptables -t nat -A PREROUTING -p tcp -d 77.108.47.120 --dport 3389 -j DNAT --to 196.100.0.17:3389

# Desktop remoto per Ornato
#iptables -t nat -A PREROUTING -p tcp -d 87.25.810.124


iptables -t nat -A POSTROUTING -d 196.100.0.17 -j SNAT --to 196.100.0.25

#PC Exenet
#iptables -t nat -A POSTROUTING -d 196.100.0.101 -j SNAT --to 196.100.0.25

# vnc per Viviana
#iptables -t nat -A POSTROUTING -d 196.100.0.5 -j SNAT --to 196.100.0.25

exit 0



$ ls -al /etc/rc.local
-rwxr-xr-x 1 root root 1760 2009-06-04 09:44 /etc/rc.local

---

### Post by iponeverything on 2009-06-04
change the first line of your rc.local to:

```
#!/bin/sh -e

```

---

### Post by LucaGiudice on 2009-06-04
I'll try

---

### Post by LucaGiudice on 2009-06-04
IT WORKS!!!

Thank you so much! I'm a newbie about Linux and Ubuntu things so I'd never tought to double check a row starting with # character!

Now I just have to set up the rc.local file correctly but that is another story

---

### Post by iponeverything on 2009-06-04
The iptables rules are pretty strait forward. 

If you are not sure what they doing:

the "Subversion" section is taking any packet destined for the IP address 77.108.47.120 and going to port 443 (HTTPS) and it's changing the destination of the packet to 196.100.0.17 port 8443. 

All of the rules are very similar.

---

### Post by LucaGiudice on 2009-06-04
Thank you very much for the kind and fast answer.

I think I'm on route now. Might I still have problems I'll contact you again.

---

### Post by LucaGiudice on 2009-06-04
Sorry but I'm asking another maybe even dumbier question:

what is the meaning of the address just after -p tcp -d?
I mean:
I have a public IP address which my provider assured me is redirected on the internal static IP address of my firewall.

So, in that position should I put the public IP address or the IP addres of the firewall itself?

---

### Post by iponeverything on 2009-06-04
```

-d

```

means destination address.

It looks like your old staic IP was 77.108.47.120 and the addresses behind your firewall are 196.100.0.0/24.

If that is the case you will need to replace 77.108.47.120 with your new static IP address.

I am bit confused about your setup though.

what is 77.108.47.120 and what is 196.100.0.17?

---

### Post by LucaGiudice on 2009-06-04
Thank you again, that makes the thing working.
Now if only my provider manages to open the ports on their router in the right direction...

---

