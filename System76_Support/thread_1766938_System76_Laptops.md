---
title: "System76 Laptops"
date: 2011-05-25
forum: System76 Support
---

### Post by iyerra on 2011-05-25
I am seriously considering the idea of owning a Linux laptop. System76 seems to be an attractive option. 
 
I am a technology consultant who is in a corporate IT environment that supports Windows XP (currently), Windows 7 (in the next few months), MS Office Apps (Word, Excel, PowerPoint, MS Project, Visio). 
 
MS Office Communicator is also used in this environment and I also need to install VPN software for remote acaccess.
 
a) My laptop frequently encounters "blue screens" and, quite honestly, I have no bandwidth to diagnose the root cause of this issue other than having to frequently reinstall the O/S and all the other personal productivity applications. 

b) Despite having adequate memory, the laptop takes "forever" to hibernate and startup. 

c) When Windows Updates are automatically downloaded, there is no guarantee that it will be installed successfully. I must point out that I have installed anything "non-standard" in my laptop.
 
I am exploring the feasibility of installing VirtualBox in a Linux machine and enhancing my overall user experience (including usability) while also ensuring that all my business requirements as described above are adequately covered. 
 
What I am not clear on is how should I get a copy of Windows XP and install it under VirtualBox? 
 
Rather than go down the path of self-service to transition from Win 7 to Linux, I'd like to figure out if there is a structured process for working with System 76 and configuring a Linux laptop that best meets my needs.
 
Thanks!
 
Ramu

---

### Post by jr223 on 2011-05-25
> **iyerra said:**
> I am seriously considering the idea of owning a Linux laptop. System76 seems to be an attractive option. 
 
I am a technology consultant who is in a corporate IT environment that supports Windows XP (currently), Windows 7 (in the next few months), MS Office Apps (Word, Excel, PowerPoint, MS Project, Visio). 
also need to install VPN software for remote acaccess.
 
a) My laptop frequently encounters "blue screens" and, quite 
b) Despite having adequate memory, the laptop takes "forever" to hibernate and startup. 
c) When Windows Updates are automatically downloaded, there is no guarantee that it will be installed successfully. I must point out that I have installed anything "non-standard" in my laptop.

What I am not clear on is how should I get a copy of Windows XP and install it under VirtualBox? 
 
Ramu


Hi,

I own a System76 Ratel (desktop) and am very very pleased.
However on the laptop front I have a dell insprion, which I installed Suse 11.3, it works great when I want to site outside on the patio.
For VPN there is no issue I use Ctirix for Linux, Citrix communicator 11, and the 9 or 10 client without the Gui for the Ratel.
Speed is excellent using Citrix to get to my work PC (WinXP).
Also open office or Libre office seem to be fine with handeling most MS formats, however if you must have office my sugestions is Wine (windows Emulator for Linux) and Office 2003.
There is also Cross over which is $ but is similar to wine.
For VM Sun Virtual Box works well with Windows XP, you will need to follow the instuctions for installation under VB heare 
[http://awebfactory.com.ar/node/387](http://awebfactory.com.ar/node/387)
There are also many articles on how to install Win7 etc. under VBox.

Cheers
JR223

---

### Post by jr223 on 2011-05-25
Opps missed one important item, yes you must have a CD/DVD windowz XP or 7 version to install with VBox.
Please look over and follow the instructions given or google them.
There is a lot of info on how to install.
There is even a site the name escapes me now where you can download VBox appliances (different apps, systems, OSes etc.) to test under VBox.
These are built inside VBox and saved as VBox appliances.

---

### Post by isantop on 2011-05-25
> **iyerra said:**
> I am seriously considering the idea of owning a Linux laptop. System76 seems to be an attractive option. 
 
I am a technology consultant who is in a corporate IT environment that supports Windows XP (currently), Windows 7 (in the next few months), MS Office Apps (Word, Excel, PowerPoint, MS Project, Visio). 
 
MS Office Communicator is also used in this environment and I also need to install VPN software for remote acaccess.
 
a) My laptop frequently encounters "blue screens" and, quite honestly, I have no bandwidth to diagnose the root cause of this issue other than having to frequently reinstall the O/S and all the other personal productivity applications. 

b) Despite having adequate memory, the laptop takes "forever" to hibernate and startup. 

c) When Windows Updates are automatically downloaded, there is no guarantee that it will be installed successfully. I must point out that I have installed anything "non-standard" in my laptop.
 
I am exploring the feasibility of installing VirtualBox in a Linux machine and enhancing my overall user experience (including usability) while also ensuring that all my business requirements as described above are adequately covered. 
 
What I am not clear on is how should I get a copy of Windows XP and install it under VirtualBox? 
 
Rather than go down the path of self-service to transition from Win 7 to Linux, I'd like to figure out if there is a structured process for working with System 76 and configuring a Linux laptop that best meets my needs.
 
Thanks!
 
Ramu

It sounds like a lot of your issues are issues with Windows in general. Ubuntu definitely would be a good path for you.

As for getting your stuff to run, I think virtualbox would be the easiest way. We have instructions on our knowledge base for setting up your own Windows Appliance in it. You'll need a standard Windows Installation Disk.

For hardware, you'll want to go with a relatively powerful system. I think a moderately spec'ed Gazelle or Serval would probably be perfect. 4GB of RAM should be enough, though 8 would be better. All of the processor options are quad-core so they should all be fine. You may want to consider going with a 500GB hard drive, but that will depend on your needs.

---

