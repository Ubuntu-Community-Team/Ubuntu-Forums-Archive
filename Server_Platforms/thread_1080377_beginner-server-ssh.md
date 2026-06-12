---
title: "beginner-server-ssh"
date: 2009-02-25
forum: Server Platforms
---

### Post by anujs on 2009-02-25
hi...I am beginner to ubuntu and linux.

I have installed ubuntu 8.10. "sudo apt-get update" command results in fetch error. I can ping other machines.  How to solve it and its text based environment, no GUI, no packages able to download, its fresh installation. Also, tell me how to access server through ssh.

---

### Post by CrucifiedEgo on 2009-02-25
In order to troubleshoot hte issue, the exact error you're seeing would be really really helpful. As far as ssh, simply do 'sudo apt-get install openssh-server'.  Note though... we'll probably need to fix your apt issue first :)

---

### Post by volkswagner on 2009-02-25
You can ping machines on the network, What about the internet?

```
host google.com
```

```
ping 209.85.171.100
```


What is output of:
```
ifconfig
```


To edit network settings

Create a backup first

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```


To edit the network/interfaces file;
```
sudo nano /etc/network/interfaces
```

You may want to temporarily change "static" to "DHCP" without quotes and restart networking to see if it will connect.

```
sudo /etc/init.d/networking restart
```

---

### Post by anujs on 2009-02-25
thanks for reply.

when i give command "sudo apt-get update" it results into number of lines with "fetch error in [http://security.ubuntu.com......bz2](http://security.ubuntu.com......bz2) or us.archive.ubuntu.com.......bz2"

Also, when i ssh this machine it results into "connection refused"

please help.

---

### Post by anujs on 2009-02-25
thanks for reply.

true..i can ping on network but can't internet. also not required as its campus firewall settings.

but to set my own machine problems are:
when i give command "sudo apt-get update" it results into number of lines with "fetch error in [http://security.ubuntu.com......bz2](http://security.ubuntu.com......bz2) or us.archive.ubuntu.com.......bz2"

Also, when i ssh this machine it results into "connection refused"

please help.

---

### Post by Zanthir on 2010-10-01
For some reason I'm having openSSH-server problems.
 
I installed it. Something like "sudo aptitude install openSSH-server," to install it from CD.
 
Then I should just have to go to my remote machine and type "ssh [EMAIL="user@host:22"]user@host:22[/EMAIL]," right?
 
I've read this before and I just want to double check with someone that it should be this simple. That should work, I should connect.
 
Thanks.

---

### Post by ricerider1 on 2010-10-01
I had to use this for update "  sudo aptitude update && sudo aptitude dist-upgrade  " without the quotes and to ssh its "   username@servername OR ip address , I use ip address myself as, so far, I haven't went public with a domain name yet. In any case I had the same problem a few time and using aptitude worked when apt-get wouldn't for some things. You still need to check output of ifconfig. I am still in diapers on the server thing, but I hope this works for you. You need not state 22, ssh will use port 22 automatically unless you choose another port.

---

