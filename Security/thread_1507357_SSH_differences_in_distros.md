---
title: "SSH differences in distros"
date: 2010-06-11
forum: Security
---

### Post by kaspar_silas on 2010-06-11
Hi all,

I have a slight annoyance that hopefully someone can solve or push me in the right direction anyway. 

I connect to a series of 4 computers with identical hardware. Two run OpenSuse 11.1 and the other two unbuntu (9.10 and 10.04). I connect to all with the basic:

ssh -X user@host

On each I run the same program. However when using the gui on the ubuntu computers there is about a one second delay between clicking and the gui event happening. A one second delay being very irritating as you can imagine. 

As computers have the same /etc/ssh/sshd_config files and ping times so I assume this is some bonus security in ubuntu not present in opensuse. (I inherited the opensuse so it may be turned off in these previously)

So the question is does anyone have any idea what this could be or even where to start looking. Incidentally the 2 host computers are all behind a fire-wall so I can would pretty much turn off any security.  

Thanks for any suggestions.

---

### Post by FuturePilot on 2010-06-11
Are the servers in the same location? Could it be that the Ubuntu server is farther away or has a slower connection than the others?

---

### Post by anomie on 2010-06-12
Right, are the four hosts (and your client system) all on the same LAN? If not, please describe the network layout.

---

### Post by kaspar_silas on 2010-06-13
Cheers,

Sorry I should have said all 4 computers are in the same room and all go through the same router to a gateway that I connect to.

---

### Post by Perkins on 2010-06-14
There are a number of things that could do this besides SSH settings.  Different LAN connection speeds, (10/100/1000 Mbit/sec), the speed of the computer in question (encrypting and decrypting data takes time) Whether compression is enabled by default, and to what level.  It's really hard to pick out just one thing and say "that's what's doing it" without actually sitting down with the hardware and examining it.

---

### Post by kaspar_silas on 2010-06-14
> **Perkins said:**
> There are a number of things that could do this besides SSH settings.  Different LAN connection speeds, (10/100/1000 Mbit/sec), the speed of the computer in question (encrypting and decrypting data takes time) Whether compression is enabled by default, and to what level.  It's really hard to pick out just one thing and say "that's what's doing it" without actually sitting down with the hardware and examining it.

The network cards are all the same and go to the same router. So I assume the LAN speeds are all the same. 

The speeds of the computers should also be close to exactly the same. The hardware is in general identical apart from RAM which does vary. However none have less than 24Gb and so I doubt that's the problem. Plus I compared two machines with the same amount of RAM amount and it still shows the OS difference.  

I also tried scp copying a big file across to all 4 computers and it took pretty much the same amount of time to all 4. 

Next I tried ssh -vvv name@host for the Ubuntu and non-ubuntu machines.
I copied the output of these and diffed these. This gave (I removed trivial differences due to hostname differences etc) 

```

< debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu3
< debug1: match: OpenSSH_5.3p1 Debian-3ubuntu3 pat OpenSSH*
---
> debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1
> debug1: match: OpenSSH_5.1 pat OpenSSH*

32,33c32,33
< debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
< debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
---
> debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
> debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

77,78c77,80
< debug1: Authentications that can continue: publickey,password
< debug3: start over, passed a different list publickey,password
---
> debug3: input_userauth_banner
> Welcome to openSUSE 11.1 - Kernel %r (%t).
> debug1: Authentications that can continue: publickey,keyboard-interactive
> debug3: start over, passed a different list publickey,keyboard-interactive

91,99c93,109
< debug3: authmethod_lookup password
< debug3: remaining preferred: ,password
< debug3: authmethod_is_enabled password
< debug1: Next authentication method: password
< debug3: packet_send2: adding 64 (len 57 padlen 7 extra_pad 64)
< debug2: we sent a password packet, wait for reply
< debug3: Wrote 144 bytes for a total of 1271
< debug1: Authentication succeeded (password).
---
> debug3: authmethod_lookup keyboard-interactive
> debug3: remaining preferred: password
> debug3: authmethod_is_enabled keyboard-interactive
> debug1: Next authentication method: keyboard-interactive
> debug2: userauth_kbdint
> debug2: we sent a keyboard-interactive packet, wait for reply
> debug3: Wrote 96 bytes for a total of 1223
> debug2: input_userauth_info_req
> debug2: input_userauth_info_req: num_prompts 1
> debug3: packet_send2: adding 32 (len 22 padlen 10 extra_pad 64)
> debug3: Wrote 80 bytes for a total of 1303
> debug2: input_userauth_info_req
> debug2: input_userauth_info_req: num_prompts 0
> debug3: packet_send2: adding 48 (len 10 padlen 6 extra_pad 64)
> debug3: Wrote 80 bytes for a total of 1383
> debug1: Authentication succeeded (keyboard-interactive).

```

At a bit of a loss over this now.

---

### Post by Perkins on 2010-06-14
Well, short of sitting down with a packet sniffer and a network tester, this is getting over my head.  The only further suggestions I have are to test the throughput between the various combinations of machines (bing from the repository might work.) and to check and see if SSH and its supporting libraries are actually the same version.  Also look in the sshd config file and see if there are any significant differences in settings (compression being the obvious one that comes to mind).  Lastly, make sure that the network port on the slow machine hasn't been locked down to a lower speed.  (Sorry, I don't remember how to check this off the top of my head.)

It could also be a bad patch-cable or ethernet line in the wall causing errors.  ifconfig should give you a clue about that.

---

### Post by kaspar_silas on 2010-06-15
> **Perkins said:**
> Well, short of sitting down with a packet sniffer and a network tester, this is getting over my head.  The only further suggestions I have are to test the throughput between the various combinations of machines (bing from the repository might work.) and to check and see if SSH and its supporting libraries are actually the same version.  Also look in the sshd config file and see if there are any significant differences in settings (compression being the obvious one that comes to mind).  Lastly, make sure that the network port on the slow machine hasn't been locked down to a lower speed.  (Sorry, I don't remember how to check this off the top of my head.)

It could also be a bad patch-cable or ethernet line in the wall causing errors.  ifconfig should give you a clue about that.

Cheers for the nod towards bing that's really useful. Alas it seemed to indicate all connections were roughly equivalent. I also tested cables and even switching them and the network cards around with no change observed.

The last thing was to set all the sshd_config the same but this also had no effect other than the ubuntu computers now showing the login message twice (just skipping that easily ignored annoyance for now).

However I did discover some differences. The ssh version were different but more important so was the default Java JVMs. The ubuntu machines are using openjdk the opensuse one Sun. As it's a Java application run through debugging eclipse this could well be the problem.

---

### Post by Perkins on 2010-06-15
To steal a line from Tremors 2, "I feel I was denied critical, need to know information."  :P

To be fair, I probably should have suggested running the application in question locally on each machine and seeing if the speed differences were still present, but I kind of assumed that that would have been obvious...  :P

---

### Post by kaspar_silas on 2010-06-16
> **Perkins said:**
> To steal a line from Tremors 2, "I feel I was denied critical, need to know information."  :P

To be fair, I probably should have suggested running the application in question locally on each machine and seeing if the speed differences were still present, but I kind of assumed that that would have been obvious...  :P

Yeah it was obvious but it required joyless physical effort in actually walking to the server room carrying a monitor.

(Strongly approve of the quoting of Tremors 2)

---

### Post by Perkins on 2010-06-17
VNC usually makes the differences between connection lag and application lag fairly obvious.  ;)

---

