---
title: "LXC connection problem, help please"
date: 2014-02-12
forum: Virtualisation
---

### Post by peter.onodi on 2014-02-12
Hey guys,
I have an irritating problem with the lxc container.
I have an ubuntu server 12.04 running and I have created 2 LXC containers (1, 2) with the original ubuntu template.
1. has internet connection with the dhcp, setting, everything is fine.
2. has internet connection with static, everything was fine.
after installing the Edubuntu-desktop on the 2., the connection just disappeared, the funny thing is, i can ping the 8.8.8.8 for 3 seconds then no answer
then I restarted and got connection for few seconds again
During this i had connection in the 1. container.
I deleted the network manager with purge, but still got the problem, I changed the nameserver to the bridge connection, but still, has connection for few seconds.
Also funny that, if i ping the host pc, i have connection for few seconds then disappear. 
any hint would be great
Thank you in advance.

---

### Post by peter.onodi on 2014-02-14
Update:  Problem solved, the problem was something brought the LXC package inside the LXC container, and thats why we could see the Bridge interface inside the container. removing the LXC package from the container solved the problem.

---

### Post by Iowan on 2014-02-14
You can help others with similar problems by marking the thread [[SOLVED}]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

### Post by peter.onodi on 2014-02-14
Oh sorry :)

---

