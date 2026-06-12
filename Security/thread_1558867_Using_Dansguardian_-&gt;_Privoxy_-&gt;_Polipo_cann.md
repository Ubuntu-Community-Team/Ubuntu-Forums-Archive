---
title: "Using Dansguardian -&gt; Privoxy -&gt; Polipo cannot worked"
date: 2010-08-22
forum: Security
---

### Post by wacky_sung on 2010-08-22
Currently i am using the [tutorial]("http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/") from Bodhi to setup [Dansguardian]("http://dansguardian.org/") to work togather with [Privoxy]("http://www.privoxy.org/") and it worked fine.Then i installed [Polipo]("http://www.pps.jussieu.fr/~jch/software/polipo/") to work with Privoxy which work as intented with additional forward the port to Privoxy.

```
Is it possible to run Polipo together with Privoxy?

Yes. In order to get the privacy enhancements of Privoxy and much (but not all) of the performance of Polipo, you should put Polipo upstream of Privoxy.

In other words, you should:

point your web browser at Privoxy (localhost:8118);
point Privoxy at Polipo (put forward / localhost:8123 in the Privoxy config file);
use no parent proxy in Polipo.
```

Now i tried to use Dansguardian togather with Privoxy and Dansguardian with the same configuration but fail.Can someone shed some light for me!Thank.;)

---

### Post by bodhi.zazen on 2010-08-22
Hard to say from what you posted.

Two quick questions - 

1. Are both privoxy and polipo running ? I know the TOR site has you change the poliop port from 8123 to 8118.

So you can not run both privoxy and polipo together if they are both using port 8118.

2. How much (or little) did you configure iptables ? You may need to flush your previous rules and write new ones.

====

Basically you want 

Firefox -> Dans -> Privoxy -> polipo ?

A. First point Firefox to port 8080 (the default for dansguardian).

In dansguardian, use privoxy as your proxy port 

```
proxyport = 8118
```

B. Now point privoxy to polipo

In /etc/privoxy/config , find the forwarding section. This line forwards privoxy to polipo

```
forward / localhost:8123
```

---

### Post by wacky_sung on 2010-08-23
> **bodhi.zazen said:**
> Hard to say from what you posted.

Two quick questions - 

1. Are both privoxy and polipo running ? I know the TOR site has you change the poliop port from 8123 to 8118.

So you can not run both privoxy and polipo together if they are both using port 8118.

2. How much (or little) did you configure iptables ? You may need to flush your previous rules and write new ones.

====

Basically you want 

Firefox -> Dans -> Privoxy -> polipo ?

A. First point Firefox to port 8080 (the default for dansguardian).

In dansguardian, use privoxy as your proxy port 

```
proxyport = 8118
```

B. Now point privoxy to polipo

In /etc/privoxy/config , find the forwarding section. This line forwards privoxy to polipo

```
forward / localhost:8123
```

Question :
1. Are both privoxy and polipo running ? I know the TOR site has you change the poliop port from 8123 to 8118.

[COLOR="Red"]Ans:[/COLOR]
Yes,i want to run Firefox(Port : 8080) -> Dans(listen to port :8080) -> Privoxy(Forward port :8123,Listen port:8118) -> polipo(port : 8123).I do not use TOR for it.

Question :
2. How much (or little) did you configure iptables ? You may need to flush your previous rules and write new ones.

[COLOR="red"]Ans:[/COLOR]
I did not change any or remove any additional iptables rules from the way i setup for privoxy and dansguardian.
```
sudo iptables -A OUTPUT -m owner --uid-owner root -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -m owner --uid-owner privoxy -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -j DROP
sudo iptables -A OUTPUT -o lo -p tcp --dport 8118 -m owner --uid-owner dansguardian -j ACCEPT
sudo iptables -A OUTPUT -o lo -p tcp --dport 8118 -m owner --uid-owner alex -j ACCEPT
sudo iptables -A OUTPUT -o lo -p tcp --dport 8118 -j DROP

```

I just ponder if it is the iptables rules issue?The problem is that it working fine with me using below.

Firefox -> Privoxy -> polipo

Basically i did prior to what you wrote below but it did not work
,except for firefox -> Privoxy -> Polipo.

```
Basically you want 

Firefox -> Dans -> Privoxy -> polipo ?

A. First point Firefox to port 8080 (the default for dansguardian).

In dansguardian, use privoxy as your proxy port 

[code]proxyport = 8118
```

B. Now point privoxy to polipo

In /etc/privoxy/config , find the forwarding section. This line forwards privoxy to polipo

```
forward / localhost:8123
```[/QUOTE]
[/CODE]

Is the problem on the iptables?Thank.

---

### Post by bodhi.zazen on 2010-08-23
Aye, that would be my guess.

Your first rule allows privoxy, but your second rule drops all traffic on ports 80 and 443, so you are probably blocking polipo.

polipo runs as the user "proxy"

Flush your iptables rules and see if it then works.

```
sudo -i
iptables-save > iptables.polipo
iptables -t nat -F
iptables -F
```

To restore, ```
sudo -i
iptables-apply iptables.polipo
```

You can edit iptables.polipo if you wish.

---

### Post by wacky_sung on 2010-08-23
I tried your method but it still does not work.:confused:

---

### Post by bodhi.zazen on 2010-08-23
Please make sure your firewall is disabled.

Restart dansguardian, privoxy, and polipo.

If it is now working, please post the relevant lines from the 3 config files (should be one line per file).

---

### Post by wacky_sung on 2010-08-24
> **bodhi.zazen said:**
> Please make sure your firewall is disabled.

Restart dansguardian, privoxy, and polipo.

If it is now working, please post the relevant lines from the 3 config files (should be one line per file).

I do not know even i have disable the firewall and restart all the services but it still cannot get connected.Not to mention using the working privoxy togather with polipo also cannot get connected without any firewall.

Below are the configuration for you to verify.

_Dansguardian_
[File 1]("http://www.yourfilelink.com/get.php?fid=565399")
[File 2]("http://www.yourfilelink.com/get.php?fid=565400")

_Privoxy_
[File 1]("http://www.yourfilelink.com/get.php?fid=565401")

_Polipo_
[File 1]("http://www.yourfilelink.com/get.php?fid=565402")

---

