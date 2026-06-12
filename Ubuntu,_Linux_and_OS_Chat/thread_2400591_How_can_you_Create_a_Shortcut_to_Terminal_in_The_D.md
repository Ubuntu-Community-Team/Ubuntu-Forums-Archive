---
title: "How can you Create a Shortcut to Terminal in The Dock Or The Desktop"
date: 2018-09-07
forum: Ubuntu, Linux and OS Chat
---

### Post by sparks79 on 2018-09-07
I am using Ubuntu Desktop 18.04.1 64bit.
Could someone tell me How to Create a Shortcut to Terminal in The Dock Or The Desktop.
When I want to do something in Terminal as Administrator/root/super user etc in a hurry , it is annoying to have to enter the same stuff all the time.
Like when I go there now and need to do something as administrator I have to Enter the Following.
Sudo -i ,  then enter my password.
So what I would like is a Shortcut to Terminal as Root ( already Logged in ) and placed wherever I want it, like on the Desktop Or in The or in that Side Bar thing, I think its called the Dash or Dock.

---

### Post by vanadium on 2018-09-08
You can create a custom .desktop file with a script that automatically launches a root shell, but you will be breaching security. It is not at all a good idea to do something in Terminal as Administrator in a hurry. Upon normal use, you in principle never need a terminal. If you need to act as root, you will not be in a hurry and deliberately open the tools to work as root. All the rest is very bad practice.

---

