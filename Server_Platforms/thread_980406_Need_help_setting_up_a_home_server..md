---
title: "Need help setting up a home server."
date: 2008-11-12
forum: Server Platforms
---

### Post by Suilenroc on 2008-11-12
Hey all. So, I recently got a hold of a great old computer. Hell, it's not even that old. It's got a p4 2.4ghz with a GeForce 7800GT and 2 gigs of DDR RAM. Overkill for a home server.

So I decided to set up a home server. But then, I found out...I have no idea where to start. After looking at tutorial after tutorial, none of them for me, I have come here to seek your advice. 

I want a home server able to do this: Receive and send e-mails. (So e-mail server), hold files for all of the computers in my household, wireless, of course. Stream music over an internet connection to a mobile platform. Allow remote access from any other internet-enabled computer. And anything else, really.

Right now, I don't have any storage other than a 4gb USB stick. I've been installing linux on it, and it works fine for testing purposes, although it obviously can't hold much information. 

So, can you guys help? I honestly don't know where to start. 

Thanks in advance! -Suilenroc

---

### Post by hictio on 2008-11-12
I see a problem with the email bit, what type of internet connection do you have?
Unless you have a domain, fixed IP, and the ISP will be able to provide you with a PTR record for your IP, you might end with a lot email bounced due to anti SPAM rules & RBL DNS lists.

---

### Post by Suilenroc on 2008-11-12
Well, if that's the case, I don't mind. I have a relatively standard 10mbps connection through roadrunner/time warner cable. I assumed that I would be able to fix the fixedIP problem by getting a dyndns address. Either way, this is more an excersize in knowledge than anything else. In the long term, I'd like to have a server for my home, in particular. Music streaming/storage, et cetera.

---

### Post by oneloveamaru on 2008-11-12
I would start with a hard drive first. Install Ubuntu Server and then figure out what software you want to run what with. Email, you have tons of options. I take the super easy route and use the Zimbra open source community builds. It's free and has a great admin interface. It's a resource hog though. My co-lo server handles it fine.

As hictio pointed out, if you have a dynamic IP, it's going to make it a little bit more complex for email but not impossible. Get a router with DDNS and go from there. DDNS meaning Dynamic DNS. It will go out and update your domain records with the new IP address. I myself just use a dynamic IP with business road runner. Easier and don't have to change anything.

---

### Post by oneloveamaru on 2008-11-12
Oh and for storage, use SAMBA of course. I'm sure everyone is on Windows. Just find out their username and password they use to log into their machine now and create a SAMBA account for them and shares. THere should be lots of information on SAMBA config.

---

### Post by Suilenroc on 2008-11-12
That sounds easy enough. I'm on Linux, myself. Ubuntu 8.10 Intrepid. Would the interface be significantly different?

And how could I access it remotely? FTP?

---

### Post by Thirtysixway on 2008-11-12
Server has no GUI but you could get something like webmin

---

### Post by hictio on 2008-11-12
Or SSH, for a command line family oriented environment :D
You'll love it and won't want to touch a mouse after, promise.

---

### Post by Suilenroc on 2008-11-12
I like the sound of SSH. Do you have a tutorial for that that I could take a look at?

---

### Post by hictio on 2008-11-12
Actually SSH is just the transport, you use SSH to connect to your server, is like telnet, but encrypted (and more powerfull)
The important thing about SSH is to secure it, don't open it to the internet, use strong passwords or public key auth, and if you must, because you really must open SSH access to the internet, use something like fail2ban to block brute force attacks and script kiddies.

---

### Post by oneloveamaru on 2008-11-12
Wow bro, you are really starting from scratch. You CAN get a gui for ubuntu server, but stay away from it. Once you know command line, you will understand why no one uses the GUI on a server. SAMBA is reversed engeneered version of Windows File Sharing. Once your SAMBA server is up and running, users can just go to it like a regular share, or even map a drive to it in My Computer. I would start with one thing at a time. Google is your friend, start with Zimbra or SAMBA. Search setting up SAMBA on Debian or Ubuntu, they are the same. Once you get that working, go to the next thing you want to set up. Don't overwhelm yourself with 5 tasks at once.

---

### Post by Suilenroc on 2008-11-12
> **hictio said:**
> Actually SSH is just the transport, you use SSH to connect to your server, is like telnet, but encrypted (and more powerfull)
The important thing about SSH is to secure it, don't open it to the internet, use strong passwords or public key auth, and if you must, because you really must open SSH access to the internet, use something like fail2ban to block brute force attacks and script kiddies.
Hehe. Well, I don't mean to be dense, or too noobish, but...I didn't get half of what you just said. I can compile gentoo nearly without the guide anymore, but when you start talking encryption or the like, I'm lost.

---

### Post by Suilenroc on 2008-11-12
> **oneloveamaru said:**
> Wow bro, you are really starting from scratch. You CAN get a gui for ubuntu server, but stay away from it. Once you know command line, you will understand why no one uses the GUI on a server. SAMBA is reversed engeneered version of Windows File Sharing. Once your SAMBA server is up and running, users can just go to it like a regular share, or even map a drive to it in My Computer. I would start with one thing at a time. Google is your friend, start with Zimbra or SAMBA. Search setting up SAMBA on Debian or Ubuntu, they are the same. Once you get that working, go to the next thing you want to set up. Don't overwhelm yourself with 5 tasks at once.
Yeah, I sure am. And I don't want a GUI for the server, I want it to be headless. (I think that's the term.) I wanna be able to, after I perform the initial installation, do everything I need from this other computer, the one that I'm typing on right now.

---

### Post by Thirtysixway on 2008-11-12
If you're going to be opening up ftp and ssh to the internet, I'd suggest changing the default ports.  This will stop 99% of brute-forcers running automated scripts to scan port 21/22.

---

### Post by oneloveamaru on 2008-11-12
I'm not talking about encryption, no need for that on anything you are running.

Set up an ubuntu server with the expectation of formatting and re-building it multiple times. When you get a good config file that works down, make a backup to your thrumb drive. Like I said, you can catch me on AIM when you have questions. I remember being a n00b back in the day. I also have MSN, Yahoo and Google Talk, in case you don't have AIM. Shoot that to me in an private msg or something.

---

### Post by Suilenroc on 2008-11-12
Awesome, thanks. Concretely, the first thing that I don't understand how to do is set up the headless server in the first place. From my limited understanding, I've gathered this:

1) Install Ubuntu server edition. 
2) Install an SSH program.
3) Install SSH client on the administrative machine, or any other machine that I need to access it on.
4) SSH into the computer, I assume via IP Adress, Username, and Password.

Will that get me access to a command line for the server without actually having that server connected to the monitor?

---

### Post by hictio on 2008-11-12
Indeed it will :D
On the Ubuntu Server, to have to start the SSH service, you'll need an SSH client, like PuTTY, if you are going to login from Windows.
Needless to say, you are going to need a monitor, and keyboard, to make the Ubuntu Server install, after that, and you are confident, you can run headless.
Be sure to see the BIOS of your new baby so it can boot w/o a keyboard.

---

### Post by oneloveamaru on 2008-11-12
SSH server installed by default, so no need to install it. You will need a monitor to run the install but once it's done, you can ssh in as the user you created and password.

Is your client running Ubuntu or another variant of LInux? If you have Windows, download Putty, that will allow you to SSH in from windows.

Once you are in, if you want to do anything, you need to do "sudo" before all commands or do a "sudo su" to become root, which some people might frown upon. Personally, I just enable the root account and log in directly as root.

Once you are in via SSH, you will be at a prompt just like a Dos command prompt. Just different commands. :)

You might want to buy a book about Linux or Ubuntu and start reading. While reading, try the commands out. 

Or go here [http://cbt.googletoad.com/?videoQ=linux+](http://cbt.googletoad.com/?videoQ=linux+) start watching the first video that's on the 2nd page. Whoever uploaded them didn't put a 0 before the 1-9, so 1-9 are last. The videos are on red hat but it's the same commands. You should learn a lot from watching those. That should give you a good head start.

---

### Post by Suilenroc on 2008-11-12
Awesome ,thanks. I'm downloading the server install CD now. I'll let you know how it goes.

---

### Post by Suilenroc on 2008-11-12
> **oneloveamaru said:**
> SSH server installed by default, so no need to install it. You will need a monitor to run the install but once it's done, you can ssh in as the user you created and password.

Is your client running Ubuntu or another variant of LInux? If you have Windows, download Putty, that will allow you to SSH in from windows.

Once you are in, if you want to do anything, you need to do "sudo" before all commands or do a "sudo su" to become root, which some people might frown upon. Personally, I just enable the root account and log in directly as root.

Once you are in via SSH, you will be at a prompt just like a Dos command prompt. Just different commands. :)

You might want to buy a book about Linux or Ubuntu and start reading. While reading, try the commands out. 

Or go here [http://cbt.googletoad.com/?videoQ=linux+](http://cbt.googletoad.com/?videoQ=linux+) start watching the first video that's on the 2nd page. Whoever uploaded them didn't put a 0 before the 1-9, so 1-9 are last. The videos are on red hat but it's the same commands. You should learn a lot from watching those. That should give you a good head start.

Oh, don't you worry about those basics, I'm not a LINUX newbie, just a SERVER newbie. Like I said earlier, I've successfully compiled Gentoo multiple times on multiple systems. While not SUPER complicated, I can sudo su like there's no tomorrow. :)

---

### Post by Suilenroc on 2008-11-13
Woo! Got it set up. I couldn't get Ubunt Server to boot off of the the USB stick, so I went with something that I knew would work: Arch Linux. Worked out just fine, got the SSH server set up and connected. I'm now connected through secure shell to root@myhost, currently running Pacman -Syu (or, for the less arch-y among us, world upgrade.) 

So, what now? What is the next step towards getting this thing mounted in Linux and Windows systems, holding/streaming files, et cetera. 

Also, security. How? >.>

---

### Post by hictio on 2008-11-13
The first step are:
- add a regular user account (if you haven't already)
- make sure that account can become root, not sure if arch has a wheel group limitation.
- add that non root user to the sudoers file (/etc/sudoers)
- don't use the root account any more, period
- disable root logins over ssh (/etc/ssh/sshd_config file, PermitRootLogin directive)
- enable only the users you trust/ need to login over ssh (the same file above, AllowUsers directive )
- install all the updates to your system
- start playing with the firewall/ iptables, (keep the keyboard and monitor handy, in case you lock yourself out of your box thru the LAN :)
Or create a cronjob that will clear the rules while you make your tests/ setup)
- do what ever you want to do with the server :)

Here is a bunch to get started.

---

### Post by Suilenroc on 2008-11-13
> **hictio said:**
> The first step are:
- add a regular user account (if you haven't already)
- make sure that account can become root, not sure if arch has a wheel group limitation.
- add that non root user to the sudoers file (/etc/sudoers)
- don't use the root account any more, period
- disable root logins over ssh (/etc/ssh/sshd_config file, PermitRootLogin directive)
- enable only the users you trust/ need to login over ssh (the same file above, AllowUsers directive )
- install all the updates to your system
- start playing with the firewall/ iptables, (keep the keyboard and monitor handy, in case you lock yourself out of your box thru the LAN :)
Or create a cronjob that will clear the rules while you make your tests/ setup)
- do what ever you want to do with the server :)

Here is a bunch to get started.

Thanks man, I'll get started on all of this stuff. And I made sure to install the Sudo package when I set up Arch this time around, I'll edit it to include my user in the sudo group. I have to relearn vi every time I do this...nano ftw.

---

### Post by hictio on 2008-11-13
> **Suilenroc said:**
> Thanks man, I'll get started on all of this stuff. And I made sure to install the Sudo package when I set up Arch this time around, I'll edit it to include my user in the sudo group. I have to relearn vi every time I do this...nano ftw.

How can I forget it!!
The first one has to be:

- install emacs

( Let zhe flamez vegins :p ;) )

---

### Post by Suilenroc on 2008-11-13
> **hictio said:**
> How can I forget it!!
The first one has to be:

- install emacs

( Let zhe flamez vegins :p ;) )

oh boy. What's emacs?

---

### Post by hictio on 2008-11-13
> **Suilenroc said:**
> oh boy. What's emacs?

I was just kidding, [emacs](http://en.wikipedia.org/wiki/Emacs) is a text editor.
See the [editor wars](http://en.wikipedia.org/wiki/Editor_wars) :D

---

### Post by Suilenroc on 2008-11-13
> **hictio said:**
> I was just kidding, [emacs](http://en.wikipedia.org/wiki/Emacs) is a text editor.
See the [editor wars](http://en.wikipedia.org/wiki/Editor_wars) :D

Ahh, gotcha, gotcha.

Well, quick update. I installed Samba, and restarted the computer just for kicks. Now, I can't connect via SSH. I know it's something simple, I just gotta find it. I'll figure it out tomorrow, and I'll keep this thread updated so that anyone else in my position can follow in my footsteps. Thanks for the help, and probably see you all tomorrow.

---

### Post by hictio on 2008-11-13
> **Suilenroc said:**
> Ahh, gotcha, gotcha.

Well, quick update. I installed Samba, and restarted the computer just for kicks. Now, I can't connect via SSH. I know it's something simple, I just gotta find it.

Is is set to start the service automagically at boot, right?
Then, if you edited the config file, check it for typos, perhaps, you can try starting the service manually and see if it has any complains.

---

### Post by Suilenroc on 2008-11-13
> **hictio said:**
> Is is set to start the service automagically at boot, right?
Then, if you edited the config file, check it for typos, perhaps, you can try starting the service manually and see if it has any complains.

I tried all those, no dice. There seems to be a problem in the initialization of ssh to being with. I type in 

```

/etc/init.d/ssh start

```

And it returns an error message, saying that ssh is not found. I tried to reinstall it, no avail. I tried ls /etc/init.d, to see if it has somehow been renamed, nada. I gotta go to sleep now, but I'll check it again in the morning if I have time. 

Thanks again for all the help, I'll definitely be returning to this thread later to continue the server setup.

---

### Post by Suilenroc on 2008-11-13
> **Suilenroc said:**
> I tried all those, no dice. There seems to be a problem in the initialization of ssh to being with. I type in 

```

/etc/init.d/ssh start

```

And it returns an error message, saying that ssh is not found. I tried to reinstall it, no avail. I tried ls /etc/init.d, to see if it has somehow been renamed, nada. I gotta go to sleep now, but I'll check it again in the morning if I have time. 

Thanks again for all the help, I'll definitely be returning to this thread later to continue the server setup.
Alrighty, I got my hands on a hard drive! It's an old one from school, just 15 gigabytes, but it's a start. I reinstalled Arch Linux (lighterweight and quicker than Ubuntu Server), and got SSH working again. My problem earlier was that I forgot that in Arch, it's not "/etc/init.d/ssh start," it's "/etc/rc.d/ssh start". rc.d replaces init.d. Other than that, it's not too different. 

So, I'll get some stuff started. Perhaps a dyn-dns to make an email server, I dunno. 

Hmm...*ponders what to do*

---

### Post by R.Bucky on 2008-11-14
I just have to throw in my 2 cents worth. In reference to your media server... I recently installed [Jinzora]("http://en.jinzora.com/") media server. It is phenominal versus my previous Gnump3d. It is a breeze to use and configure. Saying that, enjoy your new server...

---

### Post by Suilenroc on 2008-11-14
Okay, so I have a bit of a problem. I'm trying to connect to my server via SSH from a remote location, specifically, from my iPhone's 3g connection. I've made sure that ssh works on the phone, and that I am, indeed, connected to the internet, so just assume that the phone side of the equation is working. 

I've forwarded port 2222 (the port that I set ssh to run on) to my server (at 192.168.1.121, on the local network), and then try this on the phone/other computer:

```
 
ssh -p 2222 suilenroc@xx.xx.xxx.xxx

```
However, it says that no route to the host is able to be found. Anyone have any idea how to fix this?

---

### Post by Suilenroc on 2008-11-14
Alright, in a completely unrelated decision, I'm installing Ubuntu server instead of arch. Most of the tutorials that I found were for Ubuntu server, and I felt wierd asking for help on the ubuntu forums for arch linux.

---

### Post by Suilenroc on 2008-11-14
Annnddd the old HDD that I salvaged just died.

Joy. 

Well, I gotta secure another one now. *sigh*

---

### Post by hictio on 2008-11-14
Dude! That's too bad, that HDD (on its current encarnation at least) didn't even had time to learn how to walk :D

---

### Post by Suilenroc on 2008-11-15
Well, it was only 15GB anyways, so it was only for testing purposes. I'll get another one today, if it works out.

---

### Post by Suilenroc on 2008-11-15
Alllrighty, back in action. I got a new HDD, a nice 250GB IDE. Installed ubuntu forums, and SSH is working. Gonna start setting it up now, for real this time. 

So, here's what I'm planing, tell me what you guys think:

1) Install Apache, so that I can get the basic web hosting up.
2) Install an ftp server, and link it to all of my documents and music, et cetera. 
3) Install Jinzora, at the top of thsi page, and set it up, streaming my music whenver needed.

---

### Post by hictio on 2008-11-15
> **Suilenroc said:**
> 
1) Install Apache, so that I can get the basic web hosting up.
2) Install an ftp server, and link it to all of my documents and music, et cetera. 
3) Install Jinzora, at the top of thsi page, and set it up, streaming my music whenver needed.


It seems fine enough to start, Apache you can install it, among PHP + MySQL, upon the install.
One thing regarding point 2, what is your primary OS? Perhaps you can use a more convenient way of storing the data on the 150 GB HDD than FTP?

---

### Post by Suilenroc on 2008-11-15
I Use linux, but I want it to be accessable by the two windows vista machines in my house, and, eventually, via a secure connection from any machine over the internet. (I would send a Wake on Lan packet via internet, wait a few, then access it. After that, I would SSH into the machine and shut it down. That way, It's only open a few minutes, and I have access to any files anywhere.)

---

