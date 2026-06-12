---
title: "Install and run a DHCP server from Ubuntu Server"
date: 2012-04-09
forum: Server Platforms
---

### Post by Timster4life on 2012-04-09
I am looking to turn an older dell blade we have into a DHCP server Via Ubuntu Server edition 11.10.

I still consider myself very much a novice with most Linux builds but I can take directions fairly well.. 

Here are my requirements.. 
*Will need to be able to dole out a full set of Class C addy's (255)
*Will be handing them out to VoIP phone via SSL-VPN's
*Will be running 32-bit due to equipment age
*Needs to have GUI for both OS and DHCP configuration (kind of like windows server)
Note: I understand that even mentioning the word GUI sends shivers down peoples spines but this is at request of my IT director as well as myself.. I do not have the experience and knowledge under terminal to confidently and quickly make changes so it is required.. 

I have seen some older broken up guides about installing DHCP3... or even going with bind9 (We don't need DNS services)  Just want to get any ones experienced opinions or see what they think... Thank you in advance!! :p

---

### Post by collisionystm on 2012-04-09
> **Timster4life said:**
> I am looking to turn an older dell blade we have into a DHCP server Via Ubuntu Server edition 11.10.

I still consider myself very much a novice with most Linux builds but I can take directions fairly well.. 

Here are my requirements.. 
*Will need to be able to dole out a full set of Class C addy's (255)
*Will be handing them out to VoIP phone via SSL-VPN's
*Will be running 32-bit due to equipment age
*Needs to have GUI for both OS and DHCP configuration (kind of like windows server)
Note: I understand that even mentioning the word GUI sends shivers down peoples spines but this is at request of my IT director as well as myself.. I do not have the experience and knowledge under terminal to confidently and quickly make changes so it is required.. 

I have seen some older broken up guides about installing DHCP3... or even going with bind9 (We don't need DNS services)  Just want to get any ones experienced opinions or see what they think... Thank you in advance!! :p

Go with Zentyal. Free with option for paid support. Based on Ubuntu LTS. Gui and VERY VERY nice web interface.

---

### Post by Timster4life on 2012-04-09
> **collisionystm said:**
> Go with Zentyal. Free with option for paid support. Based on Ubuntu LTS. Gui and VERY VERY nice web interface.
Thanks for the info, but from what I can see this requires a paid subscription for most services.. we are looking for completely open and free.. also I would like the experience with Ubuntu since we plan on integrating it more and more as time goes on to transition out a-lot of our win servers. Thanks for the reply though!

---

### Post by haqking on 2012-04-09
```
sudo apt-get install dhcp3-server
```

edit /etc/dhcp3/dhcpd.conf file for your pool and lease information.

```
sudo /etc/init.d/dhcp3-server restart
```

and thats it pretty much.

If you really want a GUI then webmin i guess,  i dont know of any GUI DHCP managers for Linux.

I mean once its up and running thats about it.

Cheers

---

### Post by Timster4life on 2012-04-09
Hey thanks so much man, I really do appreciate it... it's great to get confirmation from what I was already thinking from more experienced users/members. I did a bit more digging and did come up with this page, any of these look reputable or worth it really? 

Thank you again!

---

### Post by haqking on 2012-04-09
> **Timster4life said:**
> Hey thanks so much man, I really do appreciate it... it's great to get confirmation from what I was already thinking from more experienced users/members. I did a bit more digging and did come up with this page, any of these look reputable or worth it really? 

Thank you again!

what page ?

I think you forgot the link ;-)

---

### Post by Timster4life on 2012-04-09
[http://www.debianhelp.co.uk/dhcpweb.htm]("http:///www.debianhelp.co.uk/dhcpweb.htm")

It's Monday.. I get my one mess up for the day,haha
Thanks!

---

### Post by haqking on 2012-04-09
> **Timster4life said:**
> [http://www.debianhelp.co.uk/dhcpweb.htm]("http:///www.debianhelp.co.uk/dhcpweb.htm")

It's Monday.. I get my one mess up for the day,haha
Thanks!

I am not familiar with any of them as i dont use a GUI for DHCP its pretty straight forward config file editing and thats it really.

I guess it could be handy for a large enterprise.

You will need to try a few out, i know a few people use Webmin which is a popular server management tool.

Peace

---

### Post by Timster4life on 2012-04-09
> **haqking said:**
> ...I know a few people use Webmin which is a popular server management tool.

Peace

You are not the first who has mentioned Webmin.. I will take a look into it

Thank you for all your help, I do really appreciate it.

Take care!

---

### Post by SeijiSensei on 2012-04-10
dhcpd is pretty much a set-it-and-forget-it type of daemon.  Unless you need to have a lot of static assignments based on MAC addresses, there's really not much maintenance required after the initial configuration.  If you do run into a problem, the first place I'd look is in the logs.

---

