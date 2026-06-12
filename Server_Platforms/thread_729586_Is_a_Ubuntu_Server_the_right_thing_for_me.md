---
title: "Is a Ubuntu Server the right thing for me?"
date: 2008-03-20
forum: Server Platforms
---

### Post by hawky on 2008-03-20
Hello everyone,

I have interested with servers for a while. I have just recently gotten my hands on a free computer, and I thought this was a good opportunity to learn about servers!

I would like to know if using a Ubuntu Server the right thing for my current setup.

This is what I intend to do.

ISP -> Ubuntu Server -> DLink DIR655 (wireless) -> 3 Computers  + DI-604  -> 3 Computers

I'm guessing that the best thing to do would be to have the routers setup as LAN to LAN. 

The general idea is that the Ubuntu Server would allow us to create an FTP server for us to easily access our files from school. It would also allow to me to play around with things such as a web server or database. But the most important feature, and mostly related to my question, is that we would like to have the Ubuntu Server acts as our downloading server. Meaning, we would have a torrent program installed on there, and everyone would simply use the server to download their torrents, that way it would be easy to regulate the speeds to increase the performance of the network and eliminate slowdowns with regards to bandwidth limitations by throttling when we need to. 

Therefore, is this a feasible setup? Will using the router after the Ubuntu Server be of any problems (we need it for wireless). Can we use it for downloading? Do you have any recommendations?

Thanks for answering all of my questions!
Marc

---

### Post by hyper_ch on 2008-03-20
> **hawky said:**
> The general idea is that the Ubuntu Server would allow us to create an FTP server for us to easily access our files from school. It would also allow to me to play around with things such as a web server or database. But the most important feature, and mostly related to my question, is that we would like to have the Ubuntu Server acts as our downloading server. Meaning, we would have a torrent program installed on there, and everyone would simply use the server to download their torrents, that way it would be easy to regulate the speeds to increase the performance of the network and eliminate slowdowns with regards to bandwidth limitations by throttling when we need to. 
You don't need to place the server outside your lan. Just build your lan with the drouter connected to your modem and then forward the according ports (20/21 for ftp, 22 for ssh/sftp/scp, 80 for http) from the router to the server.

---

### Post by jonabyte on 2008-03-20
using the server version will allow you to learn command line in Linux, which, in my opinion is the best way to start learning Linux (especially if that is something that interests you).

---

### Post by hawky on 2008-03-20
> **hyper_ch said:**
> You don't need to place the server outside your lan. Just build your lan with the drouter connected to your modem and then forward the according ports (20/21 for ftp, 22 for ssh/sftp/scp, 80 for http) from the router to the server.

I know, but I thought that having it outside my LAN could give me some added flexibility such as LAN port throttling. Am I mistaken?

---

