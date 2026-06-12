---
title: "Momentary ssh warning"
date: 2012-08-30
forum: Security
---

### Post by takitsan on 2012-08-30
Hi! Hope this is the right forum for this......

I was connected to my server via ssh and suddenly gnome-terminal stopped responding.

I closed the terminal window and reopened and tried to connect again.

I got this:

> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The RSA host key for xxxxxxxx.xxx has changed,
and the key for the corresponding IP address 192.168.1.1
is unknown. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
25:b7:b5:e4:57:1a:dc:28:51:a0:5c:6c:33:75:e1:29.
Please contact your system administrator.
Add correct host key in /home/xxx/.ssh/known_hosts to get rid of this message.
Offending RSA key in /home/xxx/.ssh/known_hosts:1
  remove with: ssh-keygen -f "/home/xxx/.ssh/known_hosts" -R xxxxxxxx.xxx
RSA host key for xxxxxxxx.xxx has changed and you have requested strict checking.
Host key verification failed.


The fingerprint is not the one from my server.

Also nothing has changed on the server side: same IP (static), same everything.

I cancelled the connection and I tried to connect a second time.

I got the same message as above.  I cancelled again,

I then tried a third time and got no warning at all, and I was asked for the password as usually.

Anyone has any idea what may have happened?  Was that a 'man in the middle attack' ?

---

### Post by cryptotheslow on 2012-08-30
Given the IP of the server is 192.168.1.1 I take it this is a private LAN.

If it's a work environment could someone else have briefly brought up a server on that IP by mistake? Is that IP excluded from any DHCP assigned ranges of IPs? 

Just thinking 192.168.1.1 and 192.168.1.254 are fairly common default IP addresses on routers - so it could easily have been someone plugging in a new router before configuring it.

How did you make the connection - using the IP address or a DNS name / hostname?

---

### Post by takitsan on 2012-08-31
Hi cryptotheslow!

It is a LAN where the router is 192.168.2.1 and the server is 192.168.2.100 (statically assigned) 

There is port forwarding for port 22 to 192.168.2.100

192.168.1.1 is not even in the DHCP pool.

Also, there was no one near the LAN at the time.

I was connecting from the outside using the DNS hostname......


However, as I am writing these words it occurs to me that organization that assigns our external IP could and holds our DNS record could have momentarily made some change that resulted in me trying to ssh into another server......

---

### Post by cryptotheslow on 2012-08-31
Or it could have been someone on the network you were on spoofing the dns response.

I'd be inclined to change up the keys just to be sure.

---

### Post by takitsan on 2012-08-31
I was connecting from a residential gateway.  There is one more computer  running Ubuntu in the LAN but I don't think it ranks high on the  culprit list.  I would check it if I knew how.

But lets suppose somehow someone was spoofing.

Since  I cancelled both connection attempts with the spoofing warning, and  then got the normal login (without warning), would it be safe to assume that the last was the correct  server?   I mean, can someone ,without messing with your known_hosts  file, send the same key as the real server so that there will be no  warning?

Also, if you know, is the MITM attack always in LANs or can it take place over the internet?

BTW,  my residential router's IP is 192.168.1.1.  It also has the ssh (22)  port open.  I tried to ssh to it to see if I can get the same key  fingerprint i got with the warning but nothing happens.

Thanks for your time on this...

---

### Post by cryptotheslow on 2012-09-01
I am by no means an expert but I believe SSHv2 is secure against mitm attacks provided the public keys are verified before use.

> **takitsan said:**
> 
Since  I cancelled both connection attempts with the spoofing warning, and  then got the normal login (without warning), would it be safe to assume that the last was the correct  server?

Yes, I believe so.

> **takitsan said:**
>  I mean, can someone ,without messing with your known_hosts  file, send the same key as the real server so that there will be no  warning?

Yes they could, they would have to spoof the real server's IP address as well though. However as they do not have the real server's private key they will be unable to decrypt your communications. The SSH RFC includes a section on potential mitm attacks that describes quite well how they are mitigated here: [http://tools.ietf.org/html/rfc4251#section-9.3.4](http://tools.ietf.org/html/rfc4251#section-9.3.4)

> **takitsan said:**
> Also, if you know, is the MITM attack always in LANs or can it take place over the internet?

Theoretically it could be any point on the route between you and the server. However, in your specific case in the first post the IP for the server (192.168.1.1) is not routable across the internet so suggests whatever happened did so on the LAN. (Leaving aside tunnelling for now).

This presentation covers various mitm methods, it's a few years old now but still mostly relevant (**** warning: 355kB PowerPoint slideshow!**) :
[http://www.security.iitk.ac.in/contents/events/workshops/iitkhack04/keynotes/ppt06.ppt](http://www.security.iitk.ac.in/contents/events/workshops/iitkhack04/keynotes/ppt06.ppt)

> **takitsan said:**
> BTW,  my residential router's IP is 192.168.1.1.  It also has the ssh (22)  port open.  I tried to ssh to it to see if I can get the same key  fingerprint i got with the warning but nothing happens.

Being on a private IP range your residential router must be doing some sort of NAT to your internet IP, it may just be that your dropped session followed quickly by a reconnection confused its NAT tables in some peculiar way leading to it connecting you to its own SSH service.

It's certainly an odd occurence for sure.

---

### Post by Bachstelze on 2012-09-04
You were using a name to connect to a private IP. How is the name -> address translation done ? You say 192.168.1.1 is your router, but you were trying to connect to a server, which probably isn't your router...

---

