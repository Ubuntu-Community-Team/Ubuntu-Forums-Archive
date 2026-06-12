---
title: "Remote Desktop"
date: 2007-06-10
forum: Server Platforms
---

### Post by TorchlightJay on 2007-06-10
So I want to be able to manage some Windows systems with my ubuntu servers. These systems are not part of my network, as in, they aren't in my office and they aren't under my IPs (the windows systems that is).

What's the most convenient way to remote connect to a windows system with ubuntu? Like I want to be able to manage those computers from my office and run some programs like anti-virus remotely. I also want to be able to manage and view networks and firewalls. You guys know of any software like that, preferably open source. If  so that would be awesome. Thanks for all your help.

---

### Post by Mr. C. on 2007-06-10
There are a couple of methods, each has pros/cons.

1) Configure the Window's stations to allow Remote Desktop connections, and use Ubuntu's Remote Deskop connection utility.  This requires that you configure your router at the PC's location to allow incoming RDP connections.  The problem with RDP is that it takes control of the deskop away from any users at the desktop - their are essentially logged out, so to speak.

2) Configure each PC to make a secure connection back to your servers using SSH and tunnel.  This allows you to avoid configuring the remote router, but requires the PCs to establish the SSH connection, which means installing and configuring an SSH client on each PC.

3) Install VNC server on each PC, and configure the remote firewall to allow inbound VNC connections.  There is no security or encyrption here - use SSH above to provide a security layer.

4) There are third-party solutions that provide such remote access, via proxy connections. They act as a go-between so that no remote firewall configuration is required.

Probably the easiest solution is to run VNC server on each PC, configure the remote firewall to all you SSH access to one of the remote machines, and configure tunnels to each machine.  This will give you secure, remote access to each remote PC.

MrC

---

### Post by TorchlightJay on 2007-06-11
Sweet, thanks. Know of any good VNC server/client software for Windows or Ubuntu? Also do you know of anything good for Windows in terms of SSH. I have heard of putty but I am not sure if that would work cause it's more for clients right? If you can throw me some titles and maybe even tutorials, I would be very grateful. Thanks all.

---

### Post by Mr. C. on 2007-06-11
I use UltraVNC for Windows (both server and viewer).

I use Tunnelier for an SSH client on Windows.  Putty is fine too, however, configuration requires registry settings, where Tunnelier allows saved profiles, allowing much easier distribution of configuration settings.

To advise further, I need to understand what access you have or do not have.  Eg. do you have access to the remote firewall and can configure it ?  Are the remote PCs in use as desktop PCs (eg. you'd be interrupting an employees work if you took over control)?  Do you have a single remote system (Windows, Linux, Unix) in which you can setup an SSH server as the gateway into the organization?

MrC

---

### Post by TorchlightJay on 2007-06-11
Well as far as I know, these guys do not have firewalls in place aside from your run of the mill routers and whatever security they might supply (which is pretty much none at all). On our end we have a firewall but it's ours so we can edit it as we see necessary. However, we are putting in firewalls into our customer computers but we'll have remote control over those. 
    These desktops are used by employees regularly. What we'd like to do is have three options available to us. 1) we'd like to be able to just monitor things in terms of network attacks and maybe do some patch management, you know, be able to see if things are kosher and maybe fix things instantly. . 2) If something happens to their computers, we want to be able to fix it almost immediately. 3) Screen capturing to see what they are doing and if they are wasting company time or doing something wrong. For #2, it wouldn't really matter if we disturbed work, their computers are not working properly anyway so we need to fix it. 
       On our end, I have a computer that I will convert into an Ubuntu server and use it to run VNC and SSH and whatever else I need to run. It'll be our dedicated remote connection server (we might also keep customer data related to remote management on there but we'll see). We want to be able to connect to their computers anytime we need from our notebooks but work through our remote connection server. I don't know if that makes any sense but that's what we'd like to do. If you have any more advice or need to know anything else, just let me know and I'll be grateful to hear advice or answer more questions. Thanks.

---

### Post by netlogic on 2007-06-11
I enjoy tightvnc for a great compression. i like putty for windows for able to easily configure to tunnel to ssh servers. port forwarding is a snap with putty. if you don't want putty to touch your registry, i recommend portable putty. it was designed to be run off a thumb drive.

don't use VNC without ssh tunneling. decrypting vnc takes few seconds.

---

### Post by Mr. C. on 2007-06-12
I see no problems in setting up what you desire.

Do you customer a service - ensure that they get a perimeter firewall.  Desktop firewalls are not sufficient.

The basics are to setup the customer's SSH server to allow remote access to each system and a tunnel for VNC.  Install the VNC service on each client PC.

When you are ready for more help, post again.

MrC

---

### Post by TorchlightJay on 2007-06-12
Kewl, sounds great. So, do I need to install a server and put SSH in at the location of my customer or am I able to install some kind of client on each desktop? Sounds like I can put a VNC client on every desktop. Like I said, I wanted to make a server dedicated to us connecting to our customers. Are you able to manage things like windows patches? Also do you know of any good programs to monitor networks? You mentioned a firewall, know of any good open source firewalls? 

I want to start working on it asap so I want to be sure, do I need to make a server in MY office dedicated to remote management or is it even necessary or serve any benefit? Thanks for all of your help, I really appreciate it.

---

### Post by Mr. C. on 2007-06-12
> **TorchlightJay said:**
> Kewl, sounds great. So, do I need to install a server and put SSH in at the location of my customer or am I able to install some kind of client on each desktop?

If you want to be able to connect to the remote site reliably, then you will want a remote, stable machine, that is always up.  So, yes, install an SSH server on that machine, and configure it to allow gateway access.

> **TorchlightJay said:**
> Sounds like I can put a VNC client on every desktop. Like I said, I wanted to make a server dedicated to us connecting to our customers.

You will want to install and configure the VNC **server** as a service on each PC.

> **TorchlightJay said:**
> Are you able to manage things like windows patches?

You have will have the remote desktop in a window in your screen.  You have complete control.

> **TorchlightJay said:**
> Also do you know of any good programs to monitor networks?

Define "monitor".  Monitor for what?

> **TorchlightJay said:**
> You mentioned a firewall, know of any good open source firewalls? 

Smoothwall.

> **TorchlightJay said:**
> 
I want to start working on it asap so I want to be sure, do I need to make a server in MY office dedicated to remote management or is it even necessary or serve any benefit? Thanks for all of your help, I really appreciate it.

You can use any machine you desire to establish the remote connection.  It all depends on how you setup security in the SSH server and the remote router.  I manage my and other systems remotely from anywhere.

MrC

---

### Post by obimeister on 2007-06-12
We use UTM firewalls with our clients. They can do all sorts of nice things including email antivirus, spam blocker, blocking users from unwated www sites or network monitoring etc. And you can manage them easily over https. And they require little work to install and maintain which is important for us. And they got vpn server for remote management. If you watch prices ie for fortigate 60A or 100A they seem pricy but pay back in less hour work, less troubles, easier setup which all are imo important when youre doing stuff to client. 

For windows updates automatic updates are usually sufficient :)

I have installed a couple of commercial version of smoothwall but I'd still change them to fortigate or watchguard for less work and trouble.

---

### Post by TorchlightJay on 2007-06-12
Thanks, everything you guys are saying is really helpful and I appreciate it. I was wondering, how are we definining "server"? Are we talking about a machine sitting somewhere that is never used or at we talking about a machine with a dedicated IP? 

Example, one of my customers is a retail outlet. They have multiple locations all over town (like 10). Each one only has one computer but all have static IPs (just how their ISP works). They are all Windows XP computers and run SP2. These are used for all the orders and communication within the company, naturally. I don't know if it makes sense to create a server for every location but if I installed one of those VNC or SSH programs you told me about on any one of those systems would that suffice?

Otherwise, I am guessing we might have to make a server for our customers and make that the SSH server and somehow network all those systems to the one system. I just want to avoid having to put an extra machine in each location. We are beginning to pick up customers with multiple locations. I really want to avoid that and I am sure my customers want to as well. I was hoping that I could just make one or a few servers on my end and somehow link their systems to it and then we can connect to the server and do the VNC and SSH stuff.

Of course, that won't be a problem if we can just install the server software on the individual systems. As far as monitor, I am concerned with keeping employees out of things that they shouldn't be doing like certain websites and what not. Also it'd be nice to monitor attacks, of course that's what firewalls are for. Essentially just know where packets are going. 

Again, I have to thank you for all of your time and patience. Thank you.

---

### Post by obimeister on 2007-06-12
I don't know decent ssh server solution for XP, I'd use XP's inbuilt PPTP server and vnc. That would work for one machine/one connection situations. There is PPTP client for linux tought its gui made with php4. 

Then there are products like [[COLOR="Red"]this[/COLOR].]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416832495&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3249522279B04") You could put one of these in each location with vpn and then have one server somewhere which would be the central point for all site vpn tunnels. Then if you tunnel all traffic into vpn tunnel and made it flow to internet from central point you would have good place to monitor traffic.

---

### Post by Mr. C. on 2007-06-12
This is a very different scenario than was initial suggested or implied.  You have multiple sites, not one site.  They are all on different networks most likely, and therefore you will need an application / device at each location

Without a dedicated device or monitoring software on each system, monitoring/blocking the remote sites will be a headache.

Get a cheap firewall/router/VNP appliance for each site.  This will be far more manageable and under your control.

MrC

---

### Post by TorchlightJay on 2007-06-12
Cool, so the one recommended is one option, do you know of any other devices, out of curiousity? So as suggested I just refer or tunnel the devices to the main server. This is still something I am curious about, does it need to connect to THEIR server or connect to ANY server. 

Basically I want to know if every single business I work with will need their own server or if I can have those appliances tunnel to our server. Either way works, I just don't want to quote more than I have to or mess things up. I am trying to set up the most convenient yet efficient way. 

Sorry for all the questions, I am not an expert on remote management, hence the posts. Would you happen to know of a good online tutorial for what we've been talking about? I am sure there are many but some are good and some aren't so if you know of any, that would be great. Again, thanks all.

---

### Post by Mr. C. on 2007-06-13
I'm not sure its very useful for me to list all of the devices I am aware of that do the same type of thing as the device already mentioned.  If you are trying to price / feature shop, describe your list of requirements.  I think you can google search as well as I can.

You need some device or application at each site.  As I mentioned, it is unlikely that all the locations for your client's are on the same network, so you cannot setup one server at one site, and expect to use it to connect to all the rest.  Think of this like the telephone - you need a phone at each location and your own location to communicate.

It seems you are in over your head a bit.  Try setting up *one* such configuration before trying to recommend such a solution to others.

MrC

---

### Post by TorchlightJay on 2007-06-14
Ya, I am probably over my head but I like to learn, hence the posting and questions. I do have an environment to test in without the risk of you know, destroying someone's business or anything of the sort so I will use the environment, attempt to "master" it and then implement elsewhere. But let me run through and tell me if I am missing anything.

I want to install a VNC server on every single device I want to control as well as the machines I want to control from. On top of that, for security purposes, I want to allow for SSH tunneling. This requires a client on each computer that has a VNC server installed and of course a SSH server somewhere. I must tunnel the SSH to the server somehow, best case with a appliance like the one mentioned and have it refer to the server. Now I also need to do this for myself and create a server and SSH clients and so on. Once all is complete, I need to make sure I have a pinhole in the firewall to allow this connection and I connect and have control. 

Did I miss or screw up anything? Also, is it possible to manage applications in Windows with VNC or SSH solution or is that a whole different can of worms? And I was wondering, I use Linux for all my computers and I have seen like SSH servers in synaptic, can I just use that and make this notebook my ssh server for connecting to the clients (or in this experimental case, my test server?) Thank you for your time and assistance and your patience. I know dealing with n00bs can be annoying and I appreciate all of your help.

---

### Post by Mr. C. on 2007-06-15
Its hard to gage if you've got it, because of terminology issues.  So, I'll try to explain in a slight different way, and see if that crystallizes the concepts more.  Your goals are to:

1) Create a secure connection from your workstation (wherever in the world that may be) to each of your client's sites (all at once, or one at a time - the concepts are the same).  If they have office A, B, and C, you need the ability to securely connect to A, B, and C.

2) Establish a VNC viewer connection (you) to a VNC server (them); there is a VNC server running on each machine to be controlled at sites A,B and C (eg. machine 1 at A, machine 2 at A, machine 3 at B, etc.).

How you accomplish 1 is a matter of personal choice: the typical solutions are either a) SSH or b) VPN.  Both do essentially the same thing, which is to create a secure connection over an insecure network.  Many appliances have built-in VPN capabilities, whereas most do not have SSH servers built-in (thereby requiring you to configure and run an SSH server on at least one host at each site A, B and C).  A variation when using SSH is to run 1 SSH server at *your* location, and to have at least 1 workstation at each site A, B, and C connect to your server.  In either case, a tunnel is configured, such that (2) above can occur securely.

VPNs are more challenging to configure for a variety of reasons, but are more available, as mentioned above, in commodity hardware.  SSH is trivial to setup, but requires an SSH server at each remote location to allow you to pierce the remote firewall.

If I had a client with sites A, B, and C, and my goals were to simply control 1 PC at each site, I would opt for an inexpensive appliance such as the Linksys mentioned, that a) supported at least 1 VPN connection, and included a firewall.  There would be one of these at each site A, B, and C, connecting directly to the broadband or other internet providing connection.  This would allow me to establish a direct connection to each appliance securely, and then to make a VNC connection with my listener to the VNC server running on the machine at A, B, and C.  When the site a B, for example, expands to add more PCs, I would install another VNC server on PC2, PC3, etc.

Should you decide to go the SSH route, you will need an SSH server running on 1 machine at each of A, B, and C.  This allows you to establish your SSH connection, and then make your VNC connection via the preconfigured tunnel you create with SSH.

As to what you can manage with VNC - think of yourself being physically at the desktop(s) at site A, B, and C.  You can do what the user sitting at the workstation can do.

Make more sense?
MrC

---

### Post by TorchlightJay on 2007-06-15
Ya, I think it does. So it sounds like we are using SSH to connect to the network, not neccessarily the individual machine, we want to make the connection between networks secure hence only requiring one machine. I am familiar with SSH and I use it almost all the time when I am doing Linux to linux (thank you command line). So when you say SSH, I am trying to apply what I already know to this concept. I am guessing that most VNC software and viewers enable you to encrypt with SSH so I just need to create a tunnel and connect using VNC but with the security of SSH (or VPN if the situation calls for it). 

Sounds pretty straight forward, I just need to find a device that supports VPN or install SSH. then I use VNC to take advantage of the secure connection between the systems. So let's say that right now, I wanted to connect, first I'd activate an SSH connection then I'd activate VNC, in that order, or is SSH something that is consistently active? I don't think it is but I can be wrong because I always have to type sudo ssh [email]black@blah.com[/email] to connect then I have a connection. Sounds like i have it and I shall get working. You answered my windows question about SSH and VNC software, there are tons of them in syanptic and sourceforge, any word on software to get from them. Thanks.

---

### Post by Mr. C. on 2007-06-15
I think you're are nearly there.  Your summary is pretty accurate.  I'll clear up what might be misconceptions I see from the loose language.

You use SSH to connect to a single machine (linux system, appliance, whaterver), not "the network".  SSH always connects one machine to another.  This connection however does provide the opportunity to access other machines on the same network via that secure connection.

Simplistically, a VPN "extends" the remote network, or host, into your offsite location, making itself available to your system locally.  Eg. if you setup a VPN connection to a remote site with network address 10.0.0.x/24, your system will receive an IP address in the 10.0.0.x/24 range and it will make your system itself appear to be on the 10.0.0.x/24 network.

Don't think of the VNC server or view as providing *any* security.  While some implementations do, ignore this.  You are providing your own security via either SSH or a VPN.  Your viewer-to-server connection will pass through an SSH tunnel, which you will configure on the remote SSH server at each site. VPN is none-the-wiser.

You have the order of "activation" correct.  Make an SSH connection to the remote site (either providing you with a remote login shell or not) , and then you start your VNC viewer and ask it to connect to localhost:5900.  The tunnel makes it appear to the VNC view that the remote server is actually on your own machine locally.  That's because the SSH software intercepts the connection attempt, and pushes it through the tunnel to the other side where the SSH server is running.. which then passes it to the VNC server on the remote system.  Voila!  As long as you keep the SSH connection alive, you will have access via the tunnel to the remote site.  Once you kill the connection, the VNC connection will also drop.  If you kill the VNC session instead, the SSH connection continues to live, and is available to your for future VNC connections.  It remains active until you kill it.

MrC

---

### Post by dannyboy79 on 2007-06-15
sounds to me like all the different stuff you want to do at each site (monitor it's web traffic, alow/disallow certain sites), you just need a super high quality software firewall which acts as a server as well for remote management OR hardware firewall.

Then as far as needing to administor the actual computer, I use tightvncserver and stunnel on my brother's WinXP Home SP2 machine to help him with it once in while. ([http://www.ibm.com/developerworks/linux/library/l-sslvnc.html](http://www.ibm.com/developerworks/linux/library/l-sslvnc.html)) 

If all your customer's sites could somehow connect to a central location prior to hitting the net, you would then be able to monitor all of that stuff at once.
Have you set the computer so that most stuff can't be done without the Admin Password, otherwise they could obviously change the software firewall properties unless there would be some way to only secure that app from changes occuring to it?

None the less, this sounds like a challenge. Here's a thought and I don't even know if it's possible??
Can you somehow make each windows computer be able to only send requests (packets) for info to a Proxy Server that you're sitting in front of, then that Proxy Server would see what it should allow thru or what it should go get frmo the internet and return it. This would allow you to see all the traffic flow thru one central place BUT like I said I don't know if that's even possible???

---

### Post by TorchlightJay on 2007-06-15
Ya, I do want to do different things but my main priority is the ability to do repairs and manage systems remotely. I would like the ability to content filter and web monitoring but that can wait. I guess I could ultimately make a proxy as stated, in theory it sounds like it might work. Ya, I know there are things out there like ZenWorks or whatever to do everything but you know, i want to try and do an open source solution. 

I shall try what Mr. C said and hopefully I can get it working. There is one thing I am curious about, I have never tried ssh and scp with Windows, can you transfer files from Linux to windows and vice versa via SSH and SCP? Oh ya, my original question, what is a good vnc and ssh program for Linux? Like can I use command line in Linux to connect to say Tunnelier or Putty in Windows or is it just a good idea to do Putty to Putty? Same for VNC, I want to use a simple yet powerful tool. Know of any? Thanks.

---

### Post by Mr. C. on 2007-06-15
> **TorchlightJay said:**
> ...There is one thing I am curious about, I have never tried ssh and scp with Windows, can you transfer files from Linux to windows and vice versa via SSH and SCP?

Yes

> Oh ya, my original question, what is a good vnc and ssh program for Linux? Like can I use command line in Linux to connect to say Tunnelier or Putty in Windows or is it just a good idea to do Putty to Putty? Same for VNC, I want to use a simple yet powerful tool. Know of any? Thanks.

Yes, command line ssh connects to any SSH [edit: server].  Use the native SSH command line client.  Use the built in VNC viewer in Ubuntu if you want - its fine.  Its just called Remote Desktop.

MrC

---

### Post by TorchlightJay on 2007-06-15
kewl Mr. C, thanks for all your help, I think i am going to try this weekend and see what happens. I really appreciate all of your help.

---

### Post by dannyboy79 on 2007-06-16
> **Mr. C. said:**
> Yes



Yes, command line ssh connects to any SSH client.  Use the native SSH command line client.  Use the built in VNC viewer in Ubuntu if you want - its fine.  Its just called Remote Desktop.

MrC
The command line ssh connects to any SSH SERVER, I believe is what you meant to say. Also, the Remote Desktop built into Ubuntu is very slow, plus all you need on your box is a viewer not a server. You'll need the server on the windows boxes and if you want the free route, I said earlier, tightvncserver is great!

---

### Post by TorchlightJay on 2007-06-16
> **dannyboy79 said:**
> The command line ssh connects to any SSH SERVER, I believe is what you meant to say. Also, the Remote Desktop built into Ubuntu is very slow, plus all you need on your box is a viewer not a server. You'll need the server on the windows boxes and if you want the free route, I said earlier, tightvncserver is great!

Well let's say I had an executable file for say an antivirus program. It's on my notebook and I want to install it on 10 computers. I can SCP the file to a server but how would I get it to the individual PC's I want to install it onto?Also, you mention Remote Desktop being slow, well what's a decent speed one? Thank you.

---

### Post by dannyboy79 on 2007-06-18
> **TorchlightJay said:**
> Well let's say I had an executable file for say an antivirus program. It's on my notebook and I want to install it on 10 computers. I can SCP the file to a server but how would I get it to the individual PC's I want to install it onto?Also, you mention Remote Desktop being slow, well what's a decent speed one? Thank you.
you would do the same SCP to the individual computers. As we have said, each of your individual computers will be running SSH servers as well as Remote Admin Servers, like I said, tightvncserver is very good for WinXP home or Pro, i have experience with it.

AS far as what viewer or server fast, I haev already stated, tighvncserver on the 10 individual windows computers and tighvncviewer on the computer you want to view them from, whether that's your laptop or your server it doesn't matter.

---

### Post by TorchlightJay on 2007-06-18
Sweet, didin't know that ticghtvncviewer was a Linux think. I am not much of a Windows user so ya. Well I'll let you know how it works. Oh, I was wondering, no one commented on the proxy idea for montioring. Does anyone have experience doing that? It sounds like it should work in theory but I am not sure if anyone has tried it or has experience. Thanks all.

---

### Post by TorchlightJay on 2007-06-29
hey, I am testing this out and am running into a small error. What do I do if tehre is say, five ocmputers on a network. Like let's say that the ISP provided them with a single IP address and through the magic of a router, they were able to give out internal ip's of 192.168.*.*, how would I connect to individual machines on that network using that one IP? Thanks all!

---

### Post by dannyboy79 on 2007-07-02
bascially you forward port 22 (or whatever port you want) to the port that you have ssh running on. For example, say you want to keep the internal machine running the std port of 22, but you don't want to open port 22 on your router because it's a commonly attacked port. Some routers you can forward a certain port, for example 3500 (or anything above 1024) to port 22 on any of the machines running ssh servers internally. My router can't do that unfortunately, so I can only forward a port to the same port that the ssh seerver internally is running on. BUT you can change the ssh port within sshd_config so if your router is like mine, you can just port forward port 3542 but make sure that your ssh server is listening on that same port.

Then all of the machines, the ones that you AREN'T port forwarding to can run the ssh server on the normal port 22. and you merely ssh into them from the  first one. It's actually pretty cool. You could always run each machine on a different port and forward each of the 5 different ports from your router to those interanl ip's but that would just be silly because then not only is 1 computer being banded on by brute force attacks, but all 5 of them are so I would only suggest opening up 1 port to one machine, then once you're in that one, you can ssh over to the next using the same command but instead of using the external ip you used originally, you use the internal ip's of the other computers. good luck

---

### Post by TorchlightJay on 2007-07-03
I think I get what you are saying Dannyboy. One of my systems has no router whatsoever, it's just one computer in the whole building so a router was superfluous. I ran OpenSSH for WIndows and it's working just fine, not unlike normal OpenSSH. Now I am naturally using the default port 22 when I SSH. Where would I change the config file if I wanted ssh to use port 3500? And let's say I get it to use 3500, how would my computer know to connect to 3500 hundred? would I just append it to the end of the host IP?

Also maybe you can help me here too. How do you tunnel with SSH? I honestly have no idea. I finally have ssh and vnc running but I can't figure out how to create a secure connection? Maybe you know how to create a tunnel or whatever. Thank you.

---

### Post by dannyboy79 on 2007-07-03
first of all, make sure that the computer that is connected straight to the internet (no router) has a great firewall and virus protection. I can't tell you how to change the port that the ssh server runs on within Windows but like I said, for linux, it's within /etc/ssh/sshd_config. You can gogle that, just type in "windows openssh port change". 
Yes, then when using the client to connect to it, you have to specifiy the port, so it'd be ssh username@ip:port EXAMPLE: ssh joe@54.67.432.21:3500

Tunneling is da bomb! That's how I connect to all my services which are running behind my router, I only allow port 22 thru the router and I open a tunnel. Using putty thru windows is easy (here's the guide: [http://vortex.brynmawr.edu/vnc/](http://vortex.brynmawr.edu/vnc/)) 
and using ssh client thru linux command line is pretty easy to, (here's the guide: [http://ubuntuforums.org/showthread.php?t=457552&highlight=tunnel+vnc](http://ubuntuforums.org/showthread.php?t=457552&highlight=tunnel+vnc))

---

### Post by TorchlightJay on 2007-07-11
hey, I have a router here that has the option of PPTP. Is that something worth considering when trying to remote connect to a network using my Linux box(es). Basically the entire network is behind this one router and it's a pretty awesome router which allows for VPN (as we have talked about earlier) but I also noticed that PPTP. Can someone fill me in on the whole PPTP thing and how it plays in with all of this or if it's even worth considering. Is there a client I'll need on my end (as well as the computer I am trying to connect to)?

On the flip side, I do have the VPN, aside from setting everything up on the router, is there anything I need to do on the individual machines or my notebook to utilize the VPN as I try to use VNC? a lot of questions i know but i m just curious. Thanks.

---

