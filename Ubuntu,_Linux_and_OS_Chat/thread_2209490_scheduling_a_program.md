---
title: "scheduling a program"
date: 2014-03-05
forum: Ubuntu, Linux and OS Chat
---

### Post by aashik2 on 2014-03-05
Is there a way by which we can schedule a program to be executed automatically evey 3 or 4 msec in linux with an RT patch? If yes can you give me a way to do it?
Thank You.

---

### Post by tgalati4 on 2014-03-06
Since you are compiling the kernel for real-time, modify the init loop and put your code there.

Some reading:

[http://linuxcommand.org/man_pages/adjtimex8.html](http://linuxcommand.org/man_pages/adjtimex8.html)

[http://en.wikipedia.org/wiki/Jiffy_%28time%29](http://en.wikipedia.org/wiki/Jiffy_%28time%29)

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1005802](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1005802)

How you implement the timer depends on what kernel you used.

---

### Post by aashik2 on 2014-03-06
@tgalati4 By doing so, how does it run automatically at equal interval of time?
for example my job is to produce pulses through the serial port. but the program should contain only the code for toggling the pin(ie the freq should not be set in the program). now the freq of the wave will be determined by interval of time between which the program is called.
I need help in the last part how can i schedule to call the program at equal interval of time?

---

### Post by tgalati4 on 2014-03-06
What is the user interface?  If frequency is controlled by a number typed into a terminal that requires code to take the number and determine the period (T) of the desired frequency and then add the correct number of NOP (no operation) or wait cycles to the loop.  How you interrupt the timer (in Jiffys) depends on the kernel and the real-time modifications that have been made.

If the frequency is controlled by a knob that varies a voltage that is fed into the sound port--that would require a very different algorithm for controlling frequency.

The challenge with using a serial port is that it has a specific baud rate (9600 Hz, 38400Hz, 115000Hz) that it operates at.  I don't know how easy it is to bypass the serial controller to send arbitrary frequency signals through it.  Typically this is done using a DAC card--digital-analog-controller with codes set to it to perform the frequency function.

Serial programming:

[http://tldp.org/HOWTO/Serial-Programming-HOWTO/](http://tldp.org/HOWTO/Serial-Programming-HOWTO/)

[http://en.wikibooks.org/wiki/Serial_Programming/Serial_Linux](http://en.wikibooks.org/wiki/Serial_Programming/Serial_Linux)

[http://stackoverflow.com/questions/10242648/programming-linux-serial-port-ttys0](http://stackoverflow.com/questions/10242648/programming-linux-serial-port-ttys0)

Frequency Generator:

[http://sine.ni.com/np/app/main/p/ap/mi/lang/en/pg/1/sn/n17:mi,n21:42/fmid/3009/](http://sine.ni.com/np/app/main/p/ap/mi/lang/en/pg/1/sn/n17:mi,n21:42/fmid/3009/)

The other option is to use the sound card and send waveforms of the correct frequency to create the pulses that you need.  This has the advantage of using a synthesizer to vary the frequency in real-time. Your 3 to 4 millisecond range is 250 to 333 Hz which is easy for the sound card to handle.

---

