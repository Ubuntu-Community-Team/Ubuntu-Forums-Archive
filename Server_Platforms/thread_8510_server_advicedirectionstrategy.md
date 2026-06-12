---
title: "server advice/direction/strategy"
date: 2004-12-18
forum: Server Platforms
---

### Post by trico on 2004-12-18
I will be venturing off into using Linux/Ubuntu as a server for our church and before I do I would like to solicit suggestions from the Ubuntu community on how to best approach it.

Here's the situation:
- a modest network of windows xp systems (about 10 or 11) networked together (cat 5 ethernet).   
- a 256 kbit/sec dsl connection to the internet.
- domain, email and website hosted by yahoo
- one of the systems is windows xp pro and acts as a file server to the others
- the rest of the systems are windows xp home and acts as client systems.

In parallel to the above, we have about 6 to 8 additional computers used for education.  They are not networked to each other and are not connected to the above office network.

I'm sure it will be irrestable for some to ask why we're not using linux on this network.   It's a question of the knowledge of the volunteers and many part time workers at the curch.  They do have some small skill (such as it is) in ms office, and windows xp, but linux is beyond their abilities.

The problem I'd like your help with is this:
1) Network the education systems and allow them access to the internet sharing the dsl link we're using for the office systems - and NOT allow them access to the rest of the network where our data resides.
2) Similarly, I'd like to add an open (unsecured) wireless access point that will allow our church members with wireless laptops access to the internet through the same dsl link and NOT allow them access to the rest of the network.

The reading I've done so far indicates that this can be done with a Linux box acting as a NAT router on the network. Good idea?  bad?  Got a better idea?  How do I get started?  Can you point me to some documentation that will help me get it implemented.

Thanks,
trico

PS: I realize the wireless request above may sound a bit strange.  What are these people doing surfing the net at church? - why aren't they singing, taking communion, reading thier bibles, etc?  :-)   

We have a program in our community here in the south of Minnesota where we open the church up to overnight stays to help homeless families, and church members are there throughout the night as a part of the program.  While they are staying overnight, our members want to bring their laptops along and do a little web-surfing.  Perfectly understandable.

---

### Post by Hellsteeth on 2004-12-19
This is a big subject and may not be answered with simple posts. However I would begin with the concept of having two linux boxes. One sitting in a dmz part of your network and the other inside your network on the safe side of your firewall.

All the users that just want internet access only would be networked into the dmz server. In the dmz server you would run DHCP (to auto configure all visiting laptops), and SQUID (proxy server). You could also run DansGuardian which would allow you some control as to what sites are accessed.  Your wireless AP would be plugged into this box’s network as well. You should also run a soft firewall like Firestarter.

Your other linux box inside your network would run a different subnet to the dmz server and would run at least SAMBA to provide a central common place for all your Windows PC’s.

Good luck

---

### Post by sime on 2004-12-22
Do one think at a time. Make a plan, and change things once at a time. 

The easiest thing I find is to start off with is setuping up a proxy server using SQUID. Then do file sharing, DHCP etc.

---

### Post by britishtrident on 2005-01-03
Two requirements a server and partitioning + protecting the network   -- for the server you have found ubuntu, here is how I would do the networking side 

I would split the network using an IPCop firewall box set up to have two  green  networks   ---  both protected  by the IPCop firewall from the internet   by the IPCop firewall but unable see each other. IPcop is free very easy to set up and will run on just about any old 586 or better hardware once setup it dosen't need a keyboard or monitor  --- the friendly guys at the IPCop Forum  will help you with this   --- it is really very easy.   I should add   IPCop includes SQUID and DHCP  and DNS relay  -- already configured and set up. I should add IPCop 1.4 installs out the box with 4 network interfaces  Red = internet,   Green = internal  protected, Blue = wireless, Orange = DMZ  but the orange can be setup as an additional protected internal network.

Again if I were doing  once it was running I would  install CopFilter on the IPCop  box to filter spam and other unwanted garbage --- also very easy but more memory and a faster processor required than for basic IPCop.


Other considerations spring to mind such as the need to throttleband width so that no single PC can hog the internet link.

---

### Post by machiner on 2005-01-08
Your server question is cake - you will get your answers here, this forum is terrific. If you get no response - email me, I'll call you and we'll get this thing done -- but be warned, I'm a penny-pincher, and I will suggest cost effective ways for you and your church to accomplish your goals.

Yahoo ain't part of it, either.

Good Luck

---

