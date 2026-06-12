---
title: "Remote Desktop to Ubuntu Server Questions"
date: 2010-12-25
forum: Server Platforms
---

### Post by aceofspades686 on 2010-12-25
**[SIZE="4"]Original Post Below this Section[/SIZE]**
After reading through the wall of text I initially posted, I realized it would be in my better interest to create a more succinct version of what I needed and what I was trying to accomplish.

**_Description_**
[INDENT]I currently have a file server setup for an organization that they need to access over the internet. While I currently have a quick fix in place, I need the ability for them to edit files located on this server, while setting some security measures in place as well as basic concurrency control. Some of the people that will be working with this are not tech savvy in the slightest, so the process needs to remain as simple as possible as far as connecting and editing the documents.[/INDENT]

**_Requirements_**
[INDENT][LIST=1]
[*]Since the server will need to be accessible over the internet, I will need an SSH tunnel in place for security reasons.
[*]Some sort of simple GUI will be needed for them to use.
[*]I wish to allow them to edit the files directly on the server (with backups being made daily) in order to eliminate the concurrency and security risks of them downloading the files to the client machine.
[/LIST][/INDENT]

**_Current Thoughts_**
[INDENT]Currently, I feel my best course of action would be VNC over SSH or similar.  This way, I could give them a simple shortcut to a script that would launch the SSH tunnel, launch the VNC client, and bring them to a functioning desktop where they can edit the files.

The problem lies in that, I have no idea how to set this up, and every tutorial I've run across either explains how to set up a simple xterm or to install the full ubuntu-desktop package.  I need something in the middle where the GUI will only run when they're connected to the server, and it will only have the programs they need.

The other problem is that, I have no experience installing Desktop Environments, so I'm not sure what individual packages would be needed.  I'm admittedly not 100% sure which DE I will be using for this, but I'm leaning towards Xfce.[/INDENT]

**Again, thank you for taking the time to read this, hopefully this makes my issues a bit more apparent.**


[SIZE="4"]**Original Post:**[/SIZE]

Hello everyone, long time reader, first time poster here, and I was wondering if I could get a little insight as to how to set something up.

Currently, I have an Ubuntu 10.10 server on my internal network.  It actually serves a variety of purposes, but for the sake of my question, its set up as a file server over the internet for a local group that I help administer.  These files (typically open office documents) need to be accessed regularly and edited/reviewed by various members of the organization.  The problem is that some of the members are not very tech savvy, so I have to make things as simple as possible for them to get to the documents, while still maintaining some semblance of security.

My current solution for this is to have them running Ubuntu virtual machines, that once they're signed in sshfs connects to the server using public/private key encryption and allows them to work on the documents from there.  This poses another problem however on the client side, because the computers running the virtual machines are somewhat older and not really best equipped to handle multiple operating systems at the same time.  They need Windows for work so trying to get them to switch to Ubuntu is out of the question.

I was thinking that my best course of action might be to set up VNC over SSH or something of the like, but I've never done anything like that before so I'm at a loss.  The biggest quandary I have with this method is that, if I were to do this I would want them to have a GUI (obviously, otherwise why would I use VNC? ;) ) but I don't want a GUI running at all times on my server.  I've searched around the internet, but none of the guides or howtos that I've found indicate that VNC is running on the server without the server either having the full ubuntu-desktop package installed or just an xterm, so if anyone could point me in the right direction on this, it would be much appreciated. (Note: I'm a noob when it comes to installing GUIs.  Typically I either have a desktop with a GUI or a server with CLI.  A machine with a primary CLI interface but GUI for some users is new to me.)

Also, I'm looking for suggestions as to which GUI to use.  I think Gnome or KDE would be a bit heavy, so I was looking into using XFCE, but I'm thinking that OpenBox or the like could be a viable alternative.  Once again, I've never set up anything like this before, so I'm not really familiar with the types of challenges that the various environments present.

Thanks in advance for your help.

---

### Post by Calimo on 2010-12-26
Hello,

I don't get the virtual machine thing. Why do you do that? Are your clients running windows? There are windows tools to "mount" a drive through SSH (such as DokanSSH), you don't need a virtual machine for that.

You may also use DAV or even just FTP if the files are public on your network, there's no need of encryption. Really, don't setup virtual machines just to connect to a file server ;)

---

### Post by aceofspades686 on 2010-12-26
Well, honestly the VM thing was just a temporary "quick fix" until I could get something more permanent in place.  The problem is that they don't need to download the files to their host machine because of security and concurrency issues.  Even though they could copy them from the VM to their host (or server to their host), the ones who know enough to figure this out are the same ones who will understand most why those rules are in place.

While the other suggestions would work, stupid me forgot to mention that they would be connecting to this server over the internet and some of the documents contain sensitive information.  That being the case, I would need the encrypted tunnel to allow them to work on these.  I'll be editing my first post to reflect that momentarily.

That's why I thought that VNC over SSH (or something similar, I'm open to suggestions) would be the better alternative.  Less client resources than a VM, less concurrency issues since they'll be editing the files directly on the server (before anyone asks, I keep automated daily backups in case something gets fubared), and they'll still be deterred from downloading the files directly to their host machine.

---

### Post by koenn on 2010-12-26
ordinarily, all you"d need is a samba server, i.e. a linux server that does  Windowscompatible file sharing - as if you'd be sharing those files from a Windows Server.
Doing samba over the internet is not only a bad idea security-wise, but it'll be too slow as well.

So, your idea of having users edit files locally (in a session on the server), is not a bad idea.

Here's an idea:
You have your users log on to the server, run applications there (file manager, (open)office suite, ...) but export the GUI of those apps back to their PC. Somewhat like a "remote desktop" but you only get the windows with the apps you need, not the entire desktop (If you're familiar with MS Terminal services, they have that too now, it's called "TS remote apps" or something)

Here's a [screenshot]("http://www.zen6478.zen.co.uk/image/cap7l.jpg") of some random linux apps running "on" a Windows desktop. 

To do something like this on a Windows client, you need to install an X server for Windows (eg Xming) on the clients.


Pros: you can run this through ssh for security, uou don't need a Desktop Environment on the server,  and you can probably pack the whole thing into a desktop shortcut command so your users won't know what's going on. 


your main problem is going to be speed -- internet is slow -- so I suggest you have a look at this and if it looks like an option, you can consider stuff like NX (which does essentially the same, but with compression and some other network optimization)

---

### Post by HermanAB on 2010-12-26
It sounds like you need webmin.

---

### Post by aceofspades686 on 2010-12-26
> **koenn said:**
> ordinarily, all you"d need is a samba server, i.e. a linux server that does  Windowscompatible file sharing - as if you'd be sharing those files from a Windows Server.
Doing samba over the internet is not only a bad idea security-wise, but it'll be too slow as well.
Right, if they were on my internal network, it would be this simple, but unfortunately they're scattered all over so I have to give them access via web.

> **koenn said:**
> 
So, your idea of having users edit files locally (in a session on the server), is not a bad idea.

Here's an idea:
You have your users log on to the server, run applications there (file manager, (open)office suite, ...) but export the GUI of those apps back to their PC. Somewhat like a "remote desktop" but you only get the windows with the apps you need, not the entire desktop (If you're familiar with MS Terminal services, they have that too now, it's called "TS remote apps" or something)

Here's a [screenshot]("http://www.zen6478.zen.co.uk/image/cap7l.jpg") of some random linux apps running "on" a Windows desktop. 

To do something like this on a Windows client, you need to install an X server for Windows (eg Xming) on the clients.


Pros: you can run this through ssh for security, uou don't need a Desktop Environment on the server,  and you can probably pack the whole thing into a desktop shortcut command so your users won't know what's going on. 


your main problem is going to be speed -- internet is slow -- so I suggest you have a look at this and if it looks like an option, you can consider stuff like NX (which does essentially the same, but with compression and some other network optimization)
I'm sort of looking at remoting the individual applications, my only concern with that would be going back to them trying to save to their local machine.  I know I can't 100% keep them from it since I'm not the admin for their computers, but any deterrent to do so is a plus, otherwise things could get a little crazy.

I had sort of glanced at NX before, but I wasn't sure about its security  (just now saw that it uses SSH tunnels to communicate) so I'll be looking into it a bit more.

> **HermanAB said:**
> It sounds like you need webmin.

I'm somewhat familiar with webmin, but I'm not entirely sure how it would help my situation.  Granted I'm not a webmin guru by any means, so maybe there's some feature I missed.  Care to elaborate a little?

---

### Post by koenn on 2010-12-26
> **aceofspades686 said:**
> 
I'm sort of looking at remoting the individual applications, my only concern with that would be going back to them trying to save to their local machine. 
That shouldn't be a problem - the remote apps would only be aware of the server, so one wouldn't be able to let them save anything to the user's machine.

Have you ever used putty to access a linux machine from a windows pc ? 
(if you haven't, now would be a good time)
what it does is:
you run  a linux shell on a linux machine, but the output is shown in a window on your windows desktop. If you run "ls" in that session, what you see is files and directories on the server.

Likewise, with "remote apps" (or X forwarding, etc), you'd run, say, OOo Writer on a server, but the output is shown in a window on your desktop PC. Still, that OOo Writer only knows files and directories on the server.

---

### Post by aceofspades686 on 2010-12-26
> **koenn said:**
> That shouldn't be a problem - the remote apps would only be aware of the server, so one wouldn't be able to let them save anything to the user's machine.

Have you ever used putty to access a linux machine from a windows pc ? 
(if you haven't, now would be a good time)
what it does is:
you run  a linux shell on a linux machine, but the output is shown in a window on your windows desktop. If you run "ls" in that session, what you see is files and directories on the server.

Likewise, with "remote apps" (or X forwarding, etc), you'd run, say, OOo Writer on a server, but the output is shown in a window on your desktop PC. Still, that OOo Writer only knows files and directories on the server.
Okay, that's one of the things I wasn't sure of, I have used Putty before, but I wasn't sure if X11 forwarding acted in the same way never having had a need for it before.  Thanks for all the advice, I'm looking around at a few of the options mentioned so I think I can get it worked out now.

---

### Post by koenn on 2010-12-26
yeah, just play around a bit to get a feel for it all, then develop/design a solution for the actual problem.

Have fun.

---

