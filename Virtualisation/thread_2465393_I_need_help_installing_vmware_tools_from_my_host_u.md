---
title: "I need help installing vmware tools from my host ubuntu OS"
date: 2021-07-31
forum: Virtualisation
---

### Post by snype9lives on 2021-07-31
google didnt help so if anyone can help me find a way to install vmware tools on ubuntu for my windows xp VM that'd be nice.

---

### Post by MAFoElffen on 2021-07-31
The VMPlayer docs say it cannot be installed straight from the host, but through the player...
> VMware Tools is not bundled with VMware Player and cannot be downloaded  separately. It must be downloaded from within VMware Player, as part of  the Tools installation process.

Prerequisite: Your VM Guest needs to have a working network connection

> To install VMware Tools in VMware Player:
  
[LIST=1]
[*] 	Power on the virtual machine.

[*] 	Log in to the virtual machine using an account with Administrator or root privileges.

[*] 	Wait for the desktop to load and be ready.

[*] 	Click **Virtual Machine > Install VMware Tools**. For Player 4.x and above, Click on **Player** >** Manage **>** Install VMware Tools**
	
	VMware Tools downloads, in the form of an ISO. VMware Player mounts the  ISO and connects it to your virtual machine's CD/DVD drive.
	 

[*]Install VMware Tools from the CD-ROM inside of your guest  operating system. For more information, see the article that refers to  your virtual machine's operating system:
[/LIST]


---

### Post by snype9lives on 2021-08-01
bruh... that thats the thing I dont see that anywhere..

---

### Post by snype9lives on 2021-08-01
nevermind it works now

---

### Post by MAFoElffen on 2021-08-01
Good to hear it is working for you now.

Please remeber to use the Thread Tools in the upper right to mark this thread as "Solved" so other can find what worked for you.

---

