---
title: "ssh and blackberry"
date: 2007-12-19
forum: Server Platforms
---

### Post by maclenin on 2007-12-19
I am trying to establish a connection between a (t-mobile) blackberry curve (8320) and a local (Edgy) server - using ssh.

Note: My ultimate goal is to be able to transfer files to and from the blackberry - using the ssh connection - both locally and remotely.

But first things first....

Background:

A. I have (sudo aptitude) installed openssh-server on the server.
B. I have installed [_midpssh_]("http://www.xk72.com/midpssh/index.php") on the blackberry.
C. I have been using a separate (Feisty) laptop to test ssh configuration issues.
D. All of these components are connected to the same local wireless network.

Status:

1. I AM able to establish an ssh connection to the server from the laptop - using the following:

```
ssh xxx.xxx.x.xxx
```

2. I am NOT able to establish a connection from the blackberry to the server - using midpdssh.

3. When I try to connect to the server (xxx.xxx.x.xxx) from the blackberry, I receive the following error message:

```
Session Error
Writer: Unable to open connection.
```

4. I am attempting my own trouble-shooting and feel that  the issue/answer might reside (perhaps, obviously) either...

a. In the ssh or sshd config settings on the server....
b. In the configuration of midpdssh on the blackberry....

...however, I am not experienced enough to know how it should all look and act - and was wondering if anyone could send along some guidance.

Thanks.

---

### Post by reckless2k2 on 2007-12-19
i could never get that program to work right. i know by default it uses protocol 1 and you need to change it to 2 because i think ubuntu only allows 2. 

either way it's going to be a hassle. i could not ever get ssh to work from blackberry while others say it works. 

it's in the config on the blackberry though and not your box unless you want to use protocol 1 and 2.

---

### Post by bmathis on 2007-12-19
I have the program working from both a Nextel 7520 as well as my new Verizon 8830. My SSH settings:> Prefer: SSH2 (SSH1 has worked as well)
Public Key: Off
Store Session Key: On
Session Key Size: 512 and in the session settings make sure its set to SSH and uses TCP/IP as the connection type, unless youre using a BES server.

Blackberries rock! :guitar:

---

### Post by maclenin on 2007-12-20
Thanks, **reckless2k2** and **bmathis**....

A. Per your suggestions, I have made (and tested) the following **mods.** to the blackberry's midpssh SSH / Settings...

Prefer: **SSH2**
Public Key: **Off**
Store Session Key: **On**
Session Key Size: **512**

...to no avail!

B. As I continue to troubleshoot, and with reference to the "**detail**" I use when I initiate a successful ssh connection to the server from the laptop...

```
laptop@laptop:~$ ssh **xxx.xxx.x.xxx**
```

...and receive a password prompt...

```
**server@xxx.xxx.x.xxx**'s password:
```

...and then connect to...

```
**server@server**:~$
```

...I wonder about the accuracy of the blackberry's current midpssh Edit Session settings:

Alias: **xxx.xxx.x.xxx**
Host: **xxx.xxx.x.xxx**
Type: SSH
Authentication (SSH only):
Username: **server**   [Note: I have also tried: **server@xxx.xxx.x.xxx**]
Password: *********
Connection Type: TCP/IP

Do these settings look accurate based on the **"detail"** I use to log in via the laptop?

C. I have also read the there are **settings** in sshd_config that I might want to mess with (and, which I am a bit reluctant to mess with, because I am able to connect via a laptop - without any trouble.  I.e. if it ain't broke....), namely:

**LoginGraceTime** [Note: I receive the connection error well before the default time (120) is reached.]
**PubkeyAuthentication** [Note: This is set to "Off" in midpssh (based on your suggestion), where it's set to "yes" (by default), in the sshd_config file - might this cause problems?]

Any other ideas re: stuff to toggle/test, or resources (in addition to the man pages) that might help me learn how to fine tune/configure my set-up and ask relevant questions?

Anyway, I really appreciate your help and suggestions!

---

### Post by bmathis on 2007-12-20
My sshd_config file is all defaults and everything works for me. I know that T-Mobile has, in the past, blocked and/or limited ports. It might be a good idea to call tech support and make sure that you can tunnel data through that port on their networks, if not, you can try changing which port ssh listens on to a higher port number.

---

### Post by maclenin on 2007-12-24
I have a feeling t-moblie port blockage might be the problem - as I have seen mention of it, elsewhere...and, as you say - you get midpssh to work and with default sshd settings (with Verizon).... I'll investigate further (re: t-mobile) and see what i find....

When you mention modifying the ssh port - is that done via the sshd_config file?

Thanks, again.

---

### Post by reckless2k2 on 2008-01-11
i got this working on my new blackberry curve (at&t). because you have a curve as well even though it's on t-mobile, it should work. 

under sessions:

```
alias: yadda
host: yadda.com
type: SSH
username: yourusername
password: yourpassword
publickey: off
connection type: default
```

under settings > SSH

```
prefer: SSH2
publickey: on
store session key:on
sessionkeysize: 1024

```

you MAY be able to use 512 key size but i'm not sure. regardless, i got this to work and i think it was because of the combo i used. 

good luck.

---

### Post by maclenin on 2008-01-15
Thanks, reckless2k2, I'll give it a whirl and let you know how it goes....

---

### Post by WadiJM on 2008-02-04
Hi All, I don't know if I'm in the rigth place. Anyway, I'm developing some apps for Nextel devices. The thing is that I have to use a Nextel conected to my computer to comunicate with other nextels, cause it only allows the usage on a  VPN network and this is a wolr around so I can test the app. So, I have to conect a Nextel phone, dial, and it should give an IP. And other phones should send packet data to that ip....Did anyone get things to work on linux?I only make it work in windows. Any help would be appreciated.
THanks in advance,
Wadi

---

### Post by maclenin on 2008-02-05
**WadiJM:**

This is probably the correct forum - though, you'd probably want to start your own/separate thread - to highlight your issue - good luck!

---

### Post by aberrios on 2008-03-15
> **bmathis said:**
> My sshd_config file is all defaults and everything works for me. I know that T-Mobile has, in the past, blocked and/or limited ports. It might be a good idea to call tech support and make sure that you can tunnel data through that port on their networks, if not, you can try changing which port ssh listens on to a higher port number.

How do you change the client connection port in the midpssh program?

---

### Post by vpsville on 2008-03-15
We use 8320's with that software just fine.  Are you sure you can connect to the server from a remote site with the same settings?

Is the server behind a router?

---

### Post by maclenin on 2008-03-28
**aberrios:**

Unfortunately, I would have to defer to others for advice on that issue!

**vpsville:**

Thanks for the reply - I have not had time to tinker, lately - but will check back when life permits!

However, just a quick couple of notes before I go:

1. The testing I am doing is from and within a local network.

2. The server and blackberry (8320) are both connected - wirelessly - to the same local network.

3. I have been able to connect to the server via ssh, from a wirelessly connected laptop, but not from the blackberry.

4. I have t-mobile as my mobile carrier and have read that their blocking of certain ports could be causing the trouble I am having with the blackberry (and midpssh).

I hope to have more time to tinker, soon....

---

