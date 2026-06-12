---
title: "Ubuntu server Dell PowerEdge t410"
date: 2011-04-14
forum: Server Platforms
---

### Post by wcorey on 2011-04-14
I installed Ubuntu Server edition 10.10 on a Dell Power Edge T410. The installation went fine but after the installer ejected the disk and I hit continue, the server rebooted to a blank screen, no login prompt no nothing. I know the keyboard was still 'talking' to the OS as the caps lock and num lock lights properly toggled. 

What would cause this?
How can I diagnose this?
What is different about the way the installer runs vs. the way server runs.

The installer recognised there were two nics. If I pointed the install at the wrong NIC would that cause a hang...although, the installer didn't hang.

---

### Post by usatonycuba on 2011-04-14
> **wcorey said:**
> I installed Ubuntu Server edition 10.10 on a Dell Power Edge T410. The installation went fine but after the installer ejected the disk and I hit continue, the server rebooted to a blank screen, no login prompt no nothing. I know the keyboard was still 'talking' to the OS as the caps lock and num lock lights properly toggled. 

What would cause this?
How can I diagnose this?
What is different about the way the installer runs vs. the way server runs.
Several things can cause this failure.. you may wanna take a hit to [https://help.ubuntu.com/community/DellDiagnosticPartitionGrub2](https://help.ubuntu.com/community/DellDiagnosticPartitionGrub2)
> **wcorey said:**
> 
The installer recognised there were two nics. If I pointed the install at the wrong NIC would that cause a hang...although, the installer didn't hang.
I think not, because (if the wrong NIC was introduced during installation process) the server should give errors at the time to try to start establishing the out connection to the network, instead of hanging on reboot..I guess  ?

---

### Post by wcorey on 2011-04-15
> **usatonycuba said:**
> Several things can cause this failure.. you may wanna take a hit to [https://help.ubuntu.com/community/DellDiagnosticPartitionGrub2](https://help.ubuntu.com/community/DellDiagnosticPartitionGrub2)

I think not, because (if the wrong NIC was introduced during installation process) the server should give errors at the time to try to start establishing the out connection to the network, instead of hanging on reboot..I guess  ?

Thanks, I will investigate this. Here is what I found out today. The Dell T410 has an integrated Video adaptor and the group was ordered with an NVIDIA Quatro video, which is apparently 2 months old (new model). I know when I installed my two XPS machines at home the install program has block (low res) 'graphics' yet upon boot now, even though they are still characters, appear in a much higher density resolution. 

What I attempted before installing server was to use a standalone Acronis True Image disk to save off the preinstalled stem image of Windows. ATI initially starts in low res graphics mode and upon selection of what to do switches to a more high res graphics mode. In the case of trying ATI when the program switched modes the monitor went dark, the machine unresponsive and the interrupts off. The factory install disables the integrated video by default and I had our tech dept enable it. However I think it still sees the nvidia graphics card and perhaps that is still, even though it is not plugged in, is causing issues. I did check and Canonical/Dell certify the T410 to run Ubunutu.  

Would it make sense an unsupport graphics card is causing the problem?

Walt

---

### Post by usatonycuba on 2011-04-15
> **wcorey said:**
> I did check and Canonical/Dell certify the T410 to run Ubunutu.  

Would it make sense an unsupport graphics card is causing the problem?

Walt
Unsupport graphics card is causing the problem?... yes that make complete sense... but

Is fully supported, according to [Ubuntu-certified hardware Models]("http://www.ubuntu.com/certification/catalog/component/pci:244E:8086/models")

---

### Post by wcorey on 2011-04-16
Hi Tony,
   Yes, the server is supported but the NVIDIA Quatro (forgot the model, but the card is brand new) doesn't appear to be from what I understand, it also has issues with Windows. This card has an HDMI slot and comes with an adapter for DVI->HDMI. Unbeknownst to me the integrated video is disabled at the factory so when they enabled it it did work but the same symptoms appeared except there was a blinking cursor but the login: prompt never was displayed. Interrupts were still enabled as I could cntrl-alt-delete to force a reboot (no video output). I think the most telling thing is the windows based Acronis True Image disk, upon resetting the video mode (resolution), caused the server to go into a wait with interrupts off. For interrupts to be off in a windows program this issue is in ring 0 as ring 3 can't do interrupts. So that made sense when I was actually connected to it but connecting to the integrated VGA it makes less sense. So I thought I'd check with you. So even though it is not being used, if that could still cause an issue I will remove the card completely. I will let you know.

Thanks!
Walt

---

### Post by usatonycuba on 2011-04-16
I'm so sorry to hear that Walt

It is really a matter of being able to put your card in compatibility mode, or else .. change it as you say ... in the case of what you mention (the compatibility mode disabled for this video server machine type) .. has a way around .. but it all depends if the card is compatible or not? .. which brings us back to the second option ... >> change it... as you said ... make change for a compatible card.

What I do not understand .. is.. if the "change" of the original equipment card ... you asked it that way? .. or HP was the one who made &#8203;&#8203;the change ? ... the question is simple .. by the fact that I am expecting 3 HP Server computers - model L350 G6 ... and they will go to ubuntu server 10.10 (just server with out GUI) .. the graphics are not much important.. I really do not care that much for video card... but I need to know the compatibility options in these cases .. and seems that your problem >> can help to prevent mine ;)

A good option (logic and for your own safety) ... give a ring to HP.. let then know about this issue and give the necessary Info of the future use that you need of your Server .. and start from the options you get from them .. Remember that you can lose the guarantee of your equipment .. in the case of "if" (you make repairs or changes in the product  by yourself).

---

### Post by wcorey on 2011-04-16
It's a little more complicated than that, actually. I didn't order the machines, nor did I pick them out. Our team has 5 CentOS servers (10 if you count the 5 retasked for Windows), remote from where we are. This worked OK when there were only 2 of us using them (was a doing a distributed system and needed multiple machines to interconnect). Now we have many more people than machines and I instituted a server reservation system but there are some cowboys in the group that don't like rules and don't like asking. What I have been advocating for some time is to take those 5 machines (10 if you count those retasked for Windows) and let me put UEC on them, those 10 machines could be easily turned into 150 VMs. More than enough for people if used properly. This has been met with deer-in-headlights syndrome so of the new machines the 5 local of us got I was going to turn mine into a UEC compute node. The guy who ordered them ordered the whizbang new 3D 1GB GPU even though none of us do graphics programming. I neither know what he was thinking or why nobody bothered to ask me my opinion. Oh, it is a Dell T410, not HP. 

The thing of it is, I don't 'KNOW' if it is the graphics card but I suspect it is since both a Windows OS and a Linux OS have problems where the install and low res graphics mode worked fine.

I will let you know.

Walt

---

### Post by usatonycuba on 2011-04-16
Sorry my bad.... make confuse at our Dell poweredge 350, and the 3 incoming ML350 G6 from HP   .....But any way will be a good thing to see what is coming... In the mid time will be good to use a diferent v.card ? .. Using Dell OpenManage tools ? .... 
[QUOTE=Dell]
Quote [From Dell]("http://www.dell.com/downloads/global/power/ps3q09-20090363-Jervis.pdf")
PowerEdge T410 incorporate the Lifecycle Controller—an embedded flash chip containing systems management components such as the system BIOS, firmware, drivers, and Dell OpenManage tools that can function independently of both media and platform OS. The Dell Unified Server Configurator offers a single simplified interface to this controller to help administrators perform tasks such as firmware updates, OS deployment, and diagnostics.[/QUOTE]

---

### Post by fabito on 2011-04-28
Any update ?

I have the same problem.  I didn't have time to inspect it yet, but I'm suspecting that is related to UEFI.

---

### Post by wcorey on 2011-04-28
> **fabito said:**
> Any update ?

I have the same problem.  I didn't have time to inspect it yet, but I'm suspecting that is related to UEFI.

We've been anticipating an office move and there were other things I needed to work on so not yet, in the next week or so I expect to. I can tell you the Dell PE T410 IS certified by both Canonical and Dell to run Ubuntu 10.10, 10.04 etc. After the office move I will remove the brand new Nvidia graphics card, and perhaps the sound card user added, and try it again. If it still does not work I will turn this into a bug and let Ubuntu support deal with it. I would be shocked if an out of the box T410 did not work after Ubuntu/Canonical AND Dell certified it.  In the mean time you could turn off UEFI and try that.

---

