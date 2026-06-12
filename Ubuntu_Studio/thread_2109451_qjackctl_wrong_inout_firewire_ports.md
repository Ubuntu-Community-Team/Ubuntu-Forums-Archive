---
title: "qjackctl wrong in/out firewire ports"
date: 2013-01-27
forum: Ubuntu Studio
---

### Post by roughi on 2013-01-27
hello
i don't know what happenend, but when i open 'connect' in qjackctl my firewire interface is represented wrongly, in-channels are on the output ports side and vice versa.
I just made my system running and got some sound thru guitarix. Then i tested soundlooper without any luck, and now today the system is upside down, grmbl... does someone know about this problem?

---

### Post by jejeman on 2013-01-27
Left are capture, right are playback, or not?
And these are not firewire ports, just audio ports.

---

### Post by roughi on 2013-01-27
Hi jejeman, 
ok, i mean audio ports. 
i added a printscreen, it says left side playback, right side capture. 
i remember, while setting up, i had 2 firewire cables connected, did this all mix up? is there a qjackctl config file to check?

---

### Post by jejeman on 2013-01-27
Well, I would take "in" as "capture", and "out" as "playback".
It can be confusing. It says above:
On the left: readable clients/output ports, which are practicly *hardware* input ports
On the right: writeable clients/input ports, which are practicly *hardware* output ports.

It is all alright, belive me. ;)

When you look this image with simple setup
[http://drobilla.net/blog/wp-content/uploads/2010/12/patchage.png](http://drobilla.net/blog/wp-content/uploads/2010/12/patchage.png)
You can see how *hardware* output ports recives signal - that is why it is *software* input port. And *hardware* input ports sends signal - that is why it is *software* output port.

I hope that this makes it clear.

---

### Post by roughi on 2013-01-28
Well, the thing is, it's not working anymore. Before i just could start guitarix and jackd and the connections were already there. Now they’re gone. 
Also strange is, that there is an firewire_in and below gx_head_amp out-port.  If i connect by hand, i get strange beeps every second. I still doubt that in/out is cranky.

like i said, i had a proper system, until i fiddled around with audacious and sooperlooper. What happened?!

---

### Post by roughi on 2013-02-07
Ok, reinstalled qjackctl and jackd with synaptic and somehow it works  again. You were right about in/out audio ports, the problem was  somewhere else.

---

