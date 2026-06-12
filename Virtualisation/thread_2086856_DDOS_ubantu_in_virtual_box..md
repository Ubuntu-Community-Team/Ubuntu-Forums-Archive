---
title: "DDOS ubantu in virtual box."
date: 2012-11-22
forum: Virtualisation
---

### Post by modaresi on 2012-11-22
There is a project that is assigned to me which has several parts. Of all the parts, I have no idea how to do the third part. 
The first part is: On a Linux or Windows host machine, install virtual machine software. Then create THREE virtual machines on the host machine. Each virtual machine is installed of a Linux OS.I have already implemented this. The second part is: Configure the virtual machines to be accessible remotely with Remote Desktop Protocol (RDP). I have done this one also. The third one and the one I have problem with is:Deploy a web server. Create a web page that contains the RDP clients. Each RDP client should correspond to a virtual machine. When somebody clicks a RDP client icon, a pop window should be given to display the remote desktop environment of that virtual machines so that s/he were working locally in front of that virtual machine. Now, how on earth can I do that? Any ideas? I know that you can install apache on the host and then use something like Guacamoleto in order to access it from anywhere and any operating system. As long as your browser supports HTML5 and ajax, there are other ones out there on Java also. But this is different. All three virtual machines have to be accessible from a single web-page. Guacamole cannot do that as far as I know. To make the matters more complicated I am required to create the web-page myself. Nope, I really don't know how to do this one. The rest is DDOS attack and this kind of stuff that I know how to do. If someone could help me with the third one, the rest would be no problem.
Thanks.

---

### Post by Groodles on 2012-11-23
Some sort of Java applet to handle the remote desktop session in a web browser?

[http://danielwebb.us/software/vnc/](http://danielwebb.us/software/vnc/) for a VNC protocol session

or

[http://properjavardp.sourceforge.net/](http://properjavardp.sourceforge.net/) for an RDP protocol session

---

