---
title: "Ubuntu Server OpenSSH help"
date: 2008-05-19
forum: Server Platforms
---

### Post by hwang251 on 2008-05-19
I recently installed OpenSSh-server onto Ubuntu Server.
I want to know, how do you know if it works properly?
When you install it, was it suppose to make any folders?
And how do you access it from another computer such as one using Ubuntu Desktop?

---

### Post by 505 on 2008-05-19
From another computer, type in the terminal "ssh user@192.168.1.2"

Substitute user from a valid user on the remote machine, and the IP address with the address of the remote machine. It should ask for a password and your in...

---

### Post by Endwin on 2008-05-19
If you are trying to access it from a windows machine [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") is a good solution, and for file transfer [WinSCP]("http://winscp.net/eng/index.php") is great.

---

### Post by Monicker on 2008-05-19
When it installed you should have seen a message that the server was starting up.

You can verify by doing 

```
ps -ef |grep ssh
```

or

```
sudo netstat -anltp|grep ssh
```


Both of which should show the ssh daemon running.

---

### Post by hwang251 on 2008-05-19
> **505 said:**
> From another computer, type in the terminal "ssh user@192.168.1.2"

Substitute user from a valid user on the remote machine, and the IP address with the address of the remote machine. It should ask for a password and your in...

That doesn't work, how do I know if my server is remote hosting or not, or giving access?

What would the address be if I typed in "ifconfig"?

---

### Post by Monicker on 2008-05-19
> **hwang251 said:**
> That doesn't work, how do I know if my server is remote hosting or not, or giving access?

What would the address be if I typed in "ifconfig"?

Eh?  Starting to sound a tad fishy here.  ;)


If the server is hosted by someone else, ask them if they are allowing inbound ssh connections.  How did you install the ssh server package?

And you should certainly know the ip address of your server.

---

### Post by hwang251 on 2008-05-19
Ok to help give more information.

The server is one which we have complete access to, we set it up.

When ubuntu server was installed, openssh-server option was selected to be installed.

Today I used the command "sudo apt-get install openssh-server"
to try to install the openssh-server again.

Afterwards I did the keygen thing suggested by the documentation.
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

Now I'm trying to test to see if we can connect to this server using another computer using ubuntu desktop

---

### Post by Monicker on 2008-05-19
Did you check for the ssh processes as I mentioned previously? What did you mean exactly when you said it "didnt work"?

The more detail you give, the easier it is for people to help you.

---

### Post by hwang251 on 2008-05-19
> **Monicker said:**
> Did you check for the ssh processes as I mentioned previously? What did you mean exactly when you said it "didnt work"?

The more detail you give, the easier it is for people to help you.

I tried both, for
"ps -ef |grep ssh"
I got
root   4000    1 0 14:56 ?     00:00:00 /usr/sbin/sshd
1000   4120 4053 0 15:49 tty1  00:00:00 grep ssh

And for
"sudo netstat -antlp|grep ssh"
I got
tcp6      0   0 :::22      :::*      LISTEN
4000/sshd

---

### Post by Dr Small on 2008-05-19
Before setting up keys, did you at least try to see if it worked?
```
ssh localhost
```

If you could connect, it means SSH is working.
Then you would just need to open port 22 in Iptables (if you even use Iptables) to allow access to port 22 on the network.

Dr Small

---

### Post by windependence on 2008-05-20
FYI, ssh is usually installed by default on most Linux distributions.

-Tim

---

### Post by Iowan on 2008-05-20
From the info you've given, it would appear ssh is running.  I'm trying to remember what loops I jumped through to get SSH working.  It seems like the ssh client was included and straight forward, but the server (**/etc/ssh/sshd_config**) needed some settings tweaked to allow connection. (I changed default port, for one thing). I may have needed to add hosts/keys in **/etc/ssh_known_hosts**.

Does [this]("https://help.ubuntu.com/community/SSHHowto") help?

---

