---
title: "Server Setup Steps"
date: 2011-08-16
forum: Server Platforms
---

### Post by SyntheticShield on 2011-08-16
I have Ubuntu Server 11.04 and a machine to install it on. All my laptops and desktop run Linux Mint 11. I am really wanting to get some experience in setting up a Linux Server not only for home but in a business environment where it would likely serve as a web server, mail server, dhcp server, etc. All the goodies. I have a great deal of documentation on how to do everything and have even set up Ubuntu Server with Webmin on top of that. But I really want to take this further and dive in deeper and learn a lot more. So I figured I would start at home, but I have a friend that is the Human Resources Manager and Financial Manager for a small piping company and desperately wants to run Linux Mint on their machines and to set up a server to serve the previously mentioned items to name a few. They are not in a big hurry but my friend asked if I would be interested in setting everything up. I explained I had not set up a server before in a business environment (particularly concerned about security, etc). He was okay with that as they are not in a hurry. Basically told me to take whatever time I needed to make sure everything was done right and secure.

So, with all that said, here's what I need. As I mentioned I have a great deal of documentation that shows me how to set up the server, set up the dhcp server, print server, etc and some articles and documentation on security. What I dont have is a real good roadmap of how to proceed. Im a logical progression kind of guy, I like to go through things step by step until I understand each one well. So my ultimate question is can anyone point me to any kind of documentation or tell me directly what the normal steps would be in setting up a server at home and/or in a business environment. Is there a do this, then this, check this then do this sort of guide around anywhere?

I would just really like to have a checklist, if possible, to go buy so that I know that I have everything needed installed (fairly easy to determine, but nonetheless) but more importantly have covered all the security bases and could use a guide or something to go through to check this off, test this, check that and so on.

Sorry for the ultra long winded post, but I wanted to be thorough. Thanks in advance for any and all assistance.

---

### Post by PierreRobiquet on 2011-08-16
Just a random thought here, but have you thought of making a virtual machine team and network to test your setup on? With enough RAM you should be able to run 3 VM's with Ubuntu Server and 2 Linux Mint copies, that will allow you to test everything before deploying. Unfortunately reading through the documentation is sometimes not enough, there are weird quirks that may only appear when you put your plan into practice.

---

### Post by SyntheticShield on 2011-08-16
Oh, Im forced with asking something that is probably going to make me look like an idiot, but so be it.

When you say VM (Virtual Machine) do you mean setting everything up in something like VirtualBox and running it from there?

---

### Post by hawk2010 on 2011-08-17
I do prefer Virtualbox because it has a powerful command line interface which is really helpful when you are running the Ubuntu server which is without the GUI

---

### Post by SyntheticShield on 2011-08-17
Well, okay then.  There's one thing Ive got to learn then.  I have never set up a virtual network inside VB.  I did not know that was possible.  The only thing Ive used VB for is to run windows and that just to run the one remaining piece of software I have there is no linux alternative for.

Can someone link me to info on how to set up a netowrk inside VB?

---

### Post by hawk2010 on 2011-08-17
What sort of network are you looking at. You have to first design your network. Will the VMs running on virtualbox  on bridged mode (meaning they have IPs from the real network) . or else will it be NATted.

---

### Post by SyntheticShield on 2011-08-17
For the purposes of testing, NATed would probably work best.  But my main focus in all this was to get or figure out the steps or checklist in setting everything up.  I know it wont be the same each and every time, but a basic overview check list was what I was after.  For instance, if you are setting up a DHCP server then you need to do this, this, and that.  Then after thats done, do this this and that to secure everything.

---

### Post by hawk2010 on 2011-08-17
Please google virtualbox manual and it is very useful. If you have only specific things we can help you outl

---

### Post by SyntheticShield on 2011-08-17
Well then.  I have a Virtual Box manual, its not the full fledged manual.  I also have the full Ubuntu Server Guide printed out.  I have downloaded and printed out guides and book until Im blue in the face on dhcp, file sharing, remote access, etc.

So please, I mean no offense by this, dont brush me off to google.  If google would have helped any, I would have not posted here. Furtermore, my original question was specific.  I was seeking some kind of checklist in the server set up process to make sure I covered everything that needed to be done in that process.

My question in response to the suggestion of networking inside virtual box was also specific, can I please be pointed to some kind of how to on that as I have never read of being able to do that within VB and as far as I knew, you could not have more than one thing running inside VB at one time.  

While google can help you find a lot of things, and I use it a lot.  I did ask specific things.  And if google could have pointed me to information I was looking for I would not have posted in a forum specifically run to help answer questions about the very same specific software I am using.

---

### Post by hawk2010 on 2011-08-17
Ok. Basically you have basically several things to look up before doing up a VM. 

1. Get the total RAM and disk space of the real server, (if your running linux headless servers i would say you may need about minimum 256MB for good performance but it may work with less)
2. Do a diagram of each VM you want to be inside VB and assign the amount of RAM and disk space you want. Note that VB support dynamically expending disk space as well. So the storage grows as you need. Also the number of network cards for each of the VMs and they mode of operation. (for .e.g NAT, bridge)
3. In the diagram state which VMs need NATtting and which VMs do not.
4. In the diagram mention which VMs you need VRDE (Remote desktop for VMs) this is very helpful. Please note that the new VB 4.1 require you to install the VB extension pack. Without it you won't be able to use VRDE
5. Basically there are three main networking modes in VB
a. Bridge mode where the Virtual adapter of the VM is bridged with your physical adapter letting it part of the real network.
b. NAT mode - where the VM is natted. 
c. Host-only - where you can have multiple VMs on a virtual switch kind of an interface. VB has an in built DHCP for this but you can specific whether to disable or to have a separate IP range by going to preferences in VB. You can have as many vbox-net type adapters with different DHCPs as you want

Hope this covers what you are looking for. let me know

---

### Post by SyntheticShield on 2011-08-18
That helps out a lot hawk, thank you very much.

---

### Post by drdos2006 on 2011-08-18
You are going to have to do some heavy reading to set up your first server.
Zentyal will get your machine running in an office environment while you learn the more detailed operations of a server. [http://www.zentyal.com/](http://www.zentyal.com/)

Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the Zentyal server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by SyntheticShield on 2011-08-18
I will most definitely check out zentyal.  I realize there is going to be a lot of reading and why I have been collecting all the documentation I can find and have went through a few reams of paper already printing it all out so I can study, note and follow.

I already have an older laptop set up with Ubuntu Server 11.04 though I dont have anything connected to it or providing any services from it.  I installed it just to work with and learn and I did find out about Webmin and have installed that as well.

And the HowTo you linked to I found yesterday after posting here and have downloaded the pdf for it and you are right, it is quite extensive and Im anxious to get it printed out so I can run through it and set up a server at home with it.

---

### Post by nyu2007 on 2011-08-18
Go ahead, and you will learn more more.
I already test my lab with servers:
1. PDC: DNS Master, OpenLDAP Master, Samba Domain Master
2. BDC: DNS Slave, OpenLDAP Replicate, Samba Domain Slave
3. MAIL Server: Zimbra ZCS 
4. File: Samba Share File.

And another if I have time.
:KS

---

