---
title: "Does Telnet Use an Internal IP Address?"
date: 2008-11-02
forum: Security
---

### Post by f.ben.isaac@gmail.com on 2008-11-02
"**telnet uses an internal IP address which is already IPv6 and whcih was mapped to the 127.0.0.1 you have configured as only (default) IP address.**"

I have not understood it fully. Can you re-explain it to me in an easier way. I just need to make sure that i understood it as i should be.

I connect from a telnet to a simple TCP server that i have created, i get such an output:

Sent 35 bytes to client : ::aff:c0fd:7fbf
Sent 35 bytes to client : ::ffff:127.0.0.1
Sent 35 bytes to client : ::ffff:127.0.0.1
Sent 35 bytes to client : ::ffff:127.0.0.1

Question was why fist IP address appears differently the second one...

The answer is given above but i need to confirm what i understood.

Note: the code that grab the client IP, is the follow:
```

.
.
.
 if (clientAddress->sa_family == AF_INET) {
                struct sockaddr_in *ipv4 = (struct sockaddr_in *)clientAddress;
                addr = &(ipv4->sin_addr);
                return addr;
        }else{
                struct sockaddr_in6 *ipv6 = (struct sockaddr_in6 *)clientAddress;
                addr = &(ipv6->sin6_addr);
                return addr;
        }
.
.
.

```

Advice!

---

### Post by cariboo on 2008-11-02
The first address looks like and ipv6 address. If you type in a terminal:

```
ifconfig
```

you will see the ipv6 address in the output eg:

```
Link encap:Ethernet  HWaddr 00:16:17:9c:84:b5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          **inet6 addr: fe80::216:17ff:fe9c:84b5/64** Scope:Link
```

IPv6 is on my list of things to learn about in the near future.

Jim

---

### Post by f.ben.isaac@gmail.com on 2008-11-02
Thanks

---

### Post by stmurray on 2008-11-03
The first thing you should do is stop using telnet and switch to ssh :) 

If you want telnet to use just IPV4, there should be a "listen" directive in it's config file that you can set (that's how it works in ssh-  for example if you want ssh to listen on all IPV6 ports you say 

```
ListenAddress ::
```

If you want to use IPV4 you say:


```
ListenAddress 0.0.0.0
``` 

)

---

