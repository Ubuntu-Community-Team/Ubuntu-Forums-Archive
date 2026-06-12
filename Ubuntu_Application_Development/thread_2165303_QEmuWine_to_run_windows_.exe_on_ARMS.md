---
title: "QEmu/Wine to run windows .exe on ARMS"
date: 2013-08-04
forum: Ubuntu Application Development
---

### Post by vezinadj on 2013-08-04
Hi,

I have developed a console application in windows (c++), and I am currently looking for a way to run it on a beaglebone black (no ubuntu desktop, ARM's). After doing some research online, I have found that some people have successfully done this using a combination QEmu and Wine, but there is no real step by step process of how to at least get started.

Has anyone else done this that could give me assistance?

I put ubuntu on my beaglebone black, and I manually compiled wine 1.3 (after 4 hours), and wrote a quick .exe that prints 'hello world' to the console and this is the std out:

ubuntu@ubuntu-armhf:~$ wineconsole --backend=curses WineTest.exe 
fixme:seh:call_stack_handlers not implemented on ARM, exceptioncode: c0000005
wine: Unhandled page fault on read access to 0xb6d30000 at address 0xb6d30000 (thread 000b), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb6d30000
fixme:seh:call_stack_handlers not implemented on ARM, exceptioncode: c0000005
wine: Unhandled page fault on read access to 0xb6d20000 at address 0xb6d20000 (thread 0009), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb6d20000

My assumption is that these read access errors are due to the architecture of the executable. Any one have any ideas on how I can get this exe running?

Thank you!

---

### Post by GwL3eNC on 2013-08-04
Hi,

 is your exe working on a windows system without C++ installed (all things static linked in)?

---

### Post by vezinadj on 2013-08-04
I am not sure, 'WineTest.exe' is a c++ program written/built in visual studio that just prints hello world to the console output. I am currently just trying to get this to work right now on the beaglebone, then I am going to try to get my larger project running.


[COLOR=#008F00][FONT=Consolas][COLOR=#0433FF]#include[/COLOR][COLOR=#000000] [/COLOR][COLOR=#B4261A]<iostream>[/COLOR][/FONT][/COLOR]
[FONT=Consolas][COLOR=#0433FF]using[/COLOR][COLOR=#000000] [/COLOR][COLOR=#0433FF]namespace[/COLOR][COLOR=#000000] std;[/COLOR][/FONT]
[FONT=Consolas][COLOR=#0433FF]int[/COLOR] main()[/FONT]
[FONT=Consolas]{[/FONT]
[COLOR=#B4261A][FONT=Consolas][COLOR=#000000]	cout << [/COLOR]"Hello world!"[COLOR=#000000];[/COLOR][/FONT][/COLOR]
[COLOR=#0433FF][FONT=Consolas][COLOR=#000000]	[/COLOR]return[COLOR=#000000] 0;[/COLOR][/FONT][/COLOR]
[FONT=Consolas]}
[/FONT]

---

### Post by GwL3eNC on 2013-08-04
Ok, I'm not shure and evtl. you have to visit a greater programming forum or wait a bit someone else can help you better. It is possible that you have a false linker setting to build a self standing exe which can run on a system without c++. Try to look at your project settings, specialy the compiler and linking options. Try to find out how to build a static linked exe in c++. 

Please dont be angry if it was not the problem, but i can only think about that.

---

