---
title: "MAC filters and speed limitations"
date: 2014-02-06
forum: Server Platforms
---

### Post by Felhazi_Andrei on 2014-02-06
Hello,


I used to own an old RedHat server that was running an Intel Pentium III. I bet you can see why I decided to upgrade.:P


I installed Ubuntu server 13.10 on the new machine. It was pretty easy for me as it was not my first time with linux. I have everything up and running but I have 3 major problems.


On the old server, built and installed by a friend (he wrote me some commands on a piece of paper :)) I was able to:



[LIST=1]
[*]_Modify the network bandwidth and shape it per IP_ editing some files in **/etc/sysconfig/htb**, where I specified a certain rate and ceil for everyone in the LAN. (The files were named by the last two decimal numbers of the IP I was working on) . After I was done, I used to run **/etc/init.d/htb** restart, and everything was working like a charm. Everybody had a max Down/Up rate of 2Mbps. Also, the overall LAN never exceeded 2Mbps.
[*]_Filter MAC addresses_ so that no one except the MACs specified in  **/etc/ethers** was able to connect to my server. I added the MAC address of the device I wanted to allow and then: **"arp -f /etc/ethers"**. Again, worked like a charm.
[*]_Have graphs of the network usage_ of every machine in my LAN available at **"\\IP_local\htb"**.
[/LIST]


My question is: Can you point me in the right directions to find out the packages i need to install and configure to implement these functionalities again? Can you tell me which packages used these config files? How do I set this up again?
Unfortunately, I can`t contact the friend who built the server for me.

Thank you in advance for your responses and I admire your patience if you read all of this.:P

---

