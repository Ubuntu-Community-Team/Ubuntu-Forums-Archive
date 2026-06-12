---
title: "VPN was working, and still is, but with error"
date: 2011-09-08
forum: Server Platforms
---

### Post by elkingrey on 2011-09-08
Hello, 
 
I am getting this error when I connect to my VPN: 
 
SIOCADDRT: File exists 
Thu Sep  8 03:33:58 2011 ERROR: Linux route add command failed: external program exited with error status: 7 
 
My VPN reaches Initialization Sequence Completed and the traffic to and  fro is fine, but I would still like to get rid of that error. 
 
If you can help me fix this I would be very grateful. Thank you.

---

### Post by SeijiSensei on 2011-09-08
> **elkingrey said:**
> 
SIOCADDRT: File exists 
Thu Sep  8 03:33:58 2011 ERROR: Linux route add command failed: external program exited with error status: 7

The route was probably already established when the command was run.  Either the route command being executed by the VPN startup is redundant, or you restarted the VPN after the route was already established.  If you can edit the script that creates the route, add a line right above it that deletes the route first:

```

ip route del 192.168.1.0/24 via 10.10.10.10
ip route add 192.168.1.0/24 via 10.10.10.10

```

If you want to be really obsessive, you can add some more code to determine whether the route already exists ("route -n | grep '192.168.1.0'") then run the delete command only if it's needed.

---

### Post by elkingrey on 2011-09-08
Interesting. I must have somehow restarted the VPN after it was already established because today I booted my computer and just now connected to my VPN and did not get any errors.

I'm curious though, last night I had disconnected and reconnected several times to my VPN. I don't understand why it still thought I was connected even though I disconnected? Well, anyways, a fresh boot with my computer seems to have solved it. Can you explain to me how this could have happened? Thanks!

---

### Post by SeijiSensei on 2011-09-08
> **elkingrey said:**
> I don't understand why it still thought I was connected even though I disconnected? Well, anyways, a fresh boot with my computer seems to have solved it. Can you explain to me how this could have happened? Thanks!

I don't think you were still connected, but the route was still in the routing table.  Some routes should vanish when the interface is deleted; I'd need to see the actual commands to know more.

For instance, if you have a route like 
```
ip route add 192.168.1.0/24 dev tun0
```
bringing down tun0 by stopping the VPN wil destroy this route.  Other routes that send packets "via" an upstream gateway like the ones I posted above may survive dropping the tunnel.  For instance, a route like 
```
ip route add 192.168.1.0/24 via 10.10.10.10
```
should survive when the tunnel is destroyed because 10.10.10.10 might still be reachable via the host's default gateway.  In reality, of course, if 10.10.10.10 is the address of the remote end of the tunnel, it will be unreachable if the tunnel doesn't exist, but the OS doesn't know that.

---

### Post by elkingrey on 2011-09-09
Is there anything you'd like to see or me to do? Or should we consider this solved?

---

### Post by SeijiSensei on 2011-09-09
If you're willing to live with the occasional irrelevant error, then just leave things as they are.  If you wrote the script that sets up routes, you might consider rewriting the routing command(s) using one of the approaches I outlined earlier.

You could also suppress the error by adding the text:

```
 > /dev/null 2>&1
```

to the end of the command that sets up the route.  That directs all output from the routing command, including errors, to the null device so it won't be displayed.

So, in general, I think this is [Solved].

---

### Post by elkingrey on 2011-09-09
Thanks!

---

