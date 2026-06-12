---
title: "ssh server not working, but &quot;ssh localhost&quot; works"
date: 2009-08-17
forum: Server Platforms
---

### Post by kangyu29 on 2009-08-17
I have one computer(computer A) with openssh-server installed, but other computers(computer B and C) in my home cannot ssh to it. They all connected to internet through a router.

computer-A: ubuntu 9.04, has openssh-server
computer-B: ubuntu netbook remix
computer-C: Centos 5, has openssh-server

A and B can ssh to C, but B and C cannot ssh to A. They all can ssh to outside ssh-servers(eg. a server at school).

The problem seems on A. I have re-installed ssh server, and tested with "ssh localhost". Everything went well, but still, cannot ssh to A from B and C.

Does anyone know what is going on here?

---

### Post by SoftwareExplorer on 2009-08-17
Are you using IP addresses or names? My computers sometimes don't like names and want IP addresses.

---

### Post by koenn on 2009-08-17
> **kangyu29 said:**
> 
Does anyone know what is going on here?
Yes, most likely.

---

### Post by jfmanamtr on 2009-08-17
Also, can B & C ping A (by IP or by name)? 

~John

---

### Post by jdakhayman on 2009-08-17
You can login locally, but not from the internet? Then it sounds like you may need to  forward port 22 to your server address in your router.

---

### Post by Rhubarb on 2009-08-17
> **kangyu29 said:**
> The problem seems on A. I have re-installed ssh server, ...

Yes, I know of this problem.

Your client computers (B and C) still have a fingerprint (or key, or whatever they're called) that you accepted when you first SSHed to computer A before you re-installed it.
Because you have since re-installed computer A, the fingerprint has changed - so your client SSH computers (B and C) get a fingerprint mismatch and will hence terminate the SSH connection attempt.

The easiest way to fix this up (though it's probably not the most elegant), is to simply delete the contents of your ~/.ssh directory on computers B and C.  I would recommend you make a backup of your ~/.ssh directory first, just in case.
Then for every client ssh connection attempt you make on computers B and C to new SSH servers, you will be prompted to accept the fingerprint / key from the SSH server.

- Then everything should work nicely again :)
There may well be a more elegant way to do this, that does not delete the fingerprints / keys from other ssh server's you've previously connected to.

---

### Post by jfmanamtr on 2009-08-17
> **jdakhayman said:**
> You can login locally, but not from the internet? Then it sounds like you may need to  forward port 22 to your server address in your router.

@jdakhayman: I think he is doing the SSH internally. He has the 3 PCs (A, B & C). A & B can ssh to C, but C & B can't ssh to A. A, B & C can ssh to a PC outside the home. 

Do you run any firewall software on PC A? Cause that also will cause troubles with incoming ssh.

~John

---

### Post by koenn on 2009-08-17
wouldn't if be easier if the OP just posts the exact error (copy paste from the terminal) he gets when he does ssh whoever@whereever in stead of having a bunch of people guessing at what the problem might be and randomly throwing solutions at it ?

---

### Post by kangyu29 on 2009-08-17
> **SoftwareExplorer said:**
> Are you using IP addresses or names? My computers sometimes don't like names and want IP addresses.

I use ip address. something like: 192.168.10.2

---

### Post by kangyu29 on 2009-08-17
> **jfmanamtr said:**
> Also, can B & C ping A (by IP or by name)? 

~John

I didn't try this, I will try it later when I get home and let you know.

---

### Post by kangyu29 on 2009-08-17
> **Rhubarb said:**
> Yes, I know of this problem.

Your client computers (B and C) still have a fingerprint (or key, or whatever they're called) that you accepted when you first SSHed to computer A before you re-installed it.
Because you have since re-installed computer A, the fingerprint has changed - so your client SSH computers (B and C) get a fingerprint mismatch and will hence terminate the SSH connection attempt.

The easiest way to fix this up (though it's probably not the most elegant), is to simply delete the contents of your ~/.ssh directory on computers B and C.  I would recommend you make a backup of your ~/.ssh directory first, just in case.
Then for every client ssh connection attempt you make on computers B and C to new SSH servers, you will be prompted to accept the fingerprint / key from the SSH server.

- Then everything should work nicely again :)
There may well be a more elegant way to do this, that does not delete the fingerprints / keys from other ssh server's you've previously connected to.

I am not sure this is the case. First, I just reinstalled ssh-server on A, but not the OS. Second, I just got my netbook, which is computer B here. This is the first attempt to connect to A(I am 98% sure about this). Anyway, I will try to delete ~/.ssh folder on B to see if it will work. And I will let you know.

---

### Post by kangyu29 on 2009-08-17
> **jfmanamtr said:**
> @jdakhayman: I think he is doing the SSH internally. He has the 3 PCs (A, B & C). A & B can ssh to C, but C & B can't ssh to A. A, B & C can ssh to a PC outside the home. 

Do you run any firewall software on PC A? Cause that also will cause troubles with incoming ssh.

~John

OK? I don't remember if I had firewall set up on A or not. Can you tell me how can I check this? 

I have another question maybe related to this(firewall) if I did have firewall. I used to have freenx client on A, and server on my computer at school, the computer I am using right now. It was working great. But I don't remember when, it started have problems. After typed user name and password, the pop-up window say something like "establish connection" and then "download desktop". And then the desktop will appear, but disappear right way. From then, I cannot have freenx working again.

Thanks for any help.

---

### Post by kangyu29 on 2009-08-17
> **koenn said:**
> wouldn't if be easier if the OP just posts the exact error (copy paste from the terminal) he gets when he does ssh whoever@whereever in stead of having a bunch of people guessing at what the problem might be and randomly throwing solutions at it ?

Sorry for confusing people here. I have thought about doing this actually. When I run ssh whoever@whereever, the command just hang there without any error. If I do ssh -v whoever@whereever, it will tell me "connecting to 192.168.10.2" and no error messages either.

---

### Post by koenn on 2009-08-17
> **kangyu29 said:**
> When I run ssh whoever@whereever, the command just hang there without any error. If I do ssh -v whoever@whereever, it will tell me "connecting to 192.168.10.2" and no error messages either.


OK, my money is on : a firewall with "DROP", although I wouldn't rule out a network problem (-> ping ?)

---

### Post by koenn on 2009-08-17
> **kangyu29 said:**
> OK? I don't remember if I had firewall set up on A or not. Can you tell me how can I check this? 

jfmanamtr seems offline, so I'll have a go:

run this
```
iptables -L -n
```
It's probably best you just post the output (in CODE tags), but if you don't want to do that, look for policies with DROP (or DENY), or rules with port 22 and DROP (or DENY)

---

### Post by kangyu29 on 2009-08-17
> **koenn said:**
> jfmanamtr seems offline, so I'll have a go:

run this
```
iptables -L -n
```
It's probably best you just post the output (in CODE tags), but if you don't want to do that, look for policies with DROP (or DENY), or rules with port 22 and DROP (or DENY)

Again, I will try it when I get home tonight. If it is a firewall issue, what should I do to fix it.

BTW, I did change the port to other number than 22 yesterday by editing /etc/ssh/sshd_config file and restarted ssh-server, didn't make any differences.

---

### Post by koenn on 2009-08-17
> **kangyu29 said:**
>  If it is a firewall issue, what should I do to fix it.
depends on the issue, and the goals to which you've configured your firewall. You will probably need to change whatever setting or combination of settings there is in your firewall configuration that prevents the ssh client from connecting to the ssh server or otherwise hinders communication between the server and the client.


find the problem first, then fix it. The other way around doesn't work.

---

### Post by SoftwareExplorer on 2009-08-17
> **kangyu29 said:**
>  BTW, I did change the port to other number than 22 yesterday by editing /etc/ssh/sshd_config file and restarted ssh-server, didn't make any differences.
If you changed the port you have to run the command like this:```
ssh user@computerb -p <portnumberhere>
```

---

### Post by kangyu29 on 2009-08-17
> **SoftwareExplorer said:**
> If you changed the port you have to run the command like this:```
ssh user@computerb -p <portnumberhere>
```

yes, I did that. in fact, i had to do this all the time to ssh to my school because of VPN blocked 22 cause I didn't have a working VPN.

---

### Post by kangyu29 on 2009-08-17
> **koenn said:**
> jfmanamtr seems offline, so I'll have a go:

run this
```
iptables -L -n
```
It's probably best you just post the output (in CODE tags), but if you don't want to do that, look for policies with DROP (or DENY), or rules with port 22 and DROP (or DENY)


Looks like it is a firewall issue. Bellow is the result after ran "sudo iptables -L -n". 

I don't really need a firewall, if there is no easy way to fix it, I wouldn't mind just remove it. I don't know when and how I installed this firewall. Could anybody tell me how to remove it if this is the case?

BTW, I did try to ping A from B without any problem. I guess it doesn't matter now.

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:138 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:68 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 4 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  224.0.0.0/4          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            224.0.0.0/4         
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         


```

---

### Post by wojox on 2009-08-17
```
iptables --flush
```

```
sudo ufw disable
```

---

### Post by kangyu29 on 2009-08-17
Thanks for all your help. I find a "firewall configuration" from administration menu. and disabled the firewall, now I can ssh to A from B without problem.

Thanks again.

---

### Post by jfmanamtr on 2009-08-18
Awesome. I glad you got that fixed. Sorry about not being online to help you out. I had some troubles at work that prevented my being able to watch the forums.

~John

---

### Post by kangyu29 on 2009-08-18
> **jfmanamtr said:**
> Awesome. I glad you got that fixed. Sorry about not being online to help you out. I had some troubles at work that prevented my being able to watch the forums.

~John

Thanks Jfmanamtr. In fact, I just did a full sync of my files from A to B last night. Works great!

But my freenx is still not working. I will spend a little more time on this tonight.

What a great community!

---

### Post by kangyu29 on 2009-08-18
Alright, freenx is working now. Nothing to do with firewall. The problem was addressed under "Troubleshooting" in this link:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

