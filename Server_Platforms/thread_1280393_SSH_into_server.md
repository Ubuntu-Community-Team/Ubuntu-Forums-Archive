---
title: "SSH into server"
date: 2009-10-02
forum: Server Platforms
---

### Post by rabidityfactor on 2009-10-02
Hi I'm a newbie and I have a problem. I'm hosting my website on a Ubuntu 9.04 server which I have setup. I haven't got the domain name yet, but have a static IP 117.240.10.210. I can access my website using this IP. The computer that is used as the server has an IP 192.168.1.101 within that network. I want to ssh into this machine.

I have installed oppenssh-server in the other machine.. But when I do 
$ssh -l username 117.240.10.210 
I get a connection timed out error.

What am I doing wrong?

Thanks in advance

---

### Post by JigglyWiggly_ on 2009-10-02
Have you port forwarded(assuming you are connecting via wan)? Also I would recommend you install webmin for a gui, [http://www.webmin.com/](http://www.webmin.com/)

Has a .deb file for you.

I connect using putty, so try that.

---

### Post by rabidityfactor on 2009-10-02
Oh I havn't checked if the ports are forwarded. Which port is that? 22? 

How come i cant ping the static IP?

---

### Post by Lars Noodén on 2009-10-02
> **rabidityfactor said:**
> Oh I havn't checked if the ports are forwarded. Which port is that? 22? 

How come i cant ping the static IP?

That might be an indication of the cause of not being able to log in.  

Check if sshd is running on the host (117.240.10.210):

pgrep -l sshd

Check if sshd_config is set to listen to your address:

sudo grep ListenAddress /etc/ssh/sshd_config

That should either be commented out or list your IP number.


---

On the client, ping the host (117.240.10.210):

ping -c 3 117.240.10.210;

You may need to open that part of the firewall using IP Tables

Then verify that sshd is accessible:

sudo scanssh -s ssh -n 22 117.240.10.210

---

Once both of those are solved you can worry about how access machines inside the LAN.

---

### Post by rabidityfactor on 2009-10-07
Ok I have forwarded the ssh port on the router.
I'am able to connect to the server using Places->Connect to Server. But I'm not able to do it via terminal.

When I type
ssh name@117.2....: port_no
I get an error saying 'ssh: Could not resolve hostname 117...'

---

### Post by Bachstelze on 2009-10-07
You must use

sss user@host -p port

---

### Post by rabidityfactor on 2009-10-07
Yay! I got it working..

The command syntax i typed in was wrong..

I did
```
ssh -l username 117.240.10.210 -p port_no
```
and it worked.

Thankyou all for heping me out.

---

### Post by rabidityfactor on 2009-10-07
> **Bachstelze said:**
> You must use

sss user@host -p port

Thanks a lot, but I had already just figured it out.

---

