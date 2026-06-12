---
title: "Allowing connections from the outside world through SSH"
date: 2010-01-09
forum: Server Platforms
---

### Post by ooloo on 2010-01-09
Hey,

I want to set up my laptop to allow connections to certain users with passwords from anywhere over the internet via SSH but I'm unsure about how I would go about doing this.
I only thought it would be the case of setting up the open-ssh server on the laptop then, using my external IP and PuTTY on another PC outside of the network, connect to the external IP through port 22 so I tried this and wait 3 or 4 minutes or so and it says the connection times out.

I have also configured my router to use port forwarding but this doesn't seem to help much either and I have LAMP setup to allow connections to external IP : 80.

The only thing I am able to do is access the laptop through the local network by using its internal IP's like 127.198.0.1:22 or something.

I was wondering if anybody knows if and could tell me how I would do this as I really want to be able to access my home computer/laptop from my work sometimes, especially if I have work at home which is not with me at work or something.

I know this is possible but I'm quite new to this type of thing and don't know what is going wrong. Have I missed something or do I need to change any .conf files or anything?

---

### Post by mk1w86 on 2010-01-09
First you will have to open the correct ports on your router (the default for SSH is 22).

You may also want to consider setting up a DNS name if your IP address is dynamic.  I use:

[http://www.dyndns.com/](http://www.dyndns.com/)

or you can use any other service compatible with your router.

---

### Post by smc18 on 2010-01-09
1.  Statically assign an IP to your laptop, i.e. 192.168.0.150
2.  Install OpenSSH server onto your laptop.  (Change default SSH port 22 to something else)
3.  Test it locally, SSH into 192.168.0.150 from another computer in your house.
4.  Setup Port Forwarding on your Router(sometimes called Virtual Server)

    Do this by forwarding all WAN/Internet/Outside Port 22/SSH request are forwarded to your laptop at 192.168.0.150 (Your SSH Server)

I advise when installing OpenSSH server you change the default port 22 to something else that you will remember.  If you leave it as the default port 22 and open up your router, you will most likely be pounded with failed SSH login attempts from outside brute force attempts.

Now from your work you can SSH into your laptop using your outside HOUSE IP address given to you from your ISP, for example 66.102.7.104, using the port you setup for SSH, and your router should send the request to your laptop.

Note: Of course this setup will only work if your leave your laptop at your house connected to your home LAN and powered on.  It does kind of defeat the purpose of having a laptop.

---

### Post by CharlesA on 2010-01-09
Also, it's quite unsafe to have SSH running on port 22, without something like DenyHost or Fail2Ban that blocks IP addresses that are trying to access the SSH server using the wrong password. 

I prefer key authentication myself.

---

### Post by stlsaint on 2010-01-10
make sure that you dont have a firewall blocking ports. Do above posted instructions to ensure you are not blocking anything. As for port change it is maybe good practice to do this but if you have key authentication you really dont need to. Here is a really helpful tutorial on securing server using public/private keys. Its better over un/pwd
[Secure using keys]("http://www.debuntu.org/ssh-key-based-authentication")

---

