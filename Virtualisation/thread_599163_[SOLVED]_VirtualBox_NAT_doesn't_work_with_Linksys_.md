---
title: "[SOLVED] VirtualBox NAT doesn't work with Linksys WRT54G"
date: 2007-11-01
forum: Virtualisation
---

### Post by Runamok on 2007-11-01
Okay guys, I have an interesting situation here.  I'm having trouble with VirtualBox's NAT configuration, but ONLY on my home network.

[INDENT]Running VirtualBox 1.5.2, with NAT redirection to the guest OS
Host = Ubuntu Fiesty 7.04 (I'm going to upgrade 7.10 in afew weeks)
Guest OS = Windows XP (MCE)[/INDENT]

My guest OS has perfect internet access over my schools Airnet, but when I come home to my Linksys WRT54G, no dice.

By elimination, It seems this would be a router problem, and Im wondering if anyone else has had this happen to them.

For the record, I've tried rebooting both OS's, manually configuring and repairing internet in WindowsXP, doing the same in Ubuntu..  nothing seems to work.  I can however, access the router's config page with my guest OSs internet connection. But noooo internet traffic on port 80 will come through!

NAT redirection works at school, but not at home.

Any suggestions?:confused:

[CENTER]:KS
[B]UPDATE: 12/4/08:KS[/CENTER]
I found a temporary fix for this problem by manually entering in the DNS information into Windows TCP/IP settings.  This allowed my to pass on internet traffic in VBox at home with my Linksys WRT54G.[/B]

---

### Post by Delvien on 2007-11-01
> **Runamok said:**
> Okay guys, I have an interesting situation here.  I'm having trouble with VirtualBox's NAT configuration, but ONLY on my home network.

[INDENT]Running VirtualBox 1.5.2, with NAT redirection to the guest OS
Host = Ubuntu Fiesty 7.04 (I'm going to upgrade 7.10 in afew weeks)
Guest OS = Windows XP (MCE)[/INDENT]

My guest OS has perfect internet access over my schools Airnet, but when I come home to my Linksys WRT54G, no dice.

By elimination, It seems this would be a router problem, and Im wondering if anyone else has had this happen to them.

For the record, I've tried rebooting both OS's, manually configuring and repairing internet in WindowsXP, doing the same in Ubuntu..  nothing seems to work.  I can however, access the router's config page with my guest OSs internet connection. But noooo internet traffic on port 80 will come through!

NAT redirection works at school, but not at home.

Any suggestions?:confused:

I use the same router, no problem here.

---

### Post by ColdFusionEESG on 2007-11-07
I'm in a very similar boat.....

Running VirtualBox 1.5.0, with NAT redirection to the guest OS
Host = Ubuntu Gutsy 7.10
Guest OS = Windows XP Pro SP 2
router = WR**K**54G

In my office I have a wired connection and all works as advertised (it just works by default using NAT).

At home my wireless connection just doesn't seem to get through to the guest OS (Win XP Pro).  I've enabled all 4 adapters using NAT and no luck.

The odd part is at the office I run ipconfig /all in the guest OS and see all the enabled adapters with IPs like 10.0.4.2 , 10.0.5.2, 10.0.4.3, etc....BUT...at home on the wireless connection I see the same IPs. So it seems like on both connnections the IPs are assigned and the same, but at home the guest OS can't connect to the net?


FYI....Linux newbie...programmer....tossing Windows (except for testing apps).....so far it's been EASY :) and GREAT \\:D/

---

### Post by Runamok on 2007-11-12
Just to update.  I've googled, and searched many forums with no success. I'm surprised I haven't found an answer (besides cumbersome bridging, which doesn't seem to bode well for a roaming wireless config) and I know my problem can't be the exception.  Thanks Coldfusion for sharing, and congrats for making the Ubuntu switch. Unfortunately, I'm still having the same problems with the spotty virtualbox NAT.  I'm hoping that one of the Ubuntu gurus can give some advice, before I give up.  

I can't understand how I can access the routers page from within the virtualized windows, but no traffic comes through. Obviously the ips are configured, and the routing is resolved, so why no internet traffic? BTW, I'm using a Dell 9300, and and intel pro wireless card (ipw2200 drivers)

P.S.

To Delvien: Since everything works for you, do you mind, or could you please share your wireless configuration?  Are you using a similar wireless card?  What versions of Ubuntu, virtualbox and Windows?  Sorry to be so nosy, but it might help me diagnose.

Thanks.

---

### Post by ColdFusionEESG on 2007-11-13
> **Runamok said:**
> Just to update.  I've googled, and searched many forums with no success. I'm surprised I haven't found an answer (besides cumbersome bridging, which doesn't seem to bode well for a roaming wireless config) and I know my problem can't be the exception.  Thanks Coldfusion for sharing, and congrats for making the Ubuntu switch. Unfortunately, I'm still having the same problems with the spotty virtualbox NAT.  I'm hoping that one of the Ubuntu gurus can give some advice, before I give up.  

I can't understand how I can access the routers page from within the virtualized windows, but no traffic comes through. Obviously the ips are configured, and the routing is resolved, so why no internet traffic? BTW, I'm using a Dell 9300, and and intel pro wireless card (ipw2200 drivers)

P.S.

To Delvien: Since everything works for you, do you mind, or could you please share your wireless configuration?  Are you using a similar wireless card?  What versions of Ubuntu, virtualbox and Windows?  Sorry to be so nosy, but it might help me diagnose.

Thanks.

Yep this is odd for sure.....even odder now that I've managed to connect to a client's VPN, but still no Internet browsing.

More on my situation in this thread:
[http://ubuntuforums.org/showthread.php?t=606215&goto=newpost](http://ubuntuforums.org/showthread.php?t=606215&goto=newpost)

I'll post here if I find a solution (and I will...hehe)

Cheers

---

### Post by Pollywoggy on 2007-11-13
> **Delvien said:**
> I use the same router, no problem here.

I use a WRT54GS and I also can't get networking to work.
I installed the deb package for Gutsy that I downloaded from the Virtualbox website and I could not get networking (NAT) to work.  I removed that deb and downloaded the one from the ubuntu repositories and I also could not get NAT to work.

I think I will have to buy VMware Workstation if I want to run XP in Kubuntu

---

### Post by Pollywoggy on 2007-11-14
I tried again using the deb for Gutsy that I downloaded from virtualbox.com and this time, I set up networking in XP so that DHCP is used.  This worked.  In prior attempts to get NAT to work, I assigned a static IP address to the XP guest and was unable to connect to anything.

---

### Post by Delvien on 2007-11-14
Sorry, didnt see your response.

I have the folloiwng:

Intell 3945 ABG card
Linksys WRT54G set to DHCP, WEP encryption 128bits with wireless Mac address filtering to my laptops card.

VirtualBox 1.5.2 NON-OSE set to NAT with only the one adapter activated.
____________

I hope thats what you were asking for.

---

### Post by ColdFusionEESG on 2007-11-14
> **Pollywoggy said:**
> I tried again using the deb for Gutsy that I downloaded from virtualbox.com and this time, I set up networking in XP so that DHCP is used.  This worked.  In prior attempts to get NAT to work, I assigned a static IP address to the XP guest and was unable to connect to anything.


I've seen mention of VirtualBox OSE and some other kind.....what's the difference?

I have the OSE version

TIA

Cheers

---

### Post by Delvien on 2007-11-15
> **ColdFusionEESG said:**
> I've seen mention of VirtualBox OSE and some other kind.....what's the difference?

I have the OSE version

TIA

Cheers

OSE is open source edition, this has fewer features than the full version for personal use ( IE USB support  is a big one (not avail on OSE version))

---

### Post by ColdFusionEESG on 2007-11-15
> **Delvien said:**
> OSE is open source edition, this has fewer features than the full version for personal use ( IE USB support  is a big one (not avail on OSE version))

LOL...I should have guessed that one ;-)

I suspect that when I added the guest additions to my 1.5.0 install it added USB support (I think I read that somewhere)

Thanks!

---

### Post by Runamok on 2007-12-04
Okay Gentlemen,

I believe I have identified the problem and found a temporary fix for my situation. 

It seems that somewhere along the way, Ubuntu's DCHP hosting is NOT passing on the DNS information to my WindowsXP guest OS. That this problem is specific for the Linksys WRT54G, I know not.  But a quick fix, I have.

So, within my guest OS I edited the properties of my network connection (AMD PCNet Family...) and told windows to no longer automatically obtain the DNS settings.  Instead I manually entered in the DNS settings that the Ubuntu Network-Manager automatically obtains from my router. (This is what the guest OS is failing to do)  Basically, I pass on the information manually.  

In your Guest OS Windows:
Right click on your internet connection, then...

Properties > General Tab > Internet Protocol (TCP/IP) > Properties > Click the radio button "Use the Following DNS Settings" > **enter the DNS settings from Ubuntu network manager

This allowed me to connect at home...  HOWEVER, since DNS settings change when you travel, I must remember to reset the radio button to "Automatically Obtain DNS Settings" when I am mobile, or on campus.

Let me know if this helps anyone else get VirtualBox and the Linksys WRT54G to play nice.

- Enjoy

---

### Post by AcidicChip on 2008-01-25
I'm not sure if you found the solution to your problem or not, but I'd check any IP blocking tools such as MoBlock. I just had this issue, and just remembered MoBlock giving me a networking issue when I was at a 10.10.* network, and I had to disable it to get internet or even network.

---

### Post by Matthewthegreat on 2008-09-14
> **Runamok said:**
> Okay Gentlemen,

I believe I have identified the problem and found a temporary fix for my situation. 

It seems that somewhere along the way, Ubuntu's DCHP hosting is NOT passing on the DNS information to my WindowsXP guest OS. That this problem is specific for the Linksys WRT54G, I know not.  But a quick fix, I have.

So, within my guest OS I edited the properties of my network connection (AMD PCNet Family...) and told windows to no longer automatically obtain the DNS settings.  Instead I manually entered in the DNS settings that the Ubuntu Network-Manager automatically obtains from my router. (This is what the guest OS is failing to do)  Basically, I pass on the information manually.  

In your Guest OS Windows:
Right click on your internet connection, then...

Properties > General Tab > Internet Protocol (TCP/IP) > Properties > Click the radio button "Use the Following DNS Settings" > **enter the DNS settings from Ubuntu network manager

This allowed me to connect at home...  HOWEVER, since DNS settings change when you travel, I must remember to reset the radio button to "Automatically Obtain DNS Settings" when I am mobile, or on campus.

Let me know if this helps anyone else get VirtualBox and the Linksys WRT54G to play nice.

- Enjoy

I know this is a big bump but I just wanted the say thanks for this post!!!

---

### Post by panthar91 on 2009-03-25
> **Matthewthegreat said:**
> I know this is a big bump but I just wanted the say thanks for this post!!!

ditto on that good buddy, this also fixed my problem!

---

### Post by MKVCrazy on 2009-12-11
> **Runamok said:**
> Okay Gentlemen,

I believe I have identified the problem and found a temporary fix for my situation. 

It seems that somewhere along the way, Ubuntu's DCHP hosting is NOT passing on the DNS information to my WindowsXP guest OS. That this problem is specific for the Linksys WRT54G, I know not.  But a quick fix, I have.

So, within my guest OS I edited the properties of my network connection (AMD PCNet Family...) and told windows to no longer automatically obtain the DNS settings.  Instead I manually entered in the DNS settings that the Ubuntu Network-Manager automatically obtains from my router. (This is what the guest OS is failing to do)  Basically, I pass on the information manually.  

In your Guest OS Windows:
[COLOR=Red]*Right click on your internet connection*[/COLOR], then...

Properties > General Tab > Internet Protocol (TCP/IP) > Properties > Click the radio button "Use the Following DNS Settings" > **enter the DNS settings from [COLOR=Red]*Ubuntu network manager*[/COLOR]

This allowed me to connect at home...  HOWEVER, since DNS settings change when you travel, I must remember to reset the radio button to "Automatically Obtain DNS Settings" when I am mobile, or on campus.

Let me know if this helps anyone else get VirtualBox and the Linksys WRT54G to play nice.

- Enjoy
Sorry for the bump but I have been searching for too long all over the net and finally found a closer answer. I am also using WRT54G and similar situations (Linux is host and Windows XP is guest). So please pardon for my late question. But I do not know how to do/proceed/understand the red color I specified above.

Where is "Ubuntu Network Manager"?
I don't have any "Network Connections" in my Windows XP (see screenshot). Everytime I create something in the wizard, they don't appear. I can only create the "Connect to Internet Through Another Computer" which is not what I am after. :(

---

### Post by cheaka on 2010-05-13
This is a known bug in VirtualBox from at least version 2.0.6 ( [http://www.virtualbox.org/ticket/3847]("http://www.virtualbox.org/ticket/3847") ). 

At that URL there is a nice workaround: in recent versions of VirtualBox, you can have the host act as a DNS proxy (instead of having to pull down DNS server names, which is where the bug is triggered).

Run:
```
VBoxManage setextradata "GUEST_VM_NAME" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/DNSProxy" 1

```

(replace GUEST_VM_NAME with the name of the guest VM you want to modify. If you don't know the name, you can run ```
 VBoxManage list vms 
``` to find it

---

