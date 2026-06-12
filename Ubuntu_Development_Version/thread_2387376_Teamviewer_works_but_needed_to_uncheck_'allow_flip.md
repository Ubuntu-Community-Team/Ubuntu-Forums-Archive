---
title: "Teamviewer works but needed to uncheck 'allow flipping' in nvidia-settings"
date: 2018-03-18
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2018-03-18
I was looking for an easy way to share the desktop across the net.
Teamviewer version 13 preview came up as free for home use.
Also allows you to set a permanent password, so then remote connections at any time to the pc.
I tried Chrome remote desktop, which works, but no permanent remote connecting. No way to add a linux pc to the list of available connections, so every connection requires a person at the remote PC.

One issue was annoying video glitch, resolved in nvidia-setting to uncheck 'allow-flipping'.

Quality also seems quite good.

I looked into other programs and guides, but actually could make not much sense of them. I did get a VNC connection going for my local lan, but have no idea how to make it work on the www internet.
The guides I saw leave out critical how to steps.

Anyone know of a decent web page I can study?

---

### Post by braghum on 2018-03-18
Teamviewer is known to have some issues since version 13 anyway. ;)

If you are looking for an alternative, maybe try NoMachine:
[https://www.nomachine.com/DT07M00078#4](https://www.nomachine.com/DT07M00078#4)

---

### Post by sdowney717 on 2018-03-21
I have a desktop file set to executable. When I go to run it by clicking on it, teamviewer disconnects the machine.
The machine is still viewed, the mouse rolls on the screen, but for the remote PC, no mouse moves, no more remote control.
Why is that?

I can startup anything in the remote PC menu ok.
I just tried it again, and it is ok, meaning it worked, so it is a little buggy.

Thanks, I will look into nomachine.

---

### Post by sdowney717 on 2018-03-21
Well Nomachine is an improvement speedwise, the screen refreshes quick.

I have a significant problem though.
One PC is running at 1080p, the other is 1024 by 768.
I can connect to the other PC ok, screen resolution is ok. Icon to control connection is visible.

But If I reverse connect, my 1080p screen becomes 1024 by 768. AND I see no ICON to control the connection.

I took a screen shot to show the problem, and I dont know how to disconnect now.
Granted, I have not tested this reversed connection with Teamviewer yet, but i will.

---

### Post by sdowney717 on 2018-03-21
Yes, teamviewer handles it fine, no changing of screen resolution on either PC.
It is very bad to downgrade the resolution so both PC's match, from a usability POV.

You can disconnect the machine by in gnome show application, server status icon.
But I see no way of transfering files since that icon when the screen resolution is downgraded is just gone.

Teamviewer added file transfer on the main remote PC view page.

BUT, it seems to be causing random reboots of the remote Linux Mint PC?
And sometimes it seems to disconnect, and sometimes causes the remote to lose keyboard and mouse, AND sometimes seems to cause the GPS to stop functioning.
What I have noticed, the Linux Mint PC does not do any of that when not connected remotely.

I have been playing with various programs for remoting. Anydesk works but has no file transfer working.

Adding more info, it may have been my PSU being underpowered for the MB and GPU. It was only 250watt PSU running a quad core 3 ghz AM3 board. I switched PSU to a 650watt one and so far not doing anything odd.
It got so bad, it was randomly rebooting even with no remote software running. So I am now running a 10 hour remote session using anydesk while it plays a 10 hour you tube video.

---

### Post by sdowney717 on 2018-03-25
> **braghum said:**
> Teamviewer is known to have some issues since version 13 anyway. ;)

If you are looking for an alternative, maybe try NoMachine:
[https://www.nomachine.com/DT07M00078#4](https://www.nomachine.com/DT07M00078#4)


I figured it out, uncheck match the resolution when connecting. It is under display properties. Not exactly easy to find.
Then it does not modify the remote's screen (server PC) to match the client ( PC viewing the remote PC)

With Nomachine, sound works well, file transfer works. Nomachine is the only one where sound and file transfers actually function.

But in Ubuntu connected as a remote PC, I can not see the control icon anywhere. In Mint it is loaded at bottom right. So when transferring files I can use that icon in the remote PC.

If 2 ubuntu PC's were connected, I imagine no way to control or share files.

Regarding TeamViewer, sound does not work, file transfer works. When I go to their forums, lots of people mention sound and file transfer not working. And been going on for a while too.

Well..., NoMachine AND Anydesk are now giving me errors when I remote into a linux Mint PC. Says cinnamon desktop is running in software rendering mode. BUT GLXINFO says differently...

> direct rendering: Yes

Teamviewer still ok. Interesting that NoMachine and Anydesk display the exact same error message.
Anyone have a clue why?
Except for sound, teamviewer just works all the time, after I switched out the weak PSU.

Update, uninstalling nvidia driver 390, then reinstalling nvidia driver 390, and the problem of software rendering went away.
Actually wondering if the hard drive on this Mint PC is failing, bad sector count has increased to 209, was 177 last week. It might be destroying data.

---

