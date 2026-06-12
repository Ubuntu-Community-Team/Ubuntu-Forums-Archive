---
title: "Web Service Not Available When Login VMWare RC1 On Hardy 8.04"
date: 2008-07-31
forum: Virtualisation
---

### Post by hobong on 2008-07-31
Hello all ....

I can not log in to VMWare Server 2.0 RC1 on My Ubuntu Hardy, 
everytime i try it's always reported error **"Web Service Not Available"** 

Anyone has solution about this Error ?

Another post said that it's caused by ipv6. I have Al read disable ipv6. 
I put "blacklist ipv6" on /etc/modprobe.d/blacklist. 

I also add :
#alias net-pf-10 ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
on /etc/modprobe.d/aliases

and My /etc/hosts is :

127.0.0.1 localhost
# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
192.168.0.21 cinema

Here's the start of VMWare Server 
hobong@cinema:~/src$ sudo /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                 done
   Virtual machine communication interface                 done
   VM communication interface socket family:               done
   Virtual ethernet                                        done
   Bridged networking on /dev/vmnet0                       done
   VMware Server Authentication Daemon (background)        done
/etc/init.d/vmware: 1252: 0: not found
Starting VMware management services:
   VMware Server Host Agent (background)                    done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                         done
hobong@cinema:~/src$ 

except this error : /etc/init.d/vmware: 1252: 0: not found


Anyone can help me with **"Web Service Not Available"** 
error 

I run a Webserver Apache2 too on my host, does Apache2 caused this problem ? I'm not sure 

Thank u

---

### Post by bmwman on 2008-08-14
Were you able to figure it out? I'm getting the same error.

P.S. Actually I got it to work, it was something else that I did before and I forgot about it. Also commenting the IPv6 lines did the trick.

---

