---
title: "Impossible to connect VNC headless"
date: 2020-04-14
forum: Server Platforms
---

### Post by crussader2 on 2020-04-14
Hello, first of all I&#8217;m new here to please redirect this topic if necessary.

I&#8217;ve got a Raspberry Pi 4 (4GB) with Ubuntu sever 19.10 and Lubuntu desktop installed. I did a headless setup as I dont have screen, keyboard or mouse to work with so I did everything via SSH but I want to access via VNC to have the desktop environment.

I followed every tutorial online but I couldn&#8217;t get it working. I did manage with Raspbian so I don&#8217;t really know what else to try, I&#8217;m very new to this.
I&#8217;ve tried with x11vnc, tiger vnc and tighvnc.

The closest I got was with this tutorial: [https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/](https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/)
But when I reached the part where I have to create an SSH tunnel to VNC server I got the error:
```

Warning: Identity file /home/ubuntu/.ssh/ubuntu19.04 not accessible: No such file or directory.
ubuntu@192.168.1.127's password: 
bind [127.0.0.1]:5901: Address already in use
channel_setup_fwd_listener_tcpip: cannot listen to port: 5901
Could not request local forwarding.

```

I don&#8217;t really know what else to do, if any has a link to a tutorial that is working for you please let me know.

Thanks

---

### Post by HermanAB on 2020-04-15
Note that VNC is mostly a Windows thing.  It works on Linux, but SSH is usually better..  Running VNC over SSH is also possible, but kinda redundant.

VNC forwards your whole desktop to another machine.  However, most machines already has a perfectly good desktop environment and overwriting the whole thing with another copy of the same thing, is a juuge waste of time and network resources - in other works: Slooowww...

SSH can be used to forward an individual application, which will then run transparently on the other machine's existing desktop.  This is of course rather more efficient.

---

### Post by slickymaster on 2020-04-15
Thread moved to **Server Platforms** for a better fit

---

### Post by crussader2 on 2020-04-15
Please I&#8217;m asking for help with a specific thing, not asking if i should do it or not, but for clarification i don&#8217;t have a computer at home, only ipad, and im learning programming and coding But I can&#8217;t spend money on a laptop or a computer so i got the raspberry and i want to connect via remote desktop to it. I managed to do it with Raspbian with no problem but I wanted to try a full real distro. Thanks

---

### Post by LHammonds on 2020-04-15
> **crussader2 said:**
> Please I’m asking for help with a specific thing, not asking if i should do it or notYou are asking for something not commonly done and the general audience here, even the very experienced, may not have ever tried this particular scenario.  You are also running on a Pi which is a VERY low-powered device not exactly geared for a full desktop GUI experience.  I have heard others talk about running a remote GUI the was extremely lightweight but I cannot remember what was used.  I will try and find it but again, this is a Pi we are talking about here...not server-class hardware.

With a Pi, you can get a full server OS running...just don't expect it to also be a database server, web server, minecraft server and desktop.

LHammonds

---

### Post by DuckHook on 2020-04-15
> **crussader2 said:**
> Please I’m asking for help with a specific thing, not asking if i should do it or not, but for clarification i don’t have a computer at home, only ipad, and im learning programming and coding But I can’t spend money on a laptop or a computer so i got the raspberry and i want to connect via remote desktop to it. I managed to do it with Raspbian with no problem but I wanted to try a full real distro. Thanks
Welcome to the forums, crussader2

Just a friendly note on netiquette:

This is a forum, not a help desk. Coming from the Windows world (I assume) you may be used to paid support that strictly answers your questions without further commentary, but the nature of a forum community is to enquire about and discuss the larger context. What this means is that when someone asks us for the best way to jump off a cliff, we do not just automatically tell them. Rather, we advise that jumping off cliffs is not good practice.

Your question is actually an excellent example of why commenting on the larger context is important:

[LIST=1]
[*]I have the most recent and powerful rPi 4B+
[*]It runs Raspbian nicely but Ubuntu desktop poorly.
[*]Only the server image of Ubuntu is officially available for this rPi.
[*]Trying to install a DE on top of it yielded poor resolution, poor performance and an awful user experience.
[*]Further layering of a remote desktop on top of this flaky foundation is bound to lead to much wailing and gnashing of teeth.
[/LIST]
It is always worthwhile listening to the larger advice from the old-timers on this forum. They have earned their spurs usually through hard-won experience and the school of hard knocks.

---

### Post by DuckHook on 2020-04-15
I should also add that if you are absolutely intent on carrying through with your plan, then you would be better off running your remote desktop off Raspbian. Your implication that it is not a "full real distro" is not accurate. Raspbian is a great distro with many Debian packages available for it. But its main advantage will be its massive user base and a community that can help you far better than the Ubuntu community can. Ubuntu users just don't tend to install desktop environments on RPi, so you are dealing with a minuscule number of people who might be able to help. On the RPi forums, I'm sure that many others have already tried to do what you're asking about, so that's where the expertise can be found.

Incidentally, another example of addressing the larger issue rather than just "your specific question".

---

### Post by crussader2 on 2020-04-15
I think we got with the wrong foot here (forgive my english as I&#8217;m not a native speaker).

I&#8217;m not coming from a Windows forum and I&#8217;m not insulting anyone, I just don&#8217;t like the idea on the forums of any type when you ask a question about something that an answer is you shouldn&#8217;t do it because of <insert reason>.

I do understand what I&#8217;m trying to do here and I know the limitations of my setup. I don&#8217;t need speed, but I do need a proper IDE as it is ATOM because all the IDEs that I found available in Raspbian are not very user friendly for a noob in programming like me.
I&#8217;ve also seen multiple videos on the internet of how a distro like Ubuntu 64 bits increases the performance by a big margin compared to the performance of Raspbian.

I&#8217;m not planning to play games nor do I need speed, but I do need some software for my purposes that is either not available in Raspbian or it performs much worse that in a distro like Ubuntu 64bits.

Therefore even if I appreciate the recommendation, it still not answer nor helps me in my problem.

Honestly I though Linux community would be more helpful but so far basically you are sending me to Raspian community back again on my first question/post which really makes me sad.

---

### Post by DuckHook on 2020-04-15
Now that we understand your context better, what you are asking makes sense. But it was not possible to reach that understanding without your explaining that context.

Nor was there ever any suggestion that your question would be ignored or met with indifference.

Perhaps I am at fault in not explaining myself well. The reason that I recommended approaching the Raspbian community was not because the Ubuntu community is disinterested or doesn't care; it is because the expertise that you are looking for is uncommon and may be hard to come by. This is purely a practical observation. If anything, it was only meant to set up realistic expectations.

I sincerely hope that someone who has done this before sees this thread and can help you.

---

### Post by crussader2 on 2020-04-15
Thanks and sorry for the misunderstanding.

i don&#8217;t want to look ungrateful at all. I&#8217;m very excited about joining the linux world and community but my knowledge is limited.

i asked here and in the raspberry forums because running Ubuntu I understand it shouldn&#8217;t be different than on a normal computer.

now I&#8217;ve tried with xfde following this tutorial: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04)

And it looks like it&#8217;s running but when I tried to access though my computer the VNC viewer tells me the port can&#8217;t be access, although I&#8217;ve checked and the ports used (5900) are open.

I&#8217;ve even created a dummy display (I had to do it in Raspbian as well) to get the remote environment but I can&#8217;t really get it to work.

Im guessing if I could acces the Pi with keyboard and monitor I could do it without a problem but right know I dont have that possibility, it must be a way to do it headless...

---

