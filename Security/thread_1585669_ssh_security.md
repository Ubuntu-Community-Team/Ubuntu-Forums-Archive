---
title: "ssh security"
date: 2010-09-30
forum: Security
---

### Post by Jonny87 on 2010-09-30
I'm running the firestarter firewall and its been showing the odd ssh attempt quite often. e.g. I've had 4 attempts today, 3 in the last 40mins.

I realize that this may be nothing to serious but it's got me curious, aside from having a secure password (which I have) is there anything that else that I can do to ensure that my system is as secure as possible from ssh?

I do use ssh within my home network so I don't want to disable it completely.

---

### Post by cj.surrusco on 2010-09-30
It's not too uncommon to have somebody try some default usernames/passwords on your ssh. There are people that scan thousands of computers to find the ones that have ssh ports open. Unless you have a *very* determined hacker, you have almost nothing to worry about with a strong password. 

If you want to take extra security measures, however, you can try using ssh keys. Take a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"). 

Also, you could change your ssh port to a very high port (ex. 40000) instead of 22, because most times hackers will only scan most commonly used ports. It takes too long for them to scan all 70000 or however many ports. This won't make a huge difference, but it is an extra measure.

---

### Post by Jonny87 on 2010-09-30
> **cj.surrusco said:**
> It's not too uncommon to have somebody try some default usernames/passwords on your ssh. There are people that scan thousands of computers to find the ones that have ssh ports open. Unless you have a *very* determined hacker, you have almost nothing to worry about with a strong password. 

If you want to take extra security measures, however, you can try using ssh keys. Take a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"). 

Also, you could change your ssh port to a very high port (ex. 40000) instead of 22, because most times hackers will only scan most commonly used ports. It takes too long for them to scan all 70000 or however many ports. This won't make a huge difference, but it is an extra measure.

Thanks, as far as changing ports go, I've never gone about doing that in linux. How do I do that for ssh?

---

### Post by cj.surrusco on 2010-09-30
> **Jonny87 said:**
> Thanks, as far as changing ports go, I've never gone about doing that in linux. How do I do that for ssh?
You would need to edit the etc/ssh/sshd_config file.

Change the line:

Port 22

to:

Port 41300

You can use whatever port you'd like, it obviously does not need to be 41300. Make sure that you open that port on your firewall though.

---

### Post by Jonny87 on 2010-09-30
> **cj.surrusco said:**
> You would need to edit the etc/ssh/sshd_config file.

Change the line:

Port 22

to:

Port 41300

You can use whatever port you'd like, it obviously does not need to be 41300. Make sure that you open that port on your firewall though.

Ok thanks for you help.

---

### Post by dmizer on 2010-10-01
If your SSH server is open to the internet, you should ditch passwords and use encrypted key pairs: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by CharlesA on 2010-10-01
> **dmizer said:**
> If your SSH server is open to the internet, you should ditch passwords and use encrypted key pairs: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
+1 to that. You'll still see attempts, but if they cannot athenticate, they cannot do any damage.

---

### Post by FuturePilot on 2010-10-01
1. Completely disable password auth and only use keys.
2. Use fail2ban or deny-hosts.

---

### Post by bodhi.zazen on 2010-10-01
See also

[http://bodhizazen.net/Tutorials/ssh_security](http://bodhizazen.net/Tutorials/ssh_security)

---

### Post by paulsp on 2010-10-02
>  I do use ssh within my home network so I don't want to disable it completely.

If this is only used WITHIN your network, the best bet it to simply firewall off the computers and ONLY give the internal network users access to ssh. That way any attempt - even if they have the right port and your keys - will fail. 

You can use UFW and then specify the IPs that need to have access.

---

### Post by Aetixintro on 2010-10-02
In Firestarter, you can rightclick on the incoming line and choose to BLOCK either incoming traffic on PORT or incoming traffic from SOURCE. Remember this is incoming.

In outgoing, you can still ALLOW port 22 or any other as you like.

Enjoy! :)

---

