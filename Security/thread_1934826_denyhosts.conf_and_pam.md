---
title: "denyhosts.conf and pam"
date: 2012-03-02
forum: Security
---

### Post by Diametric on 2012-03-02
Hi,

I have a few questions - maybe bullets will work better.

1. I found an IP in my auth.log file where someone used a dictionary attack on my box - while they were unsuccessful, how common is this?

2. Do I risk incurring the wrath of a script kiddie for running an aggressive nmap against said IP?

3.  Someone turned me on to the denyhosts package - any idea why this isn't part of the distro proper?  It just seems like that should be a default option.

4.  And lastly - should I be looking into pam setting for establishing better security practices?

Many thanks for your time.

Cheers!

---

### Post by Ms. Daisy on 2012-03-03
It's my understanding that it's incredibly common and that there are automated scripts crawling the internet looking for servers to brute force attack.

Here are some links discussing security measures for servers.

[http://askubuntu.com/questions/32246/how-to-secure-ubuntu-server-from-bruteforce-ssh-attacks](http://askubuntu.com/questions/32246/how-to-secure-ubuntu-server-from-bruteforce-ssh-attacks)
[http://www.andrewault.net/2010/05/17/securing-an-ubuntu-server/](http://www.andrewault.net/2010/05/17/securing-an-ubuntu-server/)
[http://nwlinux.com/how-to-secure-an-ubuntu-apache-web-server/](http://nwlinux.com/how-to-secure-an-ubuntu-apache-web-server/)

Frankly I'm just now starting to play with servers & securing them. So hopefully someone with more experience than me can chime in & say whether any of those link stink or not.  Or if there's a better link, please share.

---

### Post by Diametric on 2012-03-03
Cool - thanks for your reply.  I'll spend some time perusing them.

---

### Post by JKyleOKC on 2012-03-03
> **Diametric said:**
> 2. Do I risk incurring the wrath of a script kiddie for running an aggressive nmap against said IP?I wouldn't worry so much about the script kiddie as I would about my ISP's reactions. Running scans on IPs that aren't assigned to you is not allowed by most "terms of services" sets of rules, and could get your service cancelled.

Also, if the IP you're scanning is a dynamic one and gets reassigned to someone else, you might be in for some serious legal trouble if the new owner complains to the right people.

In other words, it's a Bad Idea in any case. Just block that IP from access to your system and forget about it...

---

### Post by Diametric on 2012-03-03
I didn't know about the "rules of service" - but, at least initially...for my own edification...if they scan me, I feel fairly vindicated in seeing what I can from them.

---

### Post by Dangertux on 2012-03-03
Fyi port scanning is not illegal.

You also would not likely be scanning the person responsible for the brute force in fact o can almost guarantee that you would find a server running an ssh servoce with weal credentials.

Denyhosts while it is good, is a waste of time in my opinion just impose an iptables rqte limit use keys and disable login with passwords.

Hope this helps

---

### Post by Diametric on 2012-03-03
> **Dangertux said:**
> Fyi port scanning is not illegal.

You also would not likely be scanning the person responsible for the brute force in fact o can almost guarantee that you would find a server running an ssh servoce with weal credentials.

Denyhosts while it is good, is a waste of time in my opinion just impose an iptables rqte limit use keys and disable login with passwords.

Hope this helps

Fair enough mate - thanks for the info.  I'm hoping denyhosts holds me down until I can learn iptables...or pam, which is what I've come to understand is the way to lock processes.  Thus, my original post/questions.

Cheers...

---

### Post by Dangertux on 2012-03-03
Oh my... So many typos... I really need to get used to this new phone..

Anyway i just mention the other though because on high load systems there is no point on wasting IO on something that wont be successful anyway. Of course use what works for you

---

### Post by Diametric on 2012-03-04
It's all good - I appreciate the feedback and don't stress the typos!  

Cheers...

---

