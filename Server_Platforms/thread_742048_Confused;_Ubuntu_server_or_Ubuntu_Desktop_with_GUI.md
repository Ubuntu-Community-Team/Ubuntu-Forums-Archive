---
title: "Confused; Ubuntu server or Ubuntu Desktop with GUI"
date: 2008-04-01
forum: Server Platforms
---

### Post by rgotten on 2008-04-01
I am a little bit confused, and help will be appreciated. I have decided to go the linux road to build my server,and from some advice it was my understanding that Ubuntu was the way to go. Then i realize ther eis Ubuntu Desktop and also there is a Ubuntu Server Edition. Then (since i have always being a windows person), i was inform to use the server edition and install a GUI, or use kubuntu, or use teh dektop edition and install server option. As i mention in other parts of this forum I have 3  wired computer and one wireless lapto netowr thrur a linksys router, All this sytem use Windows xp. Would like to have jpeg files, word documents and pdf files save on the server for access form all the computers on the server. 

I am willing to learn but there are so many opinion, that i would like to get the rigth orientation and guidance to choose the rigth option

coments will be appreciated

Thanks

rgotten:confused:

---

### Post by Dr Small on 2008-04-01
Unless you are prepared to use the command line on the server, you had best setup a desktop edition and build it into a server.

---

### Post by Nythain on 2008-04-01
well this really boils down to wether or not your server will have the resources to waste on a GUI...

being completely new i would suggest installing either the ubuntu or kubuntu desktop version (ubuntu = gnome kubuntu = kde, and thats basically personal prefrence)

from there you can install any of the packages that server would install, and you at least get a familiar desktop environment for your learning experience...

if at a later time you feel you are comfortable enough, you can remove the desktop environment to save on resources if you think you need to

---

### Post by c-ron on 2008-04-01
Ubuntu = Gnome
Kubuntu = KDE
Xubuntu = XFCE

Xubuntu would probably use the least system resources.
You can install the server and then add the xubuntu-desktop package .

---

### Post by netlogic on 2008-04-01
You also need to count in the increase amount of security vulnerabilities and stabilities.  It isn't recommended for any production environment. The test environment is ok Less is more in Linux.

---

### Post by rgotten on 2008-04-01
Well, I am willing to learn and would like to create a stable server where all my windows computer can access there files instead of heaving them all over the 4 different computer. From my understanding, the best way to go is install teh ubuntu server edition and then on top Xubuntu for desktop edition. 

Will the ubuntu server and Xubuntu desktop be explanatory or where should i start. I just finish creating a computer with 3 500 gb raid 5 2 gig ram with intel duo core..So where should i start?

Thanks

DRG

---

### Post by ryazkhan on 2008-04-01
I would encourage you to go with Ubuntu Desktop Edition because it is very user friendly and easy to use and configure. For files sharing I would sugguest SAMBA file sharing. Desktop and server are pretty much same but server dont have GUI and you have to configured every thing by your self. Because you said you are new to Linux so Ubuntu Desktop would be good option for you and later on when you feel comfortable with it you can go for server to save some hard drive and memory resources but good start would be Desktop edition nd for file share you definitly want samba. Please let us know what you want and where you need help!:)

---

### Post by rgotten on 2008-04-01
if i do that and then would like to go for the server edition, what will happen with the information store on the hard drive, since by that time i will have a full and running server. On the otehr hand, what is your opinion on doing the option of the ubuntu server and on top of that Kubuntu. 

Thanks for so much help

---

### Post by ramper4 on 2008-04-02
> **rgotten said:**
> On the otehr hand, what is your opinion on doing the option of the ubuntu server and on top of that Kubuntu. 

I am a relative newbie as well - after trying out AMP server on top of Kubuntu, I then tried Ubuntu Server (7.10) and installed kubuntu-desktop on top of that. Installation was pretty straightforward, except in fixing some minor glitches with the graphics driver and the sound to work. But I still prefer this solution - that is, ubuntu server first, then install kubuntu desktop on top of that, especially since I use the server as a sandbox for websites. LAMP server works perfectly with no tweaking required and it's a timesaver. Installation is pretty straightforward. Of course, you will have to install kubuntu from a black terminal the first time around. I've seen some kind of tutorial on that - will post again if I find it. If you are planning to have dual boot (which is what I have, with Vista), then some extra steps are required - and extra care with location of GRUB during installation.

Actually I came here looking for info on doing a clean install using Ubuntu server 8.04 (beta) + Kubuntu-KDE4.  Or may be I should wait three more weeks for the official release?

---

### Post by dmizer on 2008-04-02
regarding installing a gui on a server install:

server kernels are tuned to running from the cli, and sometimes have problems when you install a gui on top of them.

you are much better off installing a full desktop release (which comes installed with easily configurable tools for file sharing)

---

### Post by rgotten on 2008-04-14
--------------------------------------------------------------------------------

I have installed the server edition and have the option to install the extras: DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past and for the purpose i am building the server?

---

### Post by foolano on 2008-04-14
If you want to use a stand-alone server, I'd suggest to take a look at [eBox]("http://ebox-platform.com"). It's included with Ubuntu 8.40.

It has a simple GUI interface accessible through your browser. You can enable the samba module to share documents, it will allow you to create users and groups, for every group you can add a directory to share documents between users belonging to the group.

You can also use more of its features such as: firewall, proxy, content filter, dhcp, dns ... if you want to set up a scenario like [this]("http://trac.ebox-platform.com/wiki/Document/HowTo/SetUpNetworkScenario")

---

### Post by ism. on 2008-04-14
Hi Rgotten and other posters! I am doing the same exact thing as Rgotten and am in the same boat completely.I even have about the same computer scheme as him. I have tried both the GUI and the server edition now. In my opinion i think the GUI is bulky and messy in away(kinda weird way to describe it). I was going to go with the Server and try to learn everything the hard way but i like the install the server edition and put the Kubuntu over that idea.  Does anyone know of any guides or tips so i can try this?

thanks in advanced

-ism.

---

### Post by rgotten on 2008-04-16
Well i install everything on the server option setup, since i heard that is ligth. One thing i left with no configuration during the installation was the " mail configuration" and I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

Base on the above i have the following questions:

1) how to do the mail configuration or
2) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i need to install some componets after,  how you do this?) or
3) keep on playing for another 8 days and install server version 8.04 (by the way, will ubuntu upgrade authomatically??when new version come out??)

Thanks

rgotten

---

### Post by haryoh on 2008-04-16
refer to this post. That's a good way to know how to configure your mail server.

[http://ubuntuforums.org/showthread.php?t=661414](http://ubuntuforums.org/showthread.php?t=661414)
[http://www.howtoforge.com/lemp_nginx_mysql_php_ubuntu_debian](http://www.howtoforge.com/lemp_nginx_mysql_php_ubuntu_debian)
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

