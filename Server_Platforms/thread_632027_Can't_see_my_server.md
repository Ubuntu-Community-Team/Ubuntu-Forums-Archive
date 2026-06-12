---
title: "Can't see my server?"
date: 2007-12-05
forum: Server Platforms
---

### Post by e1ektrob0y on 2007-12-05
I have just installed ubuntu 6.06 server and am having trouble locating the server from my main box (ubuntu 7.10)
I am pretty much a server noob but i though SSH or Samba would be the way to go but it doesnt seem to work so far:( 
Is it a simple matter of just clicking Places>connect to server? Or is there something I'm missing?
Thanks...:)

---

### Post by e1ektrob0y on 2007-12-05
I have installed SSH on both machines and I now realize all i need is to configure SSH...Can someone point me in the right direction here? Thanks:)
The server is now visible from my Gutsy box but when i click on it, nothing seems to be there i think there are permission issues etc...

---

### Post by DDuong on 2007-12-05
Hello :)

So are you trying to SSH into the machine by using the terminal?  Or are you trying to access the network folder on your server?

---

### Post by e1ektrob0y on 2007-12-05
Yes i am trying to ssh into the machine using the terminal

---

### Post by DDuong on 2007-12-05
Ok,

You mentioned that you have installed Ssh on both machines.  To make sure the daemon is running on the server, do the following:

> 
ps -eaf  | grep -i ssh


If you see the following in the list, then you have the ssh daemon running (aka sshd)

> 
/usr/sbin/sshd


If that's the case, then on your gutsy pc, do the following:

> 
ssh <your server ip> -l <username>


**NOTE:  That is a lower case L **

---

### Post by e1ektrob0y on 2007-12-05
i get this 
```

root 3795 1 0 19:59? 00:00:00 /usr/sbin/sshd

ben 3935 3881 1 2 21:12 tty1 00:00:00 grep -i ssh

```

Also, how do i find out the IP of the server?

---

### Post by DDuong on 2007-12-05
If you are on your server, type:

> 
ifconfig


And you should see like eth0 with the ip address of your server.  Kinda like this:

> 
david@ubuntu:~$ ifconfig

eth0   Link encap:Ethernet  HWaddr 00:0C:29:0B:C5:73
          inet addr:172.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe0b:c573/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8029826 (7.6 MB)  TX bytes:5263052 (5.0 MB)
          Interrupt:16 Base address:0x1400


As you can see, the ip address in my example is 172.168.2.10

---

### Post by e1ektrob0y on 2007-12-05
Ok cool, thanks :) I assume this means im logged into the server then?
```
ben@ben-desktop:~$ ssh 192.168.1.4 -l ben
The authenticity of host '192.168.1.4 (192.168.1.4)' can't be established.
RSA key fingerprint is
Are you sure you want to continue connecting (yes/no)?: yes
Warning: Permanently added '192.168.1.4' (RSA) to the list of known hosts.
ben@192.168.1.4's password: 
Linux fileserver 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Dec  5 19:59:41 2007
ben@fileserver:~$ 
```
How can i now save files to the server from my pc? when i go into Places>Network>filserver, it is blank? All i really want to do is save files on the server...
p.s thanks and sorry for all the dumb questions im a noob

---

### Post by DDuong on 2007-12-05
Yep!  You are on your server now!  congrats!!  Keep a look out for this "ben@fileserver:~$".  That will tell you that you are on your file server.  

If you want to get back to your machine, you just type exit till you are back to your prompt.

BTW, having ssh enabled on your server is not needed in order to enable file sharing on your server. However, it's a great tool to get into your server and play with it from your desktop without jumping around from one monitor to another :)

> 
How can i now save files to the server from my pc? when i go into Places>Network>filserver, it is blank? All i really want to do is save files on the server...


I am not on my machine at the moment (at work) so I am unable to assist you at this point.  But check this video out and see if it can assist you.

[http://lloydpuckitt.wordpress.com/2007/10/10/how-to-file-sharing-with-ubuntu-using-samba/](http://lloydpuckitt.wordpress.com/2007/10/10/how-to-file-sharing-with-ubuntu-using-samba/)

> 
p.s thanks and sorry for all the dumb questions im a noob


hehe don't worry about it and you're welcome.  I'm here to help :)  And the community will also help you out too :)

Keep in mind, there is no such thing as a stupid question :)

---

