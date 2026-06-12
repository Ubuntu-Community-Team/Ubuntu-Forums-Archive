---
title: "SSH Downgrade via sshd_config"
date: 2008-02-24
forum: Server Platforms
---

### Post by mdeshpande on 2008-02-24
Hi, I did a apt-get on openssh-server and installed sshd, the default value in sshd_config is protocol 2 , which means only version 2 is supported by default in ubuntu fiesty. posts on the internet mentioned adding ",1" to that line in sshd_config, and restarting using "/etc/init.d/ssh restart" , i did all of that , but ' could not load host key' message appears, i looked online and i am told to use ssh-keygen to generate rsa key pair, i did that as well and restarted the server. But alas ! when i connect with v1 from a client with "ssh -1 username@server" , protocol mismatch 1 vs 2 appears. how can i simply force the sshd to operate at v1 ? i have been looking online at several places, they all seem to suggest the above things, but i just cant get it going, joined the ubuntu forum today, hoping to find a solution from the gurus :) 

put simply , i want a v1 server.

telnet localhost 22 - SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1.1
init.d/ssh restart - disabling proto v1 , could not locate host key.

If somebody can post the relevant sshd_config file also that would be of great help .

Regards,
Manoj Deshpande
Graduate Assistant
Georgia Insitute of Technology

---

### Post by Mr. C. on 2008-02-25
> 
could not locate host key.


This is pretty clear that the server is *not* setup correctly !

Give clear evidence of exactly which SSH files you created (full path names, how you created them, etc.) for the SSH server to operate in V1 mode.  You can also ramp up the server's verbosity to get more detailed log levels.  Run it manually with -D and -d (man sshd).

Both client and server negotiate protocols: both must be correctly configured.

MrC

---

### Post by wirelessmonkey on 2008-02-25
ssh  v1 is easily exploitable, I suggest that you use only version 2 unless you have a specific need for v1.

---

### Post by mdeshpande on 2008-02-25
Thanks for the replies

@ Mr C . 
I really havent touched many files, i have done only these things

1. apt-get install openssh-server
2. edit /etc/ssh/sshd_config , to change the line which says "protocol 2" , it now reads "protocol 2,1" . 
3. /etc/init.d/ssh restart .


i had used -vvv mode on client , not on the server though, do i need to run sshd exclusively ? once i install openssh-server on my machine, can i not assume all incoming ssh requests will be serviced by the server i installed ? please correct me if i am wrong.

@ wireless monkey 

i know v1 is vulnerable, i want to try ettercap on sshv1 :) final goal is to decrypt sshv1.

---

### Post by Mr. C. on 2008-02-25
Ok, I misunderstood; I thought you indicated that you did create keypairs, etc.

See: [http://www.unixguide.net/comments/sun/ssh_installation.shtml/36.shtml](http://www.unixguide.net/comments/sun/ssh_installation.shtml/36.shtml)

Please show exact error messages, not abbreviations.  Otherwise, it is too difficult to diagnose the trouble.  The error messages I see in the source code is:

> Disabling protocol version 1. Could not load host key

The server you installed with service all requests to that port it is listening on.  Using verbose logging on the *client* won't help because the server disabled V1 as it started.

MrC

---

### Post by mdeshpande on 2008-02-25
Thanks for those replies Mr.C . I got it resolved finally, realized a few things. 

1. Added 2 lines in sshd_config , for protocol 1 support. They are

Protocol 1
HostKey /etc/ssh_host_key

2. Generated ssh_host_key pair and put it in etc/ssh using 

ssh-keygen -t rsa1 -f /etc/ssh_host_key -N "" 

3. Restarted the server using 

/etc/init.d/ssh restart

---

### Post by Mr. C. on 2008-02-25
Exactly.

The HostKey line is required for you because your keys are in a non-default location (default: /etc/ssh/ssh_host_key).

Regards,
MrC

---

