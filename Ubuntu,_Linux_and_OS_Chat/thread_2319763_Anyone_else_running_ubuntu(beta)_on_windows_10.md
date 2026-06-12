---
title: "Anyone else running ubuntu(beta) on windows 10?"
date: 2016-04-07
forum: Ubuntu, Linux and OS Chat
---

### Post by neoh2 on 2016-04-07
Sorry, I know there's another thread on this, it just seems like it's more about the concept of it rather than the practical, but admins: I have faith you'll merge if necessary :-D

I just got bash shell on windows 10 up and running this morning and wondering what everyone else thinks/any tips? It feels weird even being back in windows these days tbh. So far I'm missing a couple of shortcuts like ctrl-a, workspaces, and quite a few of my goto terminal tools don't work (htop, etc), but over all I'm impressed how much stuff is there given Microsoft are posting it as "bash"

My one tip so far is that you can get around the lack of workspaces by opening multiple "bash" windows (root user is active by default, which I found unexpected for ubuntu) and the changes you make in one are instant in another. One interesting quirk is that you can run the same program - even something like apt or dpkg- in multiple windows as the same user, as see the effects instantly in the other windows; one of the first test I did was start up two windows, install ninvaders in one window and see if the other 'knew' about it yet. Final part of that tip is use with caution, I quickly got told off by dpkg for interrupting it lol

---

### Post by Bucky Ball on 2016-04-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

It's unclear what you are talking about here as you never explicitly say. Are you talking about a bash shell in Windows 10? Please clarify. Thanks.

---

### Post by neoh2 on 2016-04-07
Thanks, I edited it... is that any clearer?

---

### Post by Bucky Ball on 2016-04-07
Yes, thanks.

---

### Post by buzzingrobot on 2016-04-07
Well, I'm not a web developer who also needs to use and write for open source on the back end, so I'm not the target for any of this. 

If I was a web developer, I suppose I'd buy a Mac and get on with things, like so many already have. (Unless I was a *corporate* web developer and had no choice but to have Windows on my desk.  Then I'd jump for this.)

---

### Post by grahammechanical on 2016-04-07
> root user is active by default, which I found unexpected for ubuntu

You should not be surprised

> So as part of the engineering work, I needed to wrap the stock Ubuntu [root filesystem]("http://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-root.tar.gz") into a Windows application package (.appx) file for suitable upload to the Windows Store.

[http://blog.dustinkirkland.com/2016/03/ubuntu-on-windows.html](http://blog.dustinkirkland.com/2016/03/ubuntu-on-windows.html)

The latest HowTo from Dustin Kirkland

[http://blog.dustinkirkland.com/2016/04/howto-ubuntu-on-windows.html](http://blog.dustinkirkland.com/2016/04/howto-ubuntu-on-windows.html)

Regards.

---

### Post by Dragonbite on 2016-04-07
I'm interested in this because I do handle an external non-Microsoft web server and run Microsoft Windows in the office.

At the very least, I hope to be able to remove PuTTY (ssh) and WinSCP (scp).

Unfortunately there are no plans to jump to Windows 10 at this point (we're running Windows 7 thin clients on VMWare) so I don't know when I'll be able to check it out.  Maybe by the time we move up it will be out of beta.

---

### Post by Rocky_Bennett on 2016-04-07
Yes, I have been running Ubuntu 14.04 LTS within my Windows 10 for a couple of days. Right now I am still playing with it, but if I just go to the START icon on the bottom of my Windows 10 screen and type in Ubuntu, it will open up the BASH screen. It was very tricky to enable this feature, but I can help anybody that wants to try it.

After you install Ubuntu within Windows 10, update and then use the dist-upgrade command in order to download all of the features.

---

### Post by qamelian on 2016-04-07
The Windows 10 equivalent of workspaces is "virtual desktops".
[TABLE]
[TR]
[TD]Windows + Ctrl + D
[/TD]
[TD] Create new virtual desktop[/TD]
[/TR]
[TR]
[TD] Windows + Ctrl + F4
[/TD]
[TD] Close current virtual desktop[/TD]
[/TR]
[TR]
[TD] Windows + Ctrl + [Left][Right]
[/TD]
[TD] Switch between virtual desktops
[/TD]
[/TR]
[/TABLE]

---

### Post by Rocky_Bennett on 2016-04-07
> **qamelian said:**
> The Windows 10 equivalent of workspaces is "virtual desktops".
[TABLE]
[TR]
[TD]Windows + Ctrl + D[/TD]
[TD] Create new virtual desktop[/TD]
[/TR]
[TR]
[TD] Windows + Ctrl + F4[/TD]
[TD] Close current virtual desktop[/TD]
[/TR]
[TR]
[TD] Windows + Ctrl + [Left][Right][/TD]
[TD] Switch between virtual desktops[/TD]
[/TR]
[/TABLE]




I think that you are in the wrong thread.

---

### Post by qamelian on 2016-04-07
> **Rocky_Bennett said:**
> I think that you are in the wrong thread.

I don't think so. I was commenting on the OP's remark about the lack of workspaces in Windows 10 in his initial post.

---

### Post by Rocky_Bennett on 2016-04-08
OK, I see. Thanks. So far there is no practical use of this Ubuntu program in Windows 10, it seems to be pointless.

---

### Post by Dragonbite on 2016-04-08
> **Rocky_Bennett said:**
> Yes, I have been running Ubuntu 14.04 LTS within my Windows 10 for a couple of days. Right now I am still playing with it, but if I just go to the START icon on the bottom of my Windows 10 screen and type in Ubuntu, it will open up the BASH screen. It was very tricky to enable this feature, but I can help anybody that wants to try it.

After you install Ubuntu within Windows 10, update and then use the dist-upgrade command in order to download all of the features.

Do you have it documented somewhere?

Is it only the test/preview version of Windows 10 or can this be added to regular Windows 10?

---

### Post by grahammechanical on 2016-04-08
Is this what you are looking for?

[http://blog.dustinkirkland.com/2016/04/howto-ubuntu-on-windows.html](http://blog.dustinkirkland.com/2016/04/howto-ubuntu-on-windows.html)

Regards

---

### Post by sammiev on 2016-04-08
> **grahammechanical said:**
> Is this what you are looking for?

[http://blog.dustinkirkland.com/2016/04/howto-ubuntu-on-windows.html](http://blog.dustinkirkland.com/2016/04/howto-ubuntu-on-windows.html)

Regards

Thanks

---

### Post by SeijiSensei on 2016-04-08
> **Dragonbite said:**
> I'm interested in this because I do handle an external non-Microsoft web server and run Microsoft Windows in the office.

Unfortunately there are no plans to jump to Windows 10 at this point (we're running Windows 7 thin clients on VMWare) so I don't know when I'll be able to check it out.
You could run an Ubuntu virtual machine inside a VirtualBox session, but since you're on a thin client, I'm guessing you cannot install software.  I much prefer having a full Ubuntu VM to running Putty.

---

### Post by Dragonbite on 2016-04-08
> **SeijiSensei said:**
> You could run an Ubuntu virtual machine inside a VirtualBox session, but since you're on a thin client, I'm guessing you cannot install software.  I much prefer having a full Ubuntu VM to running Putty.

I've got full Admin rights, but they don't give us much room for space.  Our profile and files are stored elsewhere so the space for applications is constrained.

I do have 2.78GB free, so depending on where I put the Ubuntu image ... hmm...

---

### Post by Rocky_Bennett on 2016-04-08
> **Dragonbite said:**
> Do you have it documented somewhere?

Is it only the test/preview version of Windows 10 or can this be added to regular Windows 10?



Do I have what documented somewhere? I am a Windows 10 beta tester and I belong to a Windows 10 beta test group. A lot of us are running this and it is well documented in the media.

---

### Post by slickymaster on 2016-04-08
> **Dragonbite said:**
> Do you have it documented somewhere?

Is it only the test/preview version of Windows 10 or can this be added to regular Windows 10?

See this: [https://msdn.microsoft.com/en-us/commandline/wsl/install_guide](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide)

---

### Post by Rocky_Bennett on 2016-04-08
Is anybody else here running this app? This morning I tried to install Thunderbird as an experiment by using the command 

apt-get install thunderbird

on BASH in Windows 10. I sat here and watched the BASH find and connect to my local Ubuntu mirror, I watched as it downloaded and unpacked and installed Thunderbird. But after the whole thing (about 5 minutes) I can not find Thunderbird on my Windows 10 installation. 

What's up?

---

### Post by montag dp on 2016-04-08
> **Rocky_Bennett said:**
> Is anybody else here running this app? This morning I tried to install Thunderbird as an experiment by using the command 

apt-get install thunderbird

on BASH in Windows 10. I sat here and watched the BASH find and connect to my local Ubuntu mirror, I watched as it downloaded and unpacked and installed Thunderbird. But after the whole thing (about 5 minutes) I can not find Thunderbird on my Windows 10 installation. 

What's up?I'm confused about why you are trying to do that.  It's not a meant to be a full Ubuntu installation.  Only command line applications are supported.  Out of curiosity, what happens when you try to run thunderbird from the bash terminal?

---

### Post by Rocky_Bennett on 2016-04-08
Right now I am just playing with this app and I am trying all kinds of commands. I have not tried to run an app within BASH, I might try that next.

---

### Post by grahammechanical on 2016-04-08
On the desktop Thunderbird executable is in /usr/lib/

Regards.

---

### Post by Rocky_Bennett on 2016-04-09
Thanks. When ever I get a chance to log into my Windows 10 installation I will give this a go. I will probably be using my Linux all weekend.

---

