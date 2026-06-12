---
title: "Setting up a VPN, Securing Computer?"
date: 2011-10-08
forum: Security
---

### Post by Bryant.GhostInTheMachine on 2011-10-08
Being the paranoid, suspicious, and avid privacy nut that I am, I have set about the process of securing my data and my Internet. I'm also working on ways of staying as anonymous as possible in the real world, but that's for a different forum. Before I get to my question, some explanation and overview is in order:

I have, over the past year or so, done my best to safeguard my information as best I know how. I make good use of encryption in the form of Truecrypt triple-layer cascade encrypted volumes with lengthy passwords, I use a firewall and Tor for most of my internet traffic, and all of my known online accounts use twenty-one character, almost completely random passwords which are stored in an encrypted file and managed by a privacy-enhancing firefox plugin, which also clears flash cookies and warns me of privacy concerns on websites I visit. I have a plethora of firefox add-ons installed to protect me online, including a spam and tracking network blocker, a virus scanner, and Foxyproxy (which handles my connection to the Tor network). I also use good passwords on my computer and I've done all I can to prevent unauthorized access.

Based on some research I found online, there are still a few things that I want to do: lock the BIOS with a password, encrypt my entire filesystem, erase all unnecessary e-traces of myself I can get my hands on (I have a feacebook, but I'd like to keep it as a communication tool), and enhance my mobile security (android phone, already encrypted the filesystem and use Tor).

The last four items I'm not entirely sure how to put into action. I need to find a method of encrypting my filesystem without destroying my data, erase as much of my online identity as possible, and keep my phone's data and network connection secure. How should I go about these things?

Also, I have considered setting up a Virtual Private Network to provide a secure connection for my mobile phone's online traffic. I have absolutely no idea how this works in practice, and what benefits it offers over Tor. Based on the info I found online, I was considering using a secured VPN to connect my phone to a home server created from an old Dell I have lying around, which would run the traffic through a firewall, virus-detection software, secure http proxy, and on to the internet, perhaps through Tor (though that seems a bit redundant). that way, any data going over my mobile network would be unreadable by AT&T on it's way to and from the internet. Is that feasible? If so, How would I get that to work?

All help on these subjects is appreciated.

---

### Post by Dangertux on 2011-10-08
Ok wow. Where to start. I am on my phone at the moment so I will answer as much as I can but I am sure others will chime in as well. 

For the bit about deleting your online identity so to speak, that is going to be most impossible if you've used any type of social networking. Minus google indexing things social networks do not like to let you delete your info. You can send them a letter demanding a record of our information and that they remove it. However due to terms of service they may or may not have to remove it. As far as things google caches that is there to stay. 

Now on to Tor. Tor is not really as anonymous as people would like to think. For one the exit router is a huge concern the exit router in the Tor network has access to whatever data is sent unencrypted. The intermediate routers do not, they only get the encrypted data. It is because of this that Tor is weak one for data protection and two because it makes end to end corellation very easy. Particularly because most likely your DNS lookups are not being proxied. 

Now on to the VPN and those issues with the phone. Of the two Tor or VPN the VPN will protect your data better but will not protect your anonymity as well.  While Tor traffic is both sniffable and traceable it's very difficult and unlikely that the average person would try. I would still choose the VPN of the two. Now on to AT&T not being able to watch what you do, so long as you are connecting through wireless and not the AT&T data network that is not a problem. Unless you're paranoid, then you realize that AT&T has an alway on data link to your phone and the necessary software and hardware to interface with it at a "root" level. So if your paranoia stems that far it is literally impossible to secure your phone from your wireless provider. 

As far as full disk encryption without destroying your data you should be able to do this via ecryptfs. As always back up your data first just in case. 

Hope this was helpful.

---

### Post by Bryant.GhostInTheMachine on 2011-10-27
what about setting up a privacy server? I got the idea awhile back and i think i mentioned it above... i was considering using an old dell i have as an ubuntu server, and connecting to it over VPN. I can then have the server route my data through Tor, which would hide my ip address and give me at least decent anonymity while protecting my VPN-secured data. I would guess though that i'd need end-to-end encryption for my data to be truly safe, and the whole VPN thing would only protect my data as far as the server. That would be nice because I'm planning on running a mail server (if I can figure out how to make the damn thing work right) on the same machine, and thus I could fetch my email securely. Still, its not really what I'm looking for. I've tried using a Firefox addon to enforce secure HTTP connections on most sites, so im assuming the same thing could be made to work from the server (which would route the traffic it got from my VPN connection) and on to the website im trying to reach. Even so, i have no idea if that setup is secure at all, or even feasible for that matter. Any thoughts?

I also heard about 'tunneling', but I have not the faintest idea what that is or whether it will help me at all.

---

### Post by Dangertux on 2011-10-27
> **Bryant.GhostInTheMachine said:**
> what about setting up a privacy server? I got the idea awhile back and i think i mentioned it above... i was considering using an old dell i have as an ubuntu server, and connecting to it over VPN. I can then have the server route my data through Tor, which would hide my ip address and give me at least decent anonymity while protecting my VPN-secured data. I would guess though that i'd need end-to-end encryption for my data to be truly safe, and the whole VPN thing would only protect my data as far as the server. That would be nice because I'm planning on running a mail server (if I can figure out how to make the damn thing work right) on the same machine, and thus I could fetch my email securely. Still, its not really what I'm looking for. I've tried using a Firefox addon to enforce secure HTTP connections on most sites, so im assuming the same thing could be made to work from the server (which would route the traffic it got from my VPN connection) and on to the website im trying to reach. Even so, i have no idea if that setup is secure at all, or even feasible for that matter. Any thoughts?

I also heard about 'tunneling', but I have not the faintest idea what that is or whether it will help me at all.

If you're going to go with VPN I would forgo Tor entirely. It is sort of self defeating in addition to the VPN since the end point can than sniff the traffic.

---

### Post by Ex-windows on 2011-10-27
Hi,
 I am not very versed in VPN or the inner working of net traffic but being the "paranoid, suspicious, and avid privacy nut" that I am I have found that it is next to impossible too be "anonymous" while online.  Almost every website logs your IP which is directly tied to you via your ISP which has your name and address etc.  Even if you can  conceal your IP you also have a mac address which is not changable and is like a model # direct tied to the machine and ultimately you. Facebook and other social networking sites are harvesting and even selling that user info for BIG profits. Phones are another NO Privacy"  area.  Your phone again tied to you and knows exactly ( roughly) where you are, who you are. and if you use " yahoo mail" or "Gmail". Face book or twiitter or both. I would not even have any of the newer phones becuz as they are getting smarter and more "sync=able" to facebook and other things they are also now more vunerable.
  Only real way to stay private is to start from the beginng. Use a bogus name for facebook and your mail accounts. Encrypt all mail sent and recieved. NEVER use your phone for private communication. never use blue tooth ( easily hackable).
 I have all my impportant "money files" P-word protected AND encrytpted AND I dont store them on my laptop. I also dont name them what they are, ie Bank info or Money. I have them named things like "Dinner recipes" Breakfast entrees". 
  However if you do find a safer way I am truly interested as I have always been concerned with Privacy and it,s ever dwindling presence lol.
 Good luck, Hope this wasnt to rambling  :)

---

### Post by Dangertux on 2011-10-27
> **Ex-windows said:**
> Hi,
 I am not very versed in VPN or the inner working of net traffic but being the "paranoid, suspicious, and avid privacy nut" that I am I have found that it is next to impossible too be "anonymous" while online.  Almost every website logs your IP which is directly tied to you via your ISP which has your name and address etc.  Even if you can  conceal your IP you also have a mac address which is not changable and is like a model # direct tied to the machine and ultimately you. Facebook and other social networking sites are harvesting and even selling that user info for BIG profits. Phones are another NO Privacy"  area.  Your phone again tied to you and knows exactly ( roughly) where you are, who you are. and if you use " yahoo mail" or "Gmail". Face book or twiitter or both. I would not even have any of the newer phones becuz as they are getting smarter and more "sync=able" to facebook and other things they are also now more vunerable.
  Only real way to stay private is to start from the beginng. Use a bogus name for facebook and your mail accounts. Encrypt all mail sent and recieved. NEVER use your phone for private communication. never use blue tooth ( easily hackable).
 I have all my impportant "money files" P-word protected AND encrytpted AND I dont store them on my laptop. I also dont name them what they are, ie Bank info or Money. I have them named things like "Dinner recipes" Breakfast entrees". 
  However if you do find a safer way I am truly interested as I have always been concerned with Privacy and it,s ever dwindling presence lol.
 Good luck, Hope this wasnt to rambling  :)

It's actually pretty easy to change your MAC address...

This conversation is descending from practical security and privacy to the tinfoil hat club quickly. What is it you are actually trying to accomplish. If it's being untraceable, you don't have the time or resources I can guarantee you that. So maybe it's better if you set an attainable goal instead of frustrating yourself?

---

### Post by Ex-windows on 2011-10-27
> **Dangertux said:**
> It's actually pretty easy to change your MAC address...

Wow sorry for the mis info. I honestly thought the mac address was permanent. 
And my point was the same only not written as concisely. Even with our encrypted files and extra precautions we still almost got $1500 in Airlines tickets charged to our Bank. Luckily this was caught in time.

---

### Post by OpSecShellshock on 2011-10-28
From context it almost sounds as if the plan is to set up the VPN server on the same LAN as the desktop system. I'm not sure what the point of that would be.

---

### Post by Dangertux on 2011-10-28
> **OpSecShellshock said:**
> From context it almost sounds as if the plan is to set up the VPN server on the same LAN as the desktop system. I'm not sure what the point of that would be.

I was assuming that the individual might be using public wifi? 

If it is the other (VPN on LAN) there is absolutely no point whatsoever. Since you'd effectively only be encrypting LAN traffic, for 1 hop.

---

### Post by OpSecShellshock on 2011-10-28
> **Dangertux said:**
> I was assuming that the individual might be using public wifi? 

If it is the other (VPN on LAN) there is absolutely no point whatsoever. Since you'd effectively only be encrypting LAN traffic, for 1 hop.

Yeah, it would really only make sense over public wifi, but I don't get why a self-professed privacy nut would use such a thing in the first place.

---

### Post by Bryant.GhostInTheMachine on 2011-11-14
I'm not uber-experienced in the world of networking... I'm more of a OS guy than anything else. I do see your point though, in stating that it's essentially a stupid idea. I don't really know much about network security, so that's probably the source of my ignorance in this discussion. I have a firewall set up properly (I think), Tor+vidalia, and various other things like that as a safegaurd against casual hacking and tracing attempts, but I'm well aware that it would only slow down an experienced hacker and/or tyrannical Gov't snoop at best. In that vein and based on your combined recommendations, my goal is this: how can I better protect myself from a) tracing and traffic analysis b) hacking c) data theft/encryption cracking.

And yeah, I'm a tinfoil hat-type guy. Hasn't anyone read the text of the Patriot Act or the TIA Act?

---

### Post by Dangertux on 2011-11-14
> **Bryant.GhostInTheMachine said:**
> I'm not uber-experienced in the world of networking... I'm more of a OS guy than anything else. I do see your point though, in stating that it's essentially a stupid idea. I don't really know much about network security, so that's probably the source of my ignorance in this discussion. I have a firewall set up properly (I think), Tor+vidalia, and various other things like that as a safegaurd against casual hacking and tracing attempts, but I'm well aware that it would only slow down an experienced hacker and/or tyrannical Gov't snoop at best. In that vein and based on your combined recommendations, my goal is this: how can I better protect myself from a) tracing and traffic analysis b) hacking c) data theft/encryption cracking.

And yeah, I'm a tinfoil hat-type guy. Hasn't anyone read the text of the Patriot Act or the TIA Act?

First things first. Security and Privacy are not the same thing, though they are not mutually exclusive of eachother they are not necessarily inclusive either. It's best to separate the two. 

Example : The Great Wall of China was pretty secure, it wasn't particularly inconspicuous.

Now let's look at your actual questions

A -- This isn't easy, Tor is a decent way to maintain a shred of anonymity , though its not a catch all solution and isn't untraceable by any stretch of the imagination. 

B -- Learn to secure your system and network : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

*note : if you're using the non-malicious and correct definition for hacking why would you want to stop? It's a blast ;-)

C -- See B.

Hope this is helpful.

---

### Post by Bryant.GhostInTheMachine on 2012-01-14
I know it's been awhile since the last post, but I had another related query and figured I might as well post it here instead of starting a new thread. I have decided (after reading all your excellent and informative answers) on a final course of action, and I need assistance in going about it.

I plan on creating a server out of an old laptop (gave the aforementioned Dell to my sister with Lubuntu on it) and setting it up to act as a firewall, proxy filter, and SSH tunnel for any devices that connect to it. That is, it acts as the network gateway for my LAN: all devices connected to the server have their incoming and outgoing internet traffic pass through the server's proxy, firewall, and packet sniffer, and are tunneled through SSH on their way to the internet. The server would also have to log all internet traffic passing through. I would also like it to fetch my emails from an online account and store them locally, so that they can then be downloaded to my regular computer with thunderbird. Finally, I would also like this server to be able to mask my ip and, (though I haven't the faintest idea how this would be possible) broadcast a fake identity in terms of ip address, location in the real world, and other such publicly identifiable information. Feel free to ignore this last option if there's no ready answer, it seems like it would be complicated beyond all my capabilities.

Is it possible to set up a server with these capabilities and to perform these tasks? how would one go about setting up such a server if so? I know that this is kind of overboard for a civilian, but as I have pointed out, I AM paranoid...

---

### Post by CharlesA on 2012-01-14
Possible, yes. Dovecot/Postfix come to mind for the mail thing, but I don't know how to configure them.

Not sure for the other portions, but I think Squid/dans guardian can be set up as a proxy for web filtering.

---

### Post by Dangertux on 2012-01-14
What Charles said. Also hiding your ip without using a proxy external to you and still being able to make an actual connection is not just difficult it's impossible. Perhaps consider leasing a VPN?

---

### Post by mattxhand on 2012-01-15
I admire your dedication to security, but honestly I think you may going tad overboard. 

If you are going to use a VPN, I would drop Tor. I use and love Tor, but I prefer using a VPN to connect to outside resource for security reasons. You don't know who your node is on Tor.

Ultimately unless you control both points on the connection, you can't be sure of the packet integrity, but I could talk about this all day.

---

### Post by Bryant.GhostInTheMachine on 2012-01-16
I think I can configure the email server myself without a gigantic amount of trouble... a little googling should show me the path.

As for the proxy, I would like to use a proxy that would shield my ip. Any ideas?

And as for VPN... my earlier post was made in ignorance of what a VPN actually is. based on what I now know, the idea I had was to use VPN to let devices (such as my phone, comp, etc.) connect to my server securely. That way, traffic heading over a public wifi or cellular data network would be fairly secure until it reached my server. At that point, the traffic would then be sent through a proxy or system of proxies to shield my ip address and other traceable/identifiable data. Finally, it would be sent over Tor or a network tunnel to hide the traffic and it's origin. I know that Tor isn't all that secure in terms of data integrity because of the way it works, and I'm still not sure about what a network tunnel is, so I have no idea if that scheme would work. (Can anyone clarify what a tunnel is and whether it has any bearing on the above idea?)

As for me going overboard... yeah, I agree with you. I'm doing it mostly as a challenge and for fun, but I really am concerned about my privacy and security. I don't trust the government any farther than I can punt the average politician, and the PATRIOT act scares the hell out of me... it's not that I'm doing anything illegal, it's just that they don't have the right to take away my digital freedoms without my consent (which, by the way, I will NEVER consent to.) So humor me on that count.

---

### Post by sammiev on 2012-01-16
> **mattxhand said:**
> I admire your dedication to security, but honestly I think you may going tad overboard. 

If you are going to use a VPN, I would drop Tor. I use and love Tor, but I prefer using a VPN to connect to outside resource for security reasons. You don't know who your node is on Tor.

Ultimately unless you control both points on the connection, you can't be sure of the packet integrity, but I could talk about this all day.

+1 drop the Tor and use VPN for outside sites.

---

### Post by Bryant.GhostInTheMachine on 2012-01-26
The basic idea I have is to set up a server. This server connects to a router, which in turn connects to the internet via a wireless bridge to my home network and cable modem. The server would have a set of proxies, a firewall, packet logger, and intrusion detection system residing on it.

The server, then acts as a secure gateway to the internet by the following method: one connects to the server from any network over a VPN or similarly secure connection. From that point on, all internet traffic from the connected device is piped through the server's anonymizing proxies, firewall, etc. and then, scrubbed and masked, is allowed to head on to the public internet. Incoming traffic passes through the same process but in reverse and is then routed back to the device it came from.

Is that a viable idea? I wasn't sure if I really explained it earlier... I tend to ramble more often than not :P

---

### Post by kevdog on 2012-01-26
The best way to attack this program is in layers.  Total security is only done as a series of steps and if your a beginner, just take one step at a time.  Its going to take months to tweak your system how you would like.  The good part is that most Linux systems are fairly secure by default so at least its not like you are starting at ground zero.

The easiest thing to start with is likely setting up an SSH server.  You can then tunnel your remote http requests and DNS requests from your remote computer to your ssh server.  This isnt an every application solution, but its a no brainer and quick, fast to setup, and fast to execute.  Heck you can even accomplish it on a rooted android phone.

The second layer would be establish a full fledged vpn (whereby not only http and dns lookups are tunneled), but every port is tunneled from client to server.  I've only done this using openvpn, however there are other such methods.  This too is a fairly straightforward process, and is both computer and phone compatible (if your running a rooted phone that contains a tun/tap driver -- most rooted kernels do!).

Implicit in this discussion is the subject of firewalls -- iptables, or ufw.  This is an entire subject to itself and takes many months to master.  Its easy to get up and running initially, but a long time to tweak the system.

On top of this, you could run port-knocker utilities, and selinux varietis (bodhi has a good tutorial on this), however these are very advanced concepts that you would be ready for if you've already done all the background work.

---

### Post by Bryant.GhostInTheMachine on 2012-02-10
Kevdog, you're awesome.

On that note, could you perchance explain, step-by-step, how to go about each of the layers of this privacy onion? Or, barring that, point me to a tutorial on each of the necessary set-up processes?

Also, will your proposed setup function well with a mail server running alongside? And, if so, how should I modify the component programs of the mail server in order to integrate with the privacy system?

---

### Post by Bryant.GhostInTheMachine on 2012-02-10
One other note: to connect the laptop (which is something of a living fossil) to the 'net will require a wireless router modded to act as a wireless bridge. As of now I have tried half a million times to flash it to DD-WRT or something of that ilk, but I have been woefully unsuccessful. Which sucks. 

Assuming I CAN get the router (and, by extension, this entire server system thingamajig) working, are there any special modifications I have to make in that regard? (i.e. port forwarding, etc.)

---

### Post by kevdog on 2012-02-12
ddwrt comes in a few varieties, micro, mini, standard, vpn. Make sure your router is compatible and that there is enough RAM on your router for your version.  I'm not sure what you want to do with your router, but unless your running anything complex, I've only found running a vpn on the router to be useful, however this could by supplemented by running a vpn server on one of the computers on the LAN -- I like ddwrt since its faster, but it works as well on a stand-a-lone box.  As far as port forwarding, this could be done on any standard router.  iptables could directly be implemented on the ddwrt router itself, but it could also be done on the LAN computer.

---

### Post by abexman on 2012-10-05
Question: a VPN I assume encrypts all your data so your ISP can't easily see what you are doing and destination sites don't know where you are coming from? Does that look suspicious to the ISP? 

On a related question - as to browser fingerprinting. I assume this would primarily be an issue if an agent had logs of traffic (say from an ISP from a user who wasn't using a VPN or a website or group of sites), of users who were trying to be anonymous, and you could use the fingerprint to match more than one user session together to attempt to collect identifying data? The fact that your browser can be identified to be unique, is in and of itself not much of a concern since that browser id data can only be seen by certain parties along the route of your connection. A VPN can help by reducing some of the exposure in that regard.

---

### Post by Welly Wu on 2012-10-07
If you plan to connect to outside websites, then the easiest solution is to pay money to subscribe to a VPN service provider. It will create an encrypted tunnel between your PC and your ISP and route all traffic through that encrypted tunnel. Since you are using Ubuntu or GNU/Linux, then you have to find a VPN service provider that offers support for your platform. WiTopia VPN [http://www.witopia.net](http://www.witopia.net) does so. It costs $72.00 USD annually for Personal VPN PRO plan and it's worth it. You can connect up to two Internet devices to WiTopia VPN gateways worldwide at the same time in different countries.

This also allows you to connect to WiTopia VPN gateways from any ISP in any location worldwide whereas a private VPN server at home means that you have to make sure that you can connect to your home ISP. This is what makes WiTopia Personal VPN PRO service so valuable.

I use it myself and my friend shares a connection with me.

---

### Post by rookcifer on 2012-10-09
> **Dangertux said:**
> Now on to Tor. Tor is not really as anonymous as people would like to think. For one the exit router is a huge concern the exit router in the Tor network has access to whatever data is sent unencrypted. The intermediate routers do not, they only get the encrypted data. It is because of this that Tor is weak one for data protection

All of this I agree with.  Tor is an anonymity network and not a data integrity or privacy network.  There is a difference in privacy and anonymity.
  
> and two because it makes end to end corellation very easy.

This I do not agree with.  While there have been some academic attacks on Tor, I am aware of very few that have been demonstrated practically.  Thus I would have to disagree that end-to-end correlation is "very easy."  Doable by a national intelligence service maybe, but probably not by many others. 

> Particularly because most likely your DNS lookups are not being proxied.

That's only if you have misconfigured Tor.  It is fully capable of routing DNS through the network.  Indeed, this is why they now endorse the Tor browser bundle -- it is ready to go out of the box with all of the configuration done for you.

---

