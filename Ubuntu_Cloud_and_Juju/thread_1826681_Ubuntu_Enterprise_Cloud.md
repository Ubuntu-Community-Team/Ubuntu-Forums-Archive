---
title: "Ubuntu Enterprise Cloud"
date: 2011-08-16
forum: Ubuntu Cloud and Juju
---

### Post by sandrigo.net on 2011-08-16
Hi everybody. I have a question to do.

I have here in my infrastructure a machine Front-end and NC machine. After finished both installations, i had install a instance at a NC machine, it's all ok.
Now, i have a third machine to put in this private cloud. Is there need this machine to have VT extensions to be a client machine?
Other question: How can i "install" at this machine the image instantiated at NC?

Please, someone help me!

Sorry if i make some mistakes, I'm from Brazil.

Hugs.
Sandrigo

---

### Post by Dori922 on 2011-08-17
VT depends on what you want your machine to do bro!

If you want your machine to be a Node Controller you it has to have VT, because thats what UEC's default Hypervisor uses  for instances. You -can- work around this in theory using a different hypervisor, XEN but i tried to do that, wasted 2 weeks and just got a VT CPU in the end!! :P

If you want to use the machine as a Storage Controller or Cluster Controller, no, you dont need VT.

The second part of your question im confused at.. You can create as many copies of instances from the same image as you want(hardware limits aside).

Simply create a new instance from the same image on your node and attach the volume your using on the first instance to the new instance! :) 

Good luck bro, its frustrating enough but it gets easier!

Adam

---

### Post by kim0 on 2011-08-17
Thanks Dori for sharing your information. Really appreciate it

---

### Post by sandrigo.net on 2011-09-25
Hello friends of ubuntu forum!!

I have a issue in the Store Lab. When i click there i have the message below:
[B]
Error 60: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none[/B]

I've been tried update eucalyptus, but don't work yet. I had tried also:

**sudo wget -P /usr/local/share/ca-certificates/ --no-check-certificate [https://certs.godaddy.com/repository/gd-class2-root.crt](https://certs.godaddy.com/repository/gd-class2-root.crt) [https://certs.godaddy.com/repository/gd_intermediate.crt](https://certs.godaddy.com/repository/gd_intermediate.crt) [https://certs.godaddy.com/repository/gd_cross_intermediate.crt](https://certs.godaddy.com/repository/gd_cross_intermediate.crt)**[FONT=monospace]
[/FONT]**sudo  update-ca-certificates**

But until now i could resolve it.

Can somebody help me ? 

Sorry if i make some mistakes in the written, I'm from Brazil.

thank you!!

---

