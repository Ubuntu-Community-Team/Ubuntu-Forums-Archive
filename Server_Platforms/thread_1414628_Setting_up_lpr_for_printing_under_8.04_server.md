---
title: "Setting up lpr for printing under 8.04 server"
date: 2010-02-23
forum: Server Platforms
---

### Post by IdeCable on 2010-02-23
Hi all,

I managed to install a networked printer to my box by

apt-get install system-config-printer-common system-config-printer-gnome

And using the system-config-printer, I can send print test page and it works.

Now, I noticed that I don't have lpr installed on this box.

So even if I install lpr or lprng I cannot seem to make it work. 

Ohh and by the way, the only thing I use to print from that box is Acrobat Reader 9.. it is proprelly installed. I can see the networked printer entry from the program.. but for some reason Acrobat Reader 9 needs to use lpr to send the print job. 

I wish to know what I am missing here. 

I can do lpstat -v and I see my printer entry from there.

Now: the question: how can I setup lpr to work with my networked printer? 

Should I install lpr or lprng? 





What is the proper way to install a networked printer under Ubuntu-server?

---

### Post by HermanAB on 2010-02-24
[http://www.aeronetworks.ca/print-howto.html](http://www.aeronetworks.ca/print-howto.html)

Ubuntu also has the Red Hat / Mandriva system-config-printer wizard.

---

### Post by IdeCable on 2010-02-24
Hi there,

I have an 8.10 Desktop box that works fine.. I can use lpr without telling where is my networked printer..

I am trying to find out how I can set lpr to default to one printer.

I believe I am missing a config somewhere.

---

