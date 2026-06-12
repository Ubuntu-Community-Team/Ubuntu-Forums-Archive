---
title: "Trouble shooting sshd/ssh?"
date: 2009-05-23
forum: Server Platforms
---

### Post by delta_charlie on 2009-05-23
Hi all, I have been trying all day to get sshd to let me log in but no go so far.

sshd is running on a new install of Ubuntu server 8.10 and if I try to log in to localhost from the keyboard on the server it lets me in with the normal user and password I setup on the server.

The problem comes up when I try to login from a second compputer on my LAN. I can ping the server but when I try to use ssh from the second computer I get: Permission denied, please try again.

I need to take a break from this problem and was hoping for some ideas.

Thanks, DC

---

### Post by HermanAB on 2009-05-23
Open port 22/tcp in your firewall.

---

### Post by gombadi on 2009-05-23
A firewall would not be my first guess - They normally result in connection refused if they reject the packet or connection timed out if they drop the packet. As you are getting "Permission denied, please try again" it means you are making it to the sshd server.

Have a look in /var/log/auth.log to see what error it is logging when you connect.

---

### Post by delta_charlie on 2009-05-24
> **gombadi said:**
> --cut--Have a look in /var/log/auth.log to see what error it is logging when you connect.

Hi HermanAB and gombadi, thanks for the replies. After some rest I'm ready to try and figure this thing out. Here is some more info, for testing I do not have the server on the internet and the firewall is off.

I did find some clues in the auth.log file: "Invalid user delcha"

(The server with sshd is setup with delta as the main login and the netbook that I'm running ssh on has delcha as the main login).  

So it looks like I need to figure out how to configure users on sshd. So far I have not found the correct keywords for google. My goal is to set up sshd to use RSA but every howto I have found so far relies on first having basic password access.

Perhaps I simply need to add the user delcha to the server?

Thanks, DC

---

### Post by FrankT-Qc on 2009-05-24
You may do two things : either add delcha as a user on the server or log into the server as the user delta

try :
```
ssh delta@ServerName
```

have fun

---

### Post by mellowd on 2009-05-24
If you're trying to SSH from a windows box try this:

```
telnet server_ip 22
```

Yes I know you're not trying to telnet, but if the port is open then you'll get something like this:

```
SSH-2.0-OpenSSH_3.9p1
```

If you get this:

```
telnet server_ip 22
Connecting To server_ip...Could not open connection to the host, on port 22: Connect failed
```

then you know that it's your firewall, moblock, iptables or something else blocking the connection completely

---

### Post by delta_charlie on 2009-05-24
Hi all, I made some progress. First I set up tail -f /var/log/auth.log on the server in a terminal.

Then tried to long in using my Xbuntu netbook and kept getting Failed password for delta from 192.168.2.2 in the auth.log on the server.

Here is some of the screen from the netbook/client:

delcha@slaptop:~$ telnet 192.168.2.3 22
Trying 192.168.2.3...
Connected to 192.168.2.3.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
Connection closed by foreign host.
---
delcha@slaptop:~$ ssh delta@Amoeba

ssh: connect to host Amoeba port 22: Connection timed out

---
delcha@slaptop:~$ ssh delta@192.168.2.3
delta@192.168.2.3's password: 
Permission denied, please try again.
---
delcha@slaptop:~$ ssh -l delta 192.168.2.3
delta@192.168.2.3's password: 
Permission denied, please try again

At this point I was starting to think sshd does not like the user delta so I made a new test user called test and added:

AllowUsers delta test

to the /etc/ssh/sshd_config file and restarted sshd with:

cd /etc/init.d
./ssh restart

delcha@slaptop:~$ ssh -l test 192.168.2.3
test@192.168.2.3's password: 
Last login: Sun May 24 10:23:02 2009
test@Amoeba:~$

It is starting to work! :-)

delcha@slaptop:~$ ssh -l delta 192.168.2.3
delta@192.168.2.3's password: 
Permission denied, please try again.

user delta still does not work and I still have the Failed password for delta from 192.168.2.2 in the auth.log on the server.

Perhaps it has something to do with default security settings not allowing access to the main login on the server.

Glad to get at least part of the problem sorted out.

Thanks, DC

---

### Post by albinootje on 2009-05-24
> **delta_charlie said:**
> 
user delta still does not work and I still have the Failed password for delta from 192.168.2.2 in the auth.log on the server.

Are you sure the password is correct ?
Good that you made that other user, and made that work!

By the way, you can use :
```

ssh -v test@your_ssh_server

```
That's easier to type and easier to remember imho.

And something similar like this :
sftp://test@your_ssh_server works in Nautilus
And : fish://test@your_ssh_server works in Konqueror

As you can imagine ```
 sftp://-l test your_test ssh_server
``` would not work in Nautilus ;-)

---

### Post by delta_charlie on 2009-05-25
> **albinootje said:**
> Are you sure the password is correct ?
---cut---
Hi all, got it sorted out and it turned out to be the password after-all.

Did not notice until this morning that the keyboard on the server is not working correct or maybe I do not have is setup correct. The problem had to do with the CAP key, when I push it the Caps light comes on and if I push it again it goes off. Seems like it is working fine - WRONG! The password I used has uppercase letters in it so I would push the CAP key and enter the password and of course the password does not print so I go on thinking the password has uppercase letters in it. As it turned out the CAP key was not doing anything so the password was really lowercase letters. Then when I used the Xubuntu netbook to try and ssh into the server the CAP key on it was working and the password would end up wrong.

That one got me good ;)

I learned a good lesson - if you are having password troubles check the keyboard and make sure it is really outputting what it should.

Later, DC

---

