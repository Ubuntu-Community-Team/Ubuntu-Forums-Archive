---
title: "My virtualization Goals"
date: 2009-03-07
forum: Virtualisation
---

### Post by ciscostudent561 on 2009-03-07
Good day to you all, 
Thanks for your continued support.
My goal is simple but the means to achieve it not so much. 

First I'll provide a lil backround.
I am a total newbie and have no experience with Ubuntu. 
I have just purchased my new pc that i will start my project with.


What I plan to do is engineer a virtual Thin Client/Server Environment in which the end user is able to run virtual sessions in which they can access the same published programs no matter what thin client they log into. 

I am shooting to have the users to be able run simple word processing applications as well as the ability to view popular media websites ie youtube, dailymotion, imeem etc...

My pc gets here next week, so I plan to ask alot of questions :)

---

### Post by Mark Marple on 2009-03-08
Hello CiscoStudent561!
I too have the same interest.  So I hope that someone will answer soon.  My goal is:

1.  Have server run windows in VE for the few items I need it to run......Ipod and Skycaddie.
2.  Run media center type program for streaming. (I will try to use VLC, as I hear this is good.) I would like to set this up kinda like ORB (for windows).

I do have a few question, and please be nice, as I'm new to this too and I'm doing it for learning.

1. If I setup Virtualization on a server, do I still need the same software (ie. VMware server) on the main computer that I will be using?  I'm a little confused in how the VE gets sent to the computer you are working off of.  Or am I way off base?

2. In stating my first question, I assume I need to set the server up with domain name and all other server related items?  How would this work if I also have a windows system (used for work), in terms of getting to my music to listen to while I work.
Do I need the LAMP type of configuration?

Sorry Cisco..........I didn't mean to Hijack your post.  I just thought maybe 1 post could turn up info for the both of us.

Mark

---

### Post by veloce on 2009-03-08
> **ciscostudent561 said:**
> Good day to you all, 
Thanks for your continued support.
My goal is simple but the means to achieve it not so much. 

First I'll provide a lil backround.
I am a total newbie and have no experience with Ubuntu. 
I have just purchased my new pc that i will start my project with.


What I plan to do is engineer a virtual Thin Client/Server Environment in which the end user is able to run virtual sessions in which they can access the same published programs no matter what thin client they log into. 

I am shooting to have the users to be able run simple word processing applications as well as the ability to view popular media websites ie youtube, dailymotion, imeem etc...

My pc gets here next week, so I plan to ask alot of questions :)

For thin client applications there is no need to use virtualisation.  Assuming you are using all Ubuntu boxen (i.e. server and thin client) then all you need to do is:

1. allow remote sessions on the server (From Ubuntu main screen select System - Administration - Login Window. Select the "Remote" tab and allow remote sessions.
2. Log in via XDMCP from the thin clients. (It's a login option).

---

### Post by veloce on 2009-03-08
> **Mark Marple said:**
> 
1. If I setup Virtualization on a server, do I still need the same software (ie. VMware server) on the main computer that I will be using?  I'm a little confused in how the VE gets sent to the computer you are working off of.  Or am I way off base?

No. You set up vmware server on the server.

I use rdp to access the windows machines on the server (specifically gnome-rdp).

> **Mark Marple said:**
> 
2. In stating my first question, I assume I need to set the server up with domain name and all other server related items?  How would this work if I also have a windows system (used for work), in terms of getting to my music to listen to while I work.


You need to know how to connect to the vms best to use bridged networking, then each vm has an ip address on the main network.  This is the TCP/IP network so is indifferent to whether you are using linux or windows.

To access your server that is streaming your music, you need it's ip address.  You will also need to know what port it is delivering the music to - you will sort that out when you set up the music streaming software.

The music streaming is not part of your virtualisation solution so you should post elsewhere on that issue.

---

### Post by ciscostudent561 on 2009-03-10
> **veloce said:**
> For thin client applications there is no need to use virtualisation.  Assuming you are using all Ubuntu boxen (i.e. server and thin client) then all you need to do is:

1. allow remote sessions on the server (From Ubuntu main screen select System - Administration - Login Window. Select the "Remote" tab and allow remote sessions.
2. Log in via XDMCP from the thin clients. (It's a login option).

Thanks! maybe i am not asking the questiong the right way. 

,
   First and foremost, thanks for giving back to the community... Your insight is welcome and well recieved....

  Now I see that you are very experienced with Linux as a whole whilst I am not. Despite a few months of training at Technical School 3 years ago I have no Idea about Linux. I think Linux is the future and can be used for real good within communities the same way it has enhanced the K12 enviroment with Edbuntu. 

   I have just purchased a small server that I will be running many VMs and learning how to manage different Systems. My goal is to have Thin Client running Web Based Virtual OS where users can access applications and data that are centralized on Servers, like the Citrix xenapp but in a Unix enviroment. .

  I am just inquiring of any guidance on where to start before embarking on this incredible project. Thanks for taking your time to read this... i look forward to your response.

---

### Post by ciscostudent561 on 2009-03-12
any ideas folks?

---

