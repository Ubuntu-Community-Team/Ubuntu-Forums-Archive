---
title: "can't login via ssh, sftp - - cluebat please?"
date: 2015-06-30
forum: Server Platforms
---

### Post by Drone4four on 2015-06-30
I recently changed the default port for sftp by following a simple guide on YouTube called, “[How to Find and Change SFTP Port Number]("https://www.youtube.com/watch?v=Ij-I1BoRYJo")”. 

On my DigitalOcean droplet remotehost I changed the port line in /etc/ssh/sshd_config to something other than the default  (22).  Now I can't login using ssh or sftp.  Here is the error message I am now getting: 
```
$ ssh user@remotehost
ssh: connect to host remotehost port 22: Connection refused
$ 
```
So I immediately logged back in using the Console Access feature in my browser through my DigitalOcean dashboard and reverted the port line in /etc/ssh/sshd_config back to 22.  I still can't login to my remote host via ssh from my local terminal.   I also can't login to via sftp with my konqueror sftp client. Konqueror tells me this:

```
Details of the Request:
URL: sftp://user@remotehost
Protocol: sftp
Date and Time: Tuesday, June 30, 2015 02:26 PM
Additional Information: Connection refused
Description:
Connection refused
```
It's worth noting that I also tried sftp://user@remotehost:22, still no dice.

I Googled around and came across [this guide]("https://www.digitalocean.com/community/questions/port-22-connection-refused") on DigitalOcean. 
I don't have a firewall.  And there is no output for ```
sudo netstat -plutn | grep 22
```

I am doing something trivially wrong here.  Can someone please unleash a cluebat on me?

---

### Post by Drone4four on 2015-06-30
Here comes the cluebat: It turns out the problem was the Port entry in /etc/ssh/sshd_config .  It was completely FUBAR'ed. I think it had to do with Console Access erroneously capturing the '2' key about 14 times but only showing '22'.  The java-based Console Access terminal emulator is imperfect.  I don't really know.  Anyways, to reset my ssh configuration files I purged my system of openssh and reinstalled it.  I could then login perfectly, I just had to reset my rsa key, which was no problem thanks to my previous foray into the world of automatic key login in a thread I created some time ago titled, “[setting up rsa key: "Agent admitted failure" error](http://ubuntuforums.org/showthread.php?t=2268703)". Essentially I followed a guide called, “[3 Steps to Perform SSH Login Without Password Using ssh-keygen & ssh-copy-id]("http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/")”

---

