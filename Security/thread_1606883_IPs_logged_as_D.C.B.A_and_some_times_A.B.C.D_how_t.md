---
title: "IPs logged as D.C.B.A and some times A.B.C.D how to find which format is logge"
date: 2010-10-27
forum: Security
---

### Post by tapas_mishra on 2010-10-27
I see two different type of log messages in my /var/log/auth.log file
one is > 
reverse mapping checking getaddrinfo for dnet-217003.sby.dnet.net.id [115.69.217.3] failed - POSSIBLE BREAK-IN ATTEMPT!

and another is 
> reverse mapping checking getaddrinfo for client-200.121.135.240.speedy.net.pe [240.135.121.200] failed - POSSIBLE BREAK-IN ATTEMPT!


in the second log the IP address from where the connection originated was 
240.135.121.200

now the log of type one above is also present and some at some places log of type2.
If you note the IP logged in in both cases the type1 logged as 
> 115.69.217.3
and type 2 logged as
> 200.121.135.240.speedy.net.pe
in type 2 the IP actually was 240.135.121.200
which is recorded in reverse fashion.
So like this at many places the order in which it is recorded is reverse.
My problem is looking at the logs how do I find the IP from where connection originated when is it  logged as 
A.B.C.D
and when it is logged as D.C.B.A
I am not sure from the log of type 1 I quoted above 
that the IP I should block should be 
115.69.217.3
or
3.217.69.115

---

### Post by mainerror on 2010-10-27
You can use who is on them to find it out. In case of the first one it is already the correct order. The IP is an Indian IP address.

You can tell by looking at this.

> reverse mapping checking getaddrinfo for **dnet-217003.sby.dnet.net.id** [115.69.217.3] failed - POSSIBLE BREAK-IN ATTEMPT!

The TLD says net.id which indicates an Indian provider.

If you run a whois on the reversed IP addess (3.217.69.115) it says the IP address is assigned to the IP pool of General Electric Company. Its TLD is .com.

In case two the IP was also already in the correct order. Apply the same technique for line two. ;)

---

### Post by OpSecShellshock on 2010-10-27
The IP address is the one contained in the brackets.

---

