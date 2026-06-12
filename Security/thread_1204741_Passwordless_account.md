---
title: "Passwordless account"
date: 2009-07-05
forum: Security
---

### Post by lovinglinux on 2009-07-05
[color=#990000]**Important Note:**[/color] I don't want to setup a passwordless account and don't recommend trying to do so. If you have found this thread because you are tired of entering your password when using *sudo*, then you can [increase the password timeout](http://ubuntuforums.org/showthread.php?t=851828), but you should never get rid of it.

Well, here is the situation...


A friend of mine, who doesn't know much about computers, bought a netbook this week to take with her on an extended trip to Europe. She didn't realized the computer came with Linux installed and asked for my help to get the Internet working, using a 3G mobile USB modem. Unfortunatelly, we live on different cities and she was about to travel, so I scheduled a meeting using IM so I could guide her through the steps of configuration. It was hard, but I did it.

The main issue wasn't actually the procedure required to enable the modem, but the fact that I didn't know her OS. I will not mention the OS name, because this is not the issue here, but it was a Debian based distro produced here in Brazil and used by some OEM distributors.

Well, here is the odd situation. When she logged in, there was already an account configured by manufacturer and there was no indication of a default password anywhere. I needed to perform some administrative commands so I tried to use sudo. For my surprise, sudo worked without requesting a password.

Nevertheless, when I tried to save the modem configuration file in the etc directory, it failed all the time. Which was also odd, because I was able to save the same file in the etc folder, by adding a .bkp extension to it and using sudo. I needed to create a script that would cat the contents of wvdial.conf.bkp and replace the content of wvdial.conf, to update the modem DNS servers.

After several failed attempts and several troubleshooting procedures to make sure she wasn't typing the wrong path, I decided to log as root and see if I could save the file.

So, I changed to a root session using *sudo -i*. For my surprise, I was able to become root without entering any password and was able to save the file. The modem worked and she was able to browse the web. Unfortunately, she wasn't able to install new packages tho. I checked the sources.list file and it was using Ubuntu Gutsy repositories, along with a single repository of the own distro, but any attempt to download and install a package resulted ins a message saying the package wasn't available. But this is a discussion for another thread.

So, what do you think about this situation? What do you think about a manufacturer selling computers with a Linux with this configuration and most important, what could I do to help her to protect her system?

I tried to convince her to install Ubuntu, but she wasn't very happy with the idea of spending a few more hours trying to configure another distro.

---

### Post by armandh on 2009-07-05
I dumped dells Ubuntu in favor of OOTB 8.10 on my mini 9.
the list of things that did not work as I expected caused me to quickly change. 
while the stock kernel may take longer to boot, it is all there. 
for real security pick real Ubuntu!

---

### Post by Agent ME on 2009-07-05
From what I've heard, many OEM systems with Linux pre-installed are badly misconfigured, and just reinstalling a plain Linux distro to replace it can work much better.

[rant] I'm amazed that companies like Dell can manage to screw up a simple Linux install regularly. I'm sure it has to be due to pressure from MS that they cripple their Linux installs like this. Stupidity can only explain so much.

---

### Post by cariboo on 2009-07-05
Sounds to me like your friend skipped the step where she had to set up her user password, when she started up the computer.

When I sell a computer system with Windows on it, I use the oem setup option. You shouldn't be surprised how many people are still running the default setup after 6 months, mostly because it is something they know nothing about and are afraid to change anything.

---

### Post by aysiu on 2009-07-05
> **Agent ME said:**
> From what I've heard, many OEM systems with Linux pre-installed are badly misconfigured, and just reinstalling a plain Linux distro to replace it can work much better. That's been my experience.

I bought an Eee PC 701 with Xandros preinstalled, and the Asus Xandros had *sudo* without password authentication. Worse still, if you enabled a password prompt, Xandros wouldn't boot up at all. I very soon replaced it with regular Ubuntu.

Then I sold that and bought an HP Mini 1120nr with Ubuntu Hardy preinstalled, and the HP Ubuntu ("Mobile Internet Experience" they call it) also had *sudo* without password authentication. It was also slow as molasses. I replaced it almost immediately with regular Ubuntu.

---

### Post by sisco311 on 2009-07-05
> **lovinglinux said:**
> 
Unfortunately, she wasn't able to install new packages tho. I checked the sources.list file and it was using U**buntu Gutsy** repositories, along with a single repository of the own distro, but any attempt to download and install a package resulted ins a message saying the package wasn't available. 


R.I.P. Gutsy... R.I.P...
[uwiki]Releases[/uwiki]

---

### Post by lovinglinux on 2009-07-05
> **sisco311 said:**
> R.I.P. Gutsy... R.I.P...
[uwiki]Releases[/uwiki]

Yeah, I know. That's why it didn't installed any programs. I tried to replace the sources with Hardy repositories, but was a no go. Then it was already late and she didn't wanted to continue.

Can you imagine her satisfaction with the product if she didn't know me or someone else with Linux experience?

---

### Post by jrusso2 on 2009-07-06
Linspire is the only Linux distro I have ever seen that worked like that out of the box.

I am sure you can add a password if you want one.

---

