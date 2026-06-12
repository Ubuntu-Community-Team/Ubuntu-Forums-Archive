---
title: "How much bandwidth does Remote Desktop Access (RDP protocol) consume?"
date: 2019-06-18
forum: Virtualisation
---

### Post by webmiester on 2019-06-18
Dear everyone,

I want to create a server which will virtualize office computers here at work.  The virtual computers' desktop will be accessible through remote access either by RDP or some other protocol (I will be testing nomachine).  Each VM will have at least 2 LAN ports - 1 port for the internet and another port to the switch that will connect to the RPi network.  Since the remote access devices (thin clients) are mostly RPi's which just has a 100mbps LAN, do my switches still need to be gigabit switches?  Will they make a noticeable difference with a 100mbps switch?

When the office employee uses the internet, the internet traffic wont pass through the switch since it will be done by the VM which will have a more direct connection to the internet service provider router.   If we will be transferring files from one computer to another, it will be done by VM to VM, and so the files wont pass through the actual physical network.  So in reality, the switch will only handle RPi traffic manning RDP signals.  So is RDP heavy on the bandwidth?  Each 100mbps switch will only have 10-20 computers maximum.  There will be around 4 switches and these switches will connect to a gigabit switch which will be the one to connect to the VM's port.  So just to be clear,  the VM's gigabit LAN port will connect to a gigabit switch which will divide the signal into 100mps switches, where the thin client RPi's will connect to.  The server hosting the VM will of course, have gigabit LAN on it.  It s just the "thin clients" that have the 100mbps LAN ports.

In one point of view, I want to point out that thin clients and the RPis only have a 100mps LAN and RDP goes on quite smoothly with them, so perhaps they dont take up too much bandwidth.  But on the other hand, RDP does transmit the video and audio from the host computer, so perhaps transmitting this video and audio might be quite heavy on the bandwidth.  I really dont know.  What are your ideas with this?  Has anyone run network traffic analysis software on computers running RDP?  How much bandwidth do they use?  I havent purchased my switches yet, but the gigabit switches are significantly more expensive here (they cost around 4x more).  If 100mbps switches can do the job, I would rather spend the difference on things like battery backup or a better server.

If RDP consumes the full 100mbps bandwidth, then gigabit switches will really be important, but if they only consume like 5 or 10mbps, then I think the 100mbps switches should be just fine, but I dont know how much bandwidth RDP consumes.  I appreciate any inputs.  Thanks.

As for the office work, they mostly consumes stuff like visiting government websites and office applications (such as MS office).  None of the offices are officially supposed to watch youtube while at work.  There will be 2 computers using photoshop.  But I think photoshop is not quite like streaming a video.  All RDP is done through LAN, no access through the internet will be available.

---

### Post by lammert-nijhof on 2019-06-18
Get assistance from a professional maintenance organisation, you have strange ideas! 
E.g The required bandwidth for one RDP depends completely on the screen resolution, the required refresh frequency for e.g. video etc and the required response times for transactions. The loading that 10-20 computers generate, also depends on the transaction mix and frequency. In a professional organisation forget about 100 Mbps unless you only use MS-DOS thin clients, I could not even live with 100 Mbps at home anymore for one VM, any YouTube or other video display is impossible with 100 Mbps.

---

### Post by TheFu on 2019-06-18
> **lammert-nijhof said:**
> Get assistance from a professional maintenance organisation, you have strange ideas! 

Yep. Get a VDI professional who isn't tied to 1 specific solution.

Or get to testing everything and scaling up slowly.

Deploying 100base-t at this point is foolish.  It isn't just about the port speed, but the backplane capabilities inside the network gear.

I'm also concerned that any thought is given to having multiple network connections, to different networks, for end users.  If one of those is the internet, you've just asked to be hacked with N extra front-doors.  Inside a business, desktop machines should never have direct internet access. They should always go through a proxy. DNS from desktops shouldn't be able to resolve google.com or any internet address either.

I've seen lots and lots of your questions the last few months and assumed this was for a lab deployment at home for all the remote desktop stuff.  That is completely different than doing this stuff for a business where downtime means money lost.  Also, you don't need/want 1 virtual machine desktop for each end user from what I recall being said across the 20+ threads.

It isn't possible to get the correct answers for a total solution like you are considering through forums.

---

### Post by webmiester on 2019-06-19
> **TheFu said:**
> Yep. Get a VDI professional who isn't tied to 1 specific solution.

Or get to testing everything and scaling up slowly.

Deploying 100base-t at this point is foolish.  It isn't just about the port speed, but the backplane capabilities inside the network gear.

I'm also concerned that any thought is given to having multiple network connections, to different networks, for end users.  If one of those is the internet, you've just asked to be hacked with N extra front-doors.  Inside a business, desktop machines should never have direct internet access. They should always go through a proxy. DNS from desktops shouldn't be able to resolve google.com or any internet address either.

I've seen lots and lots of your questions the last few months and assumed this was for a lab deployment at home for all the remote desktop stuff.  That is completely different than doing this stuff for a business where downtime means money lost.  Also, you don't need/want 1 virtual machine desktop for each end user from what I recall being said across the 20+ threads.

It isn't possible to get the correct answers for a total solution like you are considering through forums.

ll do the testing and scaling up slowly.

First, I would like to thank you for really answering my questions on the more than 20+ threads Ive been writing on.  The system Im doing is a work in progress, and a lot has already been put up, a lot of it is already working because of your answers from the previous posts.  It is why I am very thankful.  But I still dream of new stuff and want to really improve our system.

I do have someone in mind who might be able to help.  He was my teacher at the linux administration course I took up and we used only Virtual Machines for our course...

TheFu, you have mentioned before in a previous thread that I should just hire someone... Well I actually did and got very disappointing work.  The guy promised me a linux server but installed Windows 7 instead.  I found another one who did Centos and his demos were good but his contract stated that we were to pay him a small amount for every document we print, and every test we performed, and every small item we sold...  Our lawyer junked it.  The new guy we hired just uses Windows server and VMware, and he tells me he just wants to be a consultant to help us save costs.  So Im basically converting his advice from his Windows centric / VMware Esxi versions into Linux ubuntu versions.   He was the one who proposed using VM's for separate DHCP, DNS server, and File Server into our network...but it also got me thinking....Why not VM entire desktops as well for our offices that do not really make use of heavy applications?  We are currently moving to a new data room and we are recabling, so im now deciding what switches and cables to use, so thus this question in this thread.

But just a case in point about my idea... We do have some experience with this...  About 4 years ago, we had purchased Windows CE thin clients for our school lab.  So the School Lab had a Core i7 running Windows 7, and it had 2 LAN ports.  LAN port 1 was connected to the internet, LAN port 2 connected to a switch which had 4 ports gigabit speed and 24 ports of 100mbps speed.  The Thin clients only had 100mbps LAN ports.  So the thin clients would be connected to the 100mbps ports of the switch and one of the gigabit ports of the switch would connect to LAN 2 of the server.  I think we ran like 25 thin clients to a server.

The server ran Windows 7, and each of the thin client would log-in simultaneously as individual users via RDP.  This actually worked well enough for teaching.  Now, MS used to allow this setup but changed their EULA and no longer allows this, so we had to stop the system.  The issue of course is having multiple users running on a non server Windows OS at the same time.  I've attempted to use the thin clients on Ubuntu but it doesn't work consistently.  Now this new proposed idea I have using VMs legally goes around this problem.  Instead of having a single windows install where many people will login into, I will have multiple windows installs in VMs and having only 1 user logging in per window install.  We have to license each VM of windows, its given.  Of course this thread is not about windows licenses so Ill end my discussion on this here...  But by using RPis running ubuntu instead of Windows CE clients, I can further extend this to the ability to remotely access an ubuntu desktop within the LAN as well.

As  for the proposed setup, I can't find those switches anymore that has 4 ports gigabit speed and the rest as 100mbps.  But the setup I described With a VM running a desktop OS having 1 port for the internet and 1 port for the remote access thin client is basically the same as the one in the computer lab I described above, except that we will have multiple VMs running on the server instead of having just 1 install.  Now as for DNS servers and security, we can still connect or route Port 1 of each VM into a firewall, and/or DNS server so I will have to take care of that part separately.  In this concept the thin clients (RPis) dont have direct internet access, they are only connected to the server via LAN.

---

### Post by TheFu on 2019-06-19
I would use SPICE, not RDP, unless your testing has proven that didn't work well.  SPICE should make the remote desktops behave with great performance.  There is a catch. SPICE only works from KVM guests. But it should work for any guest VM - Windows or Linux or BSD or ....   vinagre is the easiest client-access tool for it.  RDP has lots of security issues.  With SPICE you can use either ssh or TLS for channel encryption.

Again, I'd probably have 10-20 clients for each desktop VM, not a 1-for-1. That just seems wasteful and unnecessary.

When you get this all done, you will be the expert.

---

### Post by lammert-nijhof on 2019-06-19
Some simple remarks:
- I said hire a professional not a con-man. Even better being a school try to find professionals under the parents at your school. Try to organize a group of parents with IT experience. 
- Why continue with Windows 7 and Windows CE, their maintenance stops in 2020 and they will be very insecure after that. Don't use obsolete stuff!!!

Stop thinking about solutions! Start thinking about the requirement of the school for the coming years. For what do they want to use their computers? What do they like of their current system and what functionality do they want to add. 

And some direction about finding solutions:
Do they need Windows or could you use Linux? Could you use ex-lease computers with a 2nd, 3rd or 4th gen i5 processor, instead of Thin Clients for the job? If you buy 10 or 20, you could get the price down from the $50, they are priced now at Ebay.

---

### Post by webmiester on 2019-06-22
> **TheFu said:**
> I would use SPICE, not RDP, unless your testing has proven that didn't work well.  SPICE should make the remote desktops behave with great performance.  There is a catch. SPICE only works from KVM guests. But it should work for any guest VM - Windows or Linux or BSD or ....   vinagre is the easiest client-access tool for it.  RDP has lots of security issues.  With SPICE you can use either ssh or TLS for channel encryption.

Again, I'd probably have 10-20 clients for each desktop VM, not a 1-for-1. That just seems wasteful and unnecessary.

When you get this all done, you will be the expert.

I agree with having multiple users per VM instead of 1 is to 1.  The 1 is to 1 is due to software licence issues.  With Linux, it's not a problem.

---

### Post by TheFu on 2019-06-22
Windows terminal server (Remote Desktop Server?) is much cheaper than Windows licenses.  Plus there are fewer systems to patch.  People run that with 20+ users, no issues. [https://arstechnica.com/civis/viewtopic.php?t=1244319](https://arstechnica.com/civis/viewtopic.php?t=1244319) Jim Salter knows his stuff.  Lots of others in that thread doing remote desktops to Windows too.

---

### Post by webmiester on 2019-06-26
> **TheFu said:**
> I would use SPICE, not RDP, unless your testing has proven that didn't work well.  SPICE should make the remote desktops behave with great performance.  There is a catch. SPICE only works from KVM guests. But it should work for any guest VM - Windows or Linux or BSD or ....   vinagre is the easiest client-access tool for it.  RDP has lots of security issues.  With SPICE you can use either ssh or TLS for channel encryption.

Again, I'd probably have 10-20 clients for each desktop VM, not a 1-for-1. That just seems wasteful and unnecessary.

When you get this all done, you will be the expert.

I checked out SPICE.  It looks really cool!  Thank you for the referral.  Ill go try it out.

---

