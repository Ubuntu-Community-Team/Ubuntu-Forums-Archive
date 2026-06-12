---
title: "How do I help a non-tech friend troubleshoot skype over the phone?!"
date: 2010-08-21
forum: The Cafe
---

### Post by QwUo173Hy on 2010-08-21
I'm in Ireland, she's in Belgium and Skype keeps cutting out her calls on her (Ubuntu 9.10). I don't know where to start, I usually need to be sitting in front of the machine.

Does anyone have experience with this?

---

### Post by msandoy on 2010-08-21
Well, the easy sollution is to use a remote desktop app. called Teamviewer. It works on Windows, Linux and Mac. As far as I can see, it is totally secure too.

---

### Post by QwUo173Hy on 2010-08-21
That is a great idea msandoy, thank you! She's just mailed me and apparently she has a visitor coming next week who uses Ubuntu and might be able to sort it for her. Fingers crossed.

Thanks again,
Jarlath

---

### Post by rjbl on 2010-08-22
Haven't had any problems with Skypeing from 10.04, done it world-wide, box-to-box and box-to-tellingbone. Sounds more like a Skype service issue. Is it a constant, long-term issue with your friend? Is there a previous history of good use? Etc, etc. Can't see that remoting her desktop would help - Skype doesn't return helpful error messages when the connection drops and I don't think it actually has any diagnostics.

ATB
rjbl

---

### Post by msandoy on 2010-08-22
I actually use Teamviewer for remote assistance from my Ubuntu box to both other linux boxes and windows boxes. Beats guessing over the phone line any day. Installs via exe for windows (Can be run from the exe without installing.) and from deb in Ubuntu.
Remote desktop will make it easier to diagnose if the line has a problem, or if there is an application hogging the line.

---

### Post by QwUo173Hy on 2010-08-22
If it gives me access to her terminal, then it will cut the debug time by 90 percent - she's not well up on computers at all.

But it's Ubuntu 9.04 she's using and the guy who set it up for her didn't spot the problem and he's not available any more. Luckily, it seems a good tech guy & Ubuntu user will be on the scene in the coming weeks. But still, it's an interesting problem and I'm glad for the help.

If I was there, I'd upgrade her to 10.04, but over Teamviewer, I could at least get versions of software and change her software sources etc to get it up and running. I know Skype doesn't give any helpful output, but once I know version numbers and witness the behaviour, I'm sure I'll find an existing solution online.

---

### Post by msandoy on 2010-08-22
Just download .deb for Debian/ubuntu 32 or 64 bit, dependign on what is in use. Doubble click and install deb. Only thing is, it needs the root password for install. Download from: [http://www.teamviewer.com/download/index.aspx](http://www.teamviewer.com/download/index.aspx)
When you log on, you control her user, and you have full desktop and all other programs.
There are sollutions in the repositories (VNC via SSH and such), and I'm sure some of the experts in here can help you set them up, but this is the easiest I have found. I have not met anyone yet, that I could not guide trough this install and startup. 
With a desent internet connection on both sides, you should be logged in and investigating in maybe 10 minutes time.

---

### Post by QwUo173Hy on 2010-08-22
Very cool, thank you so much. I've just installed the .deb and sent her a copy via email. Hopefully we can have a proper skype conversation too.

But more importantly, it would mean I can install ubuntu for more people. I usually don't do it now because I don't want to be committed to support, but this fits nicely!

---

### Post by msandoy on 2010-08-22
Just glad to help, I have found alot of helpful advice on this forum, and just want to give some back. I do alot of personal support among my friends, and Teamviewer has become a very good tool. I just started a thread in the security forum, to see if it is possible to use VNC in a similar manner. Would be nice if Ubuntu could come with a feature similar to this by default.

---

### Post by QwUo173Hy on 2010-08-22
It would indeed be good for Ubuntu (although I don't know what the security implications might be, I can imagine all sorts of potential disaster stories if it was too accessible to the average user). Maybe the existing open-source options could be configured a bit more. The ease of use of Teamviewer is incredible.

---

### Post by julio_cortez on 2010-08-23
> **msandoy said:**
> Teamviewer has become a very good tool.
Agree.

I use it quite everyday to troubleshoot problems that customers are having both on Windows and Mac, and it helped me solve problems that I wouldn't have solved in any other way (no, I'm **NOT** going to abroad for work, no matter what:lolflag:).

In the end, I really suggest the opener to try TeamViewer if it happens again :)

---

### Post by QwUo173Hy on 2010-08-23
Well, I've just had my first run with TeamViewer -- it's AMAZING! I emailed her the .deb for her system (x64 bit) and she mailed me back the ID and password. Then I could control her system and get all the package versions and see first hand the problem behavior (which was misrepresented in her description but now I know what I'm dealing with). It looks like she has the wrong version of Skype installed and she was blown away at what was possible with technology. I think I would win many support contracts with this software.

msandoy, thank you so much - that's the best computer tip I've had all year.

---

### Post by msandoy on 2010-08-23
Your welcome. When helping non-tech friends, it's sometimes hard to get a proper description of the problem. If they do not know how to create a folder or find a file they just saved, how can you expect a proper diagnose of their problems. (I actually do support for people with this low computer skills.) Then this program is the next best thing to sitting infront of their computer. 
So, go ahead and spread the Ubuntu word. Support is now not a problem.

---

### Post by QwUo173Hy on 2010-08-27
Linux Format (LFX136) just did a roundup of remote desktop applications. I was surprised to see that TeamViewer came last. They compared: Krdc, RealVNC Java Client, Remmina, TeamViewer, TigerVNC, Vinagre and NoMachine NX Client. 

They played a computer game (Tron) remotely as an approximate indication of connection capability and quality and compared all the above products.

Teamviewer got 3 out of 10, docking marks for quality/connection speed ratio, poor audio and other reasons. Remmina got 10 out of 10.

---

