---
title: "ufw blocking remote desktop even when port is allowed"
date: 2012-02-27
forum: Security
---

### Post by Ms. Daisy on 2012-02-27
Hello. I'm using rdesktop in Ubuntu to connect to a remote windows server that I have creds on. **It works perfectly when I turn off ufw**, but when ufw is enabled it blocks the connection.

Here's what I type in a terminal to connect
```
rdesktop -f -u username -p - rdp.server.com:3389
```and when I look at my ufw logs, here's what I see

```
Feb 27 21:47:17 daisy-comp kernel: [22509.556129] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.3 DST=217.50.190.194 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=49381 DF PROTO=TCP** SPT=60955** DPT=3389 WINDOW=14600 RES=0x00 SYN URGP=0 
Feb 27 21:50:20 daisy-comp kernel: [22512.560048] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.3 DST=217.50.190.194 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=49382 DF PROTO=TCP **SPT=60956 **DPT=3389 WINDOW=14600 RES=0x00 SYN URGP=0 
Feb 27 21:53:26 daisy-comp kernel: [22518.576046] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.3 DST=217.50.190.194 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=49383 DF PROTO=TCP **SPT=60957 **DPT=3389 WINDOW=14600 RES=0x00 SYN URGP=0 
```With each failed attempt to connect, my computer incrementally tried ports 60950 through 60957.  So I wrote a rule in ufw 
```
sudo ufw allow out 60950:60957/tcp
```I restarted the firewall, opened a new terminal and tried to connect to the remote server.  FAIL. The ufw logs show that it's blocking the ports I have just specifically allowed.  

What am I doing wrong?

---

### Post by Dangertux on 2012-02-27
Have you tried this --

```

sudo ufw allow out 3389

```Hope this helps.


Just to explain why this works real quick, you're opening the source ports, this is unnecessary to allow outbound (with strict outbound policies in UFW, because there is an underlying iptables rule that will look something like this)

```

-A ufw-before-output -p tcp -m conntrack --ctstate RELATED,ESABLISHED -j ACCEPT

```

That will take care of those odd random ports for you, however what you need to do is focus on the destination port

```

DPT=3389

```

Not the source port.

P.S : Enjoy owning rdp for MSU ;-) (don't forget to try harder)

---

### Post by Ms. Daisy on 2012-02-28
Aha. Thank you. So I need to write rules to allow out on the **destination** port. (I can't really understand why my firewall would care which port I'm sending to on some other machine.  Seems like that should be the other machine's problem, not mine.)

Any idea why the exact same configuration works on my other computer? I  only allowed out on the source ports, I didn't allow out DPT=3389. Yet I'm sporting a pretty Windows desktop with ufw enabled.

---

### Post by Dangertux on 2012-02-28
> **Ms. Daisy said:**
> Aha. Thank you. So I need to write rules to allow out on the **destination** port. (I can't really understand why my firewall would care which port I'm sending to on some other machine.  Seems like that should be the other machine's problem, not mine.)

Any idea why the exact same configuration works on my other computer? I  only allowed out on the source ports, I didn't allow out DPT=3389. Yet I'm sporting a pretty Windows desktop with ufw enabled.

The other configuration shouldn't work on your other system if the outbound policy is the same. I'm guessing the outbound policy isn't the same.

You have to realize that iptables rules are based on your packet header (some on the data in the packet itself). It's checking things like destination port in the packet header.

---

### Post by Ms. Daisy on 2012-02-28
Thanks DT!

---

