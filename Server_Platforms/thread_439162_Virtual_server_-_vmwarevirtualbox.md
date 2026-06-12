---
title: "Virtual server - vmware/virtualbox"
date: 2007-05-10
forum: Server Platforms
---

### Post by encho on 2007-05-10
Hi, I wish to make virtual server on my Feisty desktop. What I want is to install Feisty/Edgy LAMP server in vmware/virtualbox and then access it from my desktop (which is host in this case) through browser. Eventually I wish for other computers in a network to access those virtual servers (even over the Internet). I am not sure how to go with IPs and stuff, as I have never attempted to do such a thing.

I have setup Edgy LAMP server in the past, registered IP on DynDNS, and it works without flaws. The thing is that I want to setup virtual servers now, only for testing purposes (different versions of apache/sql/php).

Maybe you could point me to some howto on this matter. Any help very appreciated.

---

### Post by encho on 2007-05-11
Anyone?

I have found one article on Vbox, but sounds complicated a bit:
[http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

---

### Post by PilotJLR on 2007-05-11
I'm not aware of any howtos... but I'd recommend using VMware Server. It's really pretty easy to install and use.

Once you have VMware installed, making a VM is wizard based and exactly the same as a physical install. The VM has its own unique IP address too.

So you can assign an address inside the VM, then point your browser to that address to serve up pages from the virtual LAMP server

---

### Post by encho on 2007-05-12
Cool, thanks. So I did it, you were right, it was very straight forward, I just had to select 'bridged' networking and that's it.

Now on to server config :) .

---

