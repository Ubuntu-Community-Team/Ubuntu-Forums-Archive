---
title: "Ubuntu Uncomplicated Firewall turns off after every restart"
date: 2013-03-27
forum: Security
---

### Post by Traxster on 2013-03-27
Hello to all,             

Using GUFW to configure unclomplicated firewall. Reading the  following tutorial --> [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall).  Restarts cause firewall to turn off.  How do you maintain firewall on permanently?

             Is there a way to edit existing rulesets? If so, how?      

Any help would be greatly appreciated...     


traxster

---

### Post by slickymaster on 2013-03-27
> **Traxster said:**
> Hello to all,             

Using GUFW to configure unclomplicated firewall. Reading the  following tutorial --> [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall).  Restarts cause firewall to turn off.  How do you maintain firewall on permanently?

traxster

Your firewall is enabled. Just to be sure, you can run this command:
```
sudo ufw status
```
You have to keep in mind that GUFW is a GUI and because the system does not know if the person opening it is the same person that enabled the Firewall in the terminal, you start it as the user you logged into your system with, so the GUI programs privileges are the same as that users privileges. And because the GUI can't positively tell that the firewall is active, it rather shows it as inactive.
 "Unlocking" actually means "providing the program with root privileges", so now the GUI can ask the firewall about it status and show it correctly.

---

### Post by slickymaster on 2013-03-27
> **Traxster said:**
> Is there a way to edit existing rulesets? If so, how? 
Any help would be greatly appreciated... 
traxster

You'll find a great tutorial [here]("http://www.techotopia.com/index.php/Using_gufw_and_ufw_to_Configure_an_Ubuntu_11.04_Firewall").

---

### Post by Traxster on 2013-03-27
> **slickymaster said:**
> Your firewall is enabled. Just to be sure, you can run this command:
```
sudo ufw status
```
You have to keep in mind that GUFW is a GUI and because the system does not know if the person opening it is the same person that enabled the Firewall in the terminal, you start it as the user you logged into your system with, so the GUI programs privileges are the same as that users privileges. And because the GUI can't positively tell that the firewall is active, it rather shows it as inactive.
 "Unlocking" actually means "providing the program with root privileges", so now the GUI can ask the firewall about it status and show it correctly.


oh, ok, that makes perfect sense and when I checked the status of ufw it came up as active. 

thanks again

traxster

---

### Post by slickymaster on 2013-03-28
> **Traxster said:**
> oh, ok, that makes perfect sense and when I checked the status of ufw it came up as active. 

thanks again

traxster

Glad to help you.

In order to let other people searching the forums know that this thread provides a working solution, don't forget to mark it as solved. See my signature on how to do it.

---

