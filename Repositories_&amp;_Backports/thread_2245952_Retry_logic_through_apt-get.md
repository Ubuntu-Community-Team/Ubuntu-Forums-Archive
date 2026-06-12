---
title: "Retry logic through apt-get"
date: 2014-09-27
forum: Repositories &amp; Backports
---

### Post by Nader_Benmessaoud on 2014-09-27
Folks,

I need help please to implement the retry logic through apt-get tool. Here is the scenario.

1-Try to deploy package
2-If it succeed, we process the next instruction.
3-If it fails, retry within 60sec.
4- stop retrying after 30mins, and log errors.

Anyone can confirm that the below script works as expected

while ! echo y | sudo apt-get install lamp-server^ &> /home/azureuser/aptlamp.log
    do
        sleep 60
 sudo apt-get install lamp-server^ &> /home/azureuser/aptlamp.log
    done

Thanks,

---

### Post by ian-weisser on 2014-09-27
If an apt action fails, it fails for a reason.
Retrying before addressing the reason seems like wasted effort.

---

### Post by Nader_Benmessaoud on 2014-09-29
could be any temporary network/DNS issue, that goes away after few seconds.

---

### Post by ian-weisser on 2014-09-29
Will retrying apt for 30 minutes work? Sure it will. But it seems an inelegant solution to me.
Test your network access (ping) or DNS (dig) before starting the package manager.
The package manager can, at various times, be a heavy user of disk IO, CPU, memory, and network bandwidth.

---

