---
title: "Ubuntu 15.10 LXC iptables port forwarding question"
date: 2015-12-22
forum: Virtualisation
---

### Post by bobk48 on 2015-12-22
I'm trying to port forward my host's port 80 to an LXC container running nginx. I have correctly installed both LXC on the host and nginx in a container, stated nginx in the container, and also used the lxc-info command to determine the ip address of the container as 10.0.3.223. There are no firewalls in action on either host or container. As suggested in several online posts, I have used the following two iptables commands to port forward port 80 on my host to port 80 on the container-

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 10.0.3.223:80
iptables -A FORWARD -p tcp -d 10.0.3.223 --dport 80 -j ACCEPT

But when I point my browser on another machine on the LAN to the host, I cannot connect to the nginx test page on the container. I know that because I have nginx running on the host with one form of the nginx test page, and nginx running in the container with another form of the nginx test page. The two above port forwarding commands should have made the browser bypass the host port 80 and exposed port 80 on the container, therefore showing me the nginx test page in the container.

What is interesting to me is that when I substitute port 22 for port 80 in the above two commands, I can then ssh from another machine on the network to the container, using the hosts ip address (and the username and password for the container user ubuntu)! In other words, the iptables port forwarding commands worked for port 22 but not for port 80, or so it appears.

Any suggestions about why these two commands don't work for port 80? 
Thanks!

As is usually the case with me, particularly coming from the PC-BSD and Solaris UNIX world, where forum clientele are devastatingly intelligent but rarely helpful in giving explicit and articulate answers, I had to solve this problem on my own. Not so in the Ubuntu forum community, as witnessed by the overwhelming response postings to this question. I applaud all of those who answered this post thread, bravo!!
The location of my index.html files for host and containers is actually at /var/www/html, and I was identifying host and container nginx welcome pages based off of some other bogus location I had made changes to the index.html files in. Once I identified host and container in the proper index.html file ( /var/www/html/index.nginx-debian.html), the two iptables commands were working exactly correctly.
I am about to embark upon some of the suggested network connectivity schemes indicated in this beautiful blog post-
[http://containerops.org/2013/11/19/lxc-networking/](http://containerops.org/2013/11/19/lxc-networking/)
Compare and contrast this basically 2 command method to the Docker -p option when creating a Docker container.
Also compare and contrast this 2 command method to the VirtualBox bridged network choice which is just a single GUI click to achieve something better.
Even comparable to iocage ifconfig aliasing on PC-BSD.
Correct?

---

