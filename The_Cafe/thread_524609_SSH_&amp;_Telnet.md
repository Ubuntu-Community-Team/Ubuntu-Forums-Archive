---
title: "SSH &amp; Telnet"
date: 2007-08-13
forum: The Cafe
---

### Post by xGutsAndGloryx on 2007-08-13
I am interested in learning SSH & Telnet. Does anyone know any good websites that could help me out?

---

### Post by OffHand on 2007-08-13
There are guides here on the forum... use the search function.

---

### Post by Warren Watts on 2007-08-13
Here are links useful in setting up SSH and telnet servers on your computer:

[SSH HowTo]("https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29")

[telnet HowTo]("http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html")

---

### Post by igknighted on 2007-08-13
learning ssh and telnet?  I'm not sure what you mean.  To use SSH, make sure both machines have the proper ports unblocked and the service enable (or putty installed on a windows machine), and then type 'ssh' followed by the domain name or the ip address of the machine you wish to connect to.  Then login as usual and go.  Putty in windows works basically the same way.

Telnet is rather antiquated, not sure what use you would find for it these days.

---

### Post by Bachstelze on 2007-08-13
[http://www.amazon.com/SSH-Secure-Shell-Definitive-Guide/dp/0596008953/ref=sr_1_1/102-9595506-8621753?ie=UTF8&s=books&qid=1187019701&sr=8-1](http://www.amazon.com/SSH-Secure-Shell-Definitive-Guide/dp/0596008953/ref=sr_1_1/102-9595506-8621753?ie=UTF8&s=books&qid=1187019701&sr=8-1)

Must-have book if you're interested in SSH.

@igknighted > there is much, much more to SSH than just *ssh user@host* ;)

---

### Post by ashvala on 2007-08-13
Basically Telnet is not as secure as SSH.... Telnet which you are looking at can be hacked easily... while SSH cannot....

SSH rocks Dude:guitar:

---

### Post by ssam on 2007-08-13
do not use telnet unless you are on a completely secure network. telnet send everything including passwords in plain text.

ssh is very secure (as long as you have strong password or use keys instead of password).

the server package is called openssh-server and the client is installed by default.

then from the client run
```
ssh address
```
where the address is the ip address or (if you have recent distros with avahi and are on a local network) hostname.local (run hostname in a terminal find out the hostname of a computer).

if you want to lauch graphical applications over ssh use the -X flag (capital X)
```
ssh -X address
```

look at man ssh for more options

---

### Post by dreadlord_chris on 2007-08-13
[telnet://towel.blinkenlights.nl](telnet://towel.blinkenlights.nl)

---

### Post by jseiser on 2007-08-13
i have 2 computers (both ubuntu) that have the ssh port open on the router and in iptables, both have ssh installed.  I can log into the laptop from the desktop, but when i try to copy a file over to my desktop it says "file is the same" but i dont have the file on my computer. also, when i put in hostname in the terminal i only get the desktops hostname, why doesnt i "see" the laptop on the same network? what would the command be to add the name "lintop" so i can just use justin@lintop opposed to putting in its local ip? what is the proper commadn to copy a file "yeah" from my laptop /home/justin/ to my desktops /home/justin?

scp -r [email]justin@192.168.1.151:/home/username/remotefile.txt "/home/justin"[/email] 

when i do that i get asked for my password and then it shows a transfer but it doesnt actually go :(

but the file doesnt transfer.

ok i can copy a file form my laptop to my desktop, i was logging into the ssh session and then running that command, but if i just run it like that i can do it.  Is there a way to do things like copying once logged into the other computer, or must it all be done before you log into the session?

---

### Post by Bachstelze on 2007-08-13
> **jseiser said:**
> also, when i put in hostname in the terminal i only get the desktops hostname, why doesnt i "see" the laptop on the same network? what would the command be to add the name "lintop" so i can just use justin@lintop opposed to putting in its local ip?

For your system to be able to "translate" the hostname into an IP address, you must add it to your /etc/hosts file. For example, mine looks like :

```
127.0.0.1       Ana localhost
192.168.1.2     Miu
192.168.1.4     Matsuri
192.168.1.5     Nobue
192.168.1.7     Chika
192.168.1.10    Satake

```

So I just type e. g. *ssh Miu* and I'm there.

> what is the proper commadn to copy a file "yeah" from my laptop /home/justin/ to my desktops /home/justin

Assuming you're on your laptop and the "desktop" hostname is configured as above :

```
scp /home/justin/yeah desktop:/home/justin
```

> Is there a way to do things like copying once logged into the other computer, or must it all be done before you log into the session?

If the machine you want to copy from also has a SSH server, you can do like before, but the other way around :

```
scp desktop:/home/justin/yeah /home/justin
```

---

### Post by xGutsAndGloryx on 2007-08-13
thanks everyone.. i understand telnet isn't as secure as ssh.. the only reason i am asking questions about it... is due to the fact.. i tried applying for job at a university working on computers... there required you to have some experience in ssh & telnet..    so i am wanting to learn them so i can be prepared next time

---

