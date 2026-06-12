---
title: "Updating in a network"
date: 2007-06-22
forum: Repositories &amp; Backports
---

### Post by JoseArmandoJeronymo on 2007-06-22
I run a home network with three boxes, two of them with Feisty and the third one to receive it ASA I can spare the time.

One of the boxes has an ADSL internet connection. Of course this machine gives the other two the internet connection they need via masquerading.

Now, my ISP imposes a 4GB monthly bandwith limit and although I normally do not use it all I think it rather stupid to download all updating packages via update manager three times, one for each machine. So, I am trying to make machines 2 and 3 read the archives folder in machine 1 and update from there.

Can anybody hint me the best way to do this? Would it be to mount 1's archives folder in 2 and 3 with NFS? Or would it make more sense to use Apache to send the files to those machines via HTTP? Or anything else?

Thanks

---

### Post by JoseArmandoJeronymo on 2007-06-23
I found an answer for the problem. Essentially, one uses apt-move to create a debian mirror in the router machine and a webserver to allow other machines on the lan to access the packages.

I did not try it for it seems to involve more steps than I have time for at the moment.

---

