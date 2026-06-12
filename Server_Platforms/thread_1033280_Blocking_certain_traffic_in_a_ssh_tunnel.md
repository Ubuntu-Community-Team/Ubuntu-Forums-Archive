---
title: "Blocking certain traffic in a ssh tunnel"
date: 2009-01-07
forum: Server Platforms
---

### Post by jersak on 2009-01-07
Here i am, again stuck with ssh configuration =P

I'm setting up a tunnel for gaming purposes, and therefore it should be used only for gaming. So i would like any other application besides the game to be unable to use the tunnel.

I tried to use permitopen="host : port" in authorized_keys but it does not work or im using it wrong. I've uncommented the line wich specifies the file in sshd_config (and even assigned a file in my /home/myuser folder because i couldnt find the default file).

So if you guys do know any other way to limit the traffic through the tunnel, share it with me please =)

Thanks in advance.

---

### Post by scorp123 on 2009-01-07
> **jersak said:**
>  I'm setting up a tunnel for gaming purposes, and therefore it should be used only for gaming. So i would like any other application besides the game to be unable to use the tunnel. I'd use a firewall rule here, e.g. a rule that allows the target IP and port of the game server but drops anything else.

---

### Post by jersak on 2009-01-07
Can you help me on how to do that?
I'm also using webmin, if that helps.

---

### Post by windependence on 2009-01-07
Is there a reason you are being this anal on an ssh connection? If someone doesn't have the key, they aren't getting in and if you use blowfish encryption, it would take months if not years to crack it. I don't see the point here.

-Tim

---

### Post by scorp123 on 2009-01-08
> **windependence said:**
> Is there a reason you are being this anal on an ssh connection? Who are you talking to???

> **windependence said:**
>  If someone doesn't have the key, they aren't getting in You're missing the point altogether. Please read OP's posting again. And please make sure you understood the question at hand, yes? :D

> **windependence said:**
>  I don't see the point here. Yes, I see. You don't even understand OP's question.

---

### Post by scorp123 on 2009-01-08
> **jersak said:**
> Can you help me on how to do that? There are easy-to-use applications such as "firestarter". Search these forums here.

---

### Post by scorp123 on 2009-01-08
> **jersak said:**
>  I tried to use permitopen="host : port" in authorized_keys but it does not work or im using it wrong. Something I just came across with regards to your original attempts: Can you give this a try (again)? This guy here got it working ... so maybe you could use the config example as a template and adapt it to your own needs:

"How to restrict a user only to portforwarding in SSH Tunnel"
[http://www.unixweblog.com/2007/02/21/how-to-restrict-a-user-only-to-portforwarding-in-ssh-tunnel/](http://www.unixweblog.com/2007/02/21/how-to-restrict-a-user-only-to-portforwarding-in-ssh-tunnel/)

---

### Post by HermanAB on 2009-01-08
Hmm, stopping specific types of traffic on a channel is not easy.  You need to do some Googling and reading on "Rusty Russel's amazingly inaccurate website".

What you likely need to do is create an iptables rule that will match a text string unique to a specific type of traffic, tag the packet and then drop the packet using another rule.

This is not the kind of thing anyone would want to help you with, since it iss just too painful - you'll have to figure it out on your own!

Cheers,

Herman

---

### Post by jersak on 2009-01-10
Does the traffic tunneled thorugh SSH count as a FORWARD chain in IPTables?

'Cause if it does, i could drop all traffic wich does not target the ports used by the game, couldnt i?

---

### Post by jersak on 2009-01-13
Anybody?

---

### Post by HermanAB on 2009-01-13
FORWARD is used when you forward traffic to another computer out another port.  On the local machine only the INPUT and OUTPUT chains have effect I think.

Cheers,

Herman

---

### Post by jersak on 2009-01-25
God knows how many different things i've tried, and none worked.:( Still nobody know how to do it?

---

### Post by jersak on 2009-08-20
UP after some months

---

### Post by scorp123 on 2009-08-20
> **jersak said:**
> UP after some months

You never answered this post:
[http://ubuntuforums.org/showpost.php?p=6516582&postcount=7](http://ubuntuforums.org/showpost.php?p=6516582&postcount=7)

---

