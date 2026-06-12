---
title: "- Tips"
date: 2010-03-15
forum: Security
---

### Post by NiGhtMarEs0nWax on 2010-03-15
any security tips for setting up a small home server?

it will have some basic public access to a bit torrent client, (sharing copyright **free** material ofc).

i have a standard install of Ubuntu Server with the xfce desktop, I'm looking for some basic tips.

different guides  point out different things, i was wondering if all of it was at all necessary.  what steps would you take any why?

Thanks.

---

### Post by CharlesA on 2010-03-15
If you only have a torrent going and no other services running, you should be fine with the default security settings.

---

### Post by HermanAB on 2010-03-16
Well, whatever you do - do not install VNC.  Just look a few posts down for yet another tale of VNC woe.

---

### Post by CharlesA on 2010-03-16
> **HermanAB said:**
> Well, whatever you do - do not install VNC.  Just look a few posts down for yet another tale of VNC woe.

This. If you do install VNC, secure it properly and tunnel it over SSH.

---

### Post by NiGhtMarEs0nWax on 2010-03-16
Thanks, yes, all I will be doing is running a torrent client inside a virtual machine and/or chroot through a vpn client. no other services running inside the virtual machine.

I was considering some tight iptables to allow only the needed ports for torrent and vpn traffic both in and out + a couple of other essential ports.

for the host I will require some kind of remote desktop as opposed to vnc, simply because its not easy to manage virtualbox and a torrent client through a shell. the reason I require remote desktop is because vnc will create its own login session as far as I know, so it doesn't help me with managing the current user desktop session.

I was also considering iptables for the host that completely blocked all access from the virtual machine that is running on a bridged interface and allow only the specified address,  my address.


i couldn't be sure that this is safe, so i asked you guys. what do you think?

are there any alternatives? how would i go about securing a remote desktop/vnc session besides running it over ssh?

Thanks. :)

---

### Post by cariboo on 2010-03-16
Have a look [here]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server"), for a howto on setting up a headless vm. The instructions are for VirtualBox 2.0,  but they should work with the latest version.

---

### Post by NiGhtMarEs0nWax on 2010-03-16
Thanks, i've decided against it, it hogs too much resources, it would be running on an old athlon 1800+, I've decided to go for a chroot instead.

any specific tutorials or pointers? Thanks.

---

### Post by NiGhtMarEs0nWax on 2010-03-17
bump.

---

### Post by bodhi.zazen on 2010-03-17
> **NiGhtMarEs0nWax said:**
> different guides  point out different things, i was wondering if all of it was at all necessary.  what steps would you take any why?

Thanks.

There is no substitution for understanding what and why you are doing the things suggested in the guides.

You will get different opinions to consider.

I suggest you start with the stickies at the top of the forums.

Otherwise we can answer specific questions, but only you can answer such a broad question for yourself.

If you are finding the various guides and blogs confusing you need to go to teh more technical documentation upon which things are based.

For example : [http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

### Post by NiGhtMarEs0nWax on 2010-03-18
Thanks, was helpful. I'm reading it now. I will be sure to ask you guys some questions when I am done.

I will leave this thread open for now. :)

---

