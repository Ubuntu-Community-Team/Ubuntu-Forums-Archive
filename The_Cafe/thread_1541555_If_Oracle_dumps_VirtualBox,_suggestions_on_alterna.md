---
title: "If Oracle dumps VirtualBox, suggestions on alternatives?"
date: 2010-07-29
forum: The Cafe
---

### Post by samalex on 2010-07-29
I've been a fan of VirtualBox for years, and I heavily depend on it to use work and various other apps on my laptop.  I'm getting abit skittish though with Oracle and the [suggestions of some]("http://www.muktware.com/news/26/2010/249") that they'll be pulling VirtualBox, so I'm looking for some alternatives.

VMWare is one alternative, but is there a free version? Also how does it stack-up to VirtualBox? I've never used VMWare on Linux, so is it as functional and 'just works' on Linux as VBox is?  Also are there any other apps you guys suggest I should check out?

I'm not ready to pull away from VBox just yet, but just in-case Oracle decides to turn its back on the open source community (which I anticipate will be anytime now) I'd like to be prepared.

Thanks for suggestions or comments --

Sam

---

### Post by lykwydchykyn on 2010-07-29
I wouldn't take those suggestions too seriously.  It's one guy building a conspiracy theory off the fact that VB 3.2 hasn't worked as well on his machine as previous versions.

Oracle isn't going to pull the plug on VB.  Look around, EVERY major player has a VM solution to push.  When oracle bought Sun, they were bragging about how they now have "the whole stack".  It's not going to be "the whole stack" without a virtualization platform.

Anyway, if it did suddenly disappear, we've got KVM built right into the kernel; the current qemu front-end is a little lacking, but that would probably change quickly.

---

### Post by sdowney717 on 2010-07-29
vmware server is free, just have to register to download. Been a year since I did use it. 
another is Xen hypervisor

how about a truly invisible virtual machine where it all just runs everything thrown at it regardless of what type of executable.

---

### Post by forrestcupp on 2010-07-29
> Windows XP randomly crashes inside VirtualBox, some GNU/Linux operating systems show severe instability,
:lol:
And that's because of VirtualBox?

---

### Post by TNT1 on 2010-07-29
> **lykwydchykyn said:**
> 

Anyway, if it did suddenly disappear, we've got KVM built right into the kernel; the current qemu front-end is a little lacking, but that would probably change quickly.

Yip, KVM/qemu works just fine. Not as flash and cool as Vbox, but perfectly functional.

---

### Post by Simian Man on 2010-07-29
Red Hat's [Virtual Machine Manager]("http://virt-manager.et.redhat.com/") is another good option.  It works as a frontend to Xen or KVM.  It currently isn't as easy to use as Virtualbox is though.

---

### Post by Ric_NYC on 2010-07-29
QEMU!

> QEMU is a generic and open source machine emulator and virtualizer.

When used as a machine emulator, QEMU can run OSes and programs made for one machine (e.g. an ARM board) on a different machine (e.g. your own PC). By using dynamic translation, it achieves very good performance.

When used as a virtualizer, QEMU achieves near native performances by executing the guest code directly on the host CPU.


[http://wiki.qemu.org/Main_Page](http://wiki.qemu.org/Main_Page)

---

### Post by RiceMonster on 2010-07-29
I'll worry about them dropping VirtualBox if there's an official annoucement from Oracle.

---

### Post by FuturePilot on 2010-07-29
So just because someone is seeing crashes it means Oracle is dumping Virtual Box? LOL.

---

### Post by cprofitt on 2010-07-29
I think I will go with the Rice Monster on this one... doesn't make sense that they would drop it... but if they did I am sure they would make an announcement... and at that time I could pursue alternatives.

---

### Post by CharlesA on 2010-07-29
> **RiceMonster said:**
> I'll worry about them dropping VirtualBox if there's an official annoucement from Oracle.

+1.

I've run VirtualBox (latest version) on both Linux and Windows without any problems.

The link in the OP is pure FUD and conspiracy theory.

---

### Post by samalex on 2010-07-29
> **CharlesA said:**
> +1.

I've run VirtualBox (latest version) on both Linux and Windows without any problems.

The link in the OP is pure FUD and conspiracy theory.

I agree it was laced with FUD, but I'm honestly afraid Oracle is slowly dropping/contorting the open source projects they picked-up from Sun.  Just today it's [reported]("http://www.itnews.com.au/News/221051,oracle-shuts-down-open-source-test-servers.aspx") Oracle shut down the open source test servers Sun setup.  The biggest open source package Oracle inherited from Sun that I use on a daily basis is VirtualBox, so even though the article I linked to in the OP I can't help but think Oracle will put some changes in place.

Sam

---

### Post by _h_ on 2010-07-29
I use VMWare Workstation 7.1, so I don't really have to worry. :P

---

### Post by lykwydchykyn on 2010-07-29
> **samalex said:**
> Just today it's [reported]("http://www.itnews.com.au/News/221051,oracle-shuts-down-open-source-test-servers.aspx") Oracle shut down the open source test servers Sun setup. 


Finish the rest of the sentence:

[quote=the article linked]
Oracle has shut down servers Sun Microsystems was contributing to the build farm for **open source database software, PostgreSQL**
[/quote]

The makers of Oracle and new owners of MySQL don't want to contribute to the development of PostgreSQL?  This should not surprise anyone.

---

### Post by 3rdalbum on 2010-07-29
Virtualbox OSE will live on, it's open-source. I'm sure the people who can't live without the extra features from the proprietary edition will just move over to KVM or VMWare.

---

### Post by CharlesA on 2010-07-29
I'd move onto VMware if I could get it to work without having to jump thru hoops.

---

### Post by forrestcupp on 2010-07-29
> **samalex said:**
> I agree it was laced with FUD, but I'm honestly afraid Oracle is slowly dropping/contorting the open source projects they picked-up from Sun.I'd say it's much more likely that Oracle would release the next version of VirtualBox under a proprietary license and sell it.  They're not just going to trash it.

> **CharlesA said:**
> I'd move onto VMware if I could get it to work without having to jump thru hoops.
+1

In my experience, vmware works better, but it's *a lot* harder to get it set up.  Especially if you want to use vmtools in the free vmplayer.

---

### Post by Bachstelze on 2010-07-29
> **FuturePilot said:**
> So just because someone is seeing crashes it means Oracle is dumping Virtual Box? LOL.

Maybe it's just me, but I also see the crashes very clearly.  Just today I had two kernel panics.  I just reverted to VirtualBox 3.1, it got rid of both the Oracle logo and the crashes.

---

### Post by stmiller on 2010-07-29
This is the dumbest thing I have ever read on the internet.

-> [http://www.muktware.com/news/26/2010/249](http://www.muktware.com/news/26/2010/249)

Suddenly because the logo changed, it means suddenly all the years of work in Virtualbox started not working, and having problems.


:rolleyes:

---

### Post by mooreted on 2010-07-29
> **forrestcupp said:**
> :lol:
And that's because of VirtualBox?

Yeah, that article was just lame. I have the newest VB running Windows XP and it works perfectly. No clue what that guy's problem is.

Now that you can create VMs in Vmware Viewer, I'm going to play around with that a little, but VB works just fine here.

---

### Post by jerenept on 2010-07-29
I've been running vbox ose 3.2 (from repos) for a while, and the only issue has been slowness (cheapo hardware)

This is utter FUD.

---

### Post by JustinR on 2010-07-29
I agree Oracle won't be dropping VirualBox any time soon. Its a popular product and its always been stable for me. No crashes or anything.

---

### Post by CharlesA on 2010-07-29
> **forrestcupp said:**
> 
In my experience, vmware works better, but it's *a lot* harder to get it set up.  Especially if you want to use vmtools in the free vmplayer.

I've tried to get VMWare Server2 installed on my Ubuntu box with no success. Something about an unsupported kernel and that I need to use a third-party script to get it installed.

It's been able to get installed, but it won't start the VMs. I don't know if it's caused by not having a GUI installed on my server, or what.

---

### Post by alphaniner on 2010-07-29
> **CharlesA said:**
> I've tried to get VMWare Server2 installed on my Ubuntu box with no success. Something about an unsupported kernel and that I need to use a third-party script to get it installed.

It's been able to get installed, but it won't start the VMs. I don't know if it's caused by not having a GUI installed on my server, or what.

I'm running the latest VMware Server 2 on 10.04 Server.  Had to use the script to get it installed, and the Web-UI is horrible as always, but otherwise I have had no problems.

---

### Post by Legendary_Bibo on 2010-07-29
The only problem I have with Virtual box is the fact that if I give it a lot of RAM to use, it also uses up one of my cores to its fullest. It drains my battery like crazy, but it's fine. I only have to use it occasionally. Also I noticed no one else brought this up, but so what if they drop support?! If they do then does that mean that VB is suddenly going to stop working? Virtual Box seems to run the lighter distros just fine, but struggles with the heavier distros such as Kubuntu, OpenSUSE, Windows Vista and 7 (not distros I know). As long as it runs XP for me I'm fine, I only have it installed to run WinXP for school stuff.

---

### Post by JustinR on 2010-07-29
> **Legendary_Bibo said:**
> The only problem I have with Virtual box is the fact that if I give it a lot of RAM to use, it also uses up one of my cores to its fullest. It drains my battery like crazy, but it's fine. I only have to use it occasionally. Also I noticed no one else brought this up, but so what if they drop support?! If they do then does that mean that VB is suddenly going to stop working? Virtual Box seems to run the lighter distros just fine, but struggles with the heavier distros such as Kubuntu, OpenSUSE, Windows Vista and 7 (not distros I know). As long as it runs XP for me I'm fine, I only have it installed to run WinXP for school stuff.

Thats because VirtualBox doesn't emulate a processor, it uses your processor to execute all of the Virtual machine code - so most VM's (given enough RAM) should run near native speed. So its like running two operating systems which consumes twice the power.

I hope they don't get rid of VirtualBox - its a great product.

---

### Post by phrostbyte on 2010-07-29
Kvm :)

---

### Post by Legendary_Bibo on 2010-07-29
> **JustinR said:**
> Thats because VirtualBox doesn't emulate a processor, it uses your processor to execute all of the Virtual machine code - so most VM's (given enough RAM) should run near native speed. So its like running two operating systems which consumes twice the power.

I hope they don't get rid of VirtualBox - its a great product.

Yeah but why does it have to max out a core? I might have an idea as to how it works.

---

### Post by Dustin2128 on 2010-07-29
I don't like some of the stuff oracle did upon acquisition of sun, but virtualbox is open source as I'm sure you all know. If you don't like the way it's going, just fork it.

---

### Post by CharlesA on 2010-07-29
> **alphaniner said:**
> I'm running the latest VMware Server 2 on 10.04 Server.  Had to use the script to get it installed, and the Web-UI is horrible as always, but otherwise I have had no problems.

Interesting. Does yer server have a GUI installed?

The last time I tried it, I wasn't able to even access the WebUI. The first time I tried, I was able to access the WebUI, but not start VMs.

Major pain in the butt.

---

### Post by forrestcupp on 2010-07-29
> **Dustin2128 said:**
> I don't like some of the stuff oracle did upon acquisition of sun, but virtualbox is open source as I'm sure you all know. If you don't like the way it's going, just fork it.

That's true in theory, but it usually doesn't work in practice.  When you have a large, complicated project that has been developed by certain people for the life of the project, and those people drop it, it isn't real easy for a group of new people to just take it over with no prior knowledge of its inner workings.  Also, it's usually not easy to find people who are willing to do that.

Just because a project is open source doesn't mean there are thousands of devs just waiting to jump at the chance to spend their lives investing into something that isn't going to put food on their tables.  Sometimes it happens, but you can't just expect that.

---

### Post by Dustin2128 on 2010-07-29
> **forrestcupp said:**
> That's true in theory, but it usually doesn't work in practice.  When you have a large, complicated project that has been developed by certain people for the life of the project, and those people drop it, it isn't real easy for a group of new people to just take it over with no prior knowledge of its inner workings.  Also, it's usually not easy to find people who are willing to do that.

Just because a project is open source doesn't mean there are thousands of devs just waiting to jump at the chance to spend their lives investing into something that isn't going to put food on their tables.  Sometimes it happens, but you can't just expect that.
Just saying that IMHO apart from a few minor things, vbox is fine as is. If you don't like the developments, you can just continue using the last version of the OSE you liked, contributing some minor code here and there. Update popup cancellation comes to mind.

---

### Post by forrestcupp on 2010-07-29
> **Dustin2128 said:**
> Just saying that IMHO apart from a few minor things, vbox is fine as is. If you don't like the developments, you can just continue using the last version of the OSE you liked, contributing some minor code here and there.

That's definitely true.  Just because they stop developing it doesn't mean it's just going to disappear and we all have to stop using it.

---

### Post by alphaniner on 2010-07-30
> **CharlesA said:**
> Interesting. Does yer server have a GUI installed?

The last time I tried it, I wasn't able to even access the WebUI. The first time I tried, I was able to access the WebUI, but not start VMs.

Major pain in the butt.

No GUI, pretty much just the basic Ubuntu Server installation.

I've had problems with the WebUI since 2.0 - not getting a logon dialogue, missing elements, perpetual loading, etc. - on every installation.  I actually have fewer such problems now, but I think that's primarily because it's on a much more powerful machine.  I don't think I've ever been unable to start VMs though.

---

