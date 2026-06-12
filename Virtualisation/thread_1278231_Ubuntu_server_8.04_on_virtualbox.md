---
title: "Ubuntu server 8.04 on virtualbox"
date: 2009-09-29
forum: Virtualisation
---

### Post by ragebunny on 2009-09-29
Hey, im kindda new to using servers, but i've managed to get an ubuntu server up and running on virtual pc, the other thing is im not sure if this is going to benefit me at all.

I haven't at the moment got the chance to make a real server so i thought about virtual box, i use it for ubuntu desktop all the time. 

What i need to do, for now, is put webpages on it and view them, i have managed to set up the server and have it running, i type the command ifconfig and it gives me an ip address, when i go into my host os (windows 7 business) and type it into a broswer it doesn't give me anything.

I know i need to use some sort of FTP client to upload a webpage but i couldn't get that working as well. 

So is it possible to do all this using virtual box?

So any help would be awesome.

---

### Post by joebeasley on 2009-09-29
Install the apache web server.  (sudo apt-get install apache2)  If you enabled the firewall, you need to allow connections to port 80.

---

### Post by ainsworth_t on 2009-09-29
Aside from installing the appropriate servers on your Virtual Machine, in order to reach it from your host machine - or any other computer on your network for that matter - you will have to make sure the virtual machine NIC is configured to use a Bridged Adapter.

---

### Post by ragebunny on 2009-09-29
Hey thanks for getting back to me so fast.

I got the os installed and i have Apache, mysql and php installed, i have been using this tutorial:

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

The thing is, i am not using a personal network, im am connected to the network in my uni and im starting to think that could be why its not working. When i get the ip address by typing ifconfig | grep inet it gives me an ip address that is small, like this 128.0.0.1, but if i run ipconfig in my host os (Windows) it comes up with a virtual box ethernet ip address, both those come back with nothing.

I have also been looking at this bridge network thing on virtualbox, but everytime i change something i lose the internet connection on the virtual os.

I have also tried to connect to the server by using an sftp client but that also doesn't connect.

Does anyone know of any tutorials about running a server of virtual box or a virtual machine?

Thanks again for the help,
Brian.

---

