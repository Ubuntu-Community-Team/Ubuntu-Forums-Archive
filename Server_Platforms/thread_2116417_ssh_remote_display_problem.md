---
title: "ssh remote display problem"
date: 2013-02-15
forum: Server Platforms
---

### Post by francesco_ljw on 2013-02-15
I use ssh to log onto the server from my local desktop.

The local machine is running ubuntu12.04 with OpenSSH_5.9p1
The server runs centos4.9 with OpenSSH_3.9p1

I am using the following login command
ssh -X user@server (also tried -Y)

The problem is, after log onto the server using ssh, I cannot open GUI or any display on the server.

For instance
----------------------------------------
xclock
Error: Can't open display: localhost:18.0
----------------------------------------
emacs
emacs: Cannot connect to X server localhost:18.0.
Check the DISPLAY environment variable or use `-d'.
----------------------------------------
xhost
xhost: unable to open display "localhost:18.0"
----------------------------------------

Besides,
1. I can open remote display on other servers within the LAN of the problematic server, so my local X server should be working.
2. Other users of the server also cannot open remote display from my computer.
3. Using ssh + x-window in windows could open remote display on the server.

I have been really confused by the problem for months and have tried many possible solutions I googled, however, still could not get it solved. I have been a ubuntu user for several years and would really not like to switch back to windows because of this problem.

Thanks in advance for all your help!

---

### Post by hawkmage on 2013-02-15
Usually the command to enable X tunneling is:
```
ssh -X servername
```

---

### Post by francesco_ljw on 2013-02-15
Yes, this is exactly what I am doing ... 
ssh -X user@server

Unfortunately it does not work ...

> **hawkmage said:**
> Usually the command to enable X tunneling is:
```
ssh -X servername
```

---

### Post by hawkmage on 2013-02-15
You may want to check the /etc/ssh/sshd_config amd make sure that you have the line"X11Forwarding yes"

---

### Post by francesco_ljw on 2013-02-16
Yes I have checked and enabled it on the server.

> **hawkmage said:**
> You may want to check the /etc/ssh/sshd_config amd make sure that you have the line"X11Forwarding yes"

---

### Post by volkswagner on 2013-02-16
You may also want to search sshd_config on the CentOS machine for:

```
X11UseLocalHost no
```

If it is there and set to "yes", change it to "no" or try adding the line if it does not exist.

---

### Post by francesco_ljw on 2013-02-16
It works !!! Thanks so much @volkswagner and @hawkmage , your helps are really important to me !

> **volkswagner said:**
> You may also want to search sshd_config on the CentOS machine for:

```
X11UseLocalHost no
```

If it is there and set to "yes", change it to "no" or try adding the line if it does not exist.

---

### Post by markbl on 2013-02-17
> **francesco_ljw said:**
> It works !!!
If changing that X11UseLocalHost to "no" fixes your problem then you are not even using ssh to tunnel your X connection. You have not fixed the problem, you have just bypassed it (insecurely).

---

### Post by francesco_ljw on 2013-02-18
Thanks a lot! How is X connection being tunneled in this way? Also, is there a method to fix the problem rather than bypassing it? 

Thanks again.

> **markbl said:**
> If changing that X11UseLocalHost to "no" fixes your problem then you are not even using ssh to tunnel your X connection. You have not fixed the problem, you have just bypassed it (insecurely).

---

### Post by markbl on 2013-02-18
> **francesco_ljw said:**
> Thanks a lot! How is X connection being tunneled in this way?


It is not being tunnelled at all. X is just connecting directly from client to server unencrypted over the network as X was originally designed. The ssh session may as as well be an rsh session.

> 
Also, is there a method to fix the problem rather than bypassing it?

Sorry, I have no idea. From your facts stated here it seems an odd problem. I'd use netstat to check that both ends are listening on the correct X ports etc.

---

### Post by hawkmage on 2013-02-19
By setting X11UseLocalHost to no you are still using tunneling but it is less secure since another system could use this tunnel.

If you have the X11UseLocalHost either remarked out or set to yes what do you have in your environment variable for DISPLAY?  

Also are you using IPTables?  If so are you allowing connections to/from the lo interface?

---

### Post by francesco_ljw on 2013-02-19
Thanks very much for the help. 

I am able to do my work on the server, although under platform config ... will try to fix this as soon as I could.

Thanks again @markbl

> **markbl said:**
> It is not being tunnelled at all. X is just connecting directly from client to server unencrypted over the network as X was originally designed. The ssh session may as as well be an rsh session.


Sorry, I have no idea. From your facts stated here it seems an odd problem. I'd use netstat to check that both ends are listening on the correct X ports etc.

---

### Post by francesco_ljw on 2013-02-19
Thanks again for your kind response.

With X11UseLocalHost=NO, I have the DISPLAY as 
[COLOR="red"]declare -x DISPLAY="***ServerIpAddr***:20.0"
[/COLOR]

With X11UseLocalHost=YES, I have the DISPLAY as 
[COLOR="red"]declare -x DISPLAY="localhost:20.0"
[/COLOR]

I am using IPTABLES in the server which has been setup by previous admin. I did the following operation

[COLOR="Red"]cat /etc/sysconfig/iptables | grep 'lo' 
[/COLOR]

and get the response as below.

-A RH-Firewall-1-INPUT -i lo -j ACCEPT

Is just this rule sufficient to allow lo connection?

Thanks in advance.

> **hawkmage said:**
> By setting X11UseLocalHost to no you are still using tunneling but it is less secure since another system could use this tunnel.

If you have the X11UseLocalHost either remarked out or set to yes what do you have in your environment variable for DISPLAY?  

Also are you using IPTables?  If so are you allowing connections to/from the lo interface?

---

### Post by hawkmage on 2013-02-19
That all looks fine.  Have you tried running ssh -vv -X user@server to enable the ssh debug output?

I just looked back at the versions of OpenSSH you are using and the on the server is over 8 years old.  There may very well be a incompatibility between the new on on Ubuntu and the one on the CentOS 4.9 server.  If at all posable whoever is responsable for the server should look into updating since CentOS 4.* well past its EOL date.  

I am downloading an install ISO for CentOS 4.9 and will see what I can find out once it is installed.  But the download is very slow.

---

### Post by francesco_ljw on 2013-02-22
Thanks @hawkmage, as always. Sorry for my late response as I was offline in the past several days... I agree with you that it might be the version problem which would induce compatibility issue. I have talked with another administrator and we would probably start upgrading it and see if the problem would be fixed then.

Also I have tried your suggestion by running ssh -vv -X user@server, and I grep 'X' with the following output 

debug2: x11_get_proto: /usr/bin/xauth  list :0.0 2>/dev/null
debug2: channel 0: request x11-req confirm 1
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: X11 forwarding request accepted on channel 0

Is there anything abnormal in the above?

Thanks again.

> **hawkmage said:**
> That all looks fine.  Have you tried running ssh -vv -X user@server to enable the ssh debug output?

I just looked back at the versions of OpenSSH you are using and the on the server is over 8 years old.  There may very well be a incompatibility between the new on on Ubuntu and the one on the CentOS 4.9 server.  If at all posable whoever is responsable for the server should look into updating since CentOS 4.* well past its EOL date.  

I am downloading an install ISO for CentOS 4.9 and will see what I can find out once it is installed.  But the download is very slow.

---

