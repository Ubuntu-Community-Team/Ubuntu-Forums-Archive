---
title: "PXE Server"
date: 2010-08-23
forum: Server Platforms
---

### Post by Vegan on 2010-08-23
I was wondering, how much hassle would it be to setup a PXE boot so I can boot a machine from the network.

---

### Post by msboston01 on 2010-08-25
That is a great question, Vegan. I will use the same thread if you don’t mind because I believe we are talking about the same thing. 

The idea:
I have a Windows Vista Media Center in my living room connected to an OpenFiler share (SMB) server in my basement. Everything is cool except for the noise generated from the Media Center. So I want to replace it with a thin client like  that would boot Vista Media Center from the network.

The setup:
I also have in the basement a Ubuntu 10.04 LTS desktop running which also happens to perform backups of the OpenFiler server, manage the UPS and all that jazz. I’d like to make it (ie: the Ubuntu desktop) a PXE server that would serve the boot file for the thin client in the living room. Note that I have gigabit network so performance should not be an issue.

The problem:
All the documentations and how to’s I have found so far on PXE set up is to network boot PCs to install a new OS on it. What I’d like is to keep this setup running so the thin client’s “HDD” is on the Ubuntu box forever (actually I might store it on Openfiler using iSCSI to Ubuntu but that’s easy). Anyone has some documentation on how to set that up?

Thanks

Nic

---

### Post by arrrghhh on 2010-08-25
Gigabit is helpful, a powerful PxE server rig is key (RAM is most important, but a good processor is essential too).

Sounds like you'll only run one client, so perhaps you won't need extremely beefy stats... Give it a shot, see what you can do.

[UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP) and [ThinClient How-to](https://help.ubuntu.com/community/ThinClientHowto)

That thin-client how-to looks outdated tho.  The LTSP article has a ton of links, should be able to get you going...

So did either of you use search?  I know I've answered this question (with these exact same links) at least 3x in the last couple of months...

---

### Post by msboston01 on 2010-08-25
Thanks for the links. 

To answer your question, in my case, yes I did but it's all about the right keywords I suppose.. for example, it looks like I should have used thinclient all together as opposed to two words. 

Sorry you had to answer 3 times the same thing but if you look on the bright side, folks thanked you three times ;)

Thanks again (that's 4!)

Nic

---

### Post by arrrghhh on 2010-08-25
Haha, glad I could help.  Sorry for being grumpy, been a bad day today already.  Didn't mean to take it out on you :P

---

### Post by msboston01 on 2010-08-25
No harm done, don't worry. 

UbuntuLTSP opens a brand new option here where the OS is actually running on the host (which explains the need for horsepower and RAM). I'll definitely look into this...

Initially, I was more thinking of a system where the host would serve the boot HDD to the thin-client at start up which would then load the OS... so the OS would be run on the thin-client (not the host).

Vegan, please give me this weekend to geek around with that so don't close this thread just yet (I may have some more questions).

Thanks

Nic

---

### Post by arrrghhh on 2010-08-25
> **msboston01 said:**
> Initially, I was more thinking of a system where the host would serve the boot HDD to the thin-client at start up which would then load the OS... so the OS would be run on the thin-client (not the host).

I'm not sure what the advantage of this would be... You'd still need a hard-drive and a spec'd system for the 'thin' client to boot an OS.  Having the PxE server just start the boot process doesn't make much sense, it's the running of the OS and associated applications that take the power - the boot process doesn't require a lot :P

---

### Post by Vegan on 2010-08-25
I was interested in a PXE boot to an installer of Linux.

---

### Post by gobbledigook on 2010-08-26
hey there vegan... looks like your thread got hijacked a little!! in answer to your question... it is fairly simple to set up as a PXE but it depends on a few things... [**_here is a search for documentaton_**]("http://www.google.co.uk/search?hl=en&source=hp&q=ubuntu+documentation+pxe+server&meta=&aq=f&aqi=&aql=&oq=&gs_rfai="). 

is your router the server? if so then it already handles your DHCP requests and setting up PXE is straighforward... otherwise your router will need to support dnsmasq so you can forward the request to your server, DD-WRT supports this, here is some more reading about that:

[**_dd-wrt PXE wiki_**]("http://www.dd-wrt.com/wiki/index.php/PXE")

[**_PXE boot with DD-WRT and Ubuntu_**]("http://nickpegg.com/2009/04/pxe-boot-with-dd-wrt-and-ubuntu/") - this  article may be useful too :)

---

### Post by arrrghhh on 2010-08-26
> **Vegan said:**
> I was interested in a PXE boot to an installer of Linux.

Oh, my apologies.  Your thread did get quite hijacked, and I just helped ;)

[Here](https://help.ubuntu.com/community/PXEInstallServer) is the **official** Ubuntu doc on making a PxE install server!  (You shouldn't need to worry about that dd-wrt stuff... I use dd-wrt myself, and all I did was turn off the DHCP server on the router so the Ubuntu Server then was the only thing that would hand out addresses.)

---

### Post by Lars Noodén on 2010-08-27
> **Vegan said:**
> I was interested in a PXE boot to an installer of Linux.

You can use dnsmasq to serve up a netboot installer image.  It has a built-in tftp server.  IIRC you only have to change four lines in the config file to be up and running.  I used to carry a CF card with netboot scripts using dnsmasq to substitute for what otherwise would have been a stack of install CDs.  

dnsmasq is very easy to use and has an excellent devel team and support community.

---

