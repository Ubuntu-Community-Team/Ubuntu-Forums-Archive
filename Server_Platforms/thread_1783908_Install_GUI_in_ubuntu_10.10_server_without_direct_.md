---
title: "Install GUI in ubuntu 10.10 server without direct internet access?"
date: 2011-06-16
forum: Server Platforms
---

### Post by Mohiit1502 on 2011-06-16
Hi everyone..
My very first post so I'm expecting a lot.

Prob.: I'm using ubuntu 10.10 server with no GUI, no network, very minimal packages installed(network manager, rpm, wvdial, perhaps drivers for my mobile, gedit, firefox etc. all are absent), and very less knowledge of the terminal.

Sources available to use: 1) Dual booted windows with access to n/w to download files
2) Ubuntu 9.10 liveCD with Desktop
3) Ubuntu 10.10 server liveCD
4) Access to downloaded files on windows drives

I'm accessing internet via my 3g enabled mobile which was easily discovered on ubuntu 9.10 but not here :(

Things that I've tried: 1) sudo pppconfig(not sure which port my mobile is connected to, tried all ports but failure, perhaps drivers issue)
2) Downloaded wvdial, scanModem, rpm in windows(all .tar.gz-->another issue), tried to extract but errors, dpkg won't work.
3) Extracted the files using windows' winrar, but not sure what to do of the extracted folder(that's why I'm trying rpm which is also not installed)

My questions are: 1) Can I install ubuntu 9.10 gnome using liveCD into server?
2) How to install drivers for my mobile(Sony Ericsson j20i)/where can I find them?
3) How to extract and install .tar.gz and other packages manually after they are downloaded?

Please ask for any other information/logs if needed. Awaiting a kind and a wise response.

Regards.

---

### Post by sanderd17 on 2011-06-16
Can you read this: [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

Does it help? What do you exactly want to achieve?

---

### Post by arrrghhh on 2011-06-16
If you want a GUI (a full-fledged Desktop Environment (DE)) then install ubuntu-desktop **(not the package!!!)**

Do not install ubuntu-server then do an apt-get install ubuntu-desktop.  Just simply burn an ubuntu-desktop disc and install that... You can run all the same services in the desktop edition, and you get a full GUI.

To me that seems best.  If you're going to be using a phone to tether with, the server route seems pointless (to me).  Is there a reason you choose server over desktop?

---

### Post by Mohiit1502 on 2011-06-16
Thanks for the reply sanderd17
> **sanderd17 said:**
> Can you read this: [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)
The reference was quite helpful with some new commands for me(apt-offline) but I do not have the Desktop package in my liveCD itself, because it is a server CD.

> Does it help? What do you exactly want to achieve?
First of all I need a working internet connection, for that I need some packages(wvdial etc.), and ultimately I need to install and work on oracle which I've installed on karmic once, using some article, and from that experience I know that I'll be needing GUI for a number of trials and errors.

Why I'm not working on Karmic itself? Just want to know more ;)

---

### Post by Mohiit1502 on 2011-06-16
Thanks arrrghhh for the reply
> **arrrghhh said:**
> If you want a GUI (a full-fledged Desktop Environment (DE)) then install ubuntu-desktop **(not the package!!!)**
I can't do that because I'm working offline, without GUI and there's no desktop on the liveCD as I've already mentioned.

> Do not install ubuntu-server then do an apt-get install ubuntu-desktop.  Just simply burn an ubuntu-desktop disc and install that... You can run all the same services in the desktop edition, and you get a full GUI.
I agree that there's no diff. b/w desktop and server edition in terms of services but I'm just looking to try server edition and converting it to desktop. Seems easy as far as other articles say but is not going that easy for me.
> 
Is there a reason you choose server over desktop?
No special reason.

---

### Post by arrrghhh on 2011-06-16
> **Mohiit1502 said:**
> Thanks arrrghhh for the reply

I can't do that because I'm working offline, without GUI and there's no desktop on the liveCD as I've already mentioned.


[B]I agree that there's no diff. b/w desktop and server edition in terms of services but I'm just looking to try server edition and converting it to desktop. Seems easy as far as other articles say but is not going that easy for me.
[/B]
No special reason.

Do **not** "convert" the server edition to the desktop edition.  If you want the desktop edition, install the desktop edition.  It's not easy, and you usually end up with a complete mess.  If you just install the desktop edition from the start, then you'll be much, much happier.

If you have no reason for choosing the server edition, and you want a desktop environment, then there's no point in installing the server edition.  You're basically creating a lot of work and headache, and again trying to fit a square peg into a round hole never does quite work right :p.

---

### Post by HarriU11-04 on 2011-08-23
> **arrrghhh said:**
> Do **not** "convert" the server edition to the desktop edition.  If you want the desktop edition, install the desktop edition.  It's not easy, and you usually end up with a complete mess.  If you just install the desktop edition from the start, then you'll be much, much happier.

If you have no reason for choosing the server edition, and you want a desktop environment, then there's no point in installing the server edition.  You're basically creating a lot of work and headache, and again trying to fit a square peg into a round hole never does quite work right :p.
Hello

I want to do something very similar to Mohiit, but maybe my justification is a little better thought out. Basically, I want linux OS as a base (preferably Ubuntu since thats what I'm familiar with), running squid and Dansguardian, and a vmware image of my Windows XP machine. Since I hope to continue using windows media player/browser/etc, I do not need these applications in Ubuntu, also I want as much resources, ie memory, to go to the Windows virtual machine. So I thought to install the Server edition as a minimal installation, add GUI (for vmware), the apps I need (already know how to install and configure them).

My sticking point is without network-manager and the gui, I cant get any further

---

### Post by arrrghhh on 2011-08-23
> **HarriU11-04 said:**
> Hello

I want to do something very similar to Mohiit, but maybe my justification is a little better thought out. Basically, I want linux OS as a base (preferably Ubuntu since thats what I'm familiar with), running squid and Dansguardian, and a vmware image of my Windows XP machine. Since I hope to continue using windows media player/browser/etc, I do not need these applications in Ubuntu, also I want as much resources, ie memory, to go to the Windows virtual machine. So I thought to install the Server edition as a minimal installation, add GUI (for vmware), the apps I need (already know how to install and configure them).

My sticking point is without network-manager and the gui, I cant get any further

You still don't need a GUI.

I run VBoxHeadless and RDP into the XP VM.  Works fantastically, and I don't need to put a GUI on my Ubuntu Server.

Don't try to fit a round peg into a square hole.

---

### Post by HarriU11-04 on 2011-08-24
> **arrrghhh said:**
> You still don't need a GUI.

I run VBoxHeadless and RDP into the XP VM.  Works fantastically, and I don't need to put a GUI on my Ubuntu Server.

Don't try to fit a round peg into a square hole.
I try to use the technology I know how to use to solve the problem(s) I have. Since you have found a way to do it, why dont you share the details with us not so familiar/comfortable ubuntu converts????

Please bear in mind that the more detailed your instructions are, it will cut down on confusion and requests for clarification. :)

P.S. - How the heck do you run a VMware virtual machine without the virtual display and GUI required? Just to setup VMware a new machine you need to point-n-click. (Notice I did NOT say "install Vmware"). Do you edit the .vmx file to remove the virtual display??? My head is curious now....

However its done, I dont think your solution will workfor my scenario - what if the "server" is virtual and running on the same machine a user RDP's from? You could just bypass the filter on the server.

---

### Post by arrrghhh on 2011-08-24
> **HarriU11-04 said:**
> I try to use the technology I know how to use to solve the problem(s) I have. Since you have found a way to do it, why dont you share the details with us not so familiar/comfortable ubuntu converts????

Please bear in mind that the more detailed your instructions are, it will cut down on confusion and requests for clarification. :)

P.S. - How the heck do you run a VMware virtual machine without the virtual display and GUI required? Just to setup VMware a new machine you need to point-n-click. (Notice I did NOT say "install Vmware"). Do you edit the .vmx file to remove the virtual display??? My head is curious now....

I don't use VMWare, I use VirtualBox.

It has a program, VBoxHeadless, that allows you to run a virtual machine in a completely headless manner.  Then using another computer on your network, you RDP to the server (assuming you have vRDP enabled in VirtualBox, not available on the OSE edition last time I checked) and voila.  Headless VM.

Now setting up the initial VM, I will admit was much easier with a GUI.  I just forward X over SSH.  Works quite well - the method is different depending on the client.  I use putty & xmming on Windows.  On Linux, it's quite easy, you just ssh -X into the box, and anything that requires X11 will just pop up on your screen!

Obviously if you are doing this all on a local install (IE you have a monitor hooked up to your server) then I'd say the server install is not for you.  Go for Desktop.  If you want a DE, that's the easiest and by far the best route to get a full blown DE.  Shoe-horning a DE onto the server edition is possible, but I wouldn't recommend it.  Most people run their servers in a 'headless' fashion, IE no monitor or keyboard hooked up to the server, everything is managed remotely.  This is how my server is utilized, and AFAIK this is how most servers are setup/used.

---

### Post by HarriU11-04 on 2011-08-25
Ok. Thanks for your detailed response. I have indeed gone for a DE environment. I did look at a Virtual Appliance that did exactly what I wanted, but my issue there was how to force users to use it.

---

