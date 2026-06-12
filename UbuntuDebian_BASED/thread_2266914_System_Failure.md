---
title: "System Failure"
date: 2015-02-26
forum: Ubuntu/Debian BASED
---

### Post by bryanglennshaw on 2015-02-26
I installed Elementary OS Luna on my older Acer Aspire with no problems at all. My other laptop is a Dell Inspiron 1501 which was running Ubuntu 14.10. It was slow and laggy, I assume because the machine is older, but i would like to install again on a newer machine.  I decide to install Luna on the Dell to see if it would be faster. After installation, I updated the software, and then attempted to install additional drivers for my wireless card. This is where I am having a problem. The screen goes black, then comes up with tons of text that is nothing like I have seen before. I cannot do anything. the mouse cursor/pointer is visible, but unresponsive, the F1-F12 keys do nothing. Its as if the machine is completely locked up, all I can do is shut down and restart. 

Upon restart, i go to update manager, i am told that i cannot update, but i can do a partial update. I click on Cancel. Then i get a warning that the Software index is broken and that "it is impossible to install or remove any software. " It instructs me to run "sudo apt-get install -f" in terminal. 

In terminal, when I run this command, I get    E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Upon running this command, it starts to uninstall, then deleting module version 6.20.155., then goes to installing something. at the bottom of the terminal is depmod...... then the screen goes back to black, and tons of text. 

Everytime I try to install software, or do an update, this happens. The text displayed is different for each thing i try to install, but the same result. 

I was hoping that this has been encountered before, and what can be done about it. Thank you for your time, patience, and assistance in this matter.

---

