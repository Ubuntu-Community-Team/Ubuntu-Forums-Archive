---
title: "LTSP - Thin Clients eth0 address"
date: 2011-12-03
forum: Server Platforms
---

### Post by federico85.85 on 2011-12-03
Hi guys!

After long trials i've been able to set up an LTSP server using ubuntu 11.04 and it looks like working fine:

- Thin clients boot and get their IP address;
- I get up to the login screen (in the bottom right corner appear client's name  and correct IP address);
- Users can login and work correctly.

There's just one thing i don't understand:
When i'm logged in - if i run sudo ifconfig - it shows me that client's eth0 got the same ip of server's eth0 and not the ip my client got during boot.

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Is this correct? 

Before using thin clients i tried to build a fat client and the ip shown for eth0 running sudo ifconfig was the same i got in the login screen next to the client's name.
  
I googled a lot looking for an explanation but with no success.

Hopin' someone could help me, thanks in advance for your help!

---

### Post by newbie-user on 2011-12-03
That's because a thin client runs everything off of the server and the server does all the work.  The IP of the client would appear to be the same as the server since the server will be making all network requests and not the client.

---

### Post by federico85.85 on 2011-12-04
Thanks for your reply... 
So it was as I started thinking... i just wanted to be sure.
But if clients ip appear to be as the server's one how can i ping or connect via ssh to my thin clients?
Is there a way to get the ip assigned by DHCP to the client or is this address useless?

Thanks again...

---

### Post by newbie-user on 2011-12-04
You won't be able to ping or ssh to a thin client because the thin client runs entirely off the server.  A fat client, on the other hand, would be able to use it's own ip address.  

I've had this problem when trying to do filtering and proxying on my network.  For thin clients, I'd have to filter the server.

---

