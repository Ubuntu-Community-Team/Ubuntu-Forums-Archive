---
title: "Server Help: Why is Linux so damn hard to learn?"
date: 2006-07-09
forum: Server Platforms
---

### Post by stevewburke on 2006-07-09
Hello all,

1) Could someone please help direct me to some decent resources for learning how to setup a Ubuntu server?

2) Could someone please explain why these resources are so hard to find?

Honestly, why does the Linux community make Linux so damn hard to learn? I am a very technically inclined person. I am a computer technician and web programmer. I know over 20 prorgamming languages and I run my own Windows web server using Apache, MySQL, and PHP. I'm also not intimidated at all by command prompts. I use them every day and have been since I was a kid.

I want to make the change to Linux because I believe in open-source software. I want to help others learn Linux. As a technician I work on Windows PCs every day. I make a good living from Microsoft's poorly written proprietary code. I love the Apache/MySQL/PHP package, but I don't love running it on Windows systems. I used to say that I still use Windows because I need to stay familiar with it's problems to fix it.

One day, some distributer shipped our repair shop a box of Ubuntu CDs for free and I didn't have much of an excuse not to try it. I figured that if Linux was ready for the average user, then it would be no sweat for a technically savy person to start using it and being productive. I had no trouble installing OS, but NO IDEA how to use Linux. I spent hours and days (literally) trying to find and operate a simple MP3 player with no sucess. I downloaded packages but could never figure out how to install them or run them. I searched every help resource I could find, but NO ONE would say how Linux software works. I would read things like "Linux software is distributed in packages....", but never anything like "to run a Linux software package you need to...."

Here I am trying again. I was unable to install SUSE 10.1 because the installation would lock up every time (not impressed) at the same point and no one else in all of Google's billion's of web pages had posted the same issue. I was unable to properly install the latest Debian because it would error out when I selected the server packages I wanted installed (again, not impressed). The Ubuntu file server installed smoothly, but I expected to end up with GUI desktop. In the Ubuntu documentation it also states that there are several graphical editors for configuring the server's resources. But where are they? How do I find them? Are they already installed on my system? How do I run them? Why not include this information in the documentation? Where is the GNOME desktop bragged about on the website?

I want to actually use the server, not just install it. I want to start storing files and serving web pages. So where do I put files? Do I start throwing files into the root? Gee, that doesn't seem right. Do I create share folders in the root or somewhere else? Will that interfere with OS? I know about what every file/directory is for on a Windows system. I know what to stay away from and where to put things. What do the existing folders do in Linux? I don't need step-by-step Linux for dummies instructions. I just need a short summary of how Linux works for technically inclined people so I can find my way around.

What I'm NOT Looking For:

A) "Linux was originally developed by Sir Aurther of Engelwood in 1752 ..."

B) "Linux is spelled "Linux". Linux divides your computer into things called files and folders. While never verified, it has been rumored that some people have actually managed to install a Linux distribution on thier computer and do something productive with it ..."

B) "It's not actually possible to use Linux. It's reputation for stability comes from a simple axiom: 'If you can't actually get it running, then it can never crash.' For best performance, we recommend not installing Linux at all."

What I AM Looking For:

A) "To share files you should setup a folder in the [...] folder and configure it for NFS using [...]. This is the best way because of [...]"

B) "To install a package you should copy it the [...] folder and then do this to get Ubuntu to recognize it: [...]"

I appologize if I seem cranky, but I really am. I don't have any trouble finding help for Windows based software. I don't understand why all Linux documentation I've read assumes you're either a complete moron or a Linux expert. That's why most technical people don't learn Linux and then start teaching others. A common thing to say is that Linux is for technically inclined people. However, please note that 1) I am about as techincally inclined as they come and that 2) if the Linux community wants to make any progress towards getting on the average person's desktop (and getting MS off) then it needs to step forward educate people on how to accomplish their goals with Linux. 

Thank you for your time,
Steve

---

### Post by Dr. Nick on 2006-07-09
Well Ill help with a few issuses hopefully, I believe that the gnome desktop is not included in the server version. If you were to download the live cd or alternate install cd then you would end up in gnome after the installation is finished. It should be possible to get the gnome desktop with your current server install by using this command, aptitude is a package manager in ubuntu and other debian distros.

```
sudo aptitude install ubuntu-desktop
``` 
For more info look [here]("http://www.psychocats.net/ubuntu/nox")

If possible I would stick to installing applicarions in the repositories using aptitude, this is much easier then compiling the source yourself
 
For example to install apache would be
```

** sudo aptitude install apache2**
``` 


Most of the server applications like apache are not to bad to setup, Just simply edit the config file. I forgot right off hand where the apache one is. Usually the .conf files that need editing are in /etc/*program. *When you make a webpage the files usually go in a folder calles "www" which usually falls under /var directory.

The Wiki is a excellent resource for some of this stuff

Here are a few links you may find interesting, I personally havent used any of them since it has been awhile since I played with server applications. Their maybe better documentaion of the forums/wiki this is just a could that I saw first.

[Ftp Server]("https://help.ubuntu.com/community/FtpServer")
[Nfs Server]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[Few misc servers]("https://help.ubuntu.com/community/Servers?action=show&redirect=WebAndMailServers")

I imagine someone who has done this recently can help out some more aswell

Welcome to the Forums

EDIT
A few more howtos I found in a forum search
[http://ubuntuforums.org/showthread.php?t=185913&highlight=server+howto](http://ubuntuforums.org/showthread.php?t=185913&highlight=server+howto)

Note this one, webmin was a life saver for me when I had the urge to set up a server, its a web based admin for almost all server packages
[http://ubuntuforums.org/showthread.php?t=195093&highlight=server+howto](http://ubuntuforums.org/showthread.php?t=195093&highlight=server+howto)

---

### Post by nagilum on 2006-07-10
Finding good documentation is sometimes a real pain, you're right about that. But starting from a server version of Ubuntu is also not the best thing you can do to learn Linux. Better go with the desktop version. It offers the same functionality as the server, it just has a user-friendly GUI to start from. Try to get yourself familiar with the GUI and then descend deeper into the system. Unless you plan to use the server directly for production use I'd recommend you to do that, it will definitely make the learning curve less steep.

I'm afraid I can't point you to some nice introductory manual of the Ubuntu desktop, but there's a very good and detailed manual for Debian (which Ubuntu is based upon so it applies to it as well). The manual is quite lengthy but covers almost everything you'll need. Most of the chapters are organized in the practical way that you'd like to have: "to do <xxx>, execute the following commands and you should typically see <xxx>".
[http://www.debian.org/doc/manuals/reference/reference](http://www.debian.org/doc/manuals/reference/reference)

Another good resource for HOWTOs is [http://www.tldp.org](http://www.tldp.org), although the documents there are mainly for quite specific topics (like networking) and not for a general overview or introduction.

HTH

---

### Post by dk_pa on 2006-07-10
Hmm, well, since I didn't notice it referenced a great way to start learning (for some apps with good manuals) is "man appanme" from the terminal.  So like... from terminal just type man samba .. some thing like that and you'll get some nice pages of info (hopefully).   There is also like appname --help in most cases.

I would say an overwhealming part of your post has false expectations.  Such as.. > Ubuntu file server installed smoothly, but I expected to end up with GUI desktop.

I think you're first problem is you should NOT know what to expect and not build up an expectation.  Linux is very different and takes awhile to really catch on to sometimes.  

You could start with something like SAMBA and set that up and read through the config file.  [http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html](http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html) will start you off with that.  

If you really are interested in Linux then hold off on those GUI interfaces and try learning some basic VI --> [http://goforit.unk.edu/unix/unix11.htm](http://goforit.unk.edu/unix/unix11.htm) or Nano commands.  To get into vi simply type "vi filename" from a terminal. That will get you started editing whateve filename you bring up or it will create a new file.  

> I don't need step-by-step Linux for dummies instructions. I just need a short summary of how Linux works for technically inclined people so I can find my way around.

Unfortunately I'd say that is your single biggest problem.  You may know technical things and Windows and whatever else but until you realize (and drop the ego) that this is something new you wont' be learning much.  Suck it up and admit your a n00b (we all start somewhere) and go from there.  Here a decent link to get you started tho [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by lamego on 2006-07-10
The title for this thread should be "Why do I have to read instead of clicking?" .
If you don't know nothing about Linux/Unix servers you should start by reading some guides about it before even thinking on installing it, most of your questions would be gone.
Try to find an unix administratior which have never used a Windows server and see why is so damn hard for him to learn Windows.

---

### Post by Epica on 2006-07-10
I can understand why it is so much trouble. Often the documentation skirts round issues that the writers think is blindingly obvious, but isn't so to people who know quite a bit about computers but are using linux for the first time. If better documentation was provided at all levels (and not just absolute newbie and Linux expert) then linux would be easier for people to convert to.

---

### Post by FredSambo on 2006-07-10
[http://www.admin.com/]("http://www.admin.com/") 

for great justice.

---

### Post by harisund on 2006-07-10
[QUOTE=stevewburke]Hello all,

1) Could someone please help direct me to some decent resources for learning how to setup a Ubuntu server?
[/QUOTE]
I think you have already found plenty by now. 

> 
2) Could someone please explain why these resources are so hard to find?

Maybe because either you are looking in the wrong place, or you don't know where to look? 

> ]
Honestly, why does the Linux community make Linux so damn hard to learn?

Quiet on the contrary. The Linux community plays a huge role in the success of Linux, both on the desktop and on the server. Frankly, yes, Linux does have a relatively steep learning curve. Especially for people who come from a typical Windows background. So you should be grateful for the community (I am atleast)

> 
 I am a very technically inclined person. I am a computer technician and web programmer. I know over 20 prorgamming languages and I run my own Windows web server using Apache, MySQL, and PHP. I'm also not intimidated at all by command prompts. I use them every day and have been since I was a kid.

This is good, since it will greatly lessen the slope of the learning curve. All you need to do is approach Linux with an open mind, and be prepared to un-learn everything you have learned with Windows. Linux is NOT Windows, come to grips with this conclusion. 
And yes, the command prompt can be intimidating. 

> 
I want to make the change to Linux because I believe in open-source software. 

Welcome !

> 
I want to help others learn Linux. As a technician I work on Windows PCs every day. I make a good living from Microsoft's poorly written proprietary code. I love the Apache/MySQL/PHP package, but I don't love running it on Windows systems. I used to say that I still use Windows because I need to stay familiar with it's problems to fix it.

This is excellent. You are happy in Windows land, but still want to make the switch. You are willing to help others out. I love all open source packages (in fact, in my Windows box, nothing is non-free except Windows itself :) ). 

Now, you are halfway there, but you still need a couple more stuff before you can become proficient. 
1. Patience
2. Willingness to learn something new. 
3. More patience. 

> 
One day, some distributer shipped our repair shop a box of Ubuntu CDs for free and I didn't have much of an excuse not to try it. I figured that if Linux was ready for the average user, then it would be no sweat for a technically savy person to start using it and being productive.

It all depends on how you define "productive." Listen to mp3s? Hmm.... writing some Python code? hmmm... 

>  I had no trouble installing OS, but NO IDEA how to use Linux. 

Again, it all depends on what you mean by "use Linux." Use it for what? Write code? Watch movies? Listen to songs? Browse online? 

> 
I spent hours and days (literally) trying to find and operate a simple MP3 player with no sucess. I downloaded packages but could never figure out how to install them or run them. I searched every help resource I could find, but NO ONE would say how Linux software works. I would read things like "Linux software is distributed in packages....", but never anything like "to run a Linux software package you need to...."

Here's your big problem. You are attempting something totally new, but have completely forgotten to do some background research. Let's say you have been playing the casio for years now, and I tell you that since you are good with instruments, you can work your way through this guitar and ask you to play the Mozart something. Can you do it? Ok maybe bad comparison, but the point I am trying to make is, you are attempting something completely new, and you are under the biased frame of mind that you know how to handle yourself in that new world.

> 
Here I am trying again. I was unable to install SUSE 10.1 because the installation would lock up every time (not impressed) at the same point and no one else in all of Google's billion's of web pages had posted the same issue. I was unable to properly install the latest Debian because it would error out when I selected the server packages I wanted installed (again, not impressed). 

Yes, choice. That is what makes Linux popular. You don't like something? Fine go with another option .. nobody's stopping you. On the contrary, people welcome you. Search through these forums. There are tons of Ubuntu users who actually suggest users to try other distros as well if Ubuntu doesn't fit every minute need. 

> The Ubuntu file server installed smoothly, but I expected to end up with GUI desktop. 

Yes, because probably when you installed Windows Server, it came with the regular GUI. No, Linux servers do not come with a GUI, since it takes up more space, more system resources to have a GUI running all the time, and everything you can do with a GUI you can do with a terminal as well, atleast for servers. 

> In the Ubuntu documentation it also states that there are several graphical editors for configuring the server's resources. But where are they? How do I find them? Are they already installed on my system? How do I run them? Why not include this information in the documentation? Where is the GNOME desktop bragged about on the website?

Questions, questions, questions. But no patience for answers. Why? Relax... approach things step by step. Ask and you shall be answered. 

> 
I want to actually use the server, not just install it. I want to start storing files and serving web pages. So where do I put files? Do I start throwing files into the root? Gee, that doesn't seem right. Do I create share folders in the root or somewhere else? Will that interfere with OS? I know about what every file/directory is for on a Windows system. I know what to stay away from and where to put things. What do the existing folders do in Linux? I don't need step-by-step Linux for dummies instructions. I just need a short summary of how Linux works for technically inclined people so I can find my way around.

Instead of "technically inclined people" I think you should be mentioning "people who are pros at Windows, but don't know anything about *nix". That will make people more friendly towards you. 

And actually, yes, you do need step by step instructions. Yes, we all did, and those who help others in the forums are now in a stage where they can repeat those steps for the benefit of others. 

> 
What I'm NOT Looking For:

A) "Linux was originally developed by Sir Aurther of Engelwood in 1752 ..."

B) "Linux is spelled "Linux". Linux divides your computer into things called files and folders. While never verified, it has been rumored that some people have actually managed to install a Linux distribution on thier computer and do something productive with it ..."

B) "It's not actually possible to use Linux. It's reputation for stability comes from a simple axiom: 'If you can't actually get it running, then it can never crash.' For best performance, we recommend not installing Linux at all."

Nobody gives you that either. 

> 
What I AM Looking For:

A) "To share files you should setup a folder in the [...] folder and configure it for NFS using [...]. This is the best way because of [...]"

B) "To install a package you should copy it the [...] folder and then do this to get Ubuntu to recognize it: [...]"

Yes, you will receive all of this and more. Prepare to be amazed. 

> 
I appologize if I seem cranky, but I really am. I don't have any trouble finding help for Windows based software. 

My friend, you don't realize that you have worked with Windows so long that you know exactly where to go for help and know exactly the terms to google for. (Ha! Now that google is officially a verb :) ). Just because you have probably been using Windows since childhood and had someone with Windows to help you when you initially had your problems doesn't imply everything is easy. 

I will give you a practical example. Stupid Norton, when you uninstall it, takes away your DHCP client with it. Google it. I have also worked as a system/network admin for Windows machines and I too know the difficulties with the services that run in the background. I bet you didn't magically know it, right? If you were faced that problem (I was) it would have taken you a while to figure it out. 

Search also for, if you are interested, people who have "made the switch from Linux to Windows" and you will find out how tough people have it. 

[http://home.xnet.com/~raven/Sysadmin/ASR.Quotes.html](http://home.xnet.com/~raven/Sysadmin/ASR.Quotes.html)
This web pages talks about sys admins using *nix and Windows (meaning people who are more experienced than you, my friend) and how they complain about Windows. During Windows boot time, all you see are a bunch of clouds. Think that is good? No, it hides all potentially useful boot time messages. 

> I don't have any trouble finding help for Windows based software.  Again, because you know your way through. I can tell you the same thing with Ubuntu, because I know the forums and the IRC will pull me through. :)


> 
I don't understand why all Linux documentation I've read assumes you're either a complete moron or a Linux expert.
Change that. "either a complete Linux moron or a Linux expert". I am afraid you fall in the first category (no offense intended.)

People do start out as Linux morons, yes. We all do. Ask anybody in these forums. Trust me, we all do. 

What then takes us to the level of "linux experts"? Years of sweating it out, patience. Making friends on the forums and IRC whiel trying to debug a problem. 

Again, the beauty is simply that none of "linux experts." We are all learning, and we all learn something new every single day. Such is the power of open source stuff. 

> 
 That's why most technical people don't learn Linux and then start teaching others. A common thing to say is that Linux is for technically inclined people.
If you think using the "command line" is being geeky and technical, and wearing a T-shirt that says "I use a *nix based machine and I get laid about as often as I have to reboot" doesn't make one technically inclined. Technically inclined is more of an ability to soak in new stuff (involving computers) and ultimately making a machine behave itself (irrespective of the OS). It is not about being able to install servers and websites and silly little stuff. 

> 
 However, please note that 1) I am about as techincally inclined as they come
In the windows world. Yes. Nobody denies that. 

>  and that 2) if the Linux community wants to make any progress towards getting on the average person's desktop (and getting MS off) then it needs to step forward educate people on how to accomplish their goals with Linux. 

Wait, are you talking about desktop or server? Let me tell you, an average person has nothing to do with servers. (And having anything to do with servers doesn't make you technically inclined either). There are plenty of stuff being done to eliminate Ubuntu's bug number 1. 


But yes, I do agree. Sometimes documentation is not enough and people's help just doesn't cut it either. I have seen plenty of "how do I install Apache" questions being answered by "sudo apt-get install apache2". The conversation ends there, but what the person replying deosn't realize is that just "sudo apt-get install apache2" isn't sufficient. You need to mention that the files being served are in /var/www. You need to mention that apache file structure for debian has been extensively modified (most people scream at finding an empty httpd.conf. I know.) They don't mention that "sudo a2enmod" is the nice way to add modules. They don't mention that "sudo invoke-rc.d apache2 restart" restarts the server. Without all this, the user is as nearly lost as he was before knowing the command for installing apache. 

But what you must realize is that every one of us here who offer support are doing it out of a love for the OS, and purely out of an interest to help others. We have all been helped ourselves (look for anybody who has made plenty of posts in this forum. They will have both questions and answers. I have. Out of my 400+ posts, some 150 of them are "how do I do..." and the rest are "so this is how you need to do.."


> 
Thank you for your time,
Steve

You are welcome. 

So where do you want to start?

---

### Post by venzen on 2006-07-10
Well,

Firstly, welcome to the community and keep asking questions. That's how I learnt linux. The most useful resources I can recommend are:

1. These ubuntu forums

2. [http://www.google.com/linux]("http://www.google.com/linux")

3. [http://tldp.org/]("http://tldp.org/")

Home of a thousand linux HOWTO's

4. The GNU/Debian Bible (paperback)

The thing about linux is that the learning curve is *as steep as you make it  for yourself*, in your case quite steep, since you want to start serving files and everything else asap. Half your battle is won in the fact that you have no fear of the command line. Good luck and see you around.

---

### Post by az on 2006-07-11
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by ExMachina on 2006-07-11
Ive been using Linux for 3 years now.
Ive had not so good help with most otehr distros . Mandrake , fedora , gentoo. But Ubuntu has been wonderful. I have a problem post on forums or in chat in within a few day its fix( usally an hour or two). Thank everyone.

---

### Post by LordHunter317 on 2006-07-11
> **stevewburke said:**
> 2) Could someone please explain why these resources are so hard to find?They're not.  what I see is you're not very good at searching and you're not good at asking for help. 

> Honestly, why does the Linux community make Linux so damn hard to learn?It's no harder than Windows.  You honsetly don't know what hard is.  AIX is hard(er).  VMS is hard.  OS/390 is hard.  Linux is easy.

> So where do I put files? Do I start throwing files into the root? Gee, that doesn't seem right.Well, I wouldn't put files directly in slash, but it's your system so ultimately you put your content where you please.  Some places will be eaiser to cope with than others, though.

> I know about what every file/directory is for on a Windows system.Doubtful.  Anyway, as your filesystem issues are concerned, look up the Linux Filesystem standard, which will explain things.

> I appologize if I seem cranky, but I really am. I don't have any trouble finding help for Windows based software.I personally doubt this.

> I don't understand why all Linux documentation I've read assumes you're either a complete moron or a Linux expert.Most people tend to fall into one category or the other.  The rest ask for help, solving the problem.

> A common thing to say is that Linux is for technically inclined people. However, please note that 1) I am about as techincally inclined as they come and that 2) if the Linux community wants to make any progress towards getting on the average person's desktop (and getting MS off) then it needs to step forward educate people on how to accomplish their goals with Linux. You can't educate anyone if they don't come to learn, something you utterly failed to do.

---

### Post by bluenova on 2006-07-11
It's really not so hard, just new to you. Imagine trying to setup a server in MS Windows having sat down at a MS Windows machine for the very first time. I think you wouldn't know where to 'start' (pun intended), and getting free support for setting up your Windows server would be a lot harder than with Linux.

---

### Post by uncleclinto on 2006-07-11
A-freakin-men!!!!   Halleighluya!  My feelings exactly.  I want to migrate my site from WAMP to LAMP, but I keep getting the same crap.  I also get told to look to the article found here: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06), which by my reckoning, has NOTHING to do installing and running a LAMP server.  I have the box.  I have the CD.  I just need a little more guidance than the same darn links and axioms over and over.

---

### Post by FredSambo on 2006-07-11
> **harisund said:**
> I think you have already found plenty by now. 


Maybe because either you are looking in the wrong place, or you don't know where to look? 


Quiet on the contrary. The Linux community plays a huge role in the success of Linux, both on the desktop and on the server. Frankly, yes, Linux does have a relatively steep learning curve. Especially for people who come from a typical Windows background. So you should be grateful for the community (I am atleast)


This is good, since it will greatly lessen the slope of the learning curve. All you need to do is approach Linux with an open mind, and be prepared to un-learn everything you have learned with Windows. Linux is NOT Windows, come to grips with this conclusion. 
And yes, the command prompt can be intimidating. 


Welcome !


This is excellent. You are happy in Windows land, but still want to make the switch. You are willing to help others out. I love all open source packages (in fact, in my Windows box, nothing is non-free except Windows itself :) ). 

Now, you are halfway there, but you still need a couple more stuff before you can become proficient. 
1. Patience
2. Willingness to learn something new. 
3. More patience. 


It all depends on how you define "productive." Listen to mp3s? Hmm.... writing some Python code? hmmm... 


Again, it all depends on what you mean by "use Linux." Use it for what? Write code? Watch movies? Listen to songs? Browse online? 


Here's your big problem. You are attempting something totally new, but have completely forgotten to do some background research. Let's say you have been playing the casio for years now, and I tell you that since you are good with instruments, you can work your way through this guitar and ask you to play the Mozart something. Can you do it? Ok maybe bad comparison, but the point I am trying to make is, you are attempting something completely new, and you are under the biased frame of mind that you know how to handle yourself in that new world.


Yes, choice. That is what makes Linux popular. You don't like something? Fine go with another option .. nobody's stopping you. On the contrary, people welcome you. Search through these forums. There are tons of Ubuntu users who actually suggest users to try other distros as well if Ubuntu doesn't fit every minute need. 


Yes, because probably when you installed Windows Server, it came with the regular GUI. No, Linux servers do not come with a GUI, since it takes up more space, more system resources to have a GUI running all the time, and everything you can do with a GUI you can do with a terminal as well, atleast for servers. 


Questions, questions, questions. But no patience for answers. Why? Relax... approach things step by step. Ask and you shall be answered. 


Instead of "technically inclined people" I think you should be mentioning "people who are pros at Windows, but don't know anything about *nix". That will make people more friendly towards you. 

And actually, yes, you do need step by step instructions. Yes, we all did, and those who help others in the forums are now in a stage where they can repeat those steps for the benefit of others. 


Nobody gives you that either. 


Yes, you will receive all of this and more. Prepare to be amazed. 


My friend, you don't realize that you have worked with Windows so long that you know exactly where to go for help and know exactly the terms to google for. (Ha! Now that google is officially a verb :) ). Just because you have probably been using Windows since childhood and had someone with Windows to help you when you initially had your problems doesn't imply everything is easy. 

I will give you a practical example. Stupid Norton, when you uninstall it, takes away your DHCP client with it. Google it. I have also worked as a system/network admin for Windows machines and I too know the difficulties with the services that run in the background. I bet you didn't magically know it, right? If you were faced that problem (I was) it would have taken you a while to figure it out. 

Search also for, if you are interested, people who have "made the switch from Linux to Windows" and you will find out how tough people have it. 

[http://home.xnet.com/~raven/Sysadmin/ASR.Quotes.html](http://home.xnet.com/~raven/Sysadmin/ASR.Quotes.html)
This web pages talks about sys admins using *nix and Windows (meaning people who are more experienced than you, my friend) and how they complain about Windows. During Windows boot time, all you see are a bunch of clouds. Think that is good? No, it hides all potentially useful boot time messages. 

 Again, because you know your way through. I can tell you the same thing with Ubuntu, because I know the forums and the IRC will pull me through. :)



Change that. "either a complete Linux moron or a Linux expert". I am afraid you fall in the first category (no offense intended.)

People do start out as Linux morons, yes. We all do. Ask anybody in these forums. Trust me, we all do. 

What then takes us to the level of "linux experts"? Years of sweating it out, patience. Making friends on the forums and IRC whiel trying to debug a problem. 

Again, the beauty is simply that none of "linux experts." We are all learning, and we all learn something new every single day. Such is the power of open source stuff. 


If you think using the "command line" is being geeky and technical, and wearing a T-shirt that says "I use a *nix based machine and I get laid about as often as I have to reboot" doesn't make one technically inclined. Technically inclined is more of an ability to soak in new stuff (involving computers) and ultimately making a machine behave itself (irrespective of the OS). It is not about being able to install servers and websites and silly little stuff. 


In the windows world. Yes. Nobody denies that. 


Wait, are you talking about desktop or server? Let me tell you, an average person has nothing to do with servers. (And having anything to do with servers doesn't make you technically inclined either). There are plenty of stuff being done to eliminate Ubuntu's bug number 1. 


But yes, I do agree. Sometimes documentation is not enough and people's help just doesn't cut it either. I have seen plenty of "how do I install Apache" questions being answered by "sudo apt-get install apache2". The conversation ends there, but what the person replying deosn't realize is that just "sudo apt-get install apache2" isn't sufficient. You need to mention that the files being served are in /var/www. You need to mention that apache file structure for debian has been extensively modified (most people scream at finding an empty httpd.conf. I know.) They don't mention that "sudo a2enmod" is the nice way to add modules. They don't mention that "sudo invoke-rc.d apache2 restart" restarts the server. Without all this, the user is as nearly lost as he was before knowing the command for installing apache. 

But what you must realize is that every one of us here who offer support are doing it out of a love for the OS, and purely out of an interest to help others. We have all been helped ourselves (look for anybody who has made plenty of posts in this forum. They will have both questions and answers. I have. Out of my 400+ posts, some 150 of them are "how do I do..." and the rest are "so this is how you need to do.."




You are welcome. 

So where do you want to start?


well done!

---

### Post by FredSambo on 2006-07-11
> **uncleclinto said:**
> A-freakin-men!!!!   Halleighluya!  My feelings exactly.  I want to migrate my site from WAMP to LAMP, but I keep getting the same crap.  I also get told to look to the article found here: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06), which by my reckoning, has NOTHING to do installing and running a LAMP server.  I have the box.  I have the CD.  I just need a little more guidance than the same darn links and axioms over and over.

you need to think about the steps that you need to take to migrate from windows to linux.

make a list.

that tutorial will help you install and configure an ubuntu server with the following add-ons (LAMP):

    *  Web Server: Apache 2.0
    * Database Server: MySQL 5.0
    * Mail Server: Postfix
    * DNS Server: BIND9
    * FTP Server: proftpd
    * POP3/IMAP: I will use Maildir format and therefore install Courier-POP3/Courier-IMAP.
    * Webalizer for web site statistics

it will not, however, help you migrate from your current WAMP to LAMP.

---

### Post by uncleclinto on 2006-07-11
Okay, You made your point.  This guy is frustrated, as I too am becoming.  All you can say is, "Questions, questions, questions. But no patience for answers. Why? Relax... approach things step by step. Ask and you shall be answered."  Yet, you don't answer his most salient questions.  All he wants to do (like myself) is go from server installation to a working networked server with files hosted for the world wide web.  Is that so hard?  

Okay, I buy your assertion that it is best to start with desktop linux, but let's be honest here.  I wouldn't even be here if it weren't for the fact that I run a web server.  It's very frustrating to jump on the Apache forums with a serious problem only to be told, "we can't help you because you are running WAMP on Windows instead of LAMP on Linux".  It's even more frustrating to come here and be told that I need to spend a couple of years cozying up to Desktop Linux before I can get my server up and running.  Come on!  Let's face it, flawed as y'all say it is, Windows is the standard platform for most of my development tools, such as Macromedia (Adobe is satan) Studio.  You couldn't pay me to give that up.  All I want to know about Linux is how to run a server.  The Desktop crap can wait until I'm old and bored.  

All I want is some straight forward solutions for adding files to a server and serving them up to the world, preferably acronym free ("I usually VNC the SSH to the BFE befor taking a BM on the CPU while RTFM").

---

### Post by uncleclinto on 2006-07-11
[QUOTE=FredSambo;1241951]

that tutorial will help you install and configure an ubuntu server with the following add-ons (LAMP):

    *  Web Server: Apache 2.0
    * Database Server: MySQL 5.0
    * Mail Server: Postfix
    * DNS Server: BIND9
    * FTP Server: proftpd
    * POP3/IMAP: I will use Maildir format and therefore install Courier-POP3/Courier-IMAP.
    * Webalizer for web site statistics

Does it have PHP???  I see Apache in that list... I see MySQL... I don't see PHP.  I need PHP installed and configured (something I don't want to do myself because it was a 3-day pain on Win2k) tso I can run Moodle.

---

### Post by FredSambo on 2006-07-11
> **uncleclinto said:**
> 

Does it have PHP???  I see Apache in that list... I see MySQL... I don't see PHP.  I need PHP installed and configured (something I don't want to do myself because it was a 3-day pain on Win2k) tso I can run Moodle.

no you have to add it.

```
sudo apt-get install php5-mysql phpmyadmin
```

i believe that will do it, but i am no expert.

[http://doc.gwos.org/index.php/PHP_Server](http://doc.gwos.org/index.php/PHP_Server)

---

### Post by FredSambo on 2006-07-11
it will probably still be a 3 day pain for you.  :p

---

### Post by harisund on 2006-07-11
> **uncleclinto said:**
> Okay, You made your point.  This guy is frustrated, as I too am becoming.  All you can say is, "Questions, questions, questions. But no patience for answers. Why? Relax... approach things step by step. Ask and you shall be answered."  Yet, you don't answer his most salient questions.  All he wants to do (like myself) is go from server installation to a working networked server with files hosted for the world wide web.  Is that so hard?  

Okay, I buy your assertion that it is best to start with desktop linux, but let's be honest here.  I wouldn't even be here if it weren't for the fact that I run a web server.  It's very frustrating to jump on the Apache forums with a serious problem only to be told, "we can't help you because you are running WAMP on Windows instead of LAMP on Linux".  It's even more frustrating to come here and be told that I need to spend a couple of years cozying up to Desktop Linux before I can get my server up and running.  Come on!  Let's face it, flawed as y'all say it is, Windows is the standard platform for most of my development tools, such as Macromedia (Adobe is satan) Studio.  You couldn't pay me to give that up.  All I want to know about Linux is how to run a server.  The Desktop crap can wait until I'm old and bored.  

All I want is some straight forward solutions for adding files to a server and serving them up to the world, preferably acronym free ("I usually VNC the SSH to the BFE befor taking a BM on the CPU while RTFM").

Excuse me, but I don't recollect anybody asking you to cozy up yourself with Desktop Linux. If all you wanted was to install a webserver and serve your webpage, all you had to do was ask that.

Fine, so here goes. 

First, you open up a terminal. Type in "sudo aptitude install apache2 php5"

This will install apache2, php5 (the base modules) and will configure apache2 to know that it has to parse a .php file. 

Among other things you will want to know are as follows: 

(.) By default apache2 starts running, and will continue to do so after a reboot. If you do not want apache2 to run every time you restart your machine execute "sudo update-rc.d -f apache2 remove" You will have to manually startup apache2 every time. 
-----
(.) To stop the server you should do "sudo invoke-rc.d apache2 stop" Replace stop with start if you want to start it again. 
-----
(.) Now if you have a book of apache or something, you will realize everything you need to configure apache2 are in a httpd.conf. No, not in Debian/Ubuntu. First, head over to /etc/apache2 directory in Ubuntu. 
-----
(.) The main configuration is in /etc/apache2/apache2.conf Here you can change the listening port, the user as whom it is run, the default page to serve and other such stuff. 
-----
(.) Then head over to /etc/apache2/sites-availables/default. If you have worked with apache2 this should be familiar. This is the file where you set your properties regarding virtual hosts, redirects etc. You also set the directory you want your apache2 to serve. By default, you will find it to be /var/www. You will find "/var/www/" in 2 different places. Modify both to be exactly the same, and restart apache. For example, you could change both to "/home/uncleclinto". Remember, there is a difference between setting 
both to "/home/uncleclinto" and "/home/uncleclinto/" (the trailing slash). Both have to be same. 
-----
(.) If you have worked with apache before, you will realize that there are certain modules you can enabled. Execute "sudo a2enmod" and you will be shown a list. Some good ones include 
--- rewrite : often used. Don't know myself what it does :)
--- userdir : Each user can have a public_html folder in their home directory, which can then be accessed using [http://localhost/~username](http://localhost/~username). Of course, substitute localhost with a DNS name or IP address and username as approrpriate. 
-----
(.) If you messed up your configuration, do "sudo aptitude reinstall apache2-common". This will reset the /etc/apache2 directory itself. 
-----
(.) Now head over to your browser and open [http://localhost](http://localhost) and you should see the apache serving. Yes, by default you will be shown a directory, which is because that directory doesn't have a index.html or index.php page. 

>  All I want to know about Linux is how to run a server
There you have it. What's your complaint?

You must realize, there's a big difference between asking "how do I install a web server after a server installation of Ubuntu" and asking "wtf? I installed server and now I don't have a GUI? no webserver? yadda yadda yadda blah blah blah blah *curse* *curse* *curse*" . The tone of the original post was what upset me and led me to write the lengthy post in reply. 

Ok, God help you if you take this knowledge, head over to some other OS forum and start complaining "wtf, I did apt-get and it says "command not found". Useless linux, can't even install apache even after getting a big howto on another forum" so on and so forth .. people aren't going to be very kind :) 

Seriously, do read [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html) for more information.

PS: I just happened to realize moodle is in the repos. But it is very likely that you will have to enable some more repositories and also most likely it will not be the version you want. So I am going to take the liberty to not give you that information for fear of losing someone's interest in Linux.

---

### Post by LordHunter317 on 2006-07-11
> **harisund said:**
> (.) By default apache2 starts running, and will continue to do so after a reboot. If you do not want apache2 to run every time you restart your machine execute "sudo update-rc.d -f apache2 remove" You will have to manually startup apache2 every time.update-rc.d isn't mean to be run by end-users.  Doing this will mean the symlinks will be recreated on upgrades.  Do:```
sudo rm /etc/rc2.d/*apache2
```instead.

> (.) The main configuration is in /etc/apache2/apache2.conf Here you can change the listening port, the user as whom it is run, the default page to serve and other such stuff. No, listening ports are in /etc/apache2/ports.conf and should stay there.  You should alter the shipped configuriation and put your NameVirtualHost directives there too, if you are doing name-based virtual hosting.  The default directive is in sites-enabled/000-default, where it certainly does not belong.

> (.) Then head over to /etc/apache2/sites-availables/default. If you have worked with apache2 this should be familiar. This is the file where you set your properties regarding virtual hosts, redirects etc. You also set the directory you want your apache2 to serve. By default, you will find it to be /var/www. You will find "/var/www/" in 2 different places. Modify both to be exactly the same, and restart apache. For example, you could change both to "/home/uncleclinto". Remember, there is a difference between setting 
both to "/home/uncleclinto" and "/home/uncleclinto/" (the trailing slash). Both have to be same. One probably should not modify the default DocumentRoot unless they know exactly what they are doing or the ramifications of doing so.

> (.) If you messed up your configuration, do "sudo aptitude reinstall apache2-common". This will reset the /etc/apache2 directory itself. No, it will not, because they are conffiles.  You still have to manually tell it to plow everything, or delete them for recreation.

This is part of the issue that is legtimate from the OP's complaint.  The amount of bad information out there is simply overwhelming.

---

### Post by harisund on 2006-07-11
> **LordHunter317 said:**
> update-rc.d isn't mean to be run by end-users.  Doing this will mean the symlinks will be recreated on upgrades.  Do:```
sudo rm /etc/rc2.d/*apache2
```instead.
Actually, that will only remove apache2 symbolic links from the rc2 directory, which is only for run level 2. If you want to remove it, I would suggest you remove it from all run levels and not just run level 2. 

> 
The default directive is in sites-enabled/000-default, where it certainly does not belong.

I don't know if you noticed, but sites-enabled/000-default is merely a symlink back to sites-available/default (which is what I mentioned)

> 
One probably should not modify the default DocumentRoot unless they know exactly what they are doing or the ramifications of doing so.

I am assuming of course the person has worked with apache2 and "knows exactly what they are doing"

> 
No, it will not, because they are conffiles.  You still have to manually tell it to plow everything, or delete them for recreation.

Yes, you are right. Of course, I did assume that the user would delete the entire directory in order to start from scratch. My apologies, I must have mentioned it. Oh, and "recreation" That was funny when I read it first :)

> 
This is part of the issue that is legtimate from the OP's complaint.  The amount of bad information out there is simply overwhelming.

The nature of open source is such that any bad information is always caught. "Given enough eyeballs, and all bugs are shallow" (Eric. Raymond) See, hardly had I finished typing the post, and immediately someone jumped out to point out the mistakes, which I could then rectify. 

Yes, it happens all the time. If somebody makes a wrong post (I have been both on the posting end and the recepient end.) it more or less immediately gets corrected. If you write an article incorrectly you will eventually receive tons of comments. If you make a wrong forum post pretty soon somebody will correct you. I dare you to try and make a statement of "bad information" in an IRC channel ;)

The problem stems from the fact that because of the whole "choice" thing, there happen to be a lot of ways to do the same thing, even if only dealing with the command line. Someone gets accustomed to one way, and when someone mentions something else they tend to disagree. We then need, invariably, a third person to come in and say "they are both the same" :)

---

### Post by LordHunter317 on 2006-07-11
> **harisund said:**
> Actually, that will only remove apache2 symbolic links from the rc2 directory, which is only for run level 2. If you want to remove it, I would suggest you remove it from all run levels and not just run level 2.And the problem with that is (just like update-rc.d, because it is what update-rc.d does) is that the symlinks will be recreated on upgrade.  You must keep at least one symlink around on runlevel to stop that behavior.

It's a flaw in Debian's (and hence, Ubuntu's) initscript policy, which is basically nonexistent. 

> I don't know if you noticed, but sites-enabled/000-default is merely a symlink back to sites-available/default (which is what I mentioned)And? I realize they're the same file, but my point is there is a directive in there that doesn't belong, and is best moved.

> I am assuming of course the person has worked with apache2 and "knows exactly what they are doing"Which is incorrect for a guide aimed at new Linux users.  It's best, especially with highly configurable software like Apache, to cover the minimum details necessary.

---

### Post by harisund on 2006-07-12
Ok whatever. Sorry. 

Are you happy now?

---

### Post by RShadow on 2006-07-12
Well I actually found Linux easier to learn than Windows.  Yes I had to learn both of them, I didn't magically wake up one day with the knowledge of running and administring Windows, I had to learn it, and believe me it was a real pain. What I learned in Linux ten years ago pretty much applies today.  However what I learned in Windows 3.x all went out the window when Windows 95 was released.

The point is you have to learn Linux.  Linux is not Windows, they don't operate the same.  There is no magical Windows => Linux translation book.  Nobody can tell you how to run "Linux."  You have to learn it.

Honestly I can say that you didn't do very much research before posting.. I'll demonstrate

Upon searching google for "mp3 support in Ubuntu" I'm returned with this
```

How to add MP3 support to your Linux Distribution?
Most Linux distributions made the choice not to include MP3 support by default, for instance: Ubuntu, SUSE, Fedora, Debian...etc. ...
linuxmint.com/content/view/200/51/ - 50k - Cached - Similar pages

    [PDF] How to add MP3 support to your Linux Distribution?
    File Format: PDF/Adobe Acrobat - View as HTML
    Add MP3 support in Ubuntu 6.06 - Dapper DrakeIn Ubuntu 6.06, make sure you. added the Universe and Multiverse repositories and install the package ...
    linuxmint.com/index2.php?option=com_content&do_pdf=1&id=200 - Similar pages

```

That is the first item returned.  Upon clicking on that page it not only described to me why there is no MP3 support "out of the box" but also how to enable it.

Edit: however, unlike windows which acts as a desktop and server, Linux is typicaly setup and one or the other (its more secure and easier to administer)... so there is little need for MP3 support on a server box.

---

### Post by harisund on 2006-07-12
I completely agree with you RShadow :) way to go ...

---

### Post by uncleclinto on 2006-07-12
[QUOTE=harisund;1242409]Excuse me, but I don't recollect anybody asking you to cozy up yourself with Desktop Linux. 

Sorry.  The general gist I got from the posts was that it would be a lot easier to begin with the desktop version.  It probably is.  I just wanted to start with a server.  I didn't mean to back up the use of negativity either.  I just understand the frustration of not knowing exactly how to proceed.  

I will check out the resources you posted.  Thank you.

My biggest concern is, I've never used a command prompt before... ever.  I came into computing after the DOS years were over.  The only time I've used a language based interface was to send mail through VAXA at college and restore my registry through DOS.  I have a WAMP server, but I set it all up graphically through win2k.  When I want to update my site, I drag the files i want into it through a network connecting with pretty pictures of folders.  

Will it do me any good at all to apt-get or aptitude install ubuntu desktop (my syntax probably isn't right but you know what I mean)on my LAMP server?

---

### Post by uncleclinto on 2006-07-12
Could I install ubuntu desktop then install "apache2 php5-mysql libapache2-mod-php5 mysql-server"?  Would that be any benefit??

---

### Post by harisund on 2006-07-12
Whatever I am going to say, it is likely LordHunter317 will say I am wrong, but here goes. 

Yes, you could do "sudo apt-get install ubuntu-desktop" on your terminal. After waiting while it downloads and while it installs it all, you can either reboot your computer, or do "sudo invoke-rc.d gdm start" and get a graphical login. 

Once there, you will see a familiar desktop screen, icons and all that. 

Then once again you can open your terminal from the applications menu and do "sudo apt-get install apache2 ... " and all that you have typed. 

You can still drag and drop. Open an explorer (go to places->home folder) and hit Ctrl+L. This will ask you for a location. Enter in /var/www. Here you can drag and drop whatever you want and everything can be seen from the browser using [http://localhost](http://localhost)

---

### Post by FredSambo on 2006-07-12
good advice.

i must say though, there are a number of command line tutorials out there, and most of them will get you on your feet, and the knowledge is priceless.  

the big plus to learning how to use the terminal is being able to SSH (through putty or whatever) to a server that isn't equiped with a GUI (or monitor, keyboard and mouse) on your network. 

in my case it is a nice way to access my linux servers from a windows workstation, since my users prefer windows because it is what they have at home.

it also helps to learn vi (vim) as well.

but i guess the keyword here is learn.  it takes some time.  for me it was many a late night.  :p

---

### Post by FredSambo on 2006-07-12
...and for the record, i started out with windows and am still an MCSA.

---

### Post by LordHunter317 on 2006-07-12
> **harisund said:**
> Ok whatever. Sorry. 

Are you happy now?No, I'd be happy if you weren't being a childish prick about the fact you made technical errors.

I'm only going to correct you if you make a mistake.  You can either brush it off and let it go, since it's not's a big deal, or you can act like this.  The choice is yours.

---

### Post by uncleclinto on 2006-07-13
> **harisund said:**
> You can still drag and drop. Open an explorer (go to places->home folder) and hit Ctrl+L. This will ask you for a location. Enter in /var/www. Here you can drag and drop whatever you want and everything can be seen from the browser using [http://localhost](http://localhost)

Awesome!  :D  I'll give that a try.

---

### Post by Lil_Eagle on 2006-07-13
Do you notice all the answers to the original post and no reply for the originator of this thread?  I doubt if he'll be back.  Perhaps he'll do some reading and revisit.

I love the howto on howtoforge.  ispConfig is a very handy program, and with that howto, it actually compiles!

Now if I couldl just get my router working properly, my server would be seen by the rest of the world, but alas, port forwarding isn't working properly and port 80 is still not being forwarded.  Neither is 443.  Oh well.  I've only got 4 more days of this ISP anyway, then I get a new one.  Perhaps I'll change the router in the meantime.

Linux is not hard to learn.  Linux is just different (and more logical) than windows.  There is nothing better in the world than learning something new, and with Linux one can learn something new every day for several years!  The ability to actually know what your computer is doing, and not having anyone force you to use this or that software is what freedom is.  The computer world needs to be free.

---

### Post by Lil_Eagle on 2006-07-13
Oh, another thing, as for dragging and dropping, instead of using ssh in a terminal to connect to the server, just open konquer and fish:// the server.  

For me it's fish://10.0.0.10 and it prompts for username and password.

---

### Post by Sajji on 2006-07-13
Getting back to the original topic, if I may.

I've been "tinkering" with Linux close to 5 years now and I have to admit, it's hard.  Ubuntu desktop is the best I've ever seen.  Ubuntu server, however just installs the core product and leaves you at the prompt.  

One of the reasons why NT 4 Server and Windows 2000 Server killed Novell was because uncle Gates had this bright idea of making the server software with the same GUI as the clients.  How smart was that!  Anybody remember Novell?  Crappy GUI.  80% of learning Novell was just navigating through their interface.  Along comes NT 4 Server and guess what...it looks just like NT 4 Workstation.  You don't have to learn how to create folders, drag and drop files.  You have a control panel, etc.  Everything looks and feels just like the workstation.  That makes life so much easier because then you can focus on server related tasks, not trying to figure out new ways of navigating.

I think what a lot of Linux people don't get is: why don't newbies just ask for help?  The Linux community is very responsive - true.  But why should I have to ask for help?  Linux has been around long enough to be a bit more streamlined.

I think Ubuntu is well on the way becoming another Red Hat and SuSe.  But I do think it's pretty crappy to not include a GUI with the server.  After all, if I wanted a text based server, I can get that from any of a 100 distributions of Linux.  I went to Ubuntu because of its ease-of-use.  

A bit disappointed, but I'll get over it.

:)

Sajji

---

### Post by bluenova on 2006-07-14
Hi Sajji,

You certainly have a point there. Personaly I wouldn't use Ubuntu to run any kind of server, to me it is a desktop O/S. I would choose something like CentOS. So I think if Ubuntu are to continue down the server path, that a simple GUI with GUI server tools would be a nice touch.

---

### Post by andb on 2006-07-14
A thread should be started on learning resources...

The best place to start, imho is:
[http://learnlinux.tsf.org.za/](http://learnlinux.tsf.org.za/)

Great online courses, and interestingly, sponsored by the suttleworth foundation... Make sure you check out the MOODLE area for resources, tests, etc. Beginning with these "courses" you'll have the foundation to improve. Start with a workstation, the concepts are the same for the underpinnings. And keep asking lots of questions.

---

### Post by RShadow on 2006-07-14
Not to drag this out any further, but why would a ** server ** installation contain a GUI?  Really?  Perhaps it might be nice if you are setting up a home server or by some chance you have billions of dollars to operate a data center, but most Linux server installations are done remotely.  There isn't a point in a GUI... unless you want to vlc into your box, but then you must have lots of $$$ to pay for all that bw.  Not to mention installing X means one more application to you have to patch and monitor, one more port you firewall has to worry about, and one more door for an attacker to gain entrance into your box... I dunno.. doesn't make sense to me.

---

### Post by FredSambo on 2006-07-14
i am extremely happy with ubuntu server just the way it is, i can't express how happy i am.  

it is also pretty easy to install the desktop version of ubuntu and then install the server components.

---

### Post by va3uxb on 2006-07-14
I really like the Dapper server installation. I'd run our servers at work on Dapper but we have some 3rd party proprietary stuff that forces us to use RHEL.  So I use Dapper at home for my server there.  The GUI is meaningless to me, my server is headless and I never see it, it's on a shelf in a closet.  I really liked that the clean server installation plunked me at a command line and there was no extra fluff installed.  

I'll admit that Ubuntu was a big switch for me at first.  I've used Red Hat since 1998... version 4, 5, 6, 7, then finaly RHEL 3.  Switching to Ubuntu (breezy at the time) left me feeling like I had to learn some stuff all over again.  However, it only took a week or so, and when I wiped it clean and did a fresh Dapper install last month, it was a breeze (pun intended).  

Recently I found the new documentation here:
[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

That is great stuff, I can't see anyone having too much problem if they have access to that.  

I still have some problems, like when I want to install something but don't know the correct package name that still throws me for a loop.

As for linux being hard to learn...I think it is only as hard as people make it.  If folks have either a strong desire or a pressing need, they'll learn it.  No different than anything else.

-Stephanie

---

### Post by stevewburke on 2006-07-14
Thank you all for your assistance. I had no idea the Linux community was this good about assisting others. I guess my main point was that I thought the basic concepts of Linux should be easy for a computer guy to learn. But the reality is that Linux is very different from Windows and takes more than a couple days to learn. You just have to 1) be patient, 2) learn to forget MS logic, and 3) learn the "Linux" way of getting help from the community.
-Steve

---

### Post by PanzerMKZ on 2006-07-14
I am good windows person too.  Then I popped in that ubuntu server install cd.  Here I know the basics.  I know what I want to do.  I just have to learn how to do it.  It is fun learning something new.  SMP kernels and pure CLI.  windows box I have to have a mouse.  Here I don't even need anything for I can just ssh into the box from another.  Here is a OS that allows me to have what I want.  I don't need a media player or games on a server.  Plus I don't want to think how m$'s latest and greatest would run on a dual 500 cel with a great 400meg of ram.  Ubuntu server runs great.  Oh yea the buy in price is great too.  Just the time that it is going to take me to learn.  And there is another avenue of help that I can go to other then the forums here or even the net.  I have a LUG here.  Meets once a week.  I might not end with ubuntu but that is where I started.  Thanks everyone.


Panzer

---

### Post by stevewburke on 2006-07-15
Here is exactly what I was looking for:

[http://wiki.linuxquestions.org/wiki/How_does_Linux_differ_from_Microsoft_Windows](http://wiki.linuxquestions.org/wiki/How_does_Linux_differ_from_Microsoft_Windows)
[http://wiki.linuxquestions.org/wiki/Common_Questions_and_Misconceptions](http://wiki.linuxquestions.org/wiki/Common_Questions_and_Misconceptions)

Hope it helps someone else as well.

-Steve

---

### Post by im_danny on 2006-07-17
First i'd like to say little-girls like harisund  
is the reason learning this stuff is so hard, you have A TON of pompass losers to full of there own greatness to be bothered to do anything but reply with vauge smartass replys.. go suck a Richard , because you must be a B1tch!.. now to the real stuff

I agree its really hard to learn this stuff, I think the whole move to linux would be smoother if some one posted really basic stuff..commands.. example.. First.. I AM JUST LIKE HIM.. Very windows savy.. what do you need ..let me show you ten different ways to do it type, same again with the server.. I have my own server and website, boon-dog.. check it out I'll shamelessly plug it ;) and I also control my own server.. I have VERY limited command time in puddy .. but am prUdy sim-art..Kidding Im not a dummy.. I also have read up on installing the server, I can get ..using the perfect setup.. to editing the file..  look


4 Install The SSH Server
Ubuntu does not install OpenSSH by default, therefore we do it now. Run

apt-get install ssh openssh-server

You will be prompted to insert the installation CD again.


5 Configure The Network
Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address. Edit /etc/network/interfaces and adjust it to your needs (in this example setup I will use the IP address 192.168.0.100): 

vi /etc/network/interfaces

# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).# The loopback network interfaceauto loiface lo inet loopback# The primary network interfaceauto eth0iface eth0 inet static        address 192.168.0.100        netmask 255.255.255.0        network 192.168.0.0        broadcast 192.168.0.255        gateway 192.168.0.1 

Then restart your network: 

/etc/init.d/networking restart 

Then edit /etc/hosts. Make it look like this:

vi /etc/hosts

... Umm quick question that would solve most of my troubles.. HOW?? once you type vi /etc/network/interfaces, your poped into another mode .. how the hell do ya edit that stuff? I actually figured out the insert replace to change stuff thats there.. hey here is the magic question.. how do you save and exit so you can run the next deal??? the whole.. Then restart your network:...LOL.. call me idiotboy.. just give me the answer.. hey I have spent hours trying to figure that out.. I think its a you have to be in the secret club deal??/ and ZERO reference???
then of course the vauge answer stuff like our friend harisund.. look so far this is the best forum I have found that even comes close to answering stuff.. any help my way would be great..:-k 
Thanks
Danny Williams
Boon-Dog.com

---

### Post by tgoose on 2006-07-18
I honestly don't understand how it could be thought that people don't go out of their way to help with getting Linux. A couple of days ago, from having literally never set up any kind of sever before (well, other than GNUmp3d, but that works pretty much OOTB on Linux and with a little tweaking on win32) on any platform, never having dealt without any GUI, to Ubuntu Server, selected "install LAMP server" and now I have web, FTP (in the process of setting up; I may have to switch from proFTPd!), GNUmp3d, a DC hub, and a remotely controlled bittornado (bitspider). And, basically everything I know comes from these forums (or, from somewhere someone on these forums told me to find..!)

---

### Post by tgoose on 2006-07-18
> **im_danny said:**
> 
vi /etc/hosts

... Umm quick question that would solve most of my troubles.. HOW?? once you type vi /etc/network/interfaces, your poped into another mode .. how the hell do ya edit that stuff? I actually figured out the insert replace to change stuff thats there.. hey here is the magic question.. how do you save and exit so you can run the next deal???
If it says Insert or Replace at the bottom, press Escape, then type "save! /etc/network/interfaces" (you need the ! if you're overwriting a file). For those who haven't yet worked out the insert/replace thing, you need to press Insert to start editing the file.
[/quote]

> 
the whole.. Then restart your network:...LOL.. call me idiotboy.. just give me the answer.. hey I have spent hours trying to figure that out.. I think its a you have to be in the secret club deal??/ and ZERO reference???

```
ifdown eth0
ifup eth0

```, probably.

---

### Post by im_danny on 2006-07-18
well other then the nasty letter from mike telling me harisund was not a happy camper.. I think I'm good to go!

well that should help a bit .. 
you rock tgoose.. thanks tons

---

### Post by matthew on 2006-07-18
Okay, there's way too much grumpiness in this thread. I PM'd one user because of it and received one of the most abusive replies ever. (He's on his way to a ban). Anyway, I don't see any reason for this thread to continue. Let's try again with a new thread and a better atmosphere if the question remains unresolved.

---

