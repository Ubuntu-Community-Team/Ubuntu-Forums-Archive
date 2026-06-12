---
title: "Unable to create network via Bridged Adapter."
date: 2016-03-02
forum: Virtualisation
---

### Post by Raymond Curtis on 2016-03-02
Hello guys,

I've spent many hours reading about similar problems and did everything I could to solve it on my own. My host is Windows 7, my guest is Ubuntu 15.10. I am not able to connect from my guest to host and the other way around. 
```

eth0      Link encap:Ethernet  HWaddr 08:00:27:64:53:c4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:273803 (273.8 KB)  TX bytes:273803 (273.8 KB)
```

And here are the contents of my interfaces file:[FONT=arial]

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

What can I do? Could you please help me to diagnose the problem.

Thank you.[/FONT][FONT=Arial][FONT=courier new]
[/FONT][/FONT]

---

### Post by houstonbofh on 2016-03-02
Looks like Ubuntu is fine, but the guest is not seeing the network at all.  Look to your virtualization software for this.

---

### Post by Raymond Curtis on 2016-03-03
Thank you, I will ask on their forum then.

---

### Post by MAFoElffen on 2016-03-03
There were a few things not asked in this thread... 
(1) What was the hypevisor? 
(2) Since the host was Windows, did the OP create a virtual switch from within that hypervisor, to bridge from that hypervisor's internal to host's network?

---

### Post by Raymond Curtis on 2016-03-30
Hello MAFoElffen

Thank you for your interest. Sorry but my linux knowledge is not sufficient to answer the questions you've asked.
The only thing I can say is that I haven't created any virtual switch, atleast I don't know anything about it. 
Is it possible for you to tell me how to obtain information you need to help me to solve this issue?

Regards.

---

### Post by SeijiSensei on 2016-03-30
You don't have an address assigned to eth0, nor do you have an entry for it in the interfaces file.  If you're using a bridged adapter, and your router assigns addresses with DHCP, add this to /etc/network/interfaces:

```

auto eth0
iface eth0 inet dhcp

```

---

### Post by MAFoElffen on 2016-03-31
Sideline note: Please go back to your first post > Select edit > Select advanced edit> select / highlight your output code in that post > select / press the "[SIZE=4]**#**[/SIZE]" code tag icon in the thread tools menu. Forum policy says that all code and commands should be within code tags.
## End sideline note

A Hypervisor refers to the "software" you are using to run a Virtual Machine, such as VirtualBox, or VMware Player, KVM, etc...

There are missing pieces of this puzzle: Post #2 said Ubuntu was fine... That statement was a bit premature. According to the title of your thread, you say you have a bridge. If you had an existing "bridge" to your host machine's network, then you need to confirm that the bridge is present. 

Respect to SeijiSensei, in that the file /etc/network/interfaces is not part any output of your posts, so he is assuming that is not there... What he suggests will work, if that was not present in that file, ***and*** if a bridge really does exist on your host... In diagnostics: Confirm what is present and working > Cross-off what is "not wrong" > Look for what is wrong > Fix the root of the problem.

You say your host is Windows and your guest is Ubuntu...
(1) From your Win Host-- Open a cmd window (<Win><R>cmd.exe) and post the output of
```

ipconfig /all

```
(2) From your Ubuntu VM Guest terminal console(<Cntrl><Alt><T>), please post the output of
```

cat /etc/network/interfaces

```
(3) Please answer which Virtual Machine software you are using to run your Ubuntu guest VM.

Answers to those 3 will give us invaluable info for us to be able to assist you. Without that info, we are guessing at what you *might* have going on...

---

### Post by SeijiSensei on 2016-03-31
> **MAFoElffen said:**
> Respect to SeijiSensei, in that the file /etc/network/interfaces is not part any output of your posts, so he is assuming that is not there...
With all due respect, the OP has this:

> **Raymond Curtis said:**
> And here are the contents of my interfaces file:
[FONT=courier new]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
[/FONT]

So if that is the interfaces file, it's missing the stanza for eth0.

---

### Post by MAFoElffen on 2016-03-31
I stand corrected. I missed that. ( ::embarrassed:: )

---

