---
title: "Use home server as proxy when abroad?"
date: 2011-03-11
forum: Server Platforms
---

### Post by grenness on 2011-03-11
At home I have an Ubuntu 10.10 Server which is my fileserver and squeezebox server for my home LAN.

My home internet connection is a 10/10Gbit fiber (soon to be upgraded to 25/25, I was told by my ISP).

How hard is it for me (I'm not too technical) to make my home server a proxy for surfing through when I am abroad?

The thing is: our national broadcaster ([www.nrk.no](www.nrk.no)) broadcasts live streaming TV, but only to IP addresses in Norway. When I am travelling abroad, I would like to use my home server as a proxy in order to be able to receive these streams as if I was on my home IP address (more or less like the services offered from the US in order to make it possible for non-US people to watch hulu.com etc.)

I would prefer a proxy setup, instead of slingbox or similar.

I tried searching the forums, but if there are solutions I missed I apologize.

Thanks,
Christopher

---

### Post by Lars Noodén on 2011-03-11
Your searches turned up nothing because the task is very easy -- once you know how.  

If you run the OpenSSH server on your home box, then you can connect to it as a [SOCKS proxy](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#SOCKS_Proxy) with the -D option.  

You would configure your browser to use the proxy  on the local host on port 8080 or any other port you choose.

```

  ssh -D 8080 -l myloginname *xx.yy.zz.aa*

```

For that to work you have to have SSH (port 22) [visible from outside](http://canyouseeme.org/) on your home machine so that you can make the connection.

---

### Post by grenness on 2011-03-11
> **Lars Noodén said:**
> You would configure your browser to use the proxy  on the local host on port 8080 or any other port you choose.

```

  ssh -D 8080 -l myloginname *xx.yy.zz.aa*

```


Thank you very much!

---

