---
title: "xrdp and virtualbox - missing something simple I'm sure"
date: 2012-03-22
forum: Server Platforms
---

### Post by stormi on 2012-03-22
Hello,  I'm trying to troubleshoot (what I think is likely) a simple issue.

I have a physical server, running Ubuntu Server 10.04 LTS.
Yes, it has a GUI installed on it, I found managing VirtualBox to be easier to manage with some of the graphical tools at my fingertips.

I have a virtual guest running on VirtualBox that also runs Ubuntu Server 10.04 LTS

When I start virtualbox using VBoxHeadless --startvm "webserver-vb"
it also starts listening to RDP incoming requests on the the RDP port 3389 of the host.

This is good, but... 

What's not good is that sometimes when I'm not home to setup the virtualbox session (haven't had time to script it properly, and still have to troubleshoot the module not being compiled for my kernel version and having to recompile it every time the server is rebooted issue), and can't start the webserver without the GUI.  I live in a small town where the power is out longer than my UPS can manage, and am often away to work. 

*Note: I know this isn't strictly ideal, but finding that the CLI was no longer useful after launching the above command, I found it easier in the short term to launch the GUI, open a terminal there, then I could leave it running, but still retain full control of the rest of the OS.  Doing this in an RDP session is preferable to doing it in an SSH session remotely, because killing the SSH session stops the virtual machine.  This is undesirable to say the least, and is on my list of stuff to troubleshoot.  It's a long list, but when I built it a year ago, the server needed to be up in 2 weeks, I didn't have time to transfer all of my knowledge from an RPM based distro to Ubuntu AND troubleshoot all of the "small stuff".  Now the small stuff is becoming more and more of an issue. *:lolflag:

So I installed xvnc hoping to get access to the host system, so I can run the GUI and start Virtualbox.  

After successful install, when I RDP to the host's IP, I get the guest OS.  

So, I think most things are working correctly, I just need to get to the host, not the guest.  I'm thinking this is just a configuration file change, or having to specify a port in the RDP client.  I just haven't hit on the correct search terms yet to find my answer.  

Will someone please point me in the right direction?

---

### Post by CharlesA on 2012-03-22
Check out screen.

I run virtualbox headless on an install of Lucid server.

Running this: ```
VBoxHeadless --startvm "webserver-vb"
```

Starts the VM in the foreground instead of the background.

```
VBoxHeadless --startvm "webserver-vb" &
```

Run that ^ instead.

Either that or just use:

```
vboxmanage startvm virtualmachine --type headless
```

---

### Post by stormi on 2012-03-22
Well... it looks like I was going the hard way around things!  Thanks Charles for the gentle nudge rather than calling my logic out! :) 

So, if I read the screen documentation right, I should be able to ssh to the host, use screen, start VBoxheadless in the background and detach the screen? This way, when I'm not at the house, I can still do the admin I need to via ssh, then disconnect my ssh session and not have to worry about processes stopping, and virtual guests being shut down ungracefully?  Until I manage to script all of this of course.

I do remember using the & at one point, I'm not sure anymore why I lost it, and the last command looks familiar, I can't recall why I dumped it for the VBoxHeadless.  I obviously didn't spend enough time working out whatever was giving me issues with it.

---

### Post by CharlesA on 2012-03-22
> **stormi said:**
> 
So, if I read the screen documentation right, I should be able to ssh to the host, use screen, start VBoxheadless in the background and detach the screen? This way, when I'm not at the house, I can still do the admin I need to via ssh, then disconnect my ssh session and not have to worry about processes stopping, and virtual guests being shut down ungracefully?  Until I manage to script all of this of course.

That's pretty much how it works. As long as you detach your screen session before closing SSH, the VMs will still be running.

> I do remember using the & at one point, I'm not sure anymore why I lost it, and the last command looks familiar, I can't recall why I dumped it for the VBoxHeadless.  I obviously didn't spend enough time working out whatever was giving me issues with it.

I prefer using vboxmanage, myself, but that might be due to having issues chaining commands together when I had to run vboxheadless in the background (by adding & at the end).

Check out the script here:
[http://charlesa.net/scripts/linux/vboxscript.php](http://charlesa.net/scripts/linux/vboxscript.php)

---

### Post by stormi on 2012-03-22
Wow Charles!  Thank you so much.   I'm kind of glad I  didn't find a quick solution to my original query.  I would never have happened upon you!! 

I will be looking pretty hard at that script that you and doas777 were working on.  It looks a lot nicer than anything I would have written and will save me immense amounts of time.  

It looks like doas777 was trying to do the exact same thing as I am, so I expect to be learning a lot right away here.

---

### Post by CharlesA on 2012-03-22
Yeah, doas777 did a lot of work to get the script as user friendly as possible. The version I'm using was written to do what I needed it to do, without much flexibility to do other things.

---

