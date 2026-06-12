---
title: "new to ubuntu and confused"
date: 2011-02-14
forum: Security
---

### Post by sear69 on 2011-02-14
My partners laptop was running windows but it started acting all weird and so I decided to scrap the windows and try ubuntu as i had heard so many good things about it.
I have read through alot of these forums and its a lot of info to take in and now i think i have read too much and confused myself.
I read that using ubuntu meant you didnt have to worry about viruses and so didnt need an anti virus or firewall. Having only ever used windows its hard for me to get my head round this. 
I have activted the ufw firewall thing, and would like an antivirus so that i can scan files should i wish to share them between the laptop and any other pc but am having a hard time finding anything that is up to date, easy to install and works.
Can anyone help me out here with what to use and how to install it, if there is anything?
Also with the firewall, i am so used to the ones you get with windows like mcafee's or kasperskys which ask you about permissions, eg, x wants to do this allow or deny? and you choose what it does and you can actually see it working. Is there anything that works like this with ubuntu or is it a case of me just creating rules myself with this ufw thing? and does it allow you to browse anonymously and hidden like the windows firewalls do?
Sorry if i am sounding like a complete noob but i have never used ubuntu before so i kind of am where thats concerned, always been an avid windows fan until recently when i had a hell of a lot of problems with it.
Anyways any help that you can provide would be greatly appreciated.

---

### Post by mikewhatever on 2011-02-14
Several AV vendors make installation files for Linux - Avast, AVG, F-secure, just search. The installation is usually similar to that of Windows.
UFW has a GUI called GUFW, but as far as I am aware, there is nothing like those macafee and kaspersky monstrosities.:p
The default installation of Ubuntu has no open ports, and therefore doesn't need a firewall.

---

### Post by or3x on 2011-02-14
I don't think you need any anti-virus software, I've been using ubuntu for a year without ever installing something against viruses and haven't had any problems so far. Ubuntu and linux in general is A LOT more secure than windows

---

### Post by pricetech on 2011-02-14
As mentioned above you won't need a firewall unless you install and run services on your computer.

As far as antivirus, just check the vendor's website for your favorite and see if they offer a Linux version.

---

### Post by Rubi1200 on 2011-02-14
Hi and welcome to the forums sear69 :-)

If you have a router with firewall that should suffice.

As far as anti-virus is concerned you will hear many opinions. The simple fact is that it is useless and unnecessary on Linux UNLESS you are running something like a mail server or sharing files with Windows users.

I highly recommend you read the security stickes by bodhi.zazen to get a better understanding of security on Ubuntu:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by NightwishFan on 2011-02-14
> and does it allow you to browse anonymously and hidden like the windows firewalls do?

As far as I know firewalls do not do this.

---

### Post by Irihapeti on 2011-02-14
I like to run a firewall on my laptop (netbook, actually) because I don't trust the firewalling in the cafés etc where I use it. It may be fine and probably is, but I don't want to take the chance.

Entering "sudo ufw enable" in the terminal will enable the firewall.

If the laptop only gets used at home, and is behind a router, enabling the firewall is optional.

---

### Post by The Cog on 2011-02-14
As Irihapeti says, "sudo ufw enable" in the terminal will enable the firewall. That's all you have to do. It will block all incoming connection attempts but allow all outgoing connections. A firewall isn't really needed until you install a listening service, upon which you will have to remove or reconfigure the firewall again to make the service reachable. But apart from that, a firewall won't actually do any harm. I don't know of any Linux firewalls that say "xxx wants to use the internet", and I don't really see the point. Once you have malware on your system, it can disable the AV/firewall and impersonate other applications anyway. Some AV software generates loads of logs telling you what it blocked, but they will just keep you awake worrying if you read them. 

For AV, if you're sharing files with windows users then it's worth scanning. The only av that I know of that's in the repositories is clamav. It's an on-command scanner, e.g. "calmscan /media/usbdisk". I don't know of any on-access scanner.

---

### Post by sear69 on 2011-02-14
Thanks a lot for the help :)

---

