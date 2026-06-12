---
title: "Shell Access for a Research Project"
date: 2012-07-24
forum: The Cafe
---

### Post by ShareBuntu on 2012-07-24
Does anyone know of a service that provides shell access that I can use to analyse data for a scientific research project? I'll need to install one Perl module and one C library (the module is a wrapper for the library). One Python script is also included.

I would take the traditional route and perform the task through a university/research institution, but I'm not affiliated with anyone, so I'm a bit stuck. Unfortunately I can't leave my computer on for the duration of the task either.

If anyone knows of a way to facilitate this, I am happy to give you credit. The estimated time to process the data is a couple of days, but it could take closer to a week.

If you need specific information, please PM me and I'll be happy to explain more. Of course, all the code I will run is open source so that you can see what's going on. Thank you for your time!

---

### Post by mips on 2012-07-24
[http://docs.ocf.berkeley.edu/wiki/Services_we_provide#Unix_Shell_Account](http://docs.ocf.berkeley.edu/wiki/Services_we_provide#Unix_Shell_Account) Ask the staff, you never know.
[http://blinkenshell.org/wiki/Start](http://blinkenshell.org/wiki/Start)
[http://sdf.lonestar.org/index.cgi](http://sdf.lonestar.org/index.cgi)
[http://www-03.ibm.com/systems/z/os/linux/support/community.html#register](http://www-03.ibm.com/systems/z/os/linux/support/community.html#register)
[http://aruljohn.com/freeshell/](http://aruljohn.com/freeshell/)
[http://shells.red-pill.eu/](http://shells.red-pill.eu/)
[http://www.freelinuxconsole.info/portal/](http://www.freelinuxconsole.info/portal/)
[http://www.ixibo.com/list-of-free-linuxunix-shell-account-providers/](http://www.ixibo.com/list-of-free-linuxunix-shell-account-providers/)
[http://www.cyberciti.biz/tips/interactive-shell-access.html](http://www.cyberciti.biz/tips/interactive-shell-access.html)
[http://www.bylur.net/free/](http://www.bylur.net/free/)
[http://shellmix.com/](http://shellmix.com/)

---

### Post by ShareBuntu on 2012-07-24
> **mips said:**
> [http://docs.ocf.berkeley.edu/wiki/Services_we_provide#Unix_Shell_Account](http://docs.ocf.berkeley.edu/wiki/Services_we_provide#Unix_Shell_Account) Ask the staff, you never know.
[http://blinkenshell.org/wiki/Start](http://blinkenshell.org/wiki/Start)
[http://aruljohn.com/freeshell/](http://aruljohn.com/freeshell/)
[http://shells.red-pill.eu/](http://shells.red-pill.eu/)
[http://www.freelinuxconsole.info/portal/](http://www.freelinuxconsole.info/portal/)
[http://www.ixibo.com/list-of-free-linuxunix-shell-account-providers/](http://www.ixibo.com/list-of-free-linuxunix-shell-account-providers/)
[http://www.cyberciti.biz/tips/interactive-shell-access.html](http://www.cyberciti.biz/tips/interactive-shell-access.html)
These are great, thank you. I'll start making my way through them. The only thing I'm worried about is whether shell accounts like these will allow me to run CPU intensive processes for a few days.

---

### Post by mips on 2012-07-24
> **ShareBuntu said:**
> These are great, thank you. I'll start making my way through them. The only thing I'm worried about is whether shell accounts like these will allow me to run CPU intensive processes for a few days.

Just look at my post again as I've edited it with more links. try the IBM one, those guys have lots of horsepower.

EDIT: Which country are you in? Maybe we can get you access to a linux cluster.

---

### Post by codemaniac on 2012-07-24
I used to have an shell account at IBM's Z series mainframes running RHEL .
The Service provides with access to a Linux on System z environment for the purpose of providing the Open Source community with a platform to develop, port and/or test drive your products or applications on this platform.

---

### Post by codemaniac on 2012-07-24
> **mips said:**
> [http://docs.ocf.berkeley.edu/wiki/Services_we_provide#Unix_Shell_Account](http://docs.ocf.berkeley.edu/wiki/Services_we_provide#Unix_Shell_Account) Ask the staff, you never know.
[http://blinkenshell.org/wiki/Start](http://blinkenshell.org/wiki/Start)
[http://sdf.lonestar.org/index.cgi](http://sdf.lonestar.org/index.cgi)
[http://www-03.ibm.com/systems/z/os/linux/support/community.html#register](http://www-03.ibm.com/systems/z/os/linux/support/community.html#register)
[http://aruljohn.com/freeshell/](http://aruljohn.com/freeshell/)
[http://shells.red-pill.eu/](http://shells.red-pill.eu/)
[http://www.freelinuxconsole.info/portal/](http://www.freelinuxconsole.info/portal/)
[http://www.ixibo.com/list-of-free-linuxunix-shell-account-providers/](http://www.ixibo.com/list-of-free-linuxunix-shell-account-providers/)
[http://www.cyberciti.biz/tips/interactive-shell-access.html](http://www.cyberciti.biz/tips/interactive-shell-access.html)
[http://www.bylur.net/free/](http://www.bylur.net/free/)
[http://shellmix.com/](http://shellmix.com/)

mips , I am not sure if HP's test drive is still operational .

---

### Post by Grenage on 2012-07-24
> **ShareBuntu said:**
> If anyone knows of a way to facilitate this, I am happy to give you credit. The estimated time to process the data is a couple of days, but it could take closer to a week.

A week with what sort of processing power, and would remote access be an absolute requirement?

---

### Post by ShareBuntu on 2012-07-24
I've tested the processing scripts on a few data files and judged the time required to complete the task by that. The data files do vary though, from around 200b to 1mb in size. I have around 6.5 million comparisons to do and on both my core2 and i7 it completes around 300-400 comparisons in 20-30 seconds. So it's definitely a few days of processing.

The program to run is a Python script that calls a Perl wrapper for a suffix tree written in C (there is no Python wrapper for it). It's a bit ad hoc, but it gets the job done, and I don't think doing the whole thing from Perl will improve the speed much, since the Python part only takes a split second.

Remote access isn't an absolute requirement, as I can provide instructions on the libraries required and the instructions to run the script. I'm in Australia, so I don't know if that helps getting access to a Linux cluster somewhere? :-?

---

### Post by codemaniac on 2012-07-24
> **ShareBuntu said:**
> I've tested the processing scripts on a few data files and judged the time required to complete the task by that. The data files do vary though, from around 200b to 1mb in size. I have around 6.5 million comparisons to do and on both my core2 and i7 it completes around 300-400 comparisons in 20-30 seconds. So it's definitely a few days of processing.

The program to run is a Python script that calls a Perl wrapper for a suffix tree written in C (there is no Python wrapper for it). It's a bit ad hoc, but it gets the job done, and I don't think doing the whole thing from Perl will improve the speed much, since the Python part only takes a split second.

Remote access isn't an absolute requirement, as I can provide instructions on the libraries required and the instructions to run the script. I'm in Australia, so I don't know if that helps getting access to a Linux cluster somewhere? :-?

You can run your script on a remote server with screen or nohup , 

```
man screen
```

That way you dont need to be physically man the terminal .You can just log out from the remote server and the process will be running on background till it finishes .

---

### Post by Grenage on 2012-07-24
I have a quad 2800 (is the exec multicore-capable?) that I can make available, but there's no remote access, and it would obviously take longer than a few days.

The offer is there in the very unlikely event that you can't find something more suitable.

---

### Post by mips on 2012-07-24
> **ShareBuntu said:**
> I'm in Australia, so I don't know if that helps getting access to a Linux cluster somewhere? :-?

You should try contacting local universities, maybe they can help you out.

---

