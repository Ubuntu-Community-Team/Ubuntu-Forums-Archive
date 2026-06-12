---
title: "SSH on Ubuntu VM hosted on Windows Server 2012"
date: 2016-01-14
forum: Virtualisation
---

### Post by Bijal on 2016-01-14
Hello,
I am very new to Ubuntu.
We have a Windows server 2012 in our environment.  I want a Virtual Machine with Ubuntu installed on it and from there I want to connect to the Ubuntu VM via SSH.  
1. Please advise whether this is possible
2. Can I have a GUI on the Ubuntu VM?
3. What is the best version of Ubuntu to use? (pls note this instance will be used as a production server)
4. What is the best SSH to use?
5. Where can I get the instructions of the installation of Ubuntu and SSH?

Many thanks.

---

### Post by pappu095 on 2016-01-14
Hi Bijal,

We have a Windows server 2012 in our environment.  I want a Virtual  Machine with Ubuntu installed on it and from there I want to connect to  the Ubuntu VM via SSH.  
1. Please advise whether this is possible -------->Yes this is possible, if you are using oracle virtual box then please check network on setting and click all network adapters
adapter1--->internal network--this is for network
adapter2----> bridge network--this is for bridging 
adapter3-----> NAT--this is for internet
adapter4------>host only---this is for ssh from putty of from other system

2. Can I have a GUI on the Ubuntu VM?-----> Yes, Install ubuntu of desktop version

3. What is the best version of Ubuntu to use? (pls note this instance will be used as a production server)----> try to use latest verison of ubuntu so that you can get support from ubuntu community and definitely ubuntu is being used for production server

4. What is the best SSH to use? ------> can use putty to do the ssh.

5. Where can I get the instructions of the installation of Ubuntu and SSH?----same may refer "http://ubuntuguide.org/wiki/Ubuntu_Trusty" or search on google

---

### Post by MAFoElffen on 2016-01-14
You said a VM of Ubuntu and that the instance will be used as a production server, so I am assuming that you are implying Server Edition(?)
1. Possible.
2. Yes you can, but just as secure in Win 2012 and 2012R2 recommeded now in the MSCS for security is shifting to using Server Core (without the GUI)... A Linux Server is more secure without a GUI ... It's default install is without. You could install a GUI Desktop, but the issues from that is on you and yours. Next is if your administration and management is going to just be ssh, then you don't need to have a GUI, because your not going to see it. And when you start adding a graphics layer to the mix... End users like graphics, but that shifts the priority of process to the user instead of services used in severs. That was the old-school outlook on the whys. Having said that, in some instances I install minimal X that can be loaded/unloaded as an instance (for just maintenance.)
3. That is subject to preference, but what is advised is a current version of the **LTS** version. (Long Term Support) That is the stable tract. Current is 14.03 LTS, but if you are installing in March, then it would be 16.04LTS.
4. For server side (Ubuntu Server), it is OpenSSH. For the Win Side clients, I use Putty. But my preference is to use a Linux box with a GUI as my Management console for my Linux Servers. SSH from a Linux Terminal such as Gnome Terminal or Byubo has a lot more to offer me. If you do go GUI for some reason, then you might want to think about installing Vino (ubuntu's default VNC server) and allow port 5900. On the Win side, use a VNC client compatible with Vino's TLS, such as SSVNC or RealVNC ... but be aware that theres some network load cost and lag in sharing screens... Just like with Remote Desktop... Also if-- disable Vino's encrption and tunnel through ssh.
5. The Ubuntu Server Guide... but on the Win side, Hyper-V... nothing special. I use Type I disk and everything installs and works fine. Make sure if you are doing ssh to have a domain policy or local policy to allow port 22 to be open on that server.

?VirtualBox? Win 2012 has Hyper-V as just turn it on as a feature... It's a Type I Hypervisor. VirtualBox is Hypervisor Type II. Type I is appropriate for hosting production virtual servers.

---

### Post by Bijal on 2016-01-14
Thanks Pappu,  It is a server install.  But because I am a beginner your reply does help.

Thanks for your response MAFoElffen,

It is well understood, precise and will definitely help.

---

