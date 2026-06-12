---
title: "Some advice needed on remote servers"
date: 2011-01-18
forum: Server Platforms
---

### Post by skywatcher on 2011-01-18
I'm hoping that the experts can give me some advice on a subject with which I have very little experience. The scenario is as follows.

I'm using Maverick on a laptop, and I also have VirtualBox 4 installed and working. What I would like to do, is set up a server on the laptop which I can access remotely via the internet from any other computer. The laptop will be connected via USB to a webcam and a box of my own design which will be used to monitor and control external equipment (e.g. voltage and temperature sensor inputs, simple on/off relay outputs). When I access my server from a browser, I want to see what the sensors and camera see, and I want to be able to switch things on and off. The server should preferably run on a VM so that I can still use the laptop for general work without having to interfere with the server.

Is this possible, or is it wishful thinking?

---

### Post by R.Bucky on 2011-01-18
A couple of different methods to work the issue here. 

If you have a static IP available, you can configure ThinVNC ([http://www.supportsmith.com/ThinVNC/HTML5-VNC.aspx]("http://www.supportsmith.com/ThinVNC/HTML5-VNC.aspx")) on your laptop and remote into your laptop/Virtual instance via the web. 

Alternatively, you could configure VPN and RDP into your box. This option will be slow and limiting, but inherently more secure. 

Also, you will need to ensure that your laptop is capable of operating a VM for extended periods of time without overheating or utilizing a majority of system resources. Make sure that your VM Networking is configured for Bridged so that it acts like another box on the network and not on its own subnet.

---

### Post by skywatcher on 2011-01-21
Thank you for the information. I'll give it a try.

---

