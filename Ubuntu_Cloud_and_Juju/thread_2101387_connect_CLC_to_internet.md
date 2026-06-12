---
title: "connect CLC to internet"
date: 2013-01-04
forum: Ubuntu Cloud and Juju
---

### Post by asraa on 2013-01-04
hi everybody
i try to build private cloud using UEC with eucalyptus cd install i implemented in two mechine one contain CLC,SC,CC,Walrus and the other contain node controller i am using ubuntu 11.04 LTS eucalyptus 2.02 version

The networking  in cloud implemented with two networks &#8211; private and public. The public network would be accessible to users and administrators from the &#8220;outside world&#8221;, and the private network is reserved for the backend communication, and is private for the cloud(between NCs and CLC mechine)
my problem is the two mechine(i m using 2 labtop) have one NIC eth0 its ok for node because i need one interface for private network but the problem is with CLC mechine need 2 interface eth0 (used with public)and eth1( used with private to communicate with node)
the other problem is how to bring internet connection to CLC mechine as i follow UEC guide it shoud assign a static ip addres to eth0 which is the ip address of cloud but i cant used static addres because i cant get internet connection in this case .
 

  i got internet connection from my ISP through LAN local area connection and set a VPN with user name a passward that ISP gave me and use dhcp so i dont have a static ip address  , this is on my other labtop which i used it to coonect to internet .

so how i can implement clc in mechine with one NIC , and how i can bring intetnet access to it . what shoud i do

sorry for long description please help me:(
thank you in advance

---

