---
title: "Very Well Supported Netbooks?"
date: 2010-08-04
forum: The Cafe
---

### Post by asddf on 2010-08-04
I'm looking to get a netbook but was wondering what netbooks are very well supported under the Linux distros? 

What manufacturers use parts with open source drivers?

---

### Post by snowpine on 2010-08-04
The obvious choice is System76; their netbooks come with 10.04 preinstalled, and they even have a sub-forum here on UbuntuForums! (I don't own one so I can't personally vouch.)

Other netbook models are discussed on this must-read wiki page: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by asddf on 2010-08-04
I'm in the UK so have to discount system76

---

### Post by tgm4883 on 2010-08-04
Dell has the mini 10. I think it uses a Broadcom network chipset though so not completely open source. It's pretty well supported though.

---

### Post by pcgeekguru on 2010-08-04
Well so far i have ubuntu netbook edition installed on this machine, but im looking for a distro for my other netbook. I already tried puppy linux and didnt like it too well and i still have yet to try jolicloud. I would try to do a search in yahoo or some other search engine under " linux netbook distros" or something similar to that. Thats how i found ubuntu netbook edition.

---

### Post by BrokenKingpin on 2010-08-04
My Acer Aspire One 532h runs perfectly under Ubuntu 10.04 desktop out of the box with no restricted drivers.

---

### Post by snowpine on 2010-08-04
pcgeekguru, a netbook is just a small computer. All of the major distros support netbooks, and you do not necessarily need a "netbook distro."

---

### Post by mendhak on 2010-08-04
> **asddf said:**
> I'm looking to get a netbook but was wondering what netbooks are very well supported under the Linux distros? 

What manufacturers use parts with open source drivers?
I have Asus EEE with eeebuntu installed; it is good in the sense that it's popular, so if you have problems, it's easy to find a solution or answer somewhere.  Not aware of any official support.

---

### Post by cherva on 2010-08-04
I Have Asus EeePC 1005HA and everything is working ... even the top left key that disables the touch pad ....

---

### Post by pcgeekguru on 2010-08-04
> **snowpine said:**
> pcgeekguru, a netbook is just a small computer. All of the major distros support netbooks, and you do not necessarily need a "netbook distro."

yeah i  know but im picky. i tried pclinuxos before and the screen was too stretched out so i would rather have a netbook specific distro to fit my screen better.

---

### Post by snowpine on 2010-08-04
> **pcgeekguru said:**
> yeah i  know but im picky. i tried pclinuxos before and the screen was too stretched out so i would rather have a netbook specific distro to fit my screen better.

If your screen is "stretched out" it's possible your graphics card is not recognized and is displaying the wrong resolution. Which graphic card do you have?

---

### Post by tgm4883 on 2010-08-04
Yea, sounds like a resolution issue.

---

### Post by pcgeekguru on 2010-08-04
> **snowpine said:**
> If your screen is "stretched out" it's possible your graphics card is not recognized and is displaying the wrong resolution. Which graphic card do you have? 

Well all I know is that its an intel graphics driver. So I'm guessing it's an intel grapics card.

---

### Post by snowpine on 2010-08-04
> **pcgeekguru said:**
> Well all I know is that its an intel graphics driver. So I'm guessing it's an intel grapics card.

Intel makes several different graphics cards; you can use the following terminal command to find out exactly which one:

```
lspci | grep VGA
```

---

### Post by pcgeekguru on 2010-08-04
Well i have an eepc 900hd netbook so I might try eeebuntu 3.0 NBR and see what happens.

---

### Post by lancest on 2010-08-04
Just bought an [MSI U230]("http://www.amazon.com/MSI-U230-040US-12-1-Inch-Netbook-Battery/dp/B0036OR9BK") with no operating system.
Runs great with a few minor tweaks.
Plays HD video smoothly.

---

### Post by NormanFLinux on 2010-08-04
My Dell Mini 10's Poulsbo drivers are supported under PCLOS. It also supports the HP Mini 2133's Chrome drivers.

---

### Post by NormanFLinux on 2010-08-04
You can select netbook within KDE 4.4.5 to set up a netbook configuration. Lubuntu offers a netbook option for those who want to run one under LXDE.

---

### Post by 3rdalbum on 2010-08-05
Acer Aspire One is virtually a reference platform for Ubuntu; I believe Canonical tests Ubuntu on some Aspire Ones. Both my old 8.9 inch, and my newer 10 inch dual-boot Android model work perfectly* on 10.04.

*Not quite perfectly, but pretty close. Suspending, resuming and then shutting down will still cause an onboard device to use power and drain your battery. You need to either avoid suspending entirely, or remove the battery after you have been suspending.

---

### Post by Paqman on 2010-08-05
The EeePCs seem to work really well. I can definitely vouch for the 901 and the 1000HG on Ubuntu Netbook Edition. Everything works prefectly, all the special function keys, the built in 3G on the 1000, etc.

---

### Post by pcgeekguru on 2010-08-06
> **snowpine said:**
> Intel makes several different graphics cards; you can use the following terminal command to find out exactly which one:

```
lspci | grep VGA
```

Do you put the spaces in like you have there or can they be all together?

---

### Post by snowpine on 2010-08-06
> **pcgeekguru said:**
> Do you put the spaces in like you have there or can they be all together?

Copy & paste so you don't make any typos. :)

---

### Post by Legendary_Bibo on 2010-08-06
Jolicloud looks great, but what if you're not constantly hooked up to the internet? Unless it lets you have a mix of cloud and local applications then I would say it's definitely awesome. That's the problem I have with these cloud OSs, it's either everything is on the cloud, or everything is local, there's never a mix. That's why I'm skeptical about Chrome OS.

---

