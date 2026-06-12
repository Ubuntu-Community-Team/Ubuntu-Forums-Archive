---
title: "Sims 3 Launcher Not Installing Content"
date: 2010-11-30
forum: Wine
---

### Post by The Flying Penguin on 2010-11-30
This may be a bit long but I feel the whole story is important in order to  solve this problem.

 I am running Ubuntu 10.10 64bit on an Asus ul30vt with a 1.3GHz Core 2 Duo (SU7300) and Nvidia G210M. I installed The Sims 3 from a dvd using Play On Linux 3.8.6. I have performed all the game updates and patched it with a no cd crack.
 
The game itself seems to run awesome. The problem is with the launcher and installing custom content. I am currently working with a bunch of Maxis custom content including the Riverview neighborhood so there shouldn't be any problem with the content itself. I installed it all successfully on the same machine under Windows 7 64bit.
 
At first I was completely unable to even get the launcher to work. If I tried launching it from within POL nothing would happen. If I tried to launch it from within the game I would get an error message that said &#8220;fatal error in gc &#8221; in the title and &#8220;gethreadcontext failed&#8221; in the actual pop-up box.  
 
I searched and came up with this: [http://bugs.winehq.org/show_bug.cgi?id=23246#c1](http://bugs.winehq.org/show_bug.cgi?id=23246#c1) So it appears to be an issue with mono. When I checked my processes it showed mono, ts3.exe, and ts3launcher.exe all running. Killing ts3.exe did not change anything. Mono would show it was using cpu cycles but nothing ever happened; The launcher never appeared. I read that sometimes a dual core cpu can cause thread context errors so I disabled one of my cores but that didn't change anything.

 That link has a hack in the form of a .diff file that is supposed to solve the error. I went to the Mono chat room and asked where to place the file and no one knew why POL even installed mono because ts3.exe had an embedded version of mono. Furthermore they said the embedded mono could not be patched. Well, obviously there is a reason POL installed mono. Clearly it is involved with the ts3launcher.exe as when I hovered over the mono process in the system monitor it shows the mono file path and the ts3launcher.exe file path linked together.
 
I wasn't getting anywhere trying to work with mono so I tried something different. I deleted the mono folder in The Sims 3 wine prefix and then installed the .Net 2.0 framework in its place. Now when trying to access the launcher from within the game or POL, I would get a runtime error that said &#8220;Runtime Error! R6025 &#8211; pure virtual function call&#8221; If a tried a couple more times it would instead give me a box saying &#8220;The program has encountered a problem and needs to close&#8221;instead of the runtime error.
 
But I discovered something; Now with the mono folder removed and .Net 2.0 installed, I can access the  launcher if I disable my second cpu core, using the command &#8220;echo 0 | sudo tee /sys/devices/system/cpu/cpu1/online&#8221;. So turning off my second cpu core I can access the launcher from either POL or from within the game. If I access it from within the game I need to kill ts3.exe because you can't install content while the game is running. Either way, I do get two errors about the program encountering a problem and needing to close but if I close them I can continue to use the launcher.
 
Great success right? Well, no. I can't seem to install content properly. I probably have 20-30 items and when I click install, everything seems to go fine. I get a message saying the content was installed successfully but when I click on installed content there is nothing there except for three items. It turns out these three items seem to come from the Riverview neighborhood. If I just install Riverview then I see two pairs of overalls and a water tower under installed content. And its not just the launcher erroneously reporting what is installed. When I check in the game Riverview is not installed or any other objects I try installing.
 
So now you hopefully have all the information you need. Any help would be greatly appreciated as I would really like to be able to use custom content. It's the only thing holding me back from playing it in Linux and not having to boot into Windows to play it.
 
Thanks in advance for any assistance.

---

