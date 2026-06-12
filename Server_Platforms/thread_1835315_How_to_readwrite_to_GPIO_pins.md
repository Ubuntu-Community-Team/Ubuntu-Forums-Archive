---
title: "How to read/write to GPIO pins?"
date: 2011-08-29
forum: Server Platforms
---

### Post by TecsolAus on 2011-08-29
Hi,
We're building a system to control playground equipment using an AValue ECM-LX800 single board computer, which has a pretty standard AT configuration. Part of the project will read push button inputs and operate relays to control a wheelchair accessible carousel. We're planning on writing the control process in php as there will also be a web interface.

I'm looking for techniques to read and write to the SBC's GPIO port. An example that reads and writes to a couple of pins would be ideal.  (I love blinking LEDs!)

My reasearch to date suggests I need to work with the /sys/class/gpio directory. If I LS the directory, I see 'export' and 'import' . So far I've not been able to discover how to use this!

Any suggestions very much appreciated.
James

If this is better posted an another forum, please let me know...

---

### Post by Wayne_V on 2011-08-29
I would start here:  [http://www.mjmwired.net/kernel/Documentation/gpio.txt](http://www.mjmwired.net/kernel/Documentation/gpio.txt)

---

### Post by TecsolAus on 2011-08-29
Thanks Wayne, 
It's a popular and well quoted article!
I was hoping someone might have some specific hands-on experience and examples using Ubuntu.
Cheers,
James

---

### Post by Wayne_V on 2011-08-29
you should be able to find sample code by googling 'linux gpio-sysfs example'.   Here are a couple:

[http://www.avrfreaks.net/wiki/index.php/Documentation:Linux/GPIO](http://www.avrfreaks.net/wiki/index.php/Documentation:Linux/GPIO)
[https://docs.blackfin.uclinux.org/doku.php?id=linux-kernel:drivers:gpio-sysfs](https://docs.blackfin.uclinux.org/doku.php?id=linux-kernel:drivers:gpio-sysfs)

---

### Post by TecsolAus on 2011-08-29
Thanks again.
I'm making partial progress:

The command: 
james@TSATCS:/$ sudo echo 23 > /sys/class/gpio/export
Gives the following error:
-bash: /sys/class/gpio/export: Permission denied

I read that the sudo permissions may only be applying to part of the command line, so I tried:
/$ sudo su
/# echo 023 > /sys/class/gpio/export
Which resulted in:
bash: echo: write error: Invalid argument

I also tried the GPIO number without the leading 0 Eg. 23.

Data sheet for the SBC lists ports GPO20 to GPO27, and GPI10 to GPI17

The /sys/class/gpio directory only contains two items: export and unexport. Should there be references there to the specific GPIO pins?

---

### Post by Wayne_V on 2011-08-30
Yes, to make redirection work you need to run the command in a sudo shell:

$ sudo sh -c "echo 23 > /sys/class/gpio/export"

or, you can temporarily switch to root with "sudo -s"

---

### Post by TecsolAus on 2011-09-06
Hi, the permissions makes sense.
Any ideas about the error message? I'm gueesing the actual GPIO pins  need to be defined somewhere, but I don't have a clue how to achieve  this!
The gpio directoru only has the items export, unexport. Should there be specific references to the GPIO hardware pins here also? Any clues how to create them?
Many thanks, James

---

### Post by TecsolAus on 2011-09-09
I've also found the board has a winbond W83627HG-AW IO chip. Does anyone know where drivers that allow the GPIO to be accessed in user space can be obtained?

---

### Post by daniix on 2012-02-14
Hi TecsolAus,

Have you got any success on this?

I have exactly the same problem with the same PC from Avalue:

ECM-LX800D

Any help would be really appreciated...

---

### Post by TecsolAus on 2012-02-14
Hi, It's working very well. 
Our contract programmer adapted the "Supertool" Linux program to work with the Windbond chip on the LX800D. He had to work through the data sheet dealing with the various registers in the chip. The driver runs as a system wide service, and our php based application uses it to read and write to the GPIO bits. The code is written in C. I'm happy to give you a copy of the code. 
If you are not a programmer yourself you might need to hire Russell for a few hours to assist integrate the drivers into your project. I can put you in touch if this is needed. 
Can you tell us more about what your are wanting to do?

---

### Post by daniix on 2012-02-15
Hi,

We are developing a very simple application to control an external module through usb interface. This works fine.

Additionally we need to read two alarm pins connected physically to the LX800D GPIO pins. This is what we cannot do.

I assume it could be done programming a kernel driver. What we tried is to program configure the ports from the user space as you commented in the previous posts:

/# echo [portnumber] > /sys/class/gpio/export
Which resulted in:
bash: echo: write error: Invalid argument

We don't know the port number, we tried with many with the same result.

It would be great to have a copy of the code.

Many thanks for answering.

---

### Post by Shibram14 on 2012-04-30
Hi TecsolAus,
I am facing the same problem. Can you kindly tell me how was it solved? If its possible kindly send me a copy of your code..
Thanks a lot..

---

### Post by Rigsmith on 2012-09-24
Hi

I would also appreciate a solution for A Value Hardware. Please email [email]info@rigsmith.co.uk[/email]

Kind regards

Dave

---

### Post by Rigsmith on 2012-10-01
Hi

I dont think this guy is watching the thread. Can we reopen this and get a solution on the page and public?

I am really stuck

---

