---
title: "Which virtualization is right for me?"
date: 2009-07-08
forum: Virtualisation
---

### Post by shasan on 2009-07-08
Hello! I hate to ask a question like this on a public forum, but I hope that someone with actual experience in this area will be able to advise me well. I have spent a significant amount of time investigating this and searching on my own, but I am still a bit confused about virtualization options available for Ubuntu.

So. I'm currently running Vista and I'm kind of sick of having to run Windows as my primary OS. So, I'm planning my switch back to Linux. For various reasons, I need access to specific Windows-only apps, and I have determined that Wine will not suffice for me (please trust me on this point). I am looking for a virtualization solution that will meet the following requirements:

[LIST]
[*]Run Vista Ultimate or Win7 seamlessly within an Ubuntu host desktop (a la Parallels Coherence in OSX)
[*]Fully support (in virtualized Windows) my tablet PC's pen input (in particular: I need to be able to run OneNote as though I were using Windows).
[*]Be able to seamlessly access files from applications on both the Ubuntu host and Windows guest
[*]Be able to run as many Windows applications concurrently as desired (heard this was a limitation with some VM's)
[*]Full access from Windows to all hardware resources on laptop (i.e., USB ports, network, sound (in and out). No graphics card so no worries about that! :) )
[/LIST]

The following would be nice:
[LIST]
[*]Support for displaying both Ubuntu host and Windows guest applications on multiple monitors
[*]Free as in speech.
[*]Free as in beer (though I absolutely do not mind shelling out cash if a proprietary solution works best).
[*]Oh yeah, should Just Work out of the (apt-get) box.
[/LIST]

Currently, I believe VirtualBox meets these requirements best, though I haven't seen anything about tablet support. I haven't been able to find too much about Parallels or VMWare as it relates to my specific requirements. 

Even if you can't provide a 100% answer, I'd appreciate any advice you all had. I'm doing all this on a fresh hard drive so I don't have a problem trying a few times to get it working.

---

### Post by .nedberg on 2009-07-08
I'd give VirtualBox a try!

Don't use the version in Synaptic, it is without USB support. Get the PUEL version from [virtualbox.org]("http://www.virtualbox.org/wiki/Linux_Downloads"). You can add a repository.

If it doesn't meet your requirements then I would suggest you get VMServer/Workstation.

Also, if you haven't already, have a look at the [Virtualization Mega thread]("http://ubuntuforums.org/showthread.php?t=973756").

---

### Post by mytechguru on 2009-07-08
VM Workstation or Java Virtual Box will suite to your need.

---

### Post by Murdock on 2009-07-08
> **.nedberg said:**
> 
Don't use the version in Synaptic, it is without USB support.

Your thinking of the OSE version i guess?

If you add virtualbox to you apt sources and then install virtualbox-3.0 or older thats not OSE and get usb support

there is an step by step guide here
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by .nedberg on 2009-07-08
> **Murdock said:**
> Your thinking of the OSE version i guess?

If you add virtualbox to you apt sources and then install virtualbox-3.0 or older thats not OSE and get usb support

there is an step by step guide here
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Right indeed! OSE version is in the standard repositories, without USB support. PUEL can be downloaded or installed from third party repository, with everything you need.

---

### Post by shasan on 2009-07-08
Thank you for your replies! I'm hoping someone will be able to chime in re: tablet support. :)

Also, how is support for Win7 in VirtualBox and VMWare? I've realized the only Windows media I have access to currently is the Win7 RC. Is performance improved/degraded if I install Windows to its own partition and run the VM from that? Is that recommended? I understand doing that would allow me to dual-boot into Windows if I needed to do so for whatever reason. 

Again, thanks much for your help. Always impressed by how generous with advice these forums are.

---

