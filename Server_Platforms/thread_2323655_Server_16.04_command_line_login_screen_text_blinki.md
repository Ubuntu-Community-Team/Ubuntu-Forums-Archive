---
title: "Server 16.04 command line login screen text blinking"
date: 2016-05-07
forum: Server Platforms
---

### Post by Lane_Peterson on 2016-05-07
In the past few days, there had been 2 or 3 separate notifications on the login screen that the server needed to be rebooted, which I did. Everything previously had been normal. Now, any time I reboot, when the command-line login screen comes up all the text on the screen simultaneously blinks on and off pretty regularly at just under 1 Hz for about 5 minutes, then it abruptly stops and everything is fine. It doesn't do it during the boot process, only once it gets to the tty1 login screen. While it is blinking if I attempt to type in my login and password, any keystrokes I hit while text is present on the screen appear where they are supposed to be on-screen and are read correctly by the system when I hit Enter. However, any keystrokes I hit while no text is on screen show up and accumulate in the upper left corner of the screen and do not seem to register correctly with the system, i.e., they seem to be ignored. So basically I have to time all my keystrokes one at a time to occur while text is present on-screen or it says my login is incorrect. It does not matter whether I sit and wait at the login screen for the blinking to stop, or go ahead and (very carefully) log in; whatever is on the screen continues to blink for the same amount of time. I checked each tty 1-6 and it is blinking the same for all of them. Very odd. 

I've got an Equus server with an Intel Xeon X3440 CPU at 2.53 GHz and intel server board circa 2010, using a keyboard and monitor directly attached to the server when this occurs. It hasn't happened in the Putty remote ssh terminal window but I can't say for certain that I logged in that way during the first ~5 min after a reboot. It may be relevant that what I have been working on over the past few days is trying to install a virtual machine from the command line (with kvm and first vmbuilder, then virt-install) which I did not yet succeed at, and getting VNC remote desktop going, which I finally did. During the latter process I installed and uninstalled the vnc4server and gnome-core packages before I got it to work with tightvnc-server and xfce4. Unfortunately, I did not think to document the exact stage during this process when the blinking first started. It was not immediately after I installed some package, though; I believe it was when I went to log in for the first time 2-3 days ago, noticed the message to reboot, and it started happening after that reboot.

Anyone else ever have this happen or have a clue what's causing it? Let me know what further info I can provide and thanks in advance.

---

### Post by TheFu on 2016-05-07
Welcome to the forums.

I wouldn't do anything directly on the console. Do everything over the network.  Check the system log files for any HW issues.  Managing servers is hardly ever something we do on the machine directly. It is always remote, unless there is no other option (network is down or the OS needs to be loaded).  Even then, if the server supports [IPMI]("https://en.wikipedia.org/wiki/Intelligent_Platform_Management_Interface"), we'll do it all remote.  

 Pure guesses, but sounds like a GPU failing or a PSU.  Could be a loose connection for the GPU/GPU added power - try reseating both. Best to look at the log files to see what they say.

---

### Post by Lane_Peterson on 2016-05-08
OK, I'll admit that I'm about 75% linux n00b, especially when it comes to servers, hence the original posting in "New to Ubuntu". I'm not really sure which system log files to check or what specifically to look for in there, so any additional guidance you could give would be much appreciated. My primary goal here is to put together a well-performing media server system, but I also want to learn along the way and experiment with other home uses for the server, such as VPN.

One reason I initially doubted it was hardware failure or loose connection is that the issue is very predictable and behaves exactly the same way each time, with a regular rhythym to the text blinking, only beginning on the login screen, and always stopping about five minutes after rebooting. It doesn't reoccur at all after that point. Hardware failures in my experience usually act more flakey and nonspecifically. Also, if it was the GPU wouldn't it be irrelevant whether I made a keystroke when the text was showing on screen or not? That was just my thought process; of course, I will still check the logs and the connections because you never know. Any other tests I could use to at least narrow it down to hardware vs software/configuration? Aside from rebuilding the server :)

---

### Post by TheFu on 2016-05-08
Log files: 
* [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
* [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
* [https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)

---

