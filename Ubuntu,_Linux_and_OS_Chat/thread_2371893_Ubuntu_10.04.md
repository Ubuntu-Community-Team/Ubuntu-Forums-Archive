---
title: "Ubuntu 10.04"
date: 2017-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by andrew.nederhoff on 2017-09-19
I am about to start work on a new project, and one of the requirements is to interface with a Serial I/O module for data output.  The module we have currently selected only has drivers that support Ubuntu 10.04 or earlier.  What are the major disadvantages of using 10.04 versus 16.04?  This project also needs to have a GUI (a relatively simple one) if that makes any difference.

---

### Post by cariboo on 2017-09-19
If you don't connect the system to a network, you should be OK. Support for 10.4 desktop ended 4 years ago. Ubuntu hasn't changed that much, so you may be able to use 16.04 for your project.

---

### Post by andrew.nederhoff on 2017-09-19
Would there be any potential issues with using Qt5 or C++11 since those came out after 10.04?

---

### Post by mastablasta on 2017-09-20
yes you would have issues. Have you tried 16.04 with the module? see if it works.

sometimes the drivers are no longer needed (added to kernel, replaced with alternative...) which is why they do not offer support after certain version.

---

### Post by cariboo on 2017-09-20
If you have the hardware resources, you can install 16.04 in a VM using virtualbox which is in the repositories, to try out your application in a newer version.

---

