---
title: "Securing system (new user)"
date: 2009-10-01
forum: Security
---

### Post by Accelerate- on 2009-10-01
Hello, first off I'd like to say sorry if this is in the wrong section (even though it's security related, it's fairly general questions)


So here's the little backstory. I just made the switch to Xubuntu (installed about a good 30 minutes ago), i chose it over Ubuntu and Kubuntu because this is an old laptop (Pentium 3 at 700mhz) As a former windows user, i was a security fiend, always using anti-virus scans, anti malwar scans you name it i would have them running almost 24/7, in doing so, i had virtually no performance, but a somewhat peace of mind that my computer was safe. Now i know Linux is a far more secure OS on its own, but as an OS connected to the internet, it's still fairly vulnerable. So i did my homework, to a general extent, and found that there a a few key things i need to do to secure my computer. Such as encryting my HD partition, setting up a firewall and IPtables (what is that?)

So i was wondering, how can i make sure that my laptop is secure as possible even though right now i have basically no knowledge of Linux code?

Thanks for your replies in advanced!
Vidya

---

### Post by running_rabbit07 on 2009-10-02
Welcome to Xubuntu! 

If you are used to your system being slowed by anti-virus, then you will love the speed you get now with Xubuntu.

If you plan to encrypt your hard drive which makes it more secure from physical theft, then that is great. The only way I know to do that is with the Alternate install ISO.

IP Tables is already implemented. If you would like to see what your firewall is doing and what connections are being made, then install Firestarter by either going to System>Synaptic Package Manager and search for and install Firestarter. You can also install via a terminal under the Accessories menu. Open the Terminal and enter ```
sudo apt-get install firestarter
``` then hit enter. It will ask for your password. (It does not show dots for characters entered for password.)

For an anti-virus, there is ClamAV in the Synaptic Package Manager. I have used ClamAV to scan a few files and it is faster than the Windows versions. You don't have much to worry about in the Virus field though.

To make your screen fonts look better and video codecs and flash for Firefox or Epiphany browsers, I would recommend installing ubuntu-restricted-extras via Synaptic or Terminal. To install via terminal, just open a terminal and enter this command. ```
sudo apt-get install ubuntu-restricted-extras
```Let us know if you have any more questions.

---

### Post by Accelerate- on 2009-10-02
:O this is so comprehensively easy oh wow hahaha. :]

I'm not going to be transferring any files from any computer so i don't think an anti-virus program will be necessary, but if the time arises i'll be sure to use clamAV or AVG-free ;)

I am currently a college student at UC Berkeley (freshman woo!) and am planning on going into comp sci with a minor in business. And in Berkeley, i think encryption is a must after 9pm haha those evil squirrels are vicious! :P


So i've been surfing the forums, and most of the security question responses generally revolves around closing and shielding and forwarding internet ports via firewall and router.

So i checked firestarter (thanks for the code!) and theres only one active port, but i just have a quick question. Should i keep my firewall locked or unlocked?


*Thanks a bunch-load running rabbit for the extra codec stuff!!

---

### Post by DasEi on 2009-10-02
some more basics :

sudo apt-get install rkhunter sshguard
sudo rkhunter --check                     


sudo nano /etc/ssh/ssh_config , there search permit root access = yes
(no root allowed to remote login)

sudo nano /etc/fstab ,  add a line :
tmpfs /dev/shm tmpfs defaults,ro 0 0



next to google what that above gibberish does, google: securing debian,
                                                       apparmor

---

### Post by undecim on 2009-10-02
Welcome to [X]Ubuntu.

The default install is extremely secure. Following running_rabbit07's suggestions will give you a little bit more security (and also that piece of mind that comes with deliberately protecting yourself from possible threats!.)

Just keep your packages up-to-date and relax a little. You're safe now.

If you want to encrypt your home directory, to protect yourself from identity theft resulting from physical theft, you have a few options.

If you are sure you know where your sensitive files will be, you can install ecryptfs, and set up your "Private" directory, which will transparently encrypt all your files. Just run the following code in a terminal:
```
sudo aptitude install ecryptfs-utils; ecrypts-setup-private
```
Follow the prompts to set up your private directory, and store any tax information or similar documents there.

You can also use the same method to encrypt your entire home directory. To do this, you can either re-install with the alternate install CD and select "yes" when it asks if you want to encrypt your home directory, or if you are feeling adventurous and don't mind the command line interface (for a few moments) you can do it without reinstalling. (I wish I had a link to the instructions to do it without reinstalling...)

---

### Post by Accelerate- on 2009-10-02
Thanks undecim!

I'm going to have to encrypt my entire home directory i think because all of my files are basically going to be important between my internship at oracle and all the school documents/programming assignments i'm going to be getting in the next few weeks.

So thanks for the directions!

I think that's it. All I'll be doing is typing up documents on open-office (since abiword can't handle big documents?) and the occasional pidgeon with friends.

---

### Post by rookcifer on 2009-10-02
> **Accelerate- said:**
> So here's the little backstory. I just made the switch to Xubuntu (installed about a good 30 minutes ago), i chose it over Ubuntu and Kubuntu because this is an old laptop (Pentium 3 at 700mhz) As a former windows user, i was a security fiend, always using anti-virus scans, anti malwar scans you name it i would have them running almost 24/7, in doing so, i had virtually no performance, but a somewhat peace of mind that my computer was safe. 

And still your computer was not safe.

> Now i know Linux is a far more secure OS on its own, but as an OS connected to the internet, it's still fairly vulnerable. 

No, it's not vulnerable at all in its default configuration, assuming you keep it up to date.

> So i did my homework, to a general extent, and found that there a a few key things i need to do to secure my computer. Such as encryting my HD partition, setting up a firewall and IPtables (what is that?)

Encrypting the HD will only provide physical security when the computer is powered off.  It has nothing to do with stopping remote crackers.

As for IPtables, you don't need to worry about it *unless* you install a server of some sort (VNC or SSH for instance).  The default Ubuntu install has *zero* ports open to the Internet.  This is not Windows where 4 or 5 ports are always open and can never be closed.

> So i was wondering, how can i make sure that my laptop is secure as possible even though right now i have basically no knowledge of Linux code?

The only thing you need to do is:

1) Always install updates when prompted.

2) If you install VNC or SSH, be sure to use a *strong* password to secure them.  You also want to look into fail2ban if you install SSH, and you will probably want to change the port from 22 to something random.  If you install these servers, then it is probably a good idea to go ahead and turn on UFW (firewall) or use the GUI called "GUFW."

3) If you want something that will make your box air tight, look at the AppArmor sticky at the top of this forum, or read the Wikipedia page about it to get an idea of what it is.

---

### Post by The Cog on 2009-10-02
The threats are different in Linux.

Viruses aren't a problem in Linux at the moment. That could change at any time of course, but for the moment there are no common viruses for an AV program to look for. 

Root kits are potentially a problem, and could possibly be lumped together in the virus category in the sense that you need to find them. There are a few rootkit detectors available - chkrootkit and rkhunter come to mind. Of course, a root kit follows some other compromise. We generally advise reinstalling if you get a rootkit - its the only way to be sure it's gone. But as I say, rootkits follow some other compromise and you should really be focusing on preventing a break-in in the first place.

Firewalls aren't normally necessary. A default install isn't listening for incoming connections so there's nothing to block. And if you install a service like a webserver, you normally want people to be able to connect to it, so a firewall still doesn't help unless you want to block some IP addresses and allow others (like only allowing SSH from your workplace).

Probably the biggest danger is stuff bring in yourself - programs you download from the internet or web pages with browser exploits in them. Install NoScript into firefox, and be sensible. Remember that most software you might want is available in the Ubuntu repositories.

---

### Post by running_rabbit07 on 2009-10-02
> **Accelerate- said:**
> So i checked firestarter (thanks for the code!) and theres only one active port, but i just have a quick question. Should i keep my firewall locked or unlocked?

I don't lock mine unless I think I see a fishy connection going on, but for the most part, if you are using a firewalled router, then you will be ok, because a hacker would have a hard time getting past it. Of course if you are not surfing the net or anything, then it will not hurt to lock it. Kinda the same concept of locking the door when you are home.

If you are staying in the dorms, then I highly recommend the HD encrypting.

One more thing you can do to help make your system secure it to go into BIOS and set up the password. Once that is done you can adjust the settings to make someone enter a password before being able to do anything. Make sure to use a password you can remember. Last thing you want is to be locked out of your own system. There is a reset jumkper on the motherboard, but that is harder to get to on a laptop. 

You can also password protect grub by installing startupmanager in Synaptic. That programs has a few good uses.

---

