---
title: "apt-get upgrade crash, update-initramfs udev hook crash"
date: 2015-05-25
forum: Server Platforms
---

### Post by reinaldorauch on 2015-05-25
Hi,

I have a box on Digital Ocean running Ubuntu Server 12.04.04 LTS and I went to update the thing. Doing so provoked a initramfs-tool and kernel update. So far so well until it was building the initramfs image and it chrashed, apparently, in the udev hook:

Link to the output of aptitude: [https://gist.github.com/reinaldorauch/8810d7ba5c543ee518df](https://gist.github.com/reinaldorauch/8810d7ba5c543ee518df)

There is anything that I can do to fix this? Is a production server and I'm afraid that I will not be able to reboot the box until this is fixed.

Thanks in advice ;D

---

### Post by MAFoElffen on 2015-05-26
I was going to tell you to reconfirm that all your software sources point to valid sources... Then recover and kickstart your upgrade process via:
```

sudo dpkg-reconfigure -a

```

--BUT--
What is this on? You say a "Box"... But I see alternate package "[COLOR=#333333][FONT=Consolas]linux-image-virtual[/FONT][/COLOR]"... and /dev's such as /dev/vdX, implyig this is not traditional "box" in the physical sense (metal), but rather a virtual server. Is this correct?

Next, is that I see your pastebin trying to install "linux-image-3.2.0-84-virtual". This is a bit confusing because what I see in the precise main repo tonight as being current is "linux-image-virtual (3.2.0.82.96) [security]". Do you happen to have proposed set in your sources list? Not sure I'd do that on a production server.

That is what I see. The above code may get you going... if all is there for v.84

---

### Post by reinaldorauch on 2015-05-27
> [COLOR=#000000]rather [/COLOR][COLOR=#000000]a virtual server.[/COLOR][COLOR=#000000]
[/COLOR]Yeah, is a virtual server, from Digital Ocean.

> [COLOR=#000000]Next, is [/COLOR]&#8203;[COLOR=#000000]that I see your pastebin trying to install "linux-image-3.2.0-84-virtual"[/COLOR]
Yeah, in my panic, i've tried a dist-upgrade.


Running that command you suggested gave me the output:

```
# sudo dpkg-reconfigure -a
acpid stop/waiting
acpid start/running, process 14529
acpid stop/waiting
acpid start/running, process 14596
acpid stop/waiting
acpid start/running, process 14663
acpid stop/waiting
acpid start/running, process 14730
acpid stop/waiting
acpid start/running, process 14797
acpid stop/waiting
acpid start/running, process 14878
acpid stop/waiting
acpid start/running, process 14945
acpid stop/waiting
acpid start/running, process 15012
acpid stop/waiting
acpid start/running, process 15082
acpid stop/waiting
acpid start/running, process 15152
acpid stop/waiting
acpid start/running, process 15222
acpid stop/waiting

```
... and so on, so that i did a Ctrl+C to stop it as it looked like to be in a infinite loop or something

---

