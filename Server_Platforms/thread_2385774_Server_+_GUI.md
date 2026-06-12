---
title: "Server + GUI"
date: 2018-02-24
forum: Server Platforms
---

### Post by glassonion on 2018-02-24
First - I'm new here.

Second - I've searched and tried and searched and tried and come up wanting. So I'll take the "How come you didn't use the search function" flames, and the newbie flames, and all that...I just want a problem solved. So what ever I have to take I'll take in exchange for learning.

In essence, I have a VPS server that I can install Ubuntu 14 minimal on. I wanted a bit of a gui as well. Yes I know, server + gui = for shame. Yet still that's what I would like to achieve. 

I read a tutorial and finally got xrdp and xfce running perfectly. So what's the problem you ask, well, I kind of wanted one of the nicer desktops like Unity or even Mate. But everytime I try to upgrade I must fudge something up because I have to start back over again from scratch.

Is there a tutorial I can go see, or is there someone that would take the time to help me through the command structures. I would like to have one of the more modern looking desktops like Unity or Mate + xrdp. 

Thanks and salutations to the kernel gods.

---

### Post by TheFu on 2018-02-24
Unity over remote desktop won't work well, if at all.  It wants a 3D GPU, which a remote desktop just doesn't support, especially something like VNC/RDP.

Don't use either VNC or RDP without a full VPN or ssh tunnel working first. It is a minimal security thing.

Mate should work, if you can get the keyboard mappings correct.

So ... let's start from the beginning with how I'd do it.
* I wouldn't use VNC/RDP. I'd use x2go, which is based on the NX protocol.
* Get ssh working between the client machine and the remote server.  Best to get ssh-keys working for authentication between the systems, since it is both more secure AND more convenient. How often does that happen?  Never, except for ssh.  I can't think of **any** other instance where something is both more convenient AND more secure.   ssh is the swiss-army-knife for system-to-system communications. With ssh, you get scp, sftp, ssh, and sshfs. Those are the quick things related to ssh, but there are 50 more, like rsync, most backup tools, a SOCKS PROXY, and reverse ssh, each of which is very, very, convenient.  When you install openssh, please also install fail2ban, so brute force attacks are contained.
* Install the x2go PPA on the remote server, then install the x2go-server there.
* Install the x2go PPA on the local client (I assume it is Linux/Ubuntu), then install the x2go-client there.
* Install the x2go fonts on the client-side.
* Using ssh to the server, install a minimal GUI - I'd go with LXDE or straight openbox to start.
* From the x2go-client, there's a GUI. Setup an LXDE connection to the server. Disable audio and printing, since those don't work well over the internet (ssh port forward is needed, I think).

Be happy.  BTW, x2go feels 2-3x faster than any VNC I've used.  I've used it from 5 continents back to my home desktop.  I've never used any fancy DE with it. It does have a KDE setting, but I don't know if it works or not.  There is a warning against using Unity or Gnome3.

Or you can try to make VNC/RDP to work. I'm sorry, that isn't a skill I have. Maybe someone else will answer the question soon?

If you can, I'd strongly suggest using 16.04, not 14.04.  Support for 14.04 ends next year and may have already ended for most of the GUI tools you'll want. GUI programs drop support much faster than CLI tools. Each flavor has a different support period, not necessarily 5 yrs.  When you mix your own, you are saying "I know that support for things varies wildly and I'll handle it."

No flaming. Just folks trying to help folks here.  I do hope you find this helpful.  Regardless, ssh is THE WAY.

---

### Post by glassonion on 2018-02-24
Thanks TheFu. I will set about taking what you've aid out here and seeing if I can replicate it successfully.

---

### Post by gordintoronto on 2018-02-25
If you are considering starting over from scratch, the simplest thing would be to install Ubuntu Mate, then add the server bits you want.

---

### Post by veddox on 2018-02-26
> If you are considering starting over from scratch, the simplest thing  would be to install Ubuntu Mate, then add the server bits you want.

I don't think I would do that. On a server, you don't want anything running that you don't *really* need - both for performance and security reasons. x2go really is the best option here, like TheFu said, even though you'll have to make do without the flashier desktop environments.

---

### Post by slickymaster on 2018-02-26
Thread moved to **Server Platforms** for a better fit

---

### Post by glassonion on 2018-03-01
Guys, I'm still working on this. I appreciate the input tho. I do not have a choice on what I can install on the VPS. All the options are "minimal". Which is good so I don't get a lot of stuff starting up that I don't need. 

This is not a mission critical appliance. This is more for learning.  Yeah, sure there might be other ways to learn, but hey this is the path I took.

I will hang around here and absorb as much knowledge as possible. As long as you guys don't mind the questions. I'm pretty self sustaining as far as research, but sometimes I get stuck, so I'll touch base back here. 

Thank you for your willingness to help out a noob.

---

### Post by LHammonds on 2018-03-02
FYI - You can install Oracle VirtualBox on your PC and run a virtual machine on your computer.  I do this on my Windows 10 PC to test out new operating systems or testing out new applications on top of operating systems (but I take a snapshot first so I revert back to a clean OS after I test out the app)

You can check my sig for some of my step-by-step tutorials on how I setup my production servers.

I can't really help you any with GUI stuff since I don't run a GUI on any of my servers nor do I have any interest in doing so.

LHammonds

---

