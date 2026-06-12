---
title: "New things to learn"
date: 2014-07-02
forum: The Cafe
---

### Post by Tristan_Williams on 2014-07-02
I have been using Linux (mostly Xubuntu) for the past 2 1/2 years. I can efficiently install and new system and configure it to the same level as my regular-use desktop in less than a day. I'm getting to where I am bored with Linux. I haven't learned anything new in so long it's not interesting any more.

I looked on the RHCSA/RHCE website, at the learning objectives (things you need to know to pass the tests) but they are all so vague that I really don't any more of an idea than before I looked there. 

I've tried looking online for new things to learn but they are either really overly vague (learn to run more software), or they tell me things I already know, or they don't say anything at all (they just say "hey, you should learn more, but we won't tell you what to learn")



So here's what I know already:
[LIST]
[*]I can install and configure any Ubuntu-based distro
[*]I know what each part of the filesystem is for, and where to find files and directories when I need something specific such as the logs for apt-get
[*]I know how to manage users and groups with both CLI and GUI tools
[*]I know how to install and configure most software, even the complicated ones like Netflix(doesn't work without extra packages), the good version of Google Earth, Steam, PlayonLinux, Tor, etc...
[*]I know how to compile a kernel from source
[*]I know how to maintain system packages, and update/upgrade/install/remove them properly (both CLI and GUI)
[*]I know how to do web design
[*]I know bash scripting quite well
[/LIST]

Here's what I DON'T know, but I don't know where to look in order to learn
[LIST]
[*]SSH and VPN (The online tutorials assume I already know how to use them, and just dive into complicated crap that makes no sense at all)
[*]Managing a server, or any form of server-oriented software (Same thing as SSH, they think I already know)
[*]Anything else you can think of that wasn't mentioned above
[/LIST]



I just need specific suggestions on what to learn. 
I would love to know where a GOOD tutorial for SSH is at. I need one that assumes I DON'T know how to use it
I would love to find good tutorials on anything really. But most of them assume I already know the basics. None of them are teaching the basics



Just please suggest new things to learn, and GOOD tutorials on SSH

---

### Post by Metallion on 2014-07-03
SSH would be a good thing to learn. Using it is simple enough. Start up sshd on machine A. Type 'ssh <ip of A>' in the shell on machine B. Now if you want to do the really cool stuff I suggest you look into SSH tunnels and port forwarding, [http://chamibuddhika.wordpress.com/2012/03/21/ssh-tunnelling-explained/](http://chamibuddhika.wordpress.com/2012/03/21/ssh-tunnelling-explained/)

Also have you considered learning a programming language and contributing to some open source projects? That could keep you busy virtually forever. :)

Or if programming isn't your thing and you want to learn more about Linux' internals, try a more do-it-yourself distro like Arch or Gentoo.

---

### Post by sudodus on 2014-07-03
I suggest that you ***start a new thread*** asking for help to make an openSSH server. It is very useful in a local area network. You can run it in your main desktop computer unless you intend to access it from outside your router. Then it is better to use a dedicated server.

Is this link assuming that you already know how to use SSH?

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

You can start browsing the internet for ***SSH server tutorial*** or something similar, and ask in that thread, when you need help to continue. Or even start asking for a good basic tutorial.

---

### Post by nerdtron on 2014-07-03
SSH concept:
You use you own linux computer right? Then you also use the terminal on your computer right? Good.
Now say you are using another computer in your house, but you want to access the other computer's terminal? This is where SSH comes in. From a seperate computer, you login and access the terminal of the another (remote) computer.

The syntax for ssh is like this: ssh username@IPaddress
username is the account you use to login on remote computer
IPaddress is the IP address of the remote computer

Note: you should have installed the openssh-server package on the computer you want to access remotely.

---

### Post by coldraven on 2014-07-04
If you have an Android phone then install SSHDroid, the free version from the Play store.
Then install SSH on your computer ```
sudo apt-get install ssh
```
Run SSHdroid and then from a terminal ssh into the phone using the address that SSHDroid gives you. Or in Nautilus use "Connect to server".
The default user is "root", password "admin". 
Now you can see all the files in your phone and hack away to your hearts content. Or just copy over your cat photos :)
You can run SSHdroid in the background so any new photos or files will appear in your computer every time you reload Nautilus (Ctrl+R)
Note: This only works if your phone and your computer are both using your home router, either wifi or cabled.
Here endeth the lesson :)

---

### Post by linuxyogi on 2014-07-05
After you finish learning ssh try configuring apt-cache.

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

This will take minimize traffic on your home network if you have multiply PCs running Ubuntu.

---

### Post by slooksterpsv on 2014-07-08
There's so much to learn with Linux. If you have spare HDD, turn them into NAS storage. Learning NAS is always good. If you want something time-consuming and to really make you think, try configuring an LDAP server and Client, with LDAP Login Authentication with user home directory stored on a separate NFS server or on the server with an NFS share. That one's a thinker, can be done, not as easily as Fedora, but it can be done. Then use the LDAP, create a bunch of user objects and populate a contact db with it - Evolution works, Thunderbird I think will connect too.

Server's are so much fun. If you get it down to a science, make a script and upload it here =P. I have a tut floating around somewhere on here hmm... at least for the server, client was like what did I miss????

---

### Post by veddox on 2014-07-08
It's already cropped up, but I'd mention it again: set up an Arch distro on some old machine you have lying about. It shouldn't present you with too many difficulties at your level of experience, but it might be interesting to get outside the Ubuntu universe.

Here is a starter tutorial for Arch: [http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process](http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process)

---

### Post by bashiergui on 2014-07-08
If you're going for RedHat certifications then install CentOS, which is essentially the free version of RH. There is no better way to learn than to dive in and start installing stuff. You could use VirtualBox so that you don't screw up your computer. IMO the Ubuntu documentation is the best there is in regards to open source distros and users that are inexperienced. Maybe install ssh on ubuntu and then install ssh plus everything you know about in CentOS to discover the differences.

---

