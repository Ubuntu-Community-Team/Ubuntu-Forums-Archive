---
title: "networking mode selection doubt"
date: 2011-02-07
forum: Ubuntu Cloud and Juju
---

### Post by selvawithcommunity on 2011-02-07
hello everybody and specially **kim0**

i am an engineering student studying in INDIA. for my final year project we plan to setup the private cloud and deploy the compiler application on the cloud. 
so that we are trying to setup the private cloud. for trial purpose i tried out for last 3 weeks in my home environment. but i have  faced more error and couldn't setup

so now i planned to setup the private cloud using ubuntu10.04  enterprise cloud in my college using the 2 laptops among one VT enabled processor. and eucalytus version comeup with ubuntu is 1.6.2

and i got permission for 4 ip address without any restriction.

but my doubt is:
to select which networking mode? 

[http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0](http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0)

as mentioned in the eucalyptus documention MANAGED and SYSTEM MODE is not suitable for my college network. since we have to assign the ip address manually(WITHOUT DHCP) and no VLAN available
so 1) managed NOVLAN or 
2) STATIC MODE SUITABLE FOR OUR COLLEGE.

in our college ip ranges like 192.168.xx.xx or 10.1.xx.xx
so how to setup VNET related details.

help me please.
thank you.

---

### Post by kim0 on 2011-02-07
hey, I think the default for UEC is managed_novlan, you should use that. Please try to follow exact steps for installation (from CD easier, or from packages) as detailed on
[https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)

For more info on networking, check out
[http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-7-%E2%80%93-network%C2%A0management/](http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-7-%E2%80%93-network%C2%A0management/)

All the best

---

### Post by selvawithcommunity on 2011-02-08
hai friends
i am using the CD INSTALLATION METHOD FOR SETUP THE CLOUD
1.while trying to setup the private cloud i installed CC,CLC,SC successfully on one machine. 

2. while installing node controller i cant move further. because shows the error as 

Failed to retrieve the preconfiguration file.  The file needed for preconfiguration could not be retrieved from  [http://10.1.7.103:8774/preseed/preseed.conf](http://10.1.7.103:8774/preseed/preseed.conf). The installation will proceed in non-automated mode

***1.could anyone please tell me why this happen.
and there is option available to skip this one. and i skipped it and continued the node controller installation.

*so what should i do now? may i need to add that preseed.conf file manually? or should i need to reinstall the node controller again?

4. i am using the following 3 ip's only. 10.1.7.103(for CLC,CC,SC) and 10.1.7.104 (for node controller) and 10.1.7.105(gave as the public ip for virtual instances)

but in the front end machine when i am giving the ipconfig-> it shows
two eth0
one eth0 ip is 10.1.7.103
but another eth0 available with the ip address 169.254.169.254
***the second eth0 and ip addressing confuse me? could you please help me?

---

### Post by kim0 on 2011-02-09
Hi,

The network between the frontend and the NC should have IP range that is different from the "public" network IPs. ie. If the "public" NIC of frontend is 10.1.7.103, the other NIC should have some other IP (say 192.168.33.103), that same new range should be used for NC

---

### Post by selvawithcommunity on 2011-02-09
ya kim0 i understand. actually i am not using anyother public ip's to contact my cloud outside. i am going to use the cloud only within the 10.1.7.x proxy only. so my public and private are both same. but i cant understand those second eth1. 
and those [https://10.1.7.103/preseed/preseed.conf](https://10.1.7.103/preseed/preseed.conf) is not at all problem kim0.

thank you for your reply kim0

---

