---
title: "Is Pulseaudio secure?"
date: 2018-05-26
forum: Security
---

### Post by Sami_Mattila on 2018-05-26
Why is my ubuntu sound system trying to call home?

May 26 14:06:08 kubuntu18 pulseaudio[1177]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by TheFu on 2018-05-26
I'm fairly clueless, but that never stopped me from guessing. ;)

Java introduced using reverse domains as a way to keep packaging namespaces unique and hierarchical.  They look like network resources, but usually aren't. Languages like "Go" do use network-based code by design, but I don't think that is involved here. 

"freedesktop" is the Gnome project. It is huge, so I suspect they decided the only way to keep their different projects organized was to follow the reverse namespace technique.  This greatly helps with bug reporting. We can see from the error that DBus is having problems, though I doubt it is actually dbus itself, but probably pulse audio putting things onto the bus, which aren't being pulled off by another part of pulse audio, at least not in the expected time.  DBus is a middleman, like a computer or network bus.

Pulse has network protocols inside because sockets are a convenient way to communicate between process on the same machine or in different machines. If the developer can allow that, easily, making a process both local and remote capable for no added effort, usually that is a smart idea.  When client and server programs try to communicate, but cannot (for any reason), it is common to say "did not receive a reply" - that doesn't mean any networking is leaving the system at all.  I would read this as 1 side of  the C/S pair is failing to respond, which is a common thing with PulseAudio, IME.  

If you really want to know what network traffic is or isn't happening, use a network sniffer to capture packets. This is an intermediate skill to master.

Whether any program is secure is harder to answer.  Assume none are secure and you won't be disappointed.  We know that Bluetooth is NOT secure at all.

---

