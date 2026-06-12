---
title: "UEC: Unable to ping and connect to instance"
date: 2010-03-30
forum: Server Platforms
---

### Post by Sivaa on 2010-03-30
Hi
I have set up UEC on a single machine 64 bit blade. I have followed the steps as per the documentation.
 
I am using Managed NOVlan mode. I have installed the Karmic kola image. When I try to run the instance, I get an error "no resources available. Try --addressing private". When I try addressing private, an ip address 172.19.1.2 is assigned and the instance was running. 
 
a) When trying to ping the ip, error displayed that the host is unreachable
b) I am also unable to connect to [EMAIL="ubuntu@172.19.1.2"]ubuntu@172.19.1.2[/EMAIL] using ssh. Error message is displayed that " No route to host".
 
I have searched the forums but couldnt find any solution. Please help with your suggestions or any references.
 
Appreciate your help.
 
PS: I suppose everyone is very busy. I see very limited responses to posts. Sharing your experience and expertise will be helpful for all and will reiterate the meaning of ubuntu ;) 
 
 
Cheers
Siva

---

### Post by kiranmurari on 2010-03-31
I simulated your problem on a two machine setup, but haven’t faced any issue in either ping or ssh. The instance comes up nicely with 172.19.1.2 ip address. I’m able to ping and access through ssh. I used the following command to start the instance:
```
$ euca-run-instances emi-XXXXXXXX --addressing private -k mykey
```The next thing that can be cross checked is to do a clean stop and clean start of the eucalyptus services, as eucalyptus expects a clean stop and clean start if the networking mode is changed.
```
$ sudo service eucalyptus stop CLEAN=1
$ sudo service eucalyptus-nc stop CLEAN=1
$ sudo service eucalyptus start CLEAN=1
$ sudo service eucalyptus-nc start CLEAN=1
```Hope that helps.

---

