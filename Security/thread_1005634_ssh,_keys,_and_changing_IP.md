---
title: "ssh, keys, and changing IP"
date: 2008-12-08
forum: Security
---

### Post by candtalan on 2008-12-08
I am starting out with ssh, rsa keys and vnc with tunnelling and port forwarding, and have got so far, so good, with help that is.

The server end machine is currently using a static address inside the LAN but its router is given a different IP from the ISP occasionally.

My question is, will the change of external IP affect anything other than the target address that I use for connection? Will the change, for example, make any keys invalid?

I can live with the change of IP address because the machine is attended and the owner can happily tell me what the IP lookup is at any time, but if such things wreck the rsa validity then I will probably need a different cunning plan. 
tia

---

### Post by bodhi.zazen on 2008-12-08
You should be good to go.

---

### Post by dfreer on 2008-12-10
You can also use the free dyndns service (along with the ddclient program) to keep track of the external IP address of that machine, makes it a lot easier than having to call up the owner of the machine.

Basically, it works like this: You register a free domain name for your machine, like mySSHmachine.dyndns.org. The client every X amount of minutes checks a page on the dyndns website, that reports back the current external IP address. The client sends this information to the dyndns servers, and if the external IP address has changed they update their DNS servers to associate the new IP address with the name mySSHmachine.dyndns.org.

So instead of connecting to the external IP address directly, you connect to the domain name and a DNS lookup will connect you to the proper machine, without the need to contact anyone.

When you connect to a server via SSH, it's Server Key is stored in a file, ~/.ssh/known_hosts IIRC. I do believe you will get a warning from your SSH client if a known host's IP address changes, it should say something about a possible Man-in-the-Middle attack. Just something to be aware of.

EDIT: It shouldn't invalidate any keys or anything like that, like the above poster said.

---

### Post by capn_hector on 2008-12-10
i used the setup dfreer suggested and if you add the domain name your dns service gives you to your recognized hosts file you will not get the mitm warning.

---

