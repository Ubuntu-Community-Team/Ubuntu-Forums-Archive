---
title: "Server 2008 Hyper-V - any way to boost network?"
date: 2008-11-10
forum: Virtualisation
---

### Post by jimwillsher on 2008-11-10
I've migrated my dedicated Intrepid LAMP server to a new VM in Hyper-V (Windows Server 2008 was on new tin, the LAMP was on old kit). Everything works like a dream...except for poor network performance. I'm having to use a "Legacy network adaptor" in Hyper-V as Hyper-V now uses some form of Synthetic adapter, and Hyper-V's Integration Components are not available for Ubuntu.

Has anyone any experience of improving the network performance, or possibly getting Intrepid ibex to recognise Hyper-V's Synthetic NIC?

Many thanks,


Jim

---

### Post by mmesh on 2008-12-16
> **jimwillsher said:**
> I've migrated my dedicated Intrepid LAMP server to a new VM in Hyper-V... 

Hello Jim!

I just recently installed W2K8 with Hyper-V on my home server machine and I'm thinking of installing ubuntu LAMP server to VM in Hyper-V.
I'm doing research just now of how to do it and if it is even possible...

Can You share Your hardware configuration (number of NICs and there settings in particular) and write something if You managed to solve poor network performance.

Thank You.

---

### Post by jimwillsher on 2008-12-16
Hi,

yes it's definitely possible. I've been running my live webserver in this configuration since making the posting.

Installation is  straightforward, you don't need to do anything except remove the NIC and add a legacy NIC. One optional thing that I've done is NOT set up a virtual network; instead I just share the W2K8's NIC but with a dedicated IP address.

I'm using only one NIC in Ubuntu but I've installed the amd64 release and I've assigned two cores to the VM.

Network performance is still only 100mb/s, not 1000mb/s, but I can live with that.

Hope this helps.


Jim

---

### Post by mmesh on 2008-12-16
Wow!
That was fast! :)

Thank You for the prompt reply...
It's great that there aren't any complications with the installation.
I'll just have to give it a go then.

One thing before I do that: You say > remove the NIC and add a legacy NIC
You mean physically remove from machine or do You mean from software configuration?

And... When I install LAMP server in Hyper-V I'll probably have more questions, so thank You once more in advance. ;)

---

### Post by jimwillsher on 2008-12-16
If you go into the options on the VM you'll see a network card. Remove it, then add a new hardware item called Legacy network adapter.

If you don't, Ubuntu won't find any NICs during the install.

Oh, and don't be put off by the incredibly slow screen-refreshes during the Ubuntu installation. Once it's up an running and you've got SSH access you'll be back to normal speed.


Jim

---

### Post by matthew.mattoon on 2009-05-14
Hi Jim,

This is a fairly old post however I just completed a step-by-step guide to installation of the Linux Integration Components for Hyper-V on Ubuntu and Debian.  This will upgrade your Storage devices as well as your network devices.  It works great.  If you are interested the article can be found at my blog.  [http://blog.allanglesit.com](http://blog.allanglesit.com)

-matt

---

### Post by jimwillsher on 2009-05-15
Hmmm....looks a bit scarey to me. I'd be happy to try it out, and probably will do so on a spare VM, but I'm a bit put off if I'm then tied to a specific kernel version.

But well done for doing it, and especially thanks for posting a follow-up to my original question.


Jim

---

### Post by digg1980 on 2009-09-05
A great guide which show a step by step how to boost your Linux performance on Hyper-V including the Network adapter with snapshot of each step can be found on **[Installing Linux & IC on Hyper-V ]("http://www.virtualizationteam.com/microsoft/hyper-v/install-suse-linux-enterprise-10-sp1-component-integration-for-linux-on-hyper-v.html")**

That article should be of a great help to any one trying to install Linux on Hyper-V & trying to get it well. Although the article is going the steps for SUSE as that the only supported Linux on Hyper-V, the instruction should work for most other Linux distros though might require a small difference in how you re-compile your own Linux distro.

I hope that help you as it helped me earlier :).

---

### Post by matthew.mattoon on 2010-05-29
Hi Jim,

Here is a much simpler instruction set.

[http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx](http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx)


Also to clarify what digg1980 has said...

"Although the article is going the steps for SUSE as that the only  supported Linux on Hyper-V, the instruction should work for most other  Linux distros though might require a small difference in how you  re-compile your own Linux distro."

Part of this statement is old information, and part is just wrong.  SUSE  is no longer the only supported distro (though it was at the time of  digg1980's comment).  The second part of his statement that the  instructions should work for most other Linux distributions, this is  just wrong.  The installation of the Linux ICs is very different based  on your distribution, in order to get them working you have to get  prerequisite packages installed, kernel version at the correct level,  install the modules, and configure them to start at boot.  All of these  steps are different depending on Ubuntu vs Fedora vs SUSE vs Debian etc  etc.  I have taken the time to document alot of the different  distributions installation procedures on my blog (though I am partial to  debian and ubuntu) :)


-matt

---

### Post by jimwillsher on 2010-05-29
Many thanks. Yes, I've been running Lucid Lynx in Hyper-V since Lucid was released. Method 1, on the page you've linked to. Been working well for the few weeks I've been running it.

Cheers,


Jim

---

