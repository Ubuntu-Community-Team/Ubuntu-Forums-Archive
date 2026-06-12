---
title: "Several Networking questions"
date: 2007-05-07
forum: Server Platforms
---

### Post by Dudsmacka2 on 2007-05-07
Hey everyone.  I am currently in the process of considering moving from the Wintel world to 'nix.  From everything I've read ubuntu is the way to go - so I'm going to give it the college try.  I was wondering if you guys wouldn't mind pointing me in the right direction on the following:

1.  How would I go about setting up my ubuntu box to accept remote console connections?

2.  How could I go about setting up static TCP/IP settings rather than having it obtained from DHCP?

3.  Are there any Linux-based WINS server solutions?  I couldn't seem to find any with google.

Thanks in advance!

---

### Post by rickyjones on 2007-05-07
> **Dudsmacka2 said:**
> Hey everyone.  I am currently in the process of considering moving from the Wintel world to 'nix.  From everything I've read ubuntu is the way to go - so I'm going to give it the college try.  I was wondering if you guys wouldn't mind pointing me in the right direction on the following:

1.  How would I go about setting up my ubuntu box to accept remote console connections?

2.  How could I go about setting up static TCP/IP settings rather than having it obtained from DHCP?

3.  Are there any Linux-based WINS server solutions?  I couldn't seem to find any with google.

Thanks in advance!

1) If you want remote console then you'll probably want to install the openssh-server package.

2) If you are running the Desktop version of Ubuntu then there is a nice GUI to this under System > Administration (I think!) Or, if this is Server, then you'll need to edit /etc/networking/interfaces and set your options there. The man page for the interfaces file (man interfaces) is pretty simple to follow - else I'm sure someone can type one up for you.

3) I'm not sure on that because last time I checked WINS was primarily a Microsoft technology. DNS is the way to go these days and would probably be a ton easier to setup.

Hope it helps!

-Richard

---

### Post by Bill007 on 2007-05-08
You can do all those things most times better then Windoz 


Edgy 6.10 Ubuntu Desktop or server or both

Try [http://ubuntuguide.org/wiki/Ubuntu:Edgy]("http://ubuntuguide.org/wiki/Ubuntu:Edgy")

6.10 was good everything seemed stable more stable then windozs at least I run a server in this version sweet

I network from a windows box to a 6.10 Ubuntu  Linux server via a samba server this is cool everything works fine  there is a learning curve here,  Linux is not easy you have to put time in to get an understanding but it is rewarding

 I now run two Linux servers one inside another both servers are running one subnet lan as well as a WAN, I can see from one LAN to the other on both windows machines and Linux machines Im wrapped

Feisty 7.04 Ubuntu  Desktop or server or both

Try [http://ubuntuguide.org/wiki/Ubuntu:Edgy]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

Feisty is new release and some people have or think they have problems mostly user error
I have gotten everything working to date it seemed a smoother set process more drivers in the kernel, plug and play Ubuntu have got this thing running great  this is where carefulness is required you have to be thorough when installing make sure you miss no packages


Have fun

Try dual booting that is awesome too  allows you to muck around with Linux while you make your transition 

BILL007

---

