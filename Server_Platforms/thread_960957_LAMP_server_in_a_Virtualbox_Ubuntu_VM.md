---
title: "LAMP server in a Virtualbox Ubuntu VM?"
date: 2008-10-27
forum: Server Platforms
---

### Post by vav on 2008-10-27
I wanted to set up a webserver for a low hit-count website. I have an Ubuntu machine that is used for work, so I don't want to expose this as a webserver!

Would it be any safer if I used Virtualbox on my Ubuntu work machine, created a LAMP Ubuntu install inside Virtualbox and used it as a server? Would I still need to open up the http ports on my host Ubuntu machine thus making it unsafe? Or would any intrusion damage be sandboxed in the virtual machine? 

Thanks, I'm a server newb

---

### Post by HermanAB on 2008-10-27
The VM will isolate the guest from the host against most anything.  If you use a bridged ethernet connection then there is no logical connection between the host and the guest.

---

### Post by vav on 2008-10-28
So the host will be protected from the guest webserver? That's what I was looking for. I'll still have to open the http port on the host though... (and bridge it to the guest thru the VM right?) so do I configure denyhosts or ufw to permit/deny any traffic?

---

