---
title: "isdnlog/isdnutils: /dev/isdnctrl: No such device"
date: 2010-05-05
forum: Server Platforms
---

### Post by mes2k on 2010-05-05
A few days ago I upgraded my server at home from 9.10 to 10.04 LTS (server amd64). I did a fresh install. isdnlog worked perfectly under 9.10.

A few informations:


```

$ uname -a
Linux droener 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux

```

```

$ lspci | grep ISDN
03:01.0 Network controller: AVM GmbH Fritz!PCI v2.0 ISDN (rev 02)

```

```

$ lsmod | egrep '(isdn|hisax|HiSax|avm|AVM|ISDN)'
hisax_isac 7235 0
hisax 470832 1 hisax_isac
crc_ccitt 1675 1 hisax
isdn 145942 1 hisax
avmfritz 11621 0
mISDNipac 21499 1 avmfritz
mISDN_core 91556 3 avmfritz,mISDNipac

```

If I try to start isdnutils the following error will be shown:

```

$ sudo /etc/init.d/isdnutils start
* Starting ISDN services... * There is apparently no configuration created yet.
* You can create configuration files with the 'isdnconfig' tool.
*
* If you don't want this warning in future, please create the file
* /etc/isdn/noconfig
* For more information, see /usr/share/doc/isdnutils-base/HOWTO.isdnutils.gz
isdnlog/dev/isdnctrl: No such device

```

With 9.10 I didn't need an isdn or capi config, the "no configuration" message also appeared under 9.10. It isn't needed for isdnlog, since it just is an "isdn sniffer".

Output ot isdnctrl:

```

$ sudo isdnctrl list all
Can't open /dev/isdnctrl or /dev/isdn/isdnctrl: No such device

```

But ls seems to find everything:

```

$ ls -lsa /dev/isdnctrl
0 lrwxrwxrwx 1 root root 9 2010-04-30 13:59 /dev/isdnctrl -> isdnctrl0

```

The symlink does exist:

```

$ ls -lsa /dev/isdnctrl0
0 crw-rw---- 1 root dialout 45, 64 2010-04-30 13:59 /dev/isdnctrl0

```

---

### Post by mes2k on 2010-05-06
Today's update to 2.6.32-22-server and changing the card to an AVM GmbH A1 ISDN [Fritz] (rev 02) didn't change a thing...

---

### Post by mes2k on 2010-05-10
The following solved the problem for me:

```

$ tail -3 /etc/modprobe.d/blacklist.conf 
blacklist mISDNipac
blacklist mISDN_core
blacklist avmfritz

```

---

### Post by JujuLand on 2010-06-21
Hi,

I have a similar problem with a Gazel card. It worked with 8.10, but I'm not able now to make it work on a fresh 10.04 install .

I have used an old doc here (in french)  [http://doc.cliss21.com/index.php?title=Configuration_de_l%27acc%C3%A8s_internet_avec_RNIS_%28Num%C3%A9ris_-_ISDN%29]("http://doc.cliss21.com/index.php?title=Configuration_de_l%27acc%C3%A8s_internet_avec_RNIS_%28Num%C3%A9ris_-_ISDN%29")

but I'm not sure that it can work.

I have installed :

isdnutils-doc, isdnutils, isdn-xtools and ipppd

I have tried to blacklist mISDN and hfcpci modules, but It doesn't change something, I have a message (device not found) 

I have seen that I load capi modules, is-it necessary (I haven't installed it, but it's already there)  ???

Can you help me ? 

Thanks for your answer

A+

---

### Post by JujuLand on 2010-06-23
Hi, 

The solution given by mes2k was good.

I just have had a problem with the modprobe command. One parameter was missing, and the file hisax.conf wasn't created in modprobe.d

That's now ok, except a little problem. The connection is launched when strating isdn service, and I have found, for now, no way to avoid this and also to launch connection or disconnection.

But I think to find a way to do that.

A+

---

