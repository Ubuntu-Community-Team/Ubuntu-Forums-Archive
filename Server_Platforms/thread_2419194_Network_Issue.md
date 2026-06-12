---
title: "Network Issue"
date: 2019-05-17
forum: Server Platforms
---

### Post by Bashed on 2019-05-17
Can't' figure out what someone did to this freshly installed server, but please see attached. Ubuntu 16.

The /etc/network/interfaces is still exactly how I set it up. So I'm a bit confused. Rebooting server didn't fix it either. The server has a full /24 C class subnet routed to it.

[ATTACH=CONFIG]283278[/ATTACH][ATTACH=CONFIG]283279[/ATTACH]

---

### Post by TheFu on 2019-05-17
Please post text, not images. People using screen readers can't help with images.  Any command you run can be redirected to a file then either use the mouse to select/paste it or transfer it to a system where you can.   When posting text output, please use 'code tags' so it lines up the same here as it did in the terminal.  Adv Reply (#) or Adv Edit (#)

What is the behavior?  "Issue" is vague.
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has some troubleshooting steps. I suspect you need to start at the "Next Steps" section and post that information ... as text, using code tags, please.

---

### Post by Bashed on 2019-05-17
I cannot post text. I cannot access via SSH. I had to connect via KVM (iDRAC 6) using Java. There's no ability to copy text from the virtual console window.

---

### Post by Bashed on 2019-05-18
Anyone?

---

### Post by TheFu on 2019-05-18
> **Bashed said:**
> I cannot post text. I cannot access via SSH. I had to connect via KVM (iDRAC 6) using Java. There's no ability to copy text from the virtual console window.

You can transfer files if there is a network connection using pipes for emergencies like this. 
[https://www.tecmint.com/transfer-files-between-two-linux-machines/](https://www.tecmint.com/transfer-files-between-two-linux-machines/)
 nc is usually already installed. If you don't have pv, ignore it.

So, run the commands to gather data in the link in the prior post, storage that into a file, edit the file so it is clear which output goes with exactly which command, transfer the text file to your workstation and copy/paste the output here.
Please.

I looked at the image, zoomed way in, all it says is that the networking didn't start. Without more details,  nobody can help.

---

### Post by DuckHook on 2019-05-18
> **Bashed said:**
> …freshly installed server…
I'm the furthest thing from a server guru of the sort TheFu is, but did notice this &#8593;

If it's freshly installed, perhaps the most practical advice would be to just reinstall?

---

