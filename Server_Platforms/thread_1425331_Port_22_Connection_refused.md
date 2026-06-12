---
title: "Port 22 Connection refused"
date: 2010-03-08
forum: Server Platforms
---

### Post by Ian McDonagh on 2010-03-08
Setup 
new build running Umbutu 9.10
Mac Running 10.5.8

First off I'm a total noob to Linux systems and I have tried googling everything I can think of to resolve this issue found many people getting similar issues but no one with the exact symptoms and all the suggested fixes thus far have failed.

I am trying to set up ssh server on Umbutu and I believe I have successfully started it with the ((sudo apt-get install ssh)) command. No I'm trying to log onto my Umbutu box from my mac and I constantly get the error 
ssh: connect to host XX.XX.XXX.XX (not the 127.0.0.1) port 22: connection refused
When I try and run the same thing from Umbutu it just jumps to the next line like I hit enter on an empty line.

I have made sure ssh is installed and running on the umbutu system several times and I have the remote login checked on my mac. 
I am at a total loss at this point PLEASE someone help I have been at this two nights straight and have made very little headway.

Thanks in advance.

---

### Post by lindsay7 on 2010-03-08
maybe this will help.  I just set up three computers to share files.

[http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh](http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh)

---

### Post by wirelessmonkey on 2010-03-08
```
 apt-get update
apt-get install openssh-server

```

---

### Post by Ian McDonagh on 2010-03-09
I've already ran the install comands I will try the guide and I'll run the install comands again to confirm

---

### Post by BobVila on 2010-03-09
> **Ian McDonagh said:**
> I've already ran the install comands I will try the guide and I'll run the install comands again to confirm

i think wirelessmonkey was suggesting those particular commands to make sure you installed the ssh SERVER, because your initial post said you entered 'sudo apt-get install ssh'...

---

### Post by joberly on 2010-03-09
Check to make sure sshd is running:

ps aux | grep sshd

Also check to make sure it's listening on the port you want:

sudo netstat -punta

Should have a line similar to:

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      16097/sshd

Where 22 is the port number.

Once those are confirmed, we can move on.


ALSO: Is the machine you are connecting FROM, inside the network, or outside the network? Connection refused will happen if you are either outside of the network and not forwarding ports, or if the firewall is not allowing the connection.

---

### Post by Iowan on 2010-03-09
Firewalls can also be a problem - if you have one running (on either/both machines).

---

### Post by Ian McDonagh on 2010-03-09
When I run the sudo netstat -punta command this is what I get (I think this is what it's supposed to look like)


1095/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      

And when I run ps aux | grep sshd I get this

root      1095  0.0  0.0   5364  1036 ?        Ss   22:25   0:00 /usr/sbin/sshd
ian       2115  0.0  0.0   3044   868 pts/0    S+   22:51   0:00 grep --color=auto sshd


When I run this [FONT=monospace][/FONT]apt-get update I get this (I think this is where the problem lies when I'm trying to access something seeing lock is never good)

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

And this command  [FONT=monospace][/FONT]apt-get install openssh-server gives this 

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I'm totally at a loss here. I don't understand yesterday I was thinking it was an issue on the mac side but now I'm realizing it's an issue on this end and I am out of my depth with this.

---

### Post by lindsay7 on 2010-03-10
It should be sudo apt-get or whatever. You need to use the sudo command first.

---

### Post by Ian McDonagh on 2010-03-10
I'm an idiot once they're connected under the hard drive icon on the mac there's a shared icon. I just click on that click connect punch in my password and hit screen share

---

### Post by Iowan on 2010-03-10
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

