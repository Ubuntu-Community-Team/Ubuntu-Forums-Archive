---
title: "Sudo and  using a USB smartcard reader to authencite via Active Directory and PIN"
date: 2007-08-02
forum: Server Platforms
---

### Post by toupeiro on 2007-08-02
Sound perverse enough?  It gets cuter.

So here's the jest of it.

So I can get Linux/Solaris to recognize the smartcard credential and authenticate via Active Directory.  Now, here is where it gets cute...  Sudo will only accept the PIN credential of the smartbadge inserted into a machine, which makes ssh execution a near impossibility if someone is using the console of the linux box.  

I have the source code for Sudo 1.6.9p2 And there are various configuration options to enable Kerberos support, but how can I make sudo not attempt to look at the local smartcard reader, and rather look directly to Active Directory and match my ID, and prompt me for my PIN for authentication, or pipe back to my smartcard reader (maybe its more of an openSSH recompile??)

Has anyone crossed this bridge before?  Its an uber rickety one.

---

### Post by koenn on 2007-08-03
I don't quite understand what you're saying, so I could be way off, but :
1- why does your sudo problem make it near impossible to ssh ? you switch  user in the ssh-statement and if you need root on the remote machie, you sudo "there", not "here", no ?

2- Isn't the point of kerberos to centralise authentication so once your authenticated, why do you need to come back to the smartccard reader ? 

Maybe you'll have to explain more detailed what you're trying to accomplish.

---

