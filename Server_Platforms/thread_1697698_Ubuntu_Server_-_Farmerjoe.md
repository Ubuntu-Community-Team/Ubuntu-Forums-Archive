---
title: "Ubuntu Server - Farmerjoe"
date: 2011-03-01
forum: Server Platforms
---

### Post by Soelen on 2011-03-01
Hello everyone, my name Soelen and I need some help for a tryout ^^

So I use Blender for making 3D Stuff, and since I installed Ubuntu Server 10.04 on a second pc, I want to use the Server as Renderfarm.

So for every Render order, the server have to do that.

so I found [http://farmerjoe.info/](http://farmerjoe.info/), but since I'm a bloody rookie I need help to configure it ^^; anyway I begin to explain my problems...

Farmerjoe wrote in his documentation
> 
[LIST]
[*] **LINUX**  Here is the line I have in my /etc/fstab on my linux slaves 
//<master server>/farmerjoe /render smbfs guest,uid=lobo,gid=lobo 0 0
 which mounts the shared directory on /render when they boot up.
[/LIST]
but I guess he ment

/farmerjoe /render smbfs guest,uid=lobo,gid=lobo 0 0

assumed I have the directory /farmerjoe of course.

but I dont get the render part, the second parameter. What does that mean? do I get a render drive? And if yes how do I make a network drive of it? That's my main target. All I want is to connect the mounted server drive(or folder?) with my pc which I use windows on it. Sadly I dont find some kind of that information on the internet, I guess I just use the wrong keywords...

Thanks in advance! ^^

---

### Post by renzokuken on 2011-03-01
someone correct me if im wrong here, its been a while, but when editing fstab, the first folder entry is the physical drive or network location (i.e. //farmerjoe ) and the second part (i.e. /render ) is where you want that drive/network-folder to be be mounted on the local machine.

in other words the /render folder has to exist on your local machine so you should create that folder before adding to your fstab

---

### Post by Soelen on 2011-03-02
Ah I found the solution, thanks renzokuken! :D

---

