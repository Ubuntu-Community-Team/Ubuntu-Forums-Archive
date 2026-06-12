---
title: "Noob Question VMWare vs Virtualbox"
date: 2011-07-22
forum: Virtualisation
---

### Post by onyxraven on 2011-07-22
I have dual booted before, but never quite liked it...

I am a gamer, I love linux, and its stability. However it is lacking in compatibility with my core games. 

Currently I am using win 7 as my base OS and have Virtual Box with Ubuntu installed running in seamless mode.

My problem with Virtual Box
1) can't allow more then 128mb of ram to the video capabilities
2) when I launch any program or window in Ubuntu it doesn't always come to the 'top layer' and commonly hidden behind the wall paper of windows 7 making me having to click the program on the Ubuntu task bar till it shows.   

So my question: Which virtual environment is better for hosting Ubuntu inside of windows 7(seamless required)? Before i went and tried VMware - I thought I might get peoples input rather then having to go through the headache of installing everything again. 

Sys specs:

Mobo:KGPE-D16 Server Mobo
CPU: 1x AMD Opteron 6172 - 12 core 2.1ghz
Ram: Kingston 1333 16GB
HDD&SDD: 2xDeskstar 3tb HDD and 1xRevodrive 110GB PCIeSSD 
Vid Card:3GB Gddr5 EVGA 580
Resolution:3840x1024 w/ TH2G 3x19" monitors (... analog :-/ )

---

### Post by Nohajc on 2011-07-22
Well, regarding the seamless acpect, VMware is a clear winner.
If you run your VM in Unity mode, you'll get a perfect desktop integration. 
I think it's way better than the seamless mode in VBox, especially because it uses its own app. menu while hiding the original Ubuntu panels. Each launched window is then treated as a separate app., it's not just one VBox window containing the whole desktop with transparent background.

You can even convert your existing VBox VM into a VMware type and use it in VMware Player/Workstation/Fusion (Mac), etc. :)
No need to install everything again, that's the beauty of virtualizing.

---

### Post by HarriU11-04 on 2011-07-22
VMware? Rubbish! VirtualBox all the way (well, mostly) After trying (and failing) for two weeks to clone my physical Windows partition into Ubuntu running VMware, I decided to try VirtualBox. 3 hours later: It works, I'm happy, nuff said.

---

### Post by Nohajc on 2011-07-22
Well, I don't know, but the latest VMware Workstation is actually quite good. Besides, you won't get drag&drop in VirtualBox. :D

About the cloning: No offense, but maybe you did something wrong, or haven't googled enough... 
You see, I am just running my previously existing physical installation of Windows 7 under Ubuntu host VMWare right now. :) With the option to dualboot it natively at any time (like Boot Camp in VMWare Fusion on Mac). That's even better than doing pc2vm cloning, yet it works technically in almost the same way. 

It is not an official feature on PC, but I've got it working quite easily by changing one registry key and then even installed VMTools which is not breaking the native boot as I've heard of VBox Guest Additions.

So in my opinion, VMware is better. (And according to various benchmarks, it is also faster.)

---

### Post by onyxraven on 2011-07-22
Ok, so I have VMware now,

Another noob question: is there a way to get the ubuntu taskbar to show - like i was able to do in virtual box?

---

### Post by Nohajc on 2011-07-23
Well, that's not an easy one... as I tried to explain, VMware uses its own replacement menu instead of gnome panel, so when you switch to Unity the panel is automatically hidden.

I don't know actually whether you can alter this default behaviour.
Someone has asked this question before on vmware forums but hasn't got any satisfying answer...
[http://communities.vmware.com/thread/255265](http://communities.vmware.com/thread/255265)

---

### Post by frank cox on 2011-07-24
Hi:

  I am in the process of learning VMWare to run a particular appliance ,OpemEMR . After downloading the appliance I began installing VMMware and while reading the  helps it suggested downloading a reconfigured VMWare player for Ubuntu with apt-get. So far I have had no luck finding such an animal, is there such?

Thanks

---

### Post by HarriU11-04 on 2011-08-04
> **Nohajc said:**
> 
About the cloning: No offense, but maybe you did something wrong, or haven't googled enough... 

So in my opinion, VMware is better. (And according to various benchmarks, it is also faster.)
I googled enough thank you. But I found out what the issue is. After running vmware converter ("Convert" button), I needed to click the other button on the converter panel "Configure machine". 

But I decided that there are benefits to a clean virtual machine, installing original software from scratch over taking an image of my C: partition. If the vm ever gets infected, it's relatively simple to restore to a clean machine. I just need to remember to keep data separate from the C:\ (which I do at the moment anyway), and keep a copy of all downloaded software (ditto)

---

### Post by x-D on 2011-08-06
> **Nohajc said:**
> Well, regarding the seamless acpect, VMware is a clear winner.
If you run your VM in Unity mode, you'll get a perfect desktop integration. 
I think it's way better than the seamless mode in VBox, especially because it uses its own app. menu while hiding the original Ubuntu panels. Each launched window is then treated as a separate app., it's not just one VBox window containing the whole desktop with transparent background.

You can even convert your existing VBox VM into a VMware type and use it in VMware Player/Workstation/Fusion (Mac), etc. :)
No need to install everything again, that's the beauty of virtualizing.

+1 to that. VMWare is better for Unity than VirtualBox, but I find VirtualBox is faster loading and faster doing a lot of operations on my box?

---

