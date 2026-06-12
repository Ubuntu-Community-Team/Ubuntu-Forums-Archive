---
title: "Some general settings and some basic Linux stuff."
date: 2020-04-28
forum: Ubuntu, Linux and OS Chat
---

### Post by xcfstarflight1 on 2020-04-28
**Hi good people!**
I have not been using Ubuntu for long now. It must be about a couple of months. I did use Linux from time to time before that and when I was younger,
the days you needed to compile the kernel yourself :) I had good knowledge. 

What I want to ask here is how do I see system/application/security logs? I want to see application and system logs because
my applications often hangs if I have more of them open. 

I use Ubuntu Budgie by the way.

And the same with settings for Scheduled Tasks, modifying system files etc. 
A way that explain the equalient of Windows tasks but just in the Ubuntu way of doing things. 
I am a microsoft certified technitian and engineer plus I have the Specialist certification for Office applications,
but I am choosing to use Linux because of it's incredible way to do some really creative stuff and it inspires me.

Is this statement true? It goies like:
Back in the day I used Amiga to make music, the Amiga was #1 no doubt when it came to Audio. 
Then we got an old MAC that ran TV in fullscreen with no lag.
And then we have Linux. 

The question or statement is like this: Do they all use motorola machine code? 
For example the assembly code MOV AX,10h to just move something into registered are backwards on Amiga.
You need to write MOV 10h, AX. So that is the other question.

Also, anyone else have the same idea as me? Amiga was ahead on audio and Mac was way ahead on audio and video,
who means that this may be true for Linux as well? 

Pretty long typing from me, hope someone takes the time to read it, give me feedback.  That would be so nice if someone did! This is close to my heart. 

Keep ubuntuing, keep the community alive, keep pushing forward nomatter what other people say and oh you have sphock: Live long and prosphere.
Take care everyone!

---

### Post by TheFu on 2020-04-28
> Do they all use motorola machine code? 
no.  The underlying assembly code is based on the CPU, as computers have always been since the beginning.  ibm's "power" line is probably the closest to the old 68000s that is still in production.

System logs are stored in a binary format thanks to **journald**.  Most are still replicated to text files in the /var/log/  directory, just like Unix has been doing since 1970.  Any pager, text viewer or text search/manipulation tool from almost any Unix system since the 1970s can be used to view those files.  The **journalctl** program can be used too.

---

