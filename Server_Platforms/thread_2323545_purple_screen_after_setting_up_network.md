---
title: "purple screen after setting up network"
date: 2016-05-06
forum: Server Platforms
---

### Post by mark282 on 2016-05-06
Hello,

I am trying to install Ubuntu server 64 bit 16.04 on an old inspiron 620 pc. I keep getting a purple screen when i am done setting up my network.
I have tried 32bit, i have tried 14.04 i have tried to install it without wireless adapter, i have tried to install it without the GT640.. i am out of idea's

I managed to do install ubuntu desktop without any issues.

edit: the issue i have is during the installation progress of the server version of ubuntu 16.04 and also 14.04

greetings,

Mark

---

### Post by ubu_dynamite on 2016-05-06
Sorry read that wrong this is still while installing?

> I have a virtualmachine Ubuntu server 64 bit 16.04 here that boots to a black screen but "CTRL-ALT-F1" will give me the tty to login maybe you could try that.

---

### Post by mark282 on 2016-05-06
yes this is still during the install, and ctrl-alt-f1 does nothing. i have searched some other commands that people tried. not sure if thats with the same screen or if thats ubuntu desktop boot... but that didnt seem to do anything at all.

Thx for the reply :D

---

### Post by mörgæs on 2016-05-06
Let's see more of the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by mark282 on 2016-05-07
> **mörgæs said:**
> Let's see more of the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

should i run this somewhere within the ubuntu server installation or within the up and running ubuntu desktop terminal?

---

### Post by mörgæs on 2016-05-07
Use any kind of Ubuntu you are able to get running.

---

### Post by nerdtron on 2016-05-07
> **mark282 said:**
> Hello,

I am trying to install Ubuntu server 64 bit 16.04 on an old inspiron 620 pc. I keep getting a purple screen when i am done setting up my network.
I have tried 32bit, i have tried 14.04 i have tried to install it without wireless adapter, i have tried to install it without the GT640.. i am out of idea's

I managed to do install ubuntu desktop without any issues.

edit: the issue i have is during the installation progress of the server version of ubuntu 16.04 and also 14.04

greetings,

Mark

Have you tried installing Ubuntu server edition while disconnected from the network? You can always setup the network (and other package updates) later. You just need to install the base OS and get it up and running.

---

### Post by mark282 on 2016-05-10
Oke, so. i looked carefully at when it crashed and then noticed it was after something with DHCPV6, so i looked in my router to see if it was enabled or disabled, i changed that to whatever it was not and then i could get trough the install without issues, sort of....

So now i have a server installed on this machine with 4 gig's, but its 32 bit, and i cant seem to get it 64 bits. as i am running a minecraft (game) server on it and i can't seem to give Java more heapsize. eventho i used the 64bit installer i keep getting 32bits install no matter what i have tried.

thanks for the replies. i am closing the thread as i have solved it. (if i can close it)

---

### Post by ubu_dynamite on 2016-05-10
What is the output of uname -a
```
uname -a
```

---

### Post by mark282 on 2016-05-14
uname -a results in 
Linux ubuntupc 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:39:02 UTC 2                                       016 i686 i686 i686 GNU/Linux

and i686 is 32 bit if im correct.. and java is also 32 bit installed.

---

### Post by ubu_dynamite on 2016-05-14
That is 32bit yes it is not possible to install 64bit packages on that you will have to reinstall with a 64bit OS if you want to use 64bit.

---

