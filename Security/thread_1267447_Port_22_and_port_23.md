---
title: "Port 22 and port 23"
date: 2009-09-15
forum: Security
---

### Post by caramelsoul on 2009-09-15
Im currently using firestarter as my fire wall on 9.04. I keep getting "hits" on port 22 and 23. 

Is this something i should worry about? 

Does it mean someone is trying to access my machine? 

If so what steps should i take?

---

### Post by lloyd_b on 2009-09-15
> **caramelsoul said:**
> Im currently using firestarter as my fire wall on 9.04. I keep getting "hits" on port 22 and 23. 

Is this something i should worry about? 

Does it mean someone is trying to access my machine? 

If so what steps should i take?

Port 22 is ssh, port 23 is telnet.  Both of these have to potential to provide a shell to a remote user.

This *could* be someone probing machines, looking for one that is potentially hackable.  Then again, it could be that (assuming that you're getting a dynamic IP address from your ISP) just someone trying to connect to a machine that used to be on that IP address.

In either case, you've already taken the necessary step - you have a firewall that blocks the attempts.  Other than that, about the only thing you might consider doing is, if your router supports it, blocking all incoming requests for those ports at the router.

Lloyd B.

---

### Post by lovinglinux on 2009-09-15
> **lloyd_b said:**
> Port 22 is ssh, port 23 is telnet.  Both of these have to potential to provide a shell to a remote user.

This *could* be someone probing machines, looking for one that is potentially hackable.  Then again, it could be that (assuming that you're getting a dynamic IP address from your ISP) just someone trying to connect to a machine that used to be on that IP address.

In either case, you've already taken the necessary step - you have a firewall that blocks the attempts.  Other than that, about the only thing you might consider doing is, if your router supports it, blocking all incoming requests for those ports at the router.

Lloyd B.

+1

Additionally, if you don't have an ssh server running, which would be listening to port 22, then you don't even need to protect that port with a firewall. Ports that are not listened by any servers are virtually closed and all connection attempts on those ports are refused. Ubuntu comes with no server running by default. SSH server is not even installed by default. I don't know about telnet, tho.

---

### Post by caramelsoul on 2009-09-15
OK, thanks guys for taking the time to answer that and put my mind at ease.

---

### Post by The Cog on 2009-09-16
> **caramelsoul said:**
> Im currently using firestarter as my fire wall on 9.04. I keep getting "hits" on port 22 and 23. 

Is this something i should worry about? No> Does it mean someone is trying to access my machine? Yes> 
If so what steps should i take?
Just be aware that if you ever do install an SSH server on port 22 and open it to the internet, it will be subjected to constant password-guessing. So you need good passwords or to use certificates for authentication instead. And never enable root login - that way they have to guess the username too. And never install a telnet server (port 23): SSH is more secure.

---

