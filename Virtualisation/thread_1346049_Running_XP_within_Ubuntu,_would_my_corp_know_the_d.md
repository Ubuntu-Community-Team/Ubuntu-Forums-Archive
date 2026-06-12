---
title: "Running XP within Ubuntu, would my corp know the difference?"
date: 2009-12-04
forum: Virtualisation
---

### Post by jsfour on 2009-12-04
Hey Guys,

Today my windows computer got infected with soemthing and I will more than likely need to do a complete wipe and reinstall of windows. Now, I would toss windows all together, however I must have the native office applications -all of my clients run office and I NEED 100% comparability every time. :(

So I had the idea to install ubuntu on my computer and run XP through a virtualbox to have a dual desktop environment. My question is, can I install windows normally so that it authenticates with the domain and access outlook etc through virtualbox? In essence I would have a completely seperate system running with the virtualbox. So, on boot of my computer, I would log into ubuntu and then need to log into xp and the VPN. Thus to my company, it would look like I am running XP, however I in reality I have the power of ubuntu.

Is this type of setup possible?

---

### Post by motorcity909 on 2009-12-04
My company uses remote access either via a company laptop or a browser-based VPN on any internet connected Windows PC.

As I've got a company XP laptop I've never needed to access the VPN in my VirtualBox XP but your question has prompted me to try it.

It worked fine, logged in no problem and I was able to open the web version of Outlook without any problems.

Whether any alarm bells were ringing in the IT department back at base, I don't know.  I very much doubt it.  

When I tried to log in using Firefox in Ubuntu, it made it clear the browser & OS were unsupported.  There were no such warnings in the virtual XP, so assume it was okay.

---

### Post by jsfour on 2009-12-04
So if I am understanding you correctly, you have logged into vpn via your virtual box no problem. If so thats awesome!

Would it be possible to set up an XP login screen through virtual box as if I had a separate XP computer? This way if my company ever does away with the VPN (of if i am at the home office) I will still be able to access everything I need?


- Jimi

---

### Post by motorcity909 on 2009-12-05
Within Ubuntu, I opened VirtualBox, then booted up my virtual XP.  I then opened Internet Explorer 8, went to my company's VPN web address and logged in with my username and password.  I am then able to access my corporate email and servers.

I'm not sure I understand your second point; can you expand on it please? 

Dave

---

### Post by arashiko28 on 2009-12-05
I have ms office 2007 installed through wine and works like a charm, even outlook. all you need is here:

> [http://ubuntuforums.org/showthread.php?t=1102840&highlight=install+office+2007](http://ubuntuforums.org/showthread.php?t=1102840&highlight=install+office+2007)

And you'll have ms office full compatibility without virus risks.

---

### Post by ABCC on 2009-12-06
I've used a setup like this for a few years without any problems. VPN, office, AD integration all work. Unless you need 3D accelreation it's a great setup. 

The Virtualbox version you download from Sun makes setting up networking slightly easier than the one available through apt. It also has experimental 3d support, could be handy if you need that in your vm. As for your Corp knowing the difference, not unless you show off your pc. Which you will, once you've played with wobbly Windows whilst you should be working.

---

### Post by joes7 on 2009-12-07
Yes, it will install normally as a Virtual Machine on Ubuntu. I did the very same thing, and it works fine. You can always download the official Linux Virtual Machine tools or download Virtual Box.

---

### Post by jsfour on 2009-12-07
Awesome! I think I may end up doing a ubuntu windows install :D

I have a laptop with the CRT/LCD function button that I know wont work after a ubuntu install. But does anyone know how I would connect a projector or to my laptop while on the road? Is there a command or something that I can run to switch it on?

---

### Post by ABCC on 2009-12-20
Theres a good chance it will 'just work' if you plug it in and boot the pc. Provided xorg can detect and configure it reasonable you can switch between single/dual/mirror modes with the gnome-display-properties (aka Display Preferences) tool. The other method is to use xrandr to enable it:

```
xrandr --output VGA1 --auto
```

---

### Post by memilanuk on 2009-12-20
I hate to play the devil's advocate here but...

It's not *your* computer.  It's the companies.  As such, unless you have explicit (i.e. written) permission, you risk running afoul of their IT policies by removing the OS they installed  and putting something else on there.  Most IT types I know don't encourage that kind of initiative, and instead view it as an attempt to subvert their network, or at least their little fiefdom ;)

I'd strongly recommend you talk to them, and try to obtain an okay even if its one that simply says 'you break it, you fix it - not our problem any more', or better yet, an allowance to try it out as a trial - perhaps that might open the door to more wide spread Linux deployment inside the company.

---

### Post by scorp123 on 2009-12-20
I agree with the posting above mine: better ask if it's OK if you move Windows to a virtual image ... Depending on what field you're working in you might get an immediate "OK!! Go ahead!" or not.

When I worked for Hewlett-Packard (2000-2007) I did exactly what you suggest: I had Linux on my laptops and a clone of the corporate Windows 2000 and then later Windows XP Pro images inside VMware and then later VirtualBox. How did I get permission? I didn't even ask. I didn't have to. I worked for a group that belonged to the "Large Enterprise Customer Support" division so whatever I did was OK for as long as none of those very important customers ever complained. "It's OK if it serves our customers". And thus I had a perfect "excuse" for using Linux: "I need a Unix-like OS because my customers have that too ... "  Perfect.

If you are in a similar position, e.g. you're an IT support guy working for a similar company then this might work as well for you ...

If however you have nothing whatsoever to do with IT support and thus have no "excuse" whatsoever to be using Linux ... then you better don't try that. Chances are you will find yourself in front of a clueless manager pretty soon who will then put all the blame for all the viruses that have recently hit the company network on you because you dared to bring that "hobbyist crap" into the company. Seriously. I know people who lost their jobs that way. Arguing "Linux is free and opensource. And it does not spread viruses ... " won't help.

So if you're in a non-IT position you better ask before getting yourself into trouble.

---

### Post by dcstar on 2009-12-23
> **scorp123 said:**
> 
.........
Arguing "Linux is free and opensource. And it does not spread viruses ... " won't help.


That is no argument whatsoever if you are running Windows inside a VM on any host platform, the Windows install is just as vulnerable as if was the host OS to virtually every piece of malware around. **


** Running the Windows VM in NAT mode may protect it from certain port scan malware since they cannot cross the NAT boundary.

---

### Post by scorp123 on 2009-12-23
> **dcstar said:**
> That is no argument whatsoever if you are running Windows inside a VM on any host platform, the Windows install is just as vulnerable  True.

If that were to happen (= your Windows VM got infected and starts to spread viruses) I bet they'd blame Linux too :)

So again: OP better ask for permission before installing anything onto his laptop that is not officially permitted ...

---

### Post by pricetech on 2010-01-12
Ask first.  You might find the IT department to be pleased.  Don't be surprised if they frown on it though, even if they like Linux.  Too many wannabees have created too many headaches for us to be anxious to let users do what they want with company property.

Yeah, I'm one of those &#$^@@!  IT guys.

If you have a good repore with them, they'll probably be OK with it, but let them make the call and remember that they have a responsibility to management, most of whom are clueless, so they sometimes have to "play the game"

---

### Post by estyles on 2010-01-12
> **dcstar said:**
> That is no argument whatsoever if you are running Windows inside a VM on any host platform, the Windows install is just as vulnerable as if was the host OS to virtually every piece of malware around. **


** Running the Windows VM in NAT mode may protect it from certain port scan malware since they cannot cross the NAT boundary.

Question - can you properly connect to a VPN in NAT mode?  I run a similar setup to this at work - I have an Ubuntu machine and a Windows VM (well, one development VM, and then separate VM's set up as registers and store PC's so I can imitate a store setup when testing).  However, I have set up my VM's in Bridged mode.  To be honest, I don't remember why - on the first machine I set up, something didn't work in NAT mode and I had to set it up as Bridged, but I don't remember what it was that didn't work.

I've been assuming that I need a Bridged adapter in order to maintain 2-way communications with the active directory server, but I'm a little hazy on the whole thing...

---

