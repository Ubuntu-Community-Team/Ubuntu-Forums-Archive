---
title: "New to Ubuntu, security questions"
date: 2010-03-01
forum: Security
---

### Post by Slantzalot on 2010-03-01
First off, I want to apologize because I'm sure this is the billionth thread on this topic.

I'm new to Ubuntu, (heard good things about it) and I wanted to know how much I need to worry about viruses, trojans ect. while using Ubuntu. I read a thread on this board concerning something similar to my topic where it was stated that viruses aren't much of a problem. But several of the posts on this board are also about how to get rid of spyware and malware, so naturally I'm a bit confused.

What security precautions should I take? Do I need a program like virus protection program such as Mcaffee or Norton? Are those even compatible with Ubuntu? 
If it wouldn't be too much of a hassle could someone explain how to set up whatever security measures I'll need,  or at least point me to someplace that can help me?

As I said, I'm new to all of this and I'm feeling overwhelmed, so any help will be greatly appreciated. Thanks!

---

### Post by FuturePilot on 2010-03-01
All of your questions have answers in the [Ubuntu Security Sticky]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by rookcifer on 2010-03-01
The people who ask about virus removal are usually either newbs like yourself or are people asking how to use Linux to clean up Windows machines.  The truth is there is no malware in the wild (at least none that is known).  So, no, you don't need AV.  

The security sticky at the top of this forum should cover everything you need to know.

---

### Post by crlang13 on 2010-03-01
Also check out the end of the pocket guide ([http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)).

It has info on virus scanners and firewalls.  I, personally, have a virus scanner on my computer, just in case.

Although malware is rare for linux, you are in just as much danger to phishing, so practice safe browsing.

There are also tons of add-ons you can add to firefox to check for phishing sites.  I use one called link extend.

---

### Post by houseworkshy on 2010-03-01
I used to love telling people that there was no malware for linux.  Sadly this is no-longer true
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
I'd recomend turning the inbuilt firewall on "sudo ufw default deny" followed by "sudo enable ufw" in the terminal.  Or if you prefer a gui putting firestarter in from the repositories.  Installing clamtk ( which is in the repositories ) is a good idea and perhaps rkhunter too.
If you are really worried you could also put tiger in and see what it finds.  Wireshark is also available.
One of the most useful commands in the terminal is "man".  Use that to find out what you are being told to enter into the terminal, I haven't seen malicious commands yet but there is a sticky on this site warning people that they exist.
As the sudo command has a 15 minuet timer then when you have finished what ever admin action required it enter "sudo -k" before browsing just in case.  This will mean any further admin actions will require your password again so you will be alerted if anything tries to mess around where it shouldn't.  Also be very cautious about what repositories you add and deb files.
Linux is safer yes, immune no.

---

### Post by houseworkshy on 2010-03-01
I've just noticed that this is your first post (welcome to the forums ).  My previous post may have been too much, sorry if it was.  The basics are very easy indeed and this excellent short book got me started, the pdf download is free
 [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
I learned as I set up by going through it.
The online documentation is also good, on a fresh install you should have some useful links already in your firefox bookmarks.

---

### Post by OrangeCrate on 2010-03-01
Adding...

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by rookcifer on 2010-03-01
> **houseworkshy said:**
> I used to love telling people that there was no malware for linux.  Sadly this is no-longer true
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)


That's nothing new; there has been POC malware for Linux for many years.  The question is how much of that malware is in the wild floating around.  I would say next to none.

---

### Post by FuturePilot on 2010-03-01
> **houseworkshy said:**
> 
I'd recomend turning the inbuilt firewall on "sudo ufw default deny" followed by "sudo enable ufw" in the terminal.  Or if you prefer a gui putting firestarter in from the repositories.

Firestarter and UFW are not going to mix well.

---

### Post by Slantzalot on 2010-03-01
Another quick question: I'm not logged in as root, unless I use the command "sudo password root", is this correct (for the most part)?

I just want to make sure that the first account that I created isn't a root account.

---

### Post by Slantzalot on 2010-03-01
> **FuturePilot said:**
> Firestarter and UFW are not going to mix well.

What do you mean? What should I do?

Sorry for the double post.

---

### Post by FuturePilot on 2010-03-01
> **Slantzalot said:**
> What do you mean? What should I do?

Sorry for the double post.

Firestarter and UFW are both frontends to iptables. Using two different tools to control iptables will usually end up with them overwriting each other's rules or at least creating confusing rules at are difficult to follow. It's best to just stick with one. I would not recommend Firestarter though as it's unmaintained these days. If you want a GUI check out GUFW.

---

### Post by jeancarlo on 2010-03-01
If you are working with a good security system in your Pc, there would be any problem, but for more information you can visit this web page [http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html)

---

### Post by rookcifer on 2010-03-01
> **Slantzalot said:**
> Another quick question: I'm not logged in as root, unless I use the command "sudo password root", is this correct (for the most part)?

Unless you want to enable the root account, you do not run that command (and it is "sudo passwd root").  You should not have to enable the root account at all, everything will work fine without it.

> I just want to make sure that the first account that I created isn't a root account.

The account you created when you installed Ubuntu is both a user and a root account.  What that means is whenever you are asked to enter your password, this gives root authentication.  By default, Ubuntu does not utilize the separate root account (contrary to most other distros).  Instead, whenever you need to perform a root action, you will prepend the command with "sudo."

---

### Post by TurnOfTide on 2010-03-01
Botters are always looking to add more bots to their net, wether from linux or windows or mac. All they have to do is port their bot client to linux. Google agobot3 or gaobot3 and you will clearly see in their source that they can compile and run on linux.

---

### Post by hwttdz on 2010-03-01
As a new user I think the first thing to learn is to use sudo as little as possible and only when you're sure what you're doing.  I don't believe any antivirus is currently necessary (and it's only one further complication), and I'm also ok with the default security settings (however, I know many smart admins who are not).  

As of Jan there were no reported wild linux viruses [http://www.wildlist.org/WildList/201001.htm](http://www.wildlist.org/WildList/201001.htm) (feb is not up yet)

w32 is windows, vbs is used by Microsoft office (I believe).  So the statement there are no wild linux viruses is currently true.  That is assuming you don't have sudo access, if you do then then there are six ways to sunday you could mess up your machine.  The moral of the story is use sudo as little as possible, and when you do make absolutely sure you know what you're doing.

---

### Post by Slantzalot on 2010-03-01
Just want to say thanks to everyone who has helped me out with Ubuntu! You guys are great!

---

### Post by houseworkshy on 2010-03-02
Sorry I should have been clearer than simply using the word "or" earlier.  The ufw commands in the terminal and the gui firestarter advice was intended to mean two alternatives methods rather than as both at the same time.  The gui for the ufw ( which is an acronymn for "ubuntu firewall" ) is the gufw.  
I only mentioned firestarter as setting that one up is mentioned in the pocket guide.  Both access iptables.
Appologies for the confusion

---

