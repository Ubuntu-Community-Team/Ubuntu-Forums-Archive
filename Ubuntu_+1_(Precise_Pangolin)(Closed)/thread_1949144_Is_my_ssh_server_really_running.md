---
title: "Is my ssh server really running??"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Robertjm on 2012-03-29
Hi all,

Today I installed openssh-server so I could connect my laptop to my desktop. However, when I try connecting with bitvise, the connection is refused.

Next, I tried connecting using putty on the same computer that the server is running. Again, it's immediately refused a connection. This was with trying both "localhost" as well as the ip address of the machine. I can ping my ip address, both locally and from the W7 laptop.

I tried changing to a non-standard port, but went back to Port 22 when I had problems.

Here's the thing that's confusing me. After making changes to the config file I tell it to the process to restart. However, this is what happens:

[B][COLOR="Blue"]robertjm@NA:~$ sudo restart ssh
restart: Unknown instance: [/COLOR][/B]

Next I try just to start it:

[COLOR="blue"][B]robertjm@NA:~$ sudo start ssh
[sudo] password for robertjm: 
ssh start/running, process 4121[/B][/COLOR]

As you can see, it assigns me a process. HOWEVER, when I go to my Task Manager and check for that process number, it isn't listed. I'm not killing the terminal window when I go over and open Task Manager so I'm assuming the task isn't dying at that point.

ufw is installed by default, but when I use gUFW it's telling me the firewall is currently off.

As a side note, I have been able to connect with vnc just fine, albeit it's useless since I cannot seem to use the Unity desktop that way.

What am I missing here?

Thanks!

Robert

---

### Post by CharlesA on 2012-03-29
Are you testing 12.04?

You can always check to see if sshd is running by running this:

```
ps aux | grep sshd
```

```
netstat -l | grep ssh
```

---

### Post by cariboo on 2012-03-29
To add to what CharlesA posted, if you use:

```
ssh -vv user@server
```

The output should tell you what the problem is.

---

### Post by sanderj on 2012-03-29
> **CharlesA said:**
> Are you testing 12.04?

You can always check to see if sshd is running by running this:

```
ps aux | grep sshd
```

```
netstat -l | grep ssh
```

I think that last command will only show output if ssh is running on the standard port (or, more correct: on the port that is defined by /etc/servcies). So not the the port of sshd has been manually changed in its config.

---

### Post by Robertjm on 2012-03-29
Thanks guys. Yes, 12.04 64bit here. These were all done in terminal on the same Ubuntu machine running the server.

Robert


[B][COLOR="DarkRed"]robertjm@NA:~$ ps aux |grep sshd
robertjm  4386  0.0  0.0   9376   936 pts/0    S+   12:49   0:00 grep --color=auto sshd[/COLOR][/B]

[COLOR="SeaGreen"][B]robertjm@NA:~$ netstat -l|grep ssh
unix  2      [ ACC ]     STREAM     LISTENING     12853    /tmp/keyring-lBBn1z/ssh
unix  2      [ ACC ]     STREAM     LISTENING     10091    /tmp/ssh-GzQcEElr2150/agent.2150[/B][/COLOR]

[COLOR="Blue"][B]robertjm@NA:~$ ssh -vv robertjm@110.0.0.6
OpenSSH_5.9p1 Debian-4ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 110.0.0.6 [110.0.0.6] port 22.
debug1: connect to address 110.0.0.6 port 22: Connection refused
ssh: connect to host 110.0.0.6 port 22: Connection refused[/B][/COLOR]

---

### Post by CharlesA on 2012-03-29
> **sanderj said:**
> I think that last command will only show output if ssh is running on the standard port (or, more correct: on the port that is defined by /etc/servcies). So not the the port of sshd has been manually changed in its config.
Good question. You are probably right because the service definitions are static (or at least I think they are static...)

You could always run this:

```
sudo netstat -nlp | grep sshd
```

EDIT: @Robertjm: Yeah, sshd isn't running. What happens if you try to start it?

```
sudo service ssh start
```

---

### Post by sanderj on 2012-03-29
I would say the ultimate test to see if ssh is running is this (example):

```
sander@R540:~$ sudo restart ssh
ssh start/running, process 19126
sander@R540:~$ 
sander@R540:~$ sudo netstat -lapon | grep -i listen | grep -vi listening | grep 19126
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      19126/sshd       off (0.00/0/0)
tcp6       0      0 :::22                   :::*                    LISTEN      19126/sshd       off (0.00/0/0)
sander@R540:~$
```

So restart ssh, then see if the process id is in the list.

HTH

---

### Post by sanderj on 2012-03-29
And as sshd is not running, just start it from the command line

```
sudo /usr/sbin/sshd -D -d
```

-D means "do NOT become daemon"
-d means "debug"

Post the output here ...

---

### Post by Robertjm on 2012-03-29
When I tried restarting sshd it says I have a bad configuration option on Line 52

Checking the config file I have (lines 51&52):

#PasswordAuthentication yes
\

I honestly don't remember putting that in there. I did add AllowUsers and changed the AllowEmptyPasswords to No.

Anyways, once that was commented out, it allowed me to connect on the local machine, albeit it squawked about not having a key. Will test from my laptop later.

Thanks again!

Robert

---

### Post by CharlesA on 2012-03-29
Take out the \ and try starting sshd again.

---

### Post by effenberg0x0 on 2012-03-29
I have just tested that openssh-server works out of the box in a PP Beta2 install at a VM. It's pretty much standard install, no real work or tweaking needed. The only things I did were:

```

sudo apt-get remove --purge openssh-server openssh-client (I didn't know if it was installed by default and was feeling lazy to check)
sudo mv /etc/ssh /etc/ssh.disabled (because I wanted it to start with fresh settings)
sudo apt-get install openssh-server openssh-client
sudo service ssh stop
sudo nano /etc/ssh/sshd_config
```Change SSH port to another one (default 22 is asking to have it flooded with requests continuously. In this example I'll use 64022)
```
# What ports, IPs and protocols we listen for
Port 64022
sudo service ufw stop
sudo ufw allow from 192.168.1.0/24 to any port 64022 
sudo service ufw start
sudo service ssh start
ssh -p 64022 ahsl@localhost
``` Enter Login/passwd
Success.

Then if you want to allow external (out of your lan) access, you'd have to change UFW rules:
```
sudo ufw allow 64022
sudo service ssh restart
```Then access your router and PortForward request to YourWanIP:64022 to YourServerLanIP:64022
But, if you're gonna do it, at least use encryption keys.

---

