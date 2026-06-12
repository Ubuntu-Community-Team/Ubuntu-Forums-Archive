---
title: "Ventrilo Only Working Locally"
date: 2008-10-29
forum: Server Platforms
---

### Post by cj_g0bl1n on 2008-10-29
I installed Ventrilo on my server box today.  I can get it to work locally on my network, but not on the outside web.  Here is the steps I took to install it:

1) Upload the file to the machine that you plan on running the server on. This is only important if the host computer is not the same as the computer you are currently using.

2) Open a terminal window (telnet or OpenSSH) to the host computer that will be running the server.

3) Set your working directory to where ever you want to create the ventrilo directory.

4) Type "mkdir ventrilo"

5) Type "cd ventrilo"

6) Copy the tar.gz file into this new directory.

7) Type "gunzip " followed by the name of the tar.gz file.

8) Type "tar xf " followed by the name of the tar file. (gunzip removed the gz extension).

9) Note: Some platforms allow for combining steps 7 and 8 into a single command by typing "tar zxf " followed by the name of the tar.gz file.

10) Type: "./ventrilo_srv".

Ok, then I changed the settings in the .ini file for the name and all of the good stuff like passwords, etc... (Later on I took all of this out to test if it was something I did, it wasn't.)

Then I went on my router, and on the port forwarding I set the port to 3784 (this is the port for vent, I looked it up and everything) and set the protocol to TCP (because its a TCP port...)

Now I have my server running a web and file server as well, and I'm using DynDNS for a DDNS server.  So I try both my server IP address(the global one) and my DDNS server name.  Neither work, but if I am on the same network(on the same router) then I can connect to the vent server.

So I know I'm missing something, can someone point it out for me!?

Thanks,
goblin

---

### Post by cariboo on 2008-10-29
Is ventrilo actually running? type at the prompt:

```
ps ax | grep ventrilo
```

This should tell you if the server is running or not.

Jim

---

### Post by cj_g0bl1n on 2008-10-30
Seems that I had a 2.0 client trying to connect to a 3.0 server...how am I able to connect locally then?  Weird...  Thanks for the help!

---

