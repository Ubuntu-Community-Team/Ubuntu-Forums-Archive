---
title: "What does Firestarter reeeeaaalllly do??"
date: 2009-06-10
forum: Security
---

### Post by listerdl on 2009-06-10
Is firestarter actually doing anything? I have it installed and am sure that i have the correct settings but I am not really sure what it is that it is meant to be doing - anyone be able to tell me the purpose of firestarter? Thanks!

---

### Post by doas777 on 2009-06-10
> **listerdl said:**
> Is firestarter actually doing anything? I have it installed and am sure that i have the correct settings but I am not really sure what it is that it is meant to be doing - anyone be able to tell me the purpose of firestarter? Thanks!

firestarted is a front-end tool for configuring IP tables (the built in kernel-based firewall in ubuntu). you use it to configure your service ports. if you don't have services running on that box, then there is little or no point in running firestarter.

many tell me that firestarter is passe, and to use gufw. I personally miss features in gufw, but it is better supported.

---

### Post by listerdl on 2009-06-10
> **doas777 said:**
> you use it to configure your service ports. if you don't have services running on that box, then there is little or no point in running firestarter. Not sure if I do or dont - how do i tell?

thanks for reply

---

### Post by cdenley on 2009-06-10
> **listerdl said:**
> Not sure if I do or dont - how do i tell?

thanks for reply

```

sudo netstat -tulnp

```
This will list all processes listening for connections on a TCP or UDP port. All that should be listed is avahi, and maybe dhclient. That is all that is installed by default.

---

### Post by doas777 on 2009-06-10
> **listerdl said:**
> Not sure if I do or dont - how do i tell?

thanks for reply


well, ubuntu ships with no services or open ports, so unless you installed one (like samba for file sharing) then you don't need firestarter at all.

---

### Post by ubuntu27 on 2009-06-10
You can test if you firewall is configured correctly by visiting [ShieldsUP!]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by Vanishing on 2009-06-10
> **ubuntu27 said:**
> You can test if you firewall is configured correctly by visiting [ShieldsUP!]("https://www.grc.com/x/ne.dll?bh0bkyd2")

instead of visiting that site , i think you could just do a "nmap localhost",or using another peer to nmap you peer,am i right?

---

### Post by rookcifer on 2009-06-11
> **Vanishing said:**
> instead of visiting that site , i think you could just do a "nmap localhost",or using another peer to nmap you peer,am i right?

Yeah.  I would just do:

```
nmap -sT -sU -p- -v localhost
```

from inside the network.  This will scan all 65535 TCP and UDP ports.  It should be quick since it's being ran from inside a potential firewall.  This is actually a good way to find out what services are listening (as opposed to, say, netstat).

You can run it from the outside to test the firewall, but be warned if the firewall is set to something like -A INPUT -p tcp -m tcp -j DROP, then it will take a *long time*.

---

### Post by cariboo on 2009-06-11
IF you are behind a router, Shieldsup will only check the router's firewall. Running nmap or even using the builtin port scanner will tell you which ports you have open. You use the builtin port scanner go to System-->Administration-->Network Tools-->Port Scan, enter localhost in Network Address then click scan.

If you want to use nmap, you will need to install it first, it is in the repositories, once installed open an Applications-->Accessories-->Terminal and type:

```
nmap localhost
```

You should get an output that looks something like this:

```
nmap localhost

Starting Nmap 4.76 ( http://nmap.org ) at 2009-06-10 21:37 PDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.14 seconds
```

---

### Post by the.scarecrow on 2009-06-11
> **cariboo907 said:**
> IF you are behind a router, Shieldsup will only check the router's firewall. Running nmap or even using the builtin port scanner will tell you which ports you have open. You use the builtin port scanner go to System-->Administration-->Network Tools-->Port Scan, enter localhost in Network Address then click scan.

.........

Hi, 
I tried this on my 9.04 installation and get this result:-

  631   open   ipp
35931   open   unknown

does this look normal?

I don't do any file sharing.

Thanks

---

### Post by cariboo on 2009-06-11
That looks perfectly normal, the high port is more than likely a bug in the port scan tool, that's been around since hardy. It has been reported upstream, but it seems it hasn't fixed yet.

---

### Post by bodhi.zazen on 2009-06-11
The best way to see what firestarter is doing is with iptables :

```
sudo iptables -L -v
```

This will show all the rules and the -v shows you not only specific details but counts of packets (number of packets processed by any particular rule).

IMo an easy way to see what ports are open is with lsof :

```
lsof -i -n -
```

This will list services and ports.

Scanning from localhost will give you "false positive" results as some services are bound to localhost.

Best to scan from another computer on your LAN

```
sudo nmap -v -A -PN ip_address
```

Shields up is not such a good idea as:

1. It scans your router, not your actual computer.
2. Shields up uses some "misleading" terminology such as "stealth" and implies that "stealth" is somehow more secure then "closed". Without wanting to start a huge debate, you will find the terms "steath" == "DROP" and closed = "REJECT".

Some people feel DROP is better as REJECT will somehow disclose your IP, but IMO security via obscurity is no security at all and modern cracking techniques will not be "fooled" by "DROP".

---

### Post by the.scarecrow on 2009-06-11
> **cariboo907 said:**
> That looks perfectly normal, the high port is more than likely a bug in the port scan tool, that's been around since hardy. It has been reported upstream, but it seems it hasn't fixed yet.

Oooofff thanks for that.

I've been checking out the anti virus security on my sons PC this afternoon, he uses WinXP (overblown games machine). This has made me paranoiac again, why does anyone use Windows its just too risky if your doing on-line banking with the same machine.

I'm thinking of installing Avast as on balance it gets positive feedback and its free. I just deleted McAfee because that failed to prevent or detect four Viruses getting installed.

---

### Post by doas777 on 2009-06-11
> **the.scarecrow said:**
> Hi, 
I tried this on my 9.04 installation and get this result:-

  631   open   ipp
35931   open   unknown

does this look normal?

I don't do any file sharing.

Thanks


ok, back to your original query, it looks like it will be safe to uninstall firestarter.

---

