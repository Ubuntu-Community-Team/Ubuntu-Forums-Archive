---
title: "Lubuntu and CISCO PIX 515E Firewall basic configuration"
date: 2013-11-09
forum: Security
---

### Post by HardTrickySecurity on 2013-11-09
Hi

I didnt know where to ask, feel free to move it.






My topology is simple:


My PC <------> PIX <-------> My Cable modem Motorola <------> ISP (internet)


I follow the steps on this video tutorial, and in theory it should do the trick. I dont know what am I doing wrong.


[https://www.youtube.com/watch?v=D6E2kFPwvTo](https://www.youtube.com/watch?v=D6E2kFPwvTo)
 


On the physical setup side:


1) If I connect the ethernet cable from my Motorola cable modem to my PIX Public int e0, everything looks fine, the network light blinks in green, so is passing data through it and there is connectivity. Same for the ACT light in green and it blinks in the back of the PIX. Ok, so far so good.


2) Now, the ethernet cable that goes from the PIX Private int e1 to my PC, look like something is not right there, all the lights look ok, 
except for the light ACT in the back of the PIX, it blinks but not at the same speed as the Public int e0 ACT light, it blinks way slower. I think that indicates that data is not passing through correctly, I could be wrong.


3) My ISP asign my IP address through dhcp server


4) I connect to my ISP using cable modem, the model is a Motorola Surf Board SB5100i, with enable DHCP server option turn ON


5) And I want to enale NAT, so my real public IP address assigned to me via ISP can be hide from let say hackers on the internet.


My configuration on PIX:


I dont want to put my information about my real ip address or gateway or ranges that my ISP assign me for security reasons, but if you guys tell me that you need that info in order to help me, I would put it. Or any other information.








This is what I got so far:


PART 1: (Everything looks fine, no errors)


config t
int e0 
ip address dhcp setroute
nameif outside
no shut
 
int e1
ip address 172.16.1.1 255.255.255.0
nameif inside
no shut
exit


sh int ip brief (shows all interfaces are UP and with IP's assigned properly, exactly the same as the video tutorial)






PART 2: (Everything looks fine, no errors)


global (outside) 1 inter
nat (inside) 1 172.16.1.0 255.255.255.0
exit
show route






But final result, I got no internet connection. If I go to my browser and go to google or other website there is no connection at all.






And finally I want to enable encryption to my internet connection, kinda like a vpn, but I dont know if PIX is able to do that via hardware. If not I got a cisco vpn 3000 concentrator. I think that one would do the trick for encryption, but I have to learn how to configure it. But that one is for another post I think.




Thanks

---

### Post by mr-woof on 2013-11-11
Hi,

I've not used a 515 but I do have a pix 501, I'm sure they can't be that different. By default on the pix, everything is allowed out and nothing is allowed in. 

Is the 515 different, do you need access-lists on both interfaces?

Actually, post your config. Obviously xx out any IP's/Passwords :-)

---

