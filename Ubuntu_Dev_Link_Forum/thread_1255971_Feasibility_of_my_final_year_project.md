---
title: "Feasibility of my final year project?"
date: 2009-09-02
forum: Ubuntu Dev Link Forum
---

### Post by kapmsd on 2009-09-02
Hello developers!!!
Myself and 2 other friends have an idea for our B.Tech final yr pjt(**Duration of **3 months)
We hope u guys can help us.

**Objective**:To avoid ubuntu system crashes due to incompatible updates.
          eg: I installed 9.04 and installed recommended updates and it               produced no display thereafter in the monitor(erratic unclear display rather).

**Idea**: Develop a system module which checks if new updates are compatible to dependent softwares by 
(i)installing the update(s) in some kind of virtual OS environment(We have no idea reg such virtual OS environment).
(ii)If not compatible, don't install that update in normal OS mode.

eg:I installed NetBeans IDE and it is dependent on some system file,say X.
If Update Mgr finds and lists a new verion for X,if installed,it might cause NetBeans not to work correctly.
   So we will install that update and run NetBeans IDE in virtual environment and if crashed,we will not install that update.

---

### Post by Tony Flury on 2009-09-02
The problem i can see is often that the crashes are with things that Ubuntu itself has no control - for instance Video drivers, and other hardware specific stuff - so your virtual OS environment would need to emulate all of the h/w specific stuff for that user, and bear in mind that some of the Best Virtual OS's on the market don't emulate the complete driver capabilities of the stuff like video hardware.

For a 3 month project, that is massive.

A better system might be - something like restore points, so you can install an update, and if that causes a crash, you have the option from the grub menu (maybe via the recovery portal) of removing the last updates - it probably should list the updates you have done, so you can selectively unpick - even so this would need updates to (off the top of my head) : 
apt-get (and probably things like dpkg ?)
Recovery console ?
Grub itself ?
And that is not a small job for one man in 3 months.

---

### Post by kapmsd on 2009-09-02
Thanks a lot for ur input.

In case of restore points,some problems we thought of were:
(i)If update mgr lists some 10 updates(for instance),we generally install all of them.
(ii)Even if any one caused a system crash,we would have to try 10 restore points(worst case) to get back ubuntu to stable state.

To overcome this only we thought of that idea.

---

### Post by dgtherock on 2009-09-02
Hello friends. As my friend KAPMSD explained the idea of our project i would like to brief a little. The main idea of our project aims at making the system and applications stable after the updates. Its a general thing that after some updates certain applications fail and in certain worst cases the entire OS might crash. To avoid such things I had suggested an idea. That is if an app X depends on Y and if Y gets updated then we must check whether X works with the updated version of Y. If yes the updates would proceed as usual. If not Y will not be updated and the checker tool would inform the user or the developers regarding the problem. The main problem here is we have only 3 to 4 months to do the project. We would like to have more ideas or suggestions to do this project. I suggested that we can simulate the interactions between Y and X after updation in a secured environment so that if something fails we could find that there is an incompatibility. But we want some idea how to simulate. Also such things would be time consuming. So we need some suggestions how to proceed. 

Thank you
Sudharsan

---

