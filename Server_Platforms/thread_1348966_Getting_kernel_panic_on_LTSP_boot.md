---
title: "Getting kernel panic on LTSP boot"
date: 2009-12-07
forum: Server Platforms
---

### Post by Frogging101 on 2009-12-07
I have set up an LTSP server with a 64-bit desktop computer. This computer is running Ubuntu 9.10 64-bit Desktop Edition. The computer is hooked up to a laptop via crossover cable. I do not use raid.

The problem:

When the client (the laptop) boots, it loads the initrd and vmlinuz, and then prints a long string of messages that are too fast to read, and then stops, with the errors:

```
md: if you don't use raid, use raid=noautodetect
**[A few more messages and then lists some partitions]**
No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(8,1)
Pid: 1, comm: swapper Not tainted 2.6.31-16-generic #52 Ubuntu
```

I'm not listing the Call Trace, but if it's important, tell me and I will post it! I need a fix for this problem, and I must say that in the past this forum has been of very little help, because I don't get many answers at all.

Thanks!

---

### Post by Frogging101 on 2009-12-08
Bump. Any answers?

---

### Post by Vegan on 2009-12-08
Get a real switch, they are very cheap now.

---

### Post by lykwydchykyn on 2009-12-08
Your client is failing to mount the root filesystem.

Did you set it up using NBD (default, I think) or NFS?

Can you post /etc/nbd-server/config or /etc/exports?

And did you generate the client image?

---

### Post by lykwydchykyn on 2009-12-08
> **Vegan said:**
> Get a real switch, they are very cheap now.

Crossover cables work fine, and getting a switch isn't going to fix the problem.

I use a crossover cable for testing and staging LTSP before deployment, never had problems with this approach.

---

### Post by Frogging101 on 2009-12-08
> **lykwydchykyn said:**
> Your client is failing to mount the root filesystem.

Did you set it up using NBD (default, I think) or NFS?

Can you post /etc/nbd-server/config or /etc/exports?

And did you generate the client image?

I tried an NBD setup, and if generating the image means running sudo ltsp-build-client, then yes I did generate the image.

Here is my /etc/nbd-server/config:
```

# If you want to run everything as root rather than the nbd user, you
# may either say "root" in the two following lines, or remove them
# altogether. Do not remove the [generic] section, however.
	user = nbd
	group = nbd

# What follows are export definitions. You may create as much of them as
# you want, but the section header has to be unique.
[export]
exportname = /opt/ltsp/amd64/
port = 2002

```

Thanks for your help!

---

### Post by lykwydchykyn on 2009-12-08
This is a dumb question, I guess, but does the client have a 64 bit processor?

---

### Post by Frogging101 on 2009-12-08
> **lykwydchykyn said:**
> This is a dumb question, I guess, but does the client have a 64 bit processor?

I think so, it says AMD Athlon X2, and then a small '64' in the bottom left on the sticker. Does that mean it can do 64 bit?

---

### Post by lykwydchykyn on 2009-12-08
> **Frogging101 said:**
> I think so, it says AMD Athlon X2, and then a small '64' in the bottom left on the sticker. Does that mean it can do 64 bit?

I would assume so, though if nothing else works maybe try generating a 32-bit client image.

I'm not sure what to suggest next, we might need a bit more of the error messages.

---

### Post by Frogging101 on 2009-12-08
You mean the call trace? Because there is nothing after that, and I can't see anything 'above' what I posted. I also checked the logs, but there is nothing there.

---

### Post by Frogging101 on 2009-12-08
Bump.

---

### Post by lykwydchykyn on 2009-12-09
Post the contents of /etc/ltsp/dhcpd.conf.  By default, it points clients to /opt/ltsp/i386 for the root fs.

---

### Post by Frogging101 on 2009-12-09
I deleted the 64-bit client (/opt/ltsp/amd64) and rebuilt it using 32-bit. Now, my problem is that the screen is completely blank when I boot it! This is what happens:

1. I turn on my laptop
2. The laptop gets a IP from the desktop DHCP server
3. The laptop downloads initrd.img and vmlinuz
4. The screen goes blank, and only responds to CTRL+ALT+DEL

And also, here is my dhcpd.conf:
```

# /etc/dhcp3/dhcpd.conf #
# General options
option dhcp-max-message-size 2048;
use-host-decl-names on;
deny unknown-clients; # This will stop any non-node machines from appearing on the cluster network.
deny bootp;

# DNS settings
option domain-name "ANTANICLUSTER";          # Just an example name - call it whatever you want.
option domain-name-servers 192.168.3.1;  # The server's IP address, manually configured earlier.

# Information about the network setup
subnet 192.168.3.0 netmask 255.255.255.0 {
  option routers 192.168.3.1;              # Server IP as above.
  option broadcast-address 192.168.3.255;  # Broadcast address for your network.


filename "ltsp/i386/pxelinux.0";
option root-path "/opt/ltsp/i386/";
}

# Declaring IP addresses for nodes and PXE info
group {

  host kerrighednode1 {
        fixed-address 192.168.3.101;          # IP address for the first node, kerrighednode1 for example.
        hardware ethernet 00:1e:68:b2:f1:af;  # MAC address of the node's ethernet adapter
  }

  host kerrighednode2 {
        fixed-address 192.168.3.102;
        hardware ethernet 01:2D:61:C7:17:87;
  }

  host kerrighednode3 {
        fixed-address 192.168.3.103;
        hardware ethernet 01:2D:61:C7:17:88;
  }
  host kerrighednode4 {
        fixed-address 192.168.3.104;
        hardware ethernet 01:2D:61:C7:17:89;
  }
  host kerrighednode5 {
        fixed-address 192.168.3.105;
        hardware ethernet 01:2D:61:C7:17:90;
  }
  host kerrighednode6 {
        fixed-address 192.168.3.106;
        hardware ethernet 01:2D:61:C7:17:91;
  }


  server-name "ANTANICLUSTERSERVER"; # Name of the server. Call it whatever you like.
  next-server 192.168.3.1;       # Server IP, as above.
}
```

---

### Post by lykwydchykyn on 2009-12-09
Ok, well, the original problem was that the client was looking in /opt/ltsp/i386 and the client image was at /opt/ltsp/amd64.

But if you rebuilt with a 32 bit client that should be ok now.

At this point it sounds like a video driver or video resolution issue.

Unfortunately I don't have my LTSP server available to reference at the moment, but if you know (or can find out) how to do it you might try:

 - making the client use vesa drivers
 - setting a low resolution for the client, like 800x600
 - making the client boot to a terminal only, just to make sure it's working.

If I get a chance to look at my LTSP server, I can provide more details or ideas.

---

### Post by Frogging101 on 2009-12-09
The problem somehow got fixed. Now, it goes to the GUI login interface. But there is a problem. I have made a new topic describing the problem here: [http://ubuntuforums.org/showthread.php?p=8471601]("http://ubuntuforums.org/showthread.php?p=8471601")

---

