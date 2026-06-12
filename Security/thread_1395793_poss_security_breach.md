---
title: "poss security breach"
date: 2010-02-01
forum: Security
---

### Post by johnh10000 on 2010-02-01
Hi folks been have a few probs over recent days.  so as firestarter is not that easy to configure, i went for firehol!

now still don't know how to use that properly.

now after a quick sudo tcpdump -n -i eth0 > tcpdump.txt

its obvious to me at least that anything 85.9.102.*  is not to be trusted.
see attached.

how do i ban everything and anything from that block, pref without upsetting firehol.  whats opinions of ipcop, btw.

---

### Post by frodon on 2010-02-01
Moved to Security discussion.

Just in case you are not aware of it, firestarter is obsolete and can conflict with ufw , one should use **gufw** instead.

So my best advice is to uninstall firestarter first and install gufw, then if you have issues with it report them here.

---

### Post by bodhi.zazen on 2010-02-01
> **johnh10000 said:**
> Hi folks been have a few probs over recent days.  so as firestarter is not that easy to configure, i went for firehol!

now still don't know how to use that properly.

now after a quick sudo tcpdump -n -i eth0 > tcpdump.txt

its obvious to me at least that anything 85.9.102.*  is not to be trusted.
see attached.

how do i ban everything and anything from that block, pref without upsetting firehol.  whats opinions of ipcop, btw.

You are making this more complicated then it has to be.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Or simply try iplist (simple blacklist).

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

More important , read the security sticky.

---

### Post by johnh10000 on 2010-02-01
> 
Or simply try iplist (simple blacklist).

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

More important , read the security sticky.
[/quote]

thanks not sure if i was being over paranoid!,  i found iplist, while i was waiting for, you guys replies.  so bolked them now anyways.

thanks

---

