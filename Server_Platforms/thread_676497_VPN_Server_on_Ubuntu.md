---
title: "VPN Server on Ubuntu"
date: 2008-01-23
forum: Server Platforms
---

### Post by eolatunde4 on 2008-01-23
I would like to config my server as a vpn server also.  I have installed openvpn using sudo apt-get install openvpn

However, I don't quite understand the instructions on the openvpn website.  Can someone break it down specifically for Ubuntu server as the VPN server and xp as the client?

I know I'm supposed to create a file with config info in it, but I don't know how to do that.  I am brand new to linux so instructions in "dummy" terms would be great!

Thanks

Emmanuel

Oh, my LAN is setup for 192.168.2.X

---

### Post by HermanAB on 2008-01-24
Hmm, when I hear VPN, I always ask why?

The reason is that a VPN is frequently not what is needed, especially if you are using Linux.  Chances are about 110% that what you really need is SSH.

Cheers,

Herman

---

### Post by dannyboy79 on 2008-01-24
> **HermanAB said:**
> Hmm, when I hear VPN, I always ask why?

The reason is that a VPN is frequently not what is needed, especially if you are using Linux.  Chances are about 110% that what you really need is SSH.

Cheers,

Herman
I wish I could help but I can only provide my 2 cents regarding Herman's comment.

well, chances are that he may understand what a VPN does for a person and he does have an entire network he wants access to and not just one computer.

I have 5 networked computers in my home and granted I could setup a VPN if I wanted to but I don't want to spend the time to set it up. BUT it would allow me to have access to all the computers on the network without having to run ssh servers on each one and then hop from one to the other to get my files and what not.

---

### Post by HermanAB on 2008-01-24
Yup, there are also cases where a VPN is indeed what is needed, except that it won't work in practise.  For example, accounting programs generally don't work over a VPN.  VPN's also don't work over satellite or cellphone links and so on.

So we need more info...

Cheers,

H.

---

### Post by Maxtorm on 2008-01-24
To be clear, when it comes to accounting programs -- or any programs  for that matter -- we're talking about two different layers of the OSI.

VPNs work over satellite and though broadband over cell is still less than ideal, a VPN can be configured to work over it as well. Once you have a VPN set up, it is not unusual for individual users to access the VPN over lower bandwidth connections. Bandwidth starts to become an issue as you add users behind a particular node of the VPN.

Getting back to the original poster's question, I have not set up an OpenVPN server, but have been told by someone who did that the following tutorial was helpful: [http://www.informit.com/articles/article.aspx?p=605499](http://www.informit.com/articles/article.aspx?p=605499)

---

### Post by Herman on 2008-01-24
SSH is great, I'm a big fan of SSH.

---

### Post by eolatunde4 on 2008-01-25
Thanks for the feedback.  I do know what VPN would do, and purpose.  I do have a network of computers that I need access to away from the office.  I would like to eventually added more HDs to my Ubuntu server and have everything stored there, but currently that is not an option.  Right now for the amount of data that I I'm using is spread out between the different pcs hds just do to space constraints.

I read about the benefits of SSH on a different thread.  But does anyone care to elaborate a bit on why they would prefer to use it over VPN?  

My company mainly does graphic design work and we deal with a large files.  The purpose of the VPN was to be able to access and files on the fly from remote locations.

---

### Post by HermanAB on 2008-01-25
Like SSH, OpenVPN is based on OpenSSL, a BSD project.  However, whereas OpenVPN is used to build static VPN links between sites, SSH provides a VPN on demand.  

With SSH, you create a VPN when you need it and tear it down when you are done with it.  SSH can also do a bunch of things that OpenVPN cannot do.  In effect, SSH is a far more powerful and flexible solution, which also happens to be easier to use.

All Unix machines have SSH daemon running by default - well, all except schtooopiddttt Ubuntu.  So, using Nautilus or Konqueror, I can easily connect to any other Unix machine in the world that I happen to have access to and set a bookmark on the relevant directory - so if I need to go there again, I just go to the bookmarks and click it.  I am instantly connected and I don't have to worry about keeping the VPN link up, weird connection time-outs and inexplicable VPN interruptions.

SSH also allows me to run programs remotely, so I can log onto another machine and launch any program - text or GUI based.  Sometimes, I am logged into three or four machines in different cities at the same time.

Finally, since SSH only connects what you want to connect, it is faster than a static VPN, which can get flooded by ARPs and other network crud.

On the whole, I find SSH to be more flexible and less trouble than a VPN.

Anyhoo, just my tuppence worth.

Cheers,

Herman

---

### Post by Herman on 2008-01-25
Why I prefer to use SSH rather than VPN is mainly because it's so simple, it only takes a few minutes even if you are a linux beginner, to set it up and go.

I haven't tried out OpenVPN myself, but from what I have been reading about it I have the opinion that it's a more complex way to do the same job.

Maybe I'm just lucky, but my standard $100 router already came with features I can easily configure so that I can easily ssh into all the computers in my LAN from a remote connection.

I'm not sure what to say about your requirement that you need an XP computer to be the client though. I suppose you can use [OpenSSH for Windows]("http://sshwindows.sourceforge.net/")  for that one.

Have you got a router? Or are you planning on using a computer with two network cards?

Regards, Herman :)

---

### Post by dannyboy79 on 2008-01-25
since both of you are advocates for ssh and even state that you can ssh into multiple customers at once, maybe one of you can explain how to ssh into a box that's in a private network that doesn't have a FQDN? A private network only has one externally available IP address that you can register a FQDN to, so how would you get to the other machines without having to first connect to the one, then hop over to the others. Isnt that the advantage of VPN? not to mention, now you have to setup ssh on each and everyone of the computers right?

---

### Post by HermanAB on 2008-01-25
One way is to forward different ports to the machines on the inside:
2210 = 192.168.1.10
2211 = 192.168.1.11
and so on.

Also, note that it is only on Ubuntu where you have to specially install sshd.  Every other self respecting *nix system has it running by default.  Once you have a connection up, just set a bookmark in Konqueror or PuTTY or whatever you use to connect.

Cheers,

Herman

---

### Post by dannyboy79 on 2008-01-25
> **HermanAB said:**
> One way is to forward different ports to the machines on the inside:
2210 = 192.168.1.10
2211 = 192.168.1.11
and so on.

Also, note that it is only on Ubuntu where you have to specially install sshd.  Every other self respecting *nix system has it running by default.  Once you have a connection up, just set a bookmark in Konqueror or PuTTY or whatever you use to connect.

Cheers,

Herman
so you'd have to know the ip address for this to work since you would have to type in 69.154.43.24:2210 correct (or to connect to another server 69.154.43.24:2211)? Or can you also enter say [http://mycomp.getmyip.com:2210?](http://mycomp.getmyip.com:2210?) I was unaware that you could do that if you can. 

Also, I don't see a default ssh server setup on all self-respecting *nix (as you put it)  boxes as a very secure idea at all since there's really no way to have the default setup using private/public keys and/or passphrases. Having a ssh server running only using PAM is a sure way to get hacked with all the brute force attacks that occur every second on any given ssh server's door. Next you're going to tell me that all self-respecting *nix distro's have samba listening on all interface's by default as well, which again is very insecure.

I don't want to get into an arguement about this but you have to realize how insecure a distro can be when it enables all this stuff by default, then you get newbies who have their machines hacked and files deleted and then just go back to winbloz.

---

### Post by robert_pectol on 2008-01-25
Although I agree that SSH is very easy and will suffice for about 90% of the remote access scenerios that one would come across, I can't say that I'd agree that it is a complete replacement for a good VPN.  As already pointed out, you begin to add a level of complexity to the remote networks when the machines to be accessed are behind NAT devices.  This includes ensuring that the, 'internal' machines are set up with internal static IPs, whether they be dynamically assigned based on MAC address, or just hard-coded in the networking config files.  And then there's the issue of establishing the correct port forwards to the right hosts, etc.  On a network with more than just a small handful of hosts to be remotely accessed, it becomes a pain to have to remember which port I need to connect to, in order to connect to which host!  But even if that were the extent of the added complexities involved with relying upon SSH alone, it might probably be worth it.  Unfortunately though, there are other factors to consider.  What about remote access to Windows hosts on the internal network?  Let's face it, many networks have more Windows hosts than Linux hosts (unfortunately).  Now I have to install and configure a SSH server on those hosts too?  What about SMB shares on those hosts?  Will I be able to easily access them somehow with SSH, without a bunch of extra configuration?  As you can see, it really begins to complicate things.  What started out as a simple approach to solving the problem has become more complicated than just setting up a VPN!  My take on it is this;  If you are accessing single Linux Hosts on public networks, or even accessing a small number of strictly Linux hosts behind a NAT router, then SSH is probably worth using as it will allow access to just about everything with a moderate amount of configuration.  But if your requirements involve remote access to many hosts behind a NAT router, especially in a mixed Windows and Linux network, the VPN is by far the best choice.

As far as VPNs go, I prefer OpenVPN.  It works quite nicely over satellite Internet, cellular broadband, and even dial-up connections (although painfully slow).  In fact, I've never had it NOT work from any of the vast places I've needed to access it.  I've used it from all over Europe and North America without any issues.  I'll agree that it takes a couple of hours to go through the documentation and get it configured properly.  But once you have it set up and running, it just runs and runs.  I haven't had to even look at the configuration since I set it up!  It's just always there when I need it and my experience has been that it's extremely reliable.  Oh, and did I mention that I use it nearly every day?  Since there are OpenVPN clients for both Linux and Windows, I can access it from either platform.  It's pretty cool to be at some remote location and click on network neighborhood from within Windows, or view SMB shares from Linux, and be presented with all of my home network's internal hosts' network shares!  Pretty schweeeet indeed!  :-)

---

### Post by Herman on 2008-01-25
In my particular instance, I am trying to point out that my LAN router already handles VPN or has VPN functionality built into it. It's not a particularly fancy or expensive router, and it's not even a recent model. 
I actually got it at a reduced price, maybe it was old stock. It wasn't the cheapest router in the shop, but it certainly wasn't the most expensive by any means, it's just a good ordinary mid-range router. 
Would most good routers these days come with VPN capabilities or am I just lucky? 
I'll bet most router owners wouldn't even know what their routers can do because most people probably just plug them in and if they work they throw away the instruction manual without even bothering to read it.

So at least in my instance, there's no need for me to dedicate a separate PC to the task of acting as a router and struggling through a lot of complex instructions. 
I only need to install SSH server in each of my computers and that only takes a few minutes each.
If you want to see how simple it is, just click on this link for an illustrated guide that even a child should be able to follow,[ http://users.bigpond.net.au/hermanzone/p11.htm]("http://users.bigpond.net.au/hermanzone/p11.htm")

Now, I don't have any personal problems with OpenVPN, if it's Open Source software then I'm in favor of it, maybe I can learn something here too. 
Here's a VPN HOW-TO that uses SSH, [http://tldp.org/HOWTO/VPN-HOWTO/](http://tldp.org/HOWTO/VPN-HOWTO/)
Here's the OpenVPN HOWTO, [http://openvpn.net/howto.html](http://openvpn.net/howto.html)

Open VPN uses SSL instead of SSH, apparently. Do all Windows come pre-installed with SSL? I know there is such a thing an SSH for Windows, and I know we can easily set up a computer to dual boot Windows and Ubuntu in about half an hour. I admit not all Windows fans would want to do that just so we can communicate with them though.
Oh, I see, there's an .exe download they can click on to install something. 
I would imagine there would be an SSH installer made for Windows too though that they can click to install SSH for Windows.
Hmm, I see that one of the first questions is whether you're going to use a router or a bridged connection eh?

The original poster was complaining about how difficult it is for an ordinary user to set up OpenVPN and asking for help.
So far no-one has actually been much help, but then on the other hand, we're still in the dark about hardware details.
That looks like a very long page of not very user friendly instructions to me, Will one of you VPN proponents walk Mr. eolatunde4 through all that?

Or is it simpler just to ask the following question, > Have you got a router? Which we're still awaiting an answer for.
Possibly he only has to open his router configuration in his web browser and click 'Enable VPN', tick a few settings, and install SSH.

Regards, Herman  :)

---

### Post by The Cog on 2008-01-25
I'm and OpenVPN fan myself. Its bombproof reliability and good performance have really sold me on it. SSH is quicker and easier for 1-1, but for access to a LAN/building etc, OpenVPN has to be the way to go.

For the VPN server, place a config file in /etc/openvpn. The filename must end in ".conf", and then it will be started automatically when the machine boots. It's creating the key and certificate files that's confusing, but just follow the howto exactly. Here is a viable config file. The supplied example file contains lots of text describing what each option is for. Its length can make it confusing so you can't see the wood for the trees. Here is the bare wood:> 
port 1194
proto udp
dev tun
cert myname.crt
key myname.key  # This file should be kept secret
dh dh1024.pem
server 1.2.3.0 255.255.255.0
push "route 1.0.0.0 255.0.0.0"
comp-lzo
user nobody
group nobody
persist-key
persist-tun
status openvpn-status.log
log-append  openvpn.log
verb 1
mute 10

Of course you must correct the certificate names and the IP addresses.

---

### Post by Herman on 2008-01-26
Thanks Cog,
I'll give VPN a try then, I'm curious if it really is any better than plain SSH, and since all of you VPN supporters have insisted so eloquently, I have decided to make the effort and give OpenVPN a try. 
I can already easily do everything I can imagine myself wanting to do using SSH, but a little extra knowledge can't be a bad thing and I'll have a little bit of spare time this week.
Thanks again, 
Regards, Herman  :)

---

