---
title: "making really small server for ethernet booting linux"
date: 2009-02-05
forum: The Cafe
---

### Post by xc1024 on 2009-02-05
i don't know how to describe this exactly, i was thinking about networking and i suddenly got an idea.

anyone heard of ubuntu on tap? i'm sure someone did. usage is pretty straightforward - you plug the computer using the ethernet cable to a socket and you boot ubuntu from the network. i was reading about how it is done.

here's the challenge - how to make something like this, just portable? it could perhaps be a box with 1 usb and 1 ethernet wire coming out (usb for power, eth for booting). 

i heard some routers are capable of running tftp server. there should be possible to build a simple electronic circuit to serve the linux image. storage could be a flash card or something.

i'm complete noob where it comes to electronic stuff, maybe someone more experienced could help me with this?

---

### Post by mcduck on 2009-02-05
You mean something like this: [http://en.wikipedia.org/wiki/BlackDog]("http://en.wikipedia.org/wiki/BlackDog")
[http://www.linuxdevices.com/news/NS8562564746.html]("http://www.linuxdevices.com/news/NS8562564746.html")

Sadly I don't think those are available any more, but getting a device like this would definitely be cool.. :D

---

### Post by xc1024 on 2009-02-06
i didn't mean exactly this, however it is a bit similar.

i was thinking of possibility of booting linux through ethernet, not the usb. usb would be used only as power supply.

as most routers have a tftp server and you can use it to flash firmware when they are bricked, i assume it may be a simple thing to do a similar thing, just serving a bootable linux instead of normal files. of course the mini-server COULD include the flash memory accessed by usb, why not.

---

### Post by UbuWu on 2009-02-06
Not completely what you mean, but a similar idea: the Jack pc, a pc in a power socket powered over ethernet. So it only needs a network connection, nothing else.

[http://gizmodo.com/gadgets/pcs/jack-pc-the-wall-socket-pc-177564.php](http://gizmodo.com/gadgets/pcs/jack-pc-the-wall-socket-pc-177564.php)

---

### Post by xc1024 on 2009-02-07
no. this is something _entirely_ different. the box would be only a _boot media_ just as cd, floppy or usb drive. the only difference is that it would be more sophisticated by making a computer plugged to it think that there is a network with only itself and the linux image server (box). 

the box wouldn't do _anything_ else than just serve the boot image. the computer plugged to the box would use the box only to boot. later, when the live system is loaded, box would be removed and replaced with an ethernet cable / switched to the direct connection mode. i'm including a draft of this.

basically, it works like this. you plug 1 to the target's ethernet port. you turn on the target and choose to boot from network. 5 supplies power to 2 and 3. you plug the previous ethernet cable to 4. 3 is a tftp server sending the boot image to target taking it from 2 and sending through 1. when target completes booting, you flip 6 changing the connection from 1 to 3 to 1 to 4.

sorry if i confused you, but it is the most clear way i can explain my idea.

---

### Post by xc1024 on 2009-02-17
bump

---

### Post by maybeway36 on 2009-02-17
It might be easier just to make the mini-server an LTSP server with 2 ethernet jacks - one for the Internet, and one for the clients. Then you'll need to leave the server on, of course.

---

### Post by xc1024 on 2009-02-18
Sorry if I ask a stupid question, but what does LTSP stand for?

---

### Post by haddog on 2009-02-18
Linux Terminal Server Project.

[http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by haddog on 2009-02-18
A mini ltsp...interesting. then you could administer from the clients with an 'admin account'. no gui on the server...

xc. check my thread out. search for 'LTSP Server with WIFI Internet'. btw, i have gotten the wifi to work. posting this reply from a thin client.

---

### Post by xc1024 on 2009-02-19
Sorry that I couldn't make my idea clearer and if I made you confused, but i'm looking for something more like this: [http://hackaday.com/2008/09/18/web-server-on-a-business-card-part-1/]("http://hackaday.com/2008/09/18/web-server-on-a-business-card-part-1/").

---

### Post by xc1024 on 2009-10-28
Please close the topic. I found a much simpler alternative involving a PLOP boot floppy to start the computer directly from USB.

---

### Post by haddog on 2010-04-02
Did you see this?

[http://www.linuxinsider.com/rsstory/66302.html](http://www.linuxinsider.com/rsstory/66302.html)

---

