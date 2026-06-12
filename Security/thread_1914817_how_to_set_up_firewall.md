---
title: "how to set up firewall?"
date: 2012-01-25
forum: Security
---

### Post by Matrix01 on 2012-01-25
My Xubuntu 11.10 is running from WUBI,
and
when i use Internet, Xubuntu connects WIFI in Office or Coffee shop.

will u help me to set up Firewall?

---

### Post by haqking on 2012-01-25
[http://ubuntuforums.org/showthread.php?t=1876124&page=2](http://ubuntuforums.org/showthread.php?t=1876124&page=2)

---

### Post by Matrix01 on 2012-01-28
i typed this in terminal;
sudo apt-get update && sudo apt-get install gufw
 
and,
output is;

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
k@ubuntu:~$ 


> **haqking said:**
> [http://ubuntuforums.org/showthread.php?t=1876124&page=2](http://ubuntuforums.org/showthread.php?t=1876124&page=2)

---

### Post by haqking on 2012-01-28
> **Matrix01 said:**
> i typed this in terminal;
sudo apt-get update && sudo apt-get install gufw
 
and,
output is;

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
k@ubuntu:~$

that is your system trying to update firefox for oneiric 11.10.

I am guesssing somewhere along the line you have added a PPA for it and its trying to update it.

This is nothing to do with that guide i posted or you installing a firewall.

---

### Post by Matrix01 on 2012-01-28
i thought this was the code, and install firewall,
well,
i am not sure,
will u tell me how to install firewall?

> **haqking said:**
> that is your system trying to update firefox for oneiric 11.10.

I am guesssing somewhere along the line you have added a PPA for it and its trying to update it.

This is nothing to do with that guide i posted or you installing a firewall.

---

### Post by haqking on 2012-01-28
> **Matrix01 said:**
> i thought this was the code, and install firewall,
well,
i am not sure,
will u tell me how to install firewall?

That link i posted tells you how, the first command you typed is the start, but as i said that error message you are getting is to do with firefox.

---

### Post by Matrix01 on 2012-01-28
thread has 60 posts,
is instruction in post #1?

> **haqking said:**
> That link i posted tells you how, the first command you typed is the start, but as i said that error message you are getting is to do with firefox.

---

### Post by haqking on 2012-01-28
> **Matrix01 said:**
> thread has 50 posts,
is instruction in post #1?

if you read the post you will clearly see the first post is a guide on how to install a firewall using 3 methods.

You clearly chose to try and install the first method which is GUFW.

Your error message is nothing to do installing a firewall but a error message about firefox because you have a PPA which i am guessing does not point correctly to the software or the software does not exist.

---

### Post by 0011235813 on 2012-01-28
```
 sudo ufw enable
```
```
sudo ufw logging on
```
```
sudo ufw default deny
```
Will get you started. The link haqking posted will tell you how to regulate outbound traffic as well.

---

### Post by haqking on 2012-01-28
> **0011235813 said:**
> ```
 sudo ufw enable
```
```
sudo ufw logging on
```
```
sudo ufw default deny
```
Will get you started. The link haqking posted will tell you how to regulate outbound traffic as well.

indeed although you should do the ```
sudo ufw default deny
``` before enabling the firewall if you are security/paranoid conscious.

however as mentioned read the link and guide to decide if you want UFW or GUFW or IPTables directly, either way they all control netfilter which is the firewall in the linux kernel.

and the error you are are getting is to do with your PPA's and nothing to do with installing a firewall.

Cheers

---

### Post by Matrix01 on 2012-01-28
i am not sure how to determine either ufw, gufw, or iptables. 

> **haqking said:**
> indeed although you should do the ```
sudo ufw default deny
``` before enabling the firewall if you are security/paranoid conscious.

however as mentioned read the link and guide to decide if you want UFW or GUFW or IPTables directly, either way they all control netfilter which is the firewall in the linux kernel.

and the error you are are getting is to do with your PPA's and nothing to do with installing a firewall.

Cheers

---

### Post by Matrix01 on 2012-01-28
i typed codes in terminal,
output is like this;
what does last message mean?
i am not sure if this is working.

k@ubuntu:~$ sudo ufw default deny
[sudo] password for k: 
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
k@ubuntu:~$ sudo ufw enable
Firewall is active and enabled on system startup
k@ubuntu:~$ sudo ufw logging on
Logging enabled
k@ubuntu:~$ sudo ufw default deny
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
k@ubuntu:~$ 


> **0011235813 said:**
> ```
 sudo ufw enable
```
```
sudo ufw logging on
```
```
sudo ufw default deny
```
Will get you started. The link haqking posted will tell you how to regulate outbound traffic as well.

---

### Post by Dangertux on 2012-01-28
It means that the default action is to deny all inbound packets and if you have services running you need to make rules to accommodate them. 

Hope this helps

---

### Post by 0011235813 on 2012-01-31
> **Matrix01 said:**
> i typed codes in terminal,
output is like this;
what does last message mean?
i am not sure if this is working.

k@ubuntu:~$ sudo ufw default deny
[sudo] password for k: 
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
k@ubuntu:~$ sudo ufw enable
Firewall is active and enabled on system startup
k@ubuntu:~$ sudo ufw logging on
Logging enabled
k@ubuntu:~$ sudo ufw default deny
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
k@ubuntu:~$
It means the firewall is working like it's supposed to. What that message is basically telling you is that if you have made any previous rules, your new rule may affect them.

---

### Post by Matrix01 on 2012-02-10
will u tell me what outbound traffic or inbound traffic is?

> **0011235813 said:**
> ```
 sudo ufw enable
```
```
sudo ufw logging on
```
```
sudo ufw default deny
```
Will get you started. The link haqking posted will tell you how to regulate outbound traffic as well.

---

### Post by haqking on 2012-02-11
> **Matrix01 said:**
> will u tell me what outbound traffic or inbound traffic is?

i am beginning to sense some trolling.

however....

Outbound means stuff going out
Inbound means stuff coming in

---

### Post by Matrix01 on 2012-02-11
outgoing and incoming...
that does not make sense at all...

what is going out, and 
what is coming in?


> **haqking said:**
> i am beginning to sense some trolling.

however....

Outbound means stuff going out
Inbound means stuff coming in

---

### Post by ankspo71 on 2012-02-12
Hi,
> **Matrix01 said:**
> outgoing and incoming...
that does not make sense at all...

what is going out, and 
what is coming in?

Simply put, it is Internet traffic going in and out... which is people using the internet. The internet is made up from millions of computers from around the world all connected together to form a giant network. It is kind of  like how telephones work, but more technical I suppose. Some computers are private and owned by websurfers and some computers are public and are owned by website owners who are using server software, and so on. If you are using the internet to visit a website, then your internet traffic is going out of your private computer and into the computer where that website is located. If people are trying to connect to your computer, then their traffic is coming into your computer. 

For maximum security, it is best to never allow anybody's traffic to come into your private computer (Ubuntu is already set up like this). By default, at least in Ubuntu based distributions, the iptable's basic (but secure) configuration won't allow incoming connections because there are no incoming allowed rules created, with the exception of a few system required connection rules hidden in the configuration files. All outgoing traffic (your traffic) is automatically allowed. A firewall in Linux is a utility to provide an easier way to configure the iptables, if in the event we ever need to change them, mainly to allow an incoming connection.

There are only a few different cases where you would want to let people to connect to your computer, and even then you would only want to partially open your firefall to allow certain types of incoming traffic because of security reasons. Normally most people can't connect to your private computer 'on their own free will' because of how the internet and internet related software works, but there are those few people that found ways to get around that. That's why there are iptables and firewall utilities to help block them.

More on how internet works:
[http://computer.howstuffworks.com/internet/basics/internet-infrastructure.htm](http://computer.howstuffworks.com/internet/basics/internet-infrastructure.htm)
[http://computer.howstuffworks.com/internet/basics/internet.htm](http://computer.howstuffworks.com/internet/basics/internet.htm)
Hope you find this info helpful.

---

### Post by oldos2er on 2012-02-12
> **Matrix01 said:**
> outgoing and incoming...
that does not make sense at all...

what is going out, and 
what is coming in?

Not to sound rude or impolite, but one wonders why you want a firewall if it "does not make sense at all".

Have you read the stickies at the top of this forum? There's a wealth of information there.

---

### Post by overdrank on 2012-02-12
Some post have been removed. Please keep the [_Code of Conduct_]("http://ubuntuforums.org/index.php?page=policy") when posting.

---

### Post by Matrix01 on 2012-02-15
try some out, and find out.
that's all about!
 
> **oldos2er said:**
> Not to sound rude or impolite, but one wonders why you want a firewall if it "does not make sense at all".
 
Have you read the stickies at the top of this forum? There's a wealth of information there.

---

