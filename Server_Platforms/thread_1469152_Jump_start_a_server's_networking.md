---
title: "Jump start a server's networking?"
date: 2010-05-01
forum: Server Platforms
---

### Post by wesg on 2010-05-01
My desktop server serves up files via a number of protocols and I connect to it via SSH and Avahi. Today I tried connecting to it via SSH, but it timed out. I was able to ping it, and a port scan reveals all the ports I have open on the network. THe problem is that I can't connect via SSH, HTTP, AFP, SMB or any other protocol I have established. 

Is there a way to jump start a system in a situation like mine? I have a 6 month uptime going, but I'm taking it down soon for some hardware upgrades, so a hard restart is not out of the question, but I'd rather not. I also reset the router without a solution.

---

### Post by tgalati4 on 2010-05-02
I presume that this is a remote server, where you cannot see the console.  If you have an UPS with network connectivity, you can sometimes reset the power through the UPS, but that's not as good as using the Magic SysRq keys to shut down if the machine is truly locked up.

You need to check the log files to determine the problem.  It's possible that you had a power glitch that caused your machine to be in a strange state.  I presume you have an UPS attached.  If so, you can check the UPS logs for power hiccups.

If you don't have an UPS, then you can't expect long uptimes:

tgalati4@tubuntu2:~$ uprecords
     #               Uptime | System                                    Boot up 
----------------------------+-------------------------------------------------
     1   216 days, 06:49:56 | Linux 2.6.15-28-386      Tue May 22 22:36:24 2007
     2   163 days, 23:49:22 | Linux 2.6.15-26-386      Tue Oct 24 12:19:49 2006
     3   153 days, 01:33:24 | Linux 2.6.15-29-386      Wed Dec 26 13:22:27 2007
     4   117 days, 23:40:07 | Linux 2.6.15-51-386      Thu Jun  7 10:18:37 2007
     5    94 days, 02:31:54 | Linux 2.6.15-52-386      Mon Oct 20 10:55:37 2008
     6    64 days, 20:48:44 | Linux 2.6.15-54-386      Sun Aug  2 12:56:44 2009
     7    59 days, 15:24:32 | Linux 2.6.15-53-386      Sun Feb  8 16:44:19 2009
     8    44 days, 22:39:39 | Linux 2.6.15-55-386      Sat Oct 24 10:56:14 2009
     9    44 days, 05:43:51 | Linux 2.6.15-54-386      Thu Apr 30 10:32:09 2009
    10    42 days, 22:30:09 | Linux 2.6.15-55-386      Mon Feb  8 12:17:12 2010
----------------------------+-------------------------------------------------
->  12    39 days, 05:16:01 | Linux 2.6.15-55-386      Tue Mar 23 15:47:41 2010
----------------------------+-------------------------------------------------
1up in     2 days, 16:27:01 | at                       Tue May  4 13:30:42 2010
no1 in   177 days, 01:33:56 | at                       Mon Oct 25 22:37:37 2010

My machine has been running Dapper Drake desktop (but really used as a server) continously since 6.06.  Down times have been due to updates or power outages longer than 15 minutes.

---

### Post by wesg on 2010-05-02
I'll check that out, once I get back in. Strangely, some data trickles out, because a webpage just loaded up, though it took a long time to load. I'm at 188 days. I'm going to try removing/replacing the network cable first, before resorting to a shutdown.

Also, I completely agree with the UPS statement. Our house power flickers occasionally, and I've yet to have a shutdown as a result. As an added bonus, my entire network system remains up too, so no lack of interwebz for me!

---

### Post by wesg on 2010-05-02
Another interesting development: I just went to check the hardware, and saw the disk activity light solid. Perhaps the network is saturated?

---

### Post by wesg on 2010-05-02
OK, I connected a monitor and keyboard to the system, but now I still can't log in. The console is spewing "out of memory" warnings and pressing Ctrl + Alt + F1 doesn't seem to bring up the login. I think some process has gone crazy and is eating all my memory, so the machine is still live, but is slow as molasses. How else can I gain access now? Am I using the right keyboard combination?

---

### Post by tgalati4 on 2010-05-02
Yes, sounds like a memory leak that is causing 100% CPU because of swapping.

So you have to bring it down.  Use the magic keys:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Wait 2 seconds between each command:

Alt-SysRq-R
Alt-SysRq-E
Alt-SysRq-I
Alt-SysRq-S
Alt-SysRq-U
Alt-SysRq-B

---

