---
title: "NXServer problem"
date: 2007-08-07
forum: Server Platforms
---

### Post by neptune on 2007-08-07
Hi,

I've installed the server and I'm able to connect to my Ubuntu desktop from another machine on LAN.

However, when trying to connect from outside my local network (eg: work, internet cafe, etc.), I'm unable to establish the connection.

Port 22 and 443 are allowed out by the network at my work place so I'm fairly certain that there's no firewall on their end blocking it (in fact, I've attempted to connect from a friend's place without any firewall as a test and still no connection).

My feeling is that perhaps my SSH or NXserver is not allowing external connections; as far as I know, there's no firewall running on my Fiesty install.

Can someone please assist? I'd like to be able to access my desktop while I'm away for a week in a few days.

Help is much appreciated.

Thanks!

---

### Post by primski on 2007-08-08
Well,

is your SSH daemon listening on the outside ip or just localhost? Check that in /etc/ssh/sshd_config

are you behind a router? forward accordingly.

what else?

---

### Post by neptune on 2007-08-08
> **primski said:**
> Well,

is your SSH daemon listening on the outside ip or just localhost? Check that in /etc/ssh/sshd_config

are you behind a router? forward accordingly.

what else?
What do I look for in sshd_config to add/change?

I'm behind a router and port 22 is forwarded to Ubuntu machine; it only has one IP.

Thanks!

---

### Post by primski on 2007-08-08
There is a 'ListenAddress' directive.

Set it to your machine's IP or 0.0.0.0 to have it listen on all local IP's.

If that doesn't work, it's proly your router then.

---

### Post by neptune on 2007-08-08
Ok I uncommented that line and will test in the morning from work. My router has port 22 forwarded correctly as well.

---

### Post by RealMabu on 2007-08-13
> **primski said:**
> There is a 'ListenAddress' directive.

Set it to your machine's IP or 0.0.0.0 to have it listen on all local IP's.

If that doesn't work, it's proly your router then.

I have that line commented out already:
```
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0

```
That look OK to me, right?

---

### Post by primski on 2007-08-14
No, uncomment it, aka delete the '#' in front of it.

Also, lets see how its running atm:

```

sudo lsof -i | grep ssh

```

also:
ping the server from remote location, do you get a reply or a timeout? Same when ssh-ing, you get timeout?

---

### Post by RealMabu on 2007-08-14
primski thanks for answering.

_Before_ I uncomment that line I investigate a little further.
```
sudo lsof -i | grep ssh
Password:
sshd     12122      user      3u   IPv6     47514      TCP *:8888 (LISTEN)
```
Maybe I'm wrong but I think this line tells me sshd is listening on all IPs.

I can reach the machine SSHDing and PINGing both in LAN and WAN:
_Lan: (actually, localhost ;-))_
```
user@user-feisty:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.026 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.017 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.023 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.022 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.020 ms

--- localhost ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.017/0.021/0.026/0.005 ms
user@user-feisty:~$ telnet localhost 8888
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

Connection closed by foreign host.
user@user-feisty:~$
```

_Wan: (from work PC)_
```
Microsoft Windows XP [Versione 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\user>telnet xxx.yyy.www.zzz 8888

SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

<I press Ctrl+C>

Protocol mismatch.

Connessione all'host perduta.
<Translates into "Connection lost">

C:\Documents and Settings\user>

C:\Documents and Settings\user>ping 87.13.208.137

Esecuzione di Ping 87.13.208.137 con 32 byte di dati:

Risposta da 87.13.208.137: byte=32 durata=38ms TTL=56
Risposta da 87.13.208.137: byte=32 durata=38ms TTL=56
Risposta da 87.13.208.137: byte=32 durata=38ms TTL=56
Risposta da 87.13.208.137: byte=32 durata=37ms TTL=56

Statistiche Ping per 87.13.208.137:
    Pacchetti: Trasmessi = 4, Ricevuti = 4, Persi = 0 (0% persi),
Tempo approssimativo percorsi andata/ritorno in millisecondi:
    Minimo = 37ms, Massimo =  38ms, Medio =  37ms

C:\Documents and Settings\user>
```

But _I do have some problem_ because I cant make ssh work on this statement:
```
user@user-feisty:~$ sudo su
Password:
root@user-feisty:/home/user# cd /var/lib/nxserver/home/.ssh/
root@user-feisty:/var/lib/nxserver/home/.ssh# ssh -i client.id_dsa.key nx@localhost
ssh: connect to host localhost port 22: Connection refused
root@user-feisty:/var/lib/nxserver/home/.ssh# ssh -i client.id_dsa.key nx@localhost -p 8888
Read from socket failed: Connection reset by peer
root@user-feisty:/var/lib/nxserver/home/.ssh#
```
This is actually a debugging step from [this thread]("http://ubuntuforums.org/showthread.php?t=467219") where kevdog teaches how to setup freenx.
That what I'm trying to accomplish but it looks like I have a misconfigured ssh / sshd and that's why I post here...

Any help appreciated.

---

### Post by primski on 2007-08-14
Yep, sshd does listen on all interfaces, no problems there.

The telnet attempt shows the ssh deamon working just fine on port 8888, since u got a response from it, tho ofc u cant do nothing with telnet over ssh.

My guess is you've done smth wrong with those key files.

Try connecting on ssh without any key files using just password.
```

ssh xxx.yyy.zzz.xyz. -p 8888

```

or if ur connecting from win machine, use 'putty'.

then, go on server and try setting sshd up for nx connections like in that howto.

---

### Post by RealMabu on 2007-08-15
I got it working at last.
Well actually it looks like sshd didnt restart when I tried to restart it.
I had to kill it "by hand" and then start it again. I guess it didnt re-read config file until the restart.
Thanks for your help.

---

### Post by neptune on 2007-08-17
> **primski said:**
> No, uncomment it, aka delete the '#' in front of it.

Also, lets see how its running atm:

```

sudo lsof -i | grep ssh

```

also:
ping the server from remote location, do you get a reply or a timeout? Same when ssh-ing, you get timeout?
Here's the output: 
> sshd      5372    root    3u  IPv4  18970       TCP *:ssh (LISTEN)

I can't ssh to this machine from external network; it doesn't timeout, but returns a 'refused connection'

---

### Post by neptune on 2007-08-19
Also, I've double checked that my router has open TCP port 22 to Ubuntu machine.

---

### Post by primski on 2007-08-20
> **RealMabu said:**
> I got it working at last.
Well actually it looks like sshd didnt restart when I tried to restart it.
I had to kill it "by hand" and then start it again. I guess it didnt re-read config file until the restart.
Thanks for your help.

whats all this about now ? You got it working and now it stopped all of a sudden?

---

### Post by neptune on 2007-08-20
Thats someone else jumping in the thread.

I started this thread and I haven't got it working yet (or at any time).

Your assistance is greatly appreciated.

---

### Post by primski on 2007-08-22
oh sorry, completely missed that was another person writing.

ok, back to ur problem, lets summon it up a little:

u can ssh to ur machine from LAN, but not outside world? u have forwarded port correctly on ur router? and u get a connection refused error?

hm, well, the packet goes somewhere since its refused, otherwise it'd only time out. ur router probably works as a dhcp server too, right, or u have an extra dhcp ?

keep in mind, that when connecting from the outside, u must use the router's ip, not ur internal machine ip with according port, dunno ip:8000 will be forwarded to 192.168.0.1:22

u prolly know this, but other than that, hmm, im getting out of ideas.

maybe someone else has any left?

---

### Post by neptune on 2007-08-22
My internal machines have static LAN IPs so Ubuntu always has same address; so yes, I've done port forwarding correctly on my router for port 22 (my other port forwards work fine so I'm pretty confident that this is correct also).

When connecting from outside, I use my router's external address (public internet address assigned by ISP) on port 22. Like I said, it returns a 'connection refused' instead of timeout so.... ??

---

### Post by primski on 2007-08-22
hm, i hear u man, but im really out of ideas.

perhaps firewall? ubuntu by default doesn't have firewall enabled, but maybe u have some nonstandard install, perhaps try and install it and then open port on ur box ?

long shot i know :p

---

### Post by neptune on 2007-09-13
GAH! Finally figured out the problem.

The Ubuntu setup has been working fine. Its the bloody firewall at work!

The previous security guy had said port 22 was open outgoing, however, the new guy says its not. 

I confirmed by connecting from a hotel room when I was away, and it worked without a hitch.

Thanks for your assistance bud! I appreciate it.

---

### Post by primski on 2007-09-14
sure mate, no probs, glad u figured it out.

---

