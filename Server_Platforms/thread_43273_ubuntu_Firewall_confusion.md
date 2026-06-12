---
title: "ubuntu Firewall confusion"
date: 2005-06-21
forum: Server Platforms
---

### Post by mcewen98 on 2005-06-21
I have read so many different posts about Ubuntu's lack of a "firewall" and therefore is not a good choice to use as the basis of a server.  I recently decided to use Ubuntu for my home server, because I was looking more of a hybrid - a server based upon Debian, as well as a more general usage linux box to run apps from that would recieve regular security updates.  I did a standard install of Ubuntu with Gnome and installed Firestarter and it has been working flawlessly and fast.

So now onto the confusing part.  Is it technically incorrect to say that Ubuntu does not "come with a firewall"?  Isn't iptables the building blocks for the firewall in the Linux kernel?  Ubuntu does come with this, so isn't Firestarter just a GUI that sits on top of Iptables and makes it easy to open and forward ports.

Wouldn't the correct thing to say be, "Ubuntu comes with a firewall, except it is locked down to all incoming traffic by default and there's no easy way to change it".  If it did not have a firewall at all, that would just not make any sense.

Am I wrong or confused about any of this?

Thanks,
Spencer

---

### Post by LordHunter317 on 2005-06-21
No, you're confused.

Ubuntu doesn't ship with any firewall policy OOB.

That's because it has no listening services enabled OOB.  Meaning there's no need for a firewall: why block if there is nothing there.

If you setup your own services, you will likely need to setup a firewall to secure them, and the tools are there.

---

### Post by az on 2005-06-21
Another way of looking at it is that the linux kernel is the thing that handles packets.  A firewall is a thing that handles packets in a certain way.

So, you just need something to help you configure the way the kernel handles packets.  By default, you are secure, because nothing in userspace puts you at any risk.  The moment you run something in userspace that listens to the outside world, you may consider more security.

Personnaly, if you are just going to install a firewall and open up the one port that you need to use, I do not see the point.  It is like using an umbrella and cutting a hole in it to let in the one drop of rain that is falling on you.

---

### Post by mcewen98 on 2005-06-21
[QUOTE=azz]
Personnaly, if you are just going to install a firewall and open up the one port that you need to use, I do not see the point.  It is like using an umbrella and cutting a hole in it to let in the one drop of rain that is falling on you.[/QUOTE]

Thanks for the info.  That makes more sense.  Regarding the quote above...   would apache be able to listen to the outside world by default without first configuring Firestarter or Shorewall to open port 80?

I installed Firestarter first when I did my setup, then installed the rest of the apps (mysql, apache, samba, etc).  [I am pretty sure that if I turn the firewall off in Firestarter, these services can no longer be reached from another machine.] -- This I was wrong about, stopping Firestarter seems to allow all inbound and outbound connections --

Spencer

---

### Post by knathraak on 2005-06-21
Just want to clarify a few things.

All linux distros come with a firewall and have since kernel 2.0 (or before).  Since linux 2.4, the firewall built into the kernel is iptables.  

Unless you give iptables some rules, it allows everything.  Tools like firestarter are not firewalls themselves but utilities to make it easier to configure iptables.

Host-based firewalls like iptables don't just prevent incoming traffic to listening services, they also have the ability to prevent outgoing traffic.  This is especially in environments like windows where viruses and spyware are prevelent and could be "calling home."  But it's important on any system to ensure nothing is exfiltrating data without your knowing it.  Generally it is best to start with a "deny all" policy and one by one add "allow" rules for each thing that needs to talk or listen on the network, but this can be a lot of work.  Also if someone gained user but not root access to your system, they could set up a service (say tftp) to transfer exploit code onto your machine.  They could bind it to a high port without having root access.  A "deny all" firewall would prevent this, and root would be required to open it up.

iptables does things besides accept or reject connections.  It can also log connections which is important, too.  For example you may want to allow inbound ssh, but you should probably be logging it to watch for ssh sessions that you weren't aware of.

So the lesson here, is that, yes ubuntu has a firewall, it probably isn't configured with any rules, and firewalls are important even if you don't have any services listening.

---

### Post by LordHunter317 on 2005-06-21
[QUOTE=azz]Personnaly, if you are just going to install a firewall and open up the one port that you need to use, I do not see the point.  It is like using an umbrella and cutting a hole in it to let in the one drop of rain that is falling on you.[/QUOTE]I think I understand what you're getting at, but it still shows a nieve understanding of the value of firewalls, I think.

Yes, a properly configuration server doesn't generally need a firewall at all.  However, there are plently of situations where one can be required, usually when the network daemon doesn't do enough filtering on it's own.

[quote=knathraak] But it's important on any system to ensure nothing is exfiltrating data without your knowing it.[/quote]The value of egress filtering at the host level in most situations is debatable at best.  Certainly, the number of situations where it definitively adds value is smaller than the ones where it does not definitively add value.

Egress filtering is important, but it usually makes more sense to do it on network boundaries, not host ones.

> iptables does things besides accept or reject connections. It can also log connections which is important, too. For example you may want to allow inbound ssh, but you should probably be logging it to watch for ssh sessions that you weren't aware of.SSH is a poor example as it does sufficent logging on it's own.

>  and firewalls are important even if you don't have any services listening.This is rarely the case on UNIX, unless the box is a router.

---

### Post by mcewen98 on 2005-06-21
knathraak,

Thanks.  This is what I was trying to get at, and what my original assumptions were.

Saying that "Ubuntu has no firewall" is techincally incorrect.  It has one since any recent distro with the Linux kernel does, but it is just not configured.  Firestarter allows you to easily edit the iptables settings.

Whether or not what the default inbound policy is for Ubuntu (Answering my own question from earlier, I assume it is to allow everything inbound and outbound, so Apache WOULD work out of the box), once you install Firestarter, no inbound connections will be allowed on any ports, meaning you need to explicitly open ports to allow in http, ftp, smb, etc..

Firestarters default outbound policy is to use a blacklist (Allowing all connections except for those you choose to explicitly refuse).  If you change this to the whitelist option (which sounds more secure), all ports will be closed and you will need to specify which protocols you want to allow, just like the inbound setting.  So if you choose whitelist but do not allow http, you will not be able to browse the web.

Stopping Firestarter apparently opens all inbound and outbound ports, since I still have my VNC + SSH sessions open after stopping the firewall.  They were still able to connect after closing the sessions and reopening them.

The reason that Firestarter "works automatically on startup" without the GUI actually being present is because you are just simply editing the iptables settings, and iptables will be started at boot automatically.

Being a convert from SuSE, I can see that YAST's firewall settings work this same way.

Spencer

---

### Post by LordHunter317 on 2005-06-21
[QUOTE=mcewen98]Firestarters default outbound policy is to use a blacklist (Allowing all connections except for those you choose to explicitly refuse).  If you change this to the whitelist option (which sounds more secure), all ports will be closed and you will need to specify which protocols you want to allow, just like the inbound setting.  So if you choose whitelist but do not allow http, you will not be able to browse the web.[/quote]Egress filtering at a host level isn't that simple though.

If you allow all applications outgoing web access, then an attacker has all the access they need to download stuff remotely.  You have to be extremely careful (perhaps more so than iptables allows) to do what you really want to do.

Host-level egress filtering generally only makes sense for isolated boxes on a network beyond your control (e.g., a box sitting in a hosting colo).

---

### Post by az on 2005-06-21
[QUOTE=LordHunter317]I think I understand what you're getting at, but it still shows a nieve understanding of the value of firewalls, I think.
[/QUOTE]


I have a naive view of a lot of things.  If you were in charge, would ubuntu install a firewall tool by default?   Why?

---

### Post by LordHunter317 on 2005-06-21
Well, I've been torn on this.

Ubuntu not needing a firewall policy OOB is a good thing, IMO.  I wish more distros shipped out of the box that way.

And like I said, servers don't necessarily need host-level filtering; it depends on your specific situation.  And it's not like the tools to do it aren't there, they're just not being used.

Moreover, my personal opinion of all firewall helpers I've seen is that they suck.

I think the ideal is what it is.  I have no issues with the policy.

I can think of a few solutions to do things better, but they would require a lot of restructuring of the way things are done.

I should note all of this isn't relevant to my comment towards you.  Your analogy about poking holes in an umbrella is a bit flawed.  The point to remember is a firewall generally lets me be more selective than I could with just my application.  Something that can frequently be very important.

---

### Post by az on 2005-06-22
"I should note all of this isn't relevant to my comment towards you. Your analogy about poking holes in an umbrella is a bit flawed. The point to remember is a firewall generally lets me be more selective than I could with just my application. Something that can frequently be very important."

Yes, but in the context of someone installing Hoary on a box that will run apache and maybe wordpress to show off family photos, do you think that it is important here?

I agree with you about my analogy.  What criteria (relative to Ubuntu Hoary) would you use to tell the average user that a firewall is needed?

---

### Post by LordHunter317 on 2005-06-22
[QUOTE=azz]Yes, but in the context of someone installing Hoary on a box that will run apache and maybe wordpress to show off family photos, do you think that it is important here?[/quote]It might be, it's **situation dependent**

> I agree with you about my analogy.  What criteria (relative to Ubuntu Hoary) would you use to tell the average user that a firewall is needed?It's really situation dependent.  The distribution doesn't really matter at all.  It's what you're doing with it that determines if you need a firewall or not, and what the firewall policy would entail.

Someone using Ubuntu as a home router and a webserver for example, will have to have a firewall (as iptables is how NAT is done).   But whether the webserver should be accessible by the Internet or not is dependent on what they're using for.  Ubuntu doesn't factor into that decision.

---

### Post by mcewen98 on 2005-06-22
Ok, so here is my situtation, which i'm sure is probably similar to many others.  I have a spare machine, 1ghz Athlon, 512mb of ram that I am using as my home server/linux box and hosting my website (6mbps up 768k down cable).  The wesbsite is just a basic Drupal CMS setup.

So I am running Apache2, MySQL, SSL, etc etc.. for the website.  I also use this machine for those long Bit Torrent downloads since it's always on, with a few samba shares so that my other machines can grab files and perform automatic backups of certain directories on the server.

I also use the server just for messing around with Linux, as well as FTP for transfering the occasional file from my work/family/friends, and SSHing and VNCing.

The router/firewall in front of my network (WRT54G) forwards 80,443,21,22 and the BT ports to the server, but blocks everything else incoming at that point.

Knowing this (and me not being a linux admin), what do you guys recommend?

Thanks,
Spencer

---

### Post by az on 2005-06-22
[QUOTE=mcewen98]Ok, so here is my situtation, which i'm sure is probably similar to many others.  I have a spare machine, 1ghz Athlon, 512mb of ram that I am using as my home server/linux box and hosting my website (6mbps up 768k down cable).  The wesbsite is just a basic Drupal CMS setup.

So I am running Apache2, MySQL, SSL, etc etc.. for the website.  I also use this machine for those long Bit Torrent downloads since it's always on, with a few samba shares so that my other machines can grab files and perform automatic backups of certain directories on the server.

I also use the server just for messing around with Linux, as well as FTP for transfering the occasional file from my work/family/friends, and SSHing and VNCing.

The router/firewall in front of my network (WRT54G) forwards 80,443,21,22 and the BT ports to the server, but blocks everything else incoming at that point.

Knowing this (and me not being a linux admin), what do you guys recommend?

Thanks,
Spencer[/QUOTE]

Well, I sorta took the thread off track by raising the point (again!) as to whether you actually need a firewall.

Your router is already acting as a firewall from the net to your server.  I would say that you do not need to add another level onto your box.

But then again, I would still say the same if you were running a desktop and a drupal cms on the same box attached to the internet.  
I do not think that I would be so confident if samba, ftp ssh and a whole lot of oter services were up an listening, though.

My question to LordHunter was where do you draw the line?   What packages that are in Ubuntu Hoary would you suggest either reccommend or depend on a firewall (or firewall gui)?

---

### Post by LordHunter317 on 2005-06-22
**mcewen98:**
Your chief need for a firewall would be to limit what clients are allowed to connect from SSH.  If you know that you're only going to connect from a fixed set of IPs (i.e., just from work and school) then allowing SSH access only from those IPs would increase your security.  OTOH, if you can't be certain what IPs you will always connect from, you'll lock yourself out.

Same goes for FTP or HTTP really, but usually one wants everyone to be able to access those services.

Obviously, if you don't want to or can't limit hosts, then you don't need a firewall on your server.

[quote=azz]My question to LordHunter was where do you draw the line? What packages that are in Ubuntu Hoary would you suggest either reccommend or depend on a firewall (or firewall gui)?[/quote]I wouldn't suggest any should, as it's quite dependent on the situation.  See the example I just gave him above.  He might need a firewall to limit who can SSH.  He might not.

Firewalling recommendations can't really be made unless you know what software's being run and who's it going to be served to.  I noted the one exception above (router).

As another example, the servers in my house don't do egress filtering because it's already done on the network edge.  But if I put a server in a colo, it would do egress filtering no matter what because I don't have any control over the network, and I want to limit the amount of access an attacker has.

---

### Post by mcewen98 on 2005-06-22
Since I do not know the IP address's from where I'll be SSHing and would not want to restrict HTTP/FTP, I cannot just allow specific IP's.

So, by the sounds of it, having Firestarter set firewall rules in my case is somewhat pointless, other than restricing outbound traffic, which would only be affective if all ports were blocked.

I guess the other good thing about Firestarter, which I think was mentioned earlier, is that it shows you the current active connections, and the amount of data sent and recieved, which I know you can also get other ways.

I think I'll leave it installed just for that purpose.  Now that everything is already set up, I see no point in removing it, and it's always to be better safe than sorry.  There's always the case where an exploit is found for WRT54G router (which would not surprise me), which would allow someone full access to the network.

---

### Post by gratou on 2006-08-03
Sorry to reactivate this old threat, I found it quite relevant and didn't find other such threads. Tell me if this is totally outdated please. 

I am about to start my first attempt to move on from xp, I was wondering whether there was a way to attach ports to apps, like x86 firewalls do. 

As in: incoming 80 open to the whole world, but can talk to apache only, and 21 to ftp. This way, opening ports is a lot more innocuous.

Cheers.

---

### Post by Glut on 2006-08-03
iptables can't base rules on applications. 

FWIW The argument goes along the lines of: Changing the process name is trivial, and once someone has the ability to do so they can usually modify the firewall, so filtering based on process name is useless. Also, such a feature is irrelevant to any firewall not on the local host - which is usually the case.

---

