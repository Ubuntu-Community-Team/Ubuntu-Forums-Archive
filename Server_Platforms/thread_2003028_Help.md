---
title: "Help"
date: 2012-06-13
forum: Server Platforms
---

### Post by DFergLSI on 2012-06-13
I do software/hardware testing for LSI Corp. Today I have been assigned to install Ubuntu Server 12.04 with our latest driver. Thus my nightmare began...
 
1st - no GUI of anykind. startx doesn't even work, PC is not connected to internet.
2nd - No way to install 3rd party driver duing install process.
 
I did find one pice of advise on getting a GUI "sudo apt-get install ubuntu-desktop" but this fails with "Unable to locate package ubuntu-desktop"
 
In order for me to complete this test for LSI I need to be able to..
 
Update to the latest driver from USB during install/update driver on an already installed system.
 
Acess the USB after the server starts up..
 
Install our MSM utility and our command line utiltiy "megacli." and test acordingly.
 
I have been doing these tests under RH, Suse for the last three months and wondered why we didn't support Ubuntu Sever.... I have my own theory now as to why we don't.

---

### Post by Jake.Debord on 2012-06-13
I don't think ubuntu desktop is included in the distro... depends on where you got it. Usually it isn't. You could try to find the package and install it manually since its not attached to the internet. But, if your not familiar enough with the command line for a manual install I suggest attaching to internet and trying again.

---

### Post by DFergLSI on 2012-06-13
> **Jake.Debord said:**
> I don't think ubuntu desktop is included in the distro... depends on where you got it. Usually it isn't. You could try to find the package and install it manually since its not attached to the internet. But, if your not familiar enough with the command line for a manual install I suggest attaching to internet and trying again.
 
 
I can do command prompts if somone can tell me what the commands are and how to use them. I just don't know the ones specific to Linux. 
 
I can't change anything from the default install. If we can't get our drivers to install and/or our tools to work without needing additional things not proviced by Ubutu then I will simply have to report the failue and move on.
 
The purpose of this test is to see if our tools/drivers work on Ubuntu and what steps are needed. I do have to admit RH, Suse, all have so far been pretty easy and straight forward. Ubuntu not so much....

---

### Post by Jake.Debord on 2012-06-13
I'm not sure what tools and drivers you are trying to test because I am not familiar with LSI. Did you test on Redhat workstation and Suse with GUI? Ubuntu also has a desktop version that includes a gui that I would suggest if you don't want to connect the Ubuntu server to the internet to download the GUI for Ubuntu Server. Depending on what the tools do, Ubuntu Desktop GUI will probably work just as well for you.

---

### Post by DFergLSI on 2012-06-13
> **Jake.Debord said:**
> I'm not sure what tools and drivers you are trying to test because I am not familiar with LSI. Did you test on Redhat workstation and Suse with GUI? Ubuntu also has a desktop version that includes a gui that I would suggest if you don't want to connect the Ubuntu server to the internet to download the GUI for Ubuntu Server. Depending on what the tools do, Ubuntu Desktop GUI will probably work just as well for you.
 
LSI makes RAID Cards and chips.  A rather large company..anyway.  I work in the testing lab.  So far we have not supported Ubuntu but have RH and Suse, so we aleady know how to install all of this stuff on those.  I use Ubuntu Desktop on my laptop as my main OS and like it.  That is probably why I was given this task.   As far as I know this is the first time anyone here has tried to test our hardware/softwware with Ubunu.  The desktop version is not what I am to be testing as the LSI MegaRaid controller and it's family of hardware is not designed for the home user it is for the Enterprise user.
 
Frankly I am stunned.  Ubuntu has done such a great job on making their Desktop easy to use and understand but the server is almost at the opposite end.

---

### Post by LHammonds on 2012-06-13
If I had the know-how, I certainly would do my best to help you out.  Support for LSI in Ubuntu Server would be a great thing to have.

One thing I would suggest is the rename of your thread title from "**Help**" to "**Help with installing LSI RAID drivers on Ubuntu Server**"  That should get much better attention from those browsing the threads.

---

### Post by DFergLSI on 2012-06-13
> **LHammonds said:**
> If I had the know-how, I certainly would do my best to help you out. Support for LSI in Ubuntu Server would be a great thing to have.
 
One thing I would suggest is the rename of your thread title from "**Help**" to "**Help with installing LSI RAID drivers on Ubuntu Server**" That should get much better attention from those browsing the threads.
 
Can't seem to change this thread title.  Will start a new one with your suggestion.

---

### Post by spynappels on 2012-06-13
> **DFergLSI said:**
>  The desktop version is not what I am to be testing as the LSI MegaRaid controller and it's family of hardware is not designed for the home user it is for the Enterprise user.
 
Frankly I am stunned.  Ubuntu has done such a great job on making their Desktop easy to use and understand but the server is almost at the opposite end.

While I agree that having the LSI RAID cards supported in Ubuntu would be good, as most Ubuntu servers are run without a GUI, testing with a GUI may give a spurious result. 

Do you simply need the GUI to be able to install the MegaCLI binaries to test you can access the RAID card config from inside the OS? I presume it would be testing access from the CLI anyway, as that is what I've used on RHEL in a customised caching server, but that had the MegaCLI integrated into the custom CLI, there is no GUI on that server.

I guess I'm asking for some more details on exactly what you want to test, and whether you anticipate only needing the GUI to install the MegaCLI libraries and possibly some GUI frontend?

btw, there is a good reason that the server by default has no GUI, you would find that most *nix based server OSs do not have a GUI in production, and those which do often are administered by people from a Windows background, who rely on a GUI.
All the RHEL and Solaris10 servers we run at work (1000+) have no GUI and are administered through SSH/CLI only.

---

### Post by wojox on 2012-06-13
> **DFergLSI said:**
> 
 
I did find one pice of advise on getting a GUI "sudo apt-get install ubuntu-desktop" but this fails with "Unable to locate package ubuntu-desktop"

```
sudo apt-get update; sudo apt-get install ubuntu-dektop
```

May also help: [ServerGUI]("https://help.ubuntu.com/community/ServerGUI")

---

### Post by arrrghhh on 2012-06-14
> **DFergLSI said:**
> Can't seem to change this thread title.  Will start a new one with your suggestion.

If you click "Go Advanced" after trying to edit your first post, you should be able to edit the title.

;)

---

