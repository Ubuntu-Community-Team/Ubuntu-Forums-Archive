---
title: "Which IP blocker"
date: 2009-03-10
forum: Security
---

### Post by tommyperkins on 2009-03-10
Hi,

I've got Firestarter installed on my Ubuntu server but was wondering if anyone could recommend a good IP Blocker?

I've read about Peerguardian, Protowall, MoBlock and IPblock but unsure which one is the most effective?

Thanks.

---

### Post by Nxion on 2009-03-10
Is there something specific you want to block or are you looking for something in general? And when you say that you installed Firestarter on Ubuntu Server, you mean that your are using the desktop version but want to make it a server right?

Firestarted is a GUI front end for iptables. I would recommend also checking out how to configure it at the command line level. This should get you started:
[URL="https://help.ubuntu.com/community/IptablesHowTo"]
https://help.ubuntu.com/community/IptablesHowTo[/URL]

There is a guide that someone wrote for a very simple guide to iptables but I cant find it right now. I will post when I do :)

---

### Post by bodhi.zazen on 2009-03-10
See also : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

If you want a simple black list with a GUI interface see Ipblock : [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by lovinglinux on 2009-03-10
> **tommyperkins said:**
> Hi,

I've got Firestarter installed on my Ubuntu server but was wondering if anyone could recommend a good IP Blocker?

I've read about Peerguardian, Protowall, MoBlock and IPblock but unsure which one is the most effective?

Thanks.

Peerguardian and Protowall are Windows applications. There was a Peerguardian for Linux that doesn't work anymore and has been replaced with Moblock.

Both Moblock and IPBlock (iplist) are great. I prefer moblock because it has bult-in scripts to handle regular iptables rules, so you don't need Firestarter if you know iptables commands.

---

### Post by tommyperkins on 2009-03-10
Thanks for all your replies.

I've installed Ubuntu 8.04 Server Edition but added the GNOME desktop as I feel more comfortable using a GUI. (Get confused working with command line). 

Because of this I'd prefer something with a GUI which can blacklist a database of know bad IP's. I'm using KTorrent and so just after some advice on adding extra security.

Hope this makes sense!

---

### Post by lovinglinux on 2009-03-10
> **tommyperkins said:**
> Thanks for all your replies.

I've installed Ubuntu 8.04 Server Edition but added the GNOME desktop as I feel more comfortable using a GUI. (Get confused working with command line). 

Because of this I'd prefer something with a GUI which can blacklist a database of know bad IP's. I'm using KTorrent and so just after some advice on adding extra security.

Hope this makes sense!

For moblock you can use mobloquer GUI, which is great and it still working, but without a current maintainer (I guess). IPBlock has it's own GUI.

---

### Post by tommyperkins on 2009-03-10
> **lovinglinux said:**
> For moblock you can use mobloquer GUI, which is great and it still working, but without a current maintainer (I guess). IPBlock has it's own GUI.

Ok, thanks. I'll give IPBlock a go alongside Firestarter.

---

### Post by lovinglinux on 2009-03-10
> **tommyperkins said:**
> Ok, thanks. I'll give IPBlock a go alongside Firestarter.

Please keep in mind that you need to start Firestarter before IPBlock or Moblock, otherwise they wont block anything.

> Does IPblock work with other firewall applications ?
Yes. But IPblock needs to be started after other firewall applications. 

> If other firewalls are started/reloaded after MoBlock, then you need to restart MoBlock again. You will be fine, if the iptables rules which send traffic to MoBlock's iptables chains (moblock_in, moblock_out and moblock_fw) stand before all other iptables rules which ACCEPT traffic.

This also applies when you change Firestarter policies. If you change a firewall police when having enabled the option "apply policy changes immediately" or if you then hit the "apply changes" button, then Firestarter rules will override IPBlock rules, making it useless. This means you cannot play around with Firestarter while running IPBlock like you probably did with Windows firewalls and Peerguardian. If you do, then you must reload IPBlock immediately. You will still have a few seconds of unfiltered connections coming through, which could be _____ (fill the blank based on your paranoia level).

---

### Post by hyper_ch on 2009-03-11
are you sure you even need to alter your default configuration and use firestarter?

---

