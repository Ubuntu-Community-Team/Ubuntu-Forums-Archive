---
title: "Problem with Terminal in Ubuntu 8.04 in VirtualBox"
date: 2008-06-21
forum: Virtualisation
---

### Post by Virtua-Touch on 2008-06-21
I'm on a Windows XP host running Ubuntu 8.04 Hardy inside VirtualBox. My problem is that when I try to install something through terminal (it's too much time to go to Add/Remove or Synaptic) with sudo apt-install applicationhere, it will not let me type my password. Apt-get doesn't work, because it says that I am not root. My keyboard works everywhere else inside VBox, but not when using the sudo command. Thanks in advance.

---

### Post by Virtua-Touch on 2008-06-22
Sorry for the double post, but I really need this working.

I've tried it in VMware also, and I'm getting the same results. Unable to type password after a sudo command is very frustrating. Personally, I love Ubuntu and I do not want to give it up just because of this problem. Please help.

---

### Post by bluefrog on 2008-06-23
what makes you think your keyboard does not work for sudo? Because you don't see anything as you typed? This is normal. Type your password and hit enter.

---

### Post by Virtua-Touch on 2008-06-23
Nevermind. I used ```
sudo aptitude install amsn
``` And it worked.

---

