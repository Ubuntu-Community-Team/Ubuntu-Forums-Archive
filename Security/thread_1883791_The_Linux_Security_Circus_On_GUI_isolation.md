---
title: "The Linux Security Circus: On GUI isolation"
date: 2011-11-19
forum: Security
---

### Post by BigCityCat on 2011-11-19
Can someone explain this to me? It sounds serious.

[http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html](http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html)

> So, let me stress this one more time: if you have two GUI applications, e.g. an OpenOffice Word Processor, and a stupid Tetris game, both of which granted access to your screen (your X server), then there is no isolation between those two apps. Even if they run as different user accounts! Even if they are somehow sandboxed by SELinux or whatever! None, zero, null, nil!

The X server architecture, designed long time ago by some happy hippies who just thought all the people apps are good and non-malicious, simply allows any GUI application to control any other one. No bugs, no exploits, no tricks, are required. This is all by design. One application can sniff or inject keystrokes to another one, can take snapshots of the screen occupied by windows belonging to another one, etc.

---

### Post by Dangertux on 2011-11-19
> **BigCityCat said:**
> Can someone explain this to me? It sounds serious.

[http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html](http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html)


This has been thrown around quite a few times at this point. A little back history on the author in case you don't know. She was a presenter at Black Hat in 2005 and became somewhat famous in the field of virtualization security for coming up with the "first" hypervisor root kit. She called it blue pill, as it seems she is rather fond of references from The Matrix films (I've read a few of her papers lol). She is very clever, and so are the other researchers working for ITL.

However, that being said ; this is absolutely nothing new. She is pointing out that X11 was never meant to be mainstream, at least not from a security point of view. I believe she gives a little demo in that article, you can try it for yourself and see exactly what she is talking about. Ultimately this is a plug for qubes OS (though its a good one). She is pointing out that isolation between different GUI applications is sub par, in that they all have access to the same input/output devices.

Hence, one application can "spy" on another. This obviously brings concerns (for both privacy and security) as banshee can watch what's happening in firefox (you know where you're logging into your banking site). 

She presents an alternative in qubes in that essentially the OS itself is nothing but a hypervisor and every application is virtualized inside its own instance, this is one approach to separating the GUI apps access to eachother, albeit a rather resource intensive one lol.

Does this clarify?

---

### Post by BigCityCat on 2011-11-20
> **Dangertux said:**
> This has been thrown around quite a few times at this point. A little back history on the author in case you don't know. She was a presenter at Black Hat in 2005 and became somewhat famous in the field of virtualization security for coming up with the "first" hypervisor root kit. She called it blue pill, as it seems she is rather fond of references from The Matrix films (I've read a few of her papers lol). She is very clever, and so are the other researchers working for ITL.

However, that being said ; this is absolutely nothing new. She is pointing out that X11 was never meant to be mainstream, at least not from a security point of view. I believe she gives a little demo in that article, you can try it for yourself and see exactly what she is talking about. Ultimately this is a plug for qubes OS (though its a good one). She is pointing out that isolation between different GUI applications is sub par, in that they all have access to the same input/output devices.

Hence, one application can "spy" on another. This obviously brings concerns (for both privacy and security) as banshee can watch what's happening in firefox (you know where you're logging into your banking site). 

She presents an alternative in qubes in that essentially the OS itself is nothing but a hypervisor and every application is virtualized inside its own instance, this is one approach to separating the GUI apps access to eachother, albeit a rather resource intensive one lol.

Does this clarify?

Sure thats pretty interesting. I guess still ultimately it comes down to being careful what you install. I highly doubt Banshee is going to be watching my web browser unless I installed a compromised version outside of the repos.

---

### Post by OpSecShellshock on 2011-11-20
> **BigCityCat said:**
> Sure thats pretty interesting. I guess still ultimately it comes down to being careful what you install. I highly doubt Banshee is going to be watching my web browser unless I installed a compromised version outside of the repos.

Well it's possible that what they call a "specially-crafted" (read: malicious) media file could cause the legitimate version to at least attempt to do such a thing. That would be a highly specific situation that not many people stand a chance of having to deal with, though.

---

### Post by BigCityCat on 2011-11-20
This is one reason why I am really looking forward to Wayland. All though it's my understanding that Wayland will be extremely dependent on x-server in the beginning. I wonder if the Wayland project is aware of this info.

---

### Post by OpSecShellshock on 2011-11-20
Maybe, but there's an option available now: hardware is relatively cheap, and so sensitive tasks can be performed on discrete, dedicated systems that are not used for anything convenient or fun. That's probably not *as* true in the enterprise space, though for small-to-medium shops it's still worth looking into. It's cheaper than a managed service, and probably cheaper than an enterprise license for virtual desktop solutions.

---

### Post by Dangertux on 2011-11-20
It's pretty much a known factor by most that X Server functions in that way. I really think she was just pointing out that it's rather easy for it to occur (hence including the little demo). By design X is going to allow this to happen, there really isn't much you can do about it (hence the reference to MAC with SELinux). It's one of those, "It's a feature not a bug" kind of things.

Ultimately it's not that serious either, it is easy to create a keylogger, particularly considering there are no real AV solutions to bypass. So, doing it with X Server is just one way. 

She also mentions injecting key-strokes into a program, this is where things get more interesting, the concept being a browser could be exploited then used to inject code into another application that is running. However as OpSecShellshock pointed out, from an attacker's point of view this probably isn't the best route. That entire attack is based on the chance that you are using that web browser, that is compromised at the exact moment you're also using whatever application would be compromised by it. Or vice versa, opening a malicious media file, and trying to compromise a browser, of course in theory you could just have X server open the browser or application at that point, then inject code. That being said I'm fairly certain anyone would become a little more than suspicious about firing up a song and suddenly their browser opens, crashes and there is now network activity that wasn't there. 

Like all research it's one of those. Hey guys this CAN happen. Realistically if you're worried about this and don't have something like NoScript, than you're probably barking up the wrong tree in terms of things that are LIKELY to happen to you.

---

