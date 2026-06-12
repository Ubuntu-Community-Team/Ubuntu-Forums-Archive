---
title: "Yet Another &quot;Travelling with a laptop&quot; question....."
date: 2018-01-20
forum: Security
---

### Post by Pat201 on 2018-01-20
I've searched and read many threads.  I've started on the Security How-To to learn more.  The more I learn, the more my head is swimming and I have no idea what to do.  I've been using a Linux desktop for probably 8-10 years.  I understand how to tweak things "behind the scenes", but I am in no way a power user or security guru.  Far from it.  

I'm leaving on a business trip in a week to be gone for 2-3 weeks.  My laptop will not be used for business, but mostly paying personal bills if the due date is before I can get home and pay them in a timely manner.  I don't have to check email while I'm gone, but I'd like to, I don't have to access FB and probably won't, but I wouldn't mind checking hobby web-sites or general purpose web site reading due to boredom during down-time.  I have an HP Stream that I'll take with me that I just put a new install of Lubuntu 16.04 on.  I haven't installed any additional software as of yet.  I also just installed Turnkey Linux File Server on a internal box at home on my cable modem network.  My thought was to install the OpenVPN server on that server and access it via OpenVPN on my laptop, but after reading here, with my overall lack of knowledge and only a week to get all this done (along with a ton of other honey-do's and whatnot), don't know that I could get that done and get it set up right.  

So my 2nd thought after reading here would be to buy a VPN through a reputable service for a month and use that.  If I have more travel in the future (I hope not), I could extend it to a yearly contract, I guess.  But even then, I'm not sure I'd be secure.  I'm not transferring national security secrets or anything of the sort, I'd just like to be able to pay bills, read email (only if I feel I need to) and do some internet browsing during down time.  I just don't want my bank account to be emptied out, ya know?  I don't have a problem installing a 2nd set of Linux on a USB stick and using that for my private stuff and then using the drive in the laptop for hobby stuff or vice versa or even disabling the laptop drive and using two separate USB stick installs, but like I said, my head is kind of swimming now with all these details and I'm not really sure what to do.  A lot of threads I've read are also outdated and things have been hacked since people made the suggestions so that adds to my confusion.  So if anyone could help me with a current setup suggestion, I'd appreciate it.  I was an IT guy "back in the day" but that was about 15 years ago.....  I don't mind putting in the time and I can figure out pretty much anything, but I don't guess I have time to become a certified computer security expert in a week.  :)  Thanks for the help.

Pat

Oh yeah, all this is assuming I'll just be accessing hotel wifi spots.  I was thinking of buying a USB NIC with an RJ-45 but read that really that is no more secure than wifi, so I guess that shoots that idea.  :)

---

### Post by TheFu on 2018-01-20
There are multiple security considerations when traveling.  Each of those has different mitigation strategies depending on your level of risk aversion.  Traveling within your country means you probably are familiar enough with laws to know what is legal and what isn't.  Traveling to other countries creates a new level of issues, since many countries have VERY different laws around encryption and use of encrypted network tools.

I can only say how I do it.

I don't take any data with me except for entertainment - recorded TV shows, movies. I do not take a work laptop with me when traveling for pleasure. Company policy doesn't allow that.  For overseas work travel, we check out wiped laptops with no data on them, just a VPN client (which may not work) and our SecureID FOB.  Only web access is expected when on travel, through the VPN.

I try not to depend on my laptop for security when traveling overseas.  I never trust a smartphone, ever.

I don't trust any of the networks I'm on when outside home or work, which means using either ssh, an ssh-tunnel/proxy or openvpn.  Each of these techniques often fail due to local network filtering.  The most certain method to have 1 or the other work is also not high performance and eats the primary port that the other tool would also need to get around issues.  We're talking about 443/tcp.

People tend to have trouble getting openvpn working because there are so many options, each which impact security, performance and usability. For example, UDP is faster than TCP, but many hotels will filter UDP, so that can't be used.  Many people want to access their home network from a Windows computer using the VPN.  This requires a setting that allows broadcast packets from the LAN over the VPN.  That can destroy VPN performance, depending on the number of clients.  OpenVPN, once setup, is pretty easy for end-users to connect with from pretty much every platform.

ssh, on the other hand, is only useful for TCP connections, but web browsing is TCP.  ssh is much easier to setup, but a little harder to use if you don't have a full OS. Using an ssh-proxy on Android is a little harder.

Depending on where you are, hotel wifi can be really bad.  Regardless, that network shouldn't be trusted.  

Ok, since I don't trust the network and don't take any data with me, I know that stuff is secure - back home.  So, I use a remote desktop back to my home network to do anything that needs security like email, banking, stock trading, and most internet browsing.  This means that pretty much any computer I have available during a trip just needs 2 programs on it for me - ssh-client and x2go to make a remote connection over ssh back to the house.

In my travels, I've found wifi to be pretty much everywhere and only the old-school 4-star and above hotels have in-room ethernet anymore.  Plus in some of those places, internet access is $8/day addon.

A commercial VPN provider just shifts the exit for your traffic to some data center that has a much more dangerous network, IMHO.  I only use a paid VPN provider when I'm at home and don't want to appear like I'm at home. ;)  For everything else, I use my ssh-server and/or my openvpn server.

Anyways, you have some decisions to make and lots of testing to accomplish.  Try your public library, a chain restaurant and a local restaurant/cafe.  Each of those will have different connection challenges for openvpn and ssh.  You'll see what I mean.

---

### Post by DuckHook on 2018-01-20
Your instincts are sound and you've come to a good place for advice. Now, wow&#8230; where to begin?

Let's not inundate you with detail. Your head is already spinning.

Before starting please note that security is highly personal. There is no one-size-fits-all. It depends on your risk tolerance balanced against your tolerance for inconvenience. But with those caveats out of the way and in no particular order, here's what I would do:

[LIST=1]
[*]A VPN is a must. Don't try to set one up yourself. There's nothing wrong with doing so&#8212;you just won't have the time to learn, implement, debug, etc in one week. Besides, the commercial ones are great (and pretty cheap). I use Private Internet Access, but there are dozens of good ones out there. Google for reviews.
[*]Anything is better than WIFI, but a simple NIC is not much better. Bad actors hooked into the hotel network can also sniff your wired data. It's just easier over WIFI. However, your VPN looks after that whether WIFI or wired.
[*]Many veterans advise whole-disk encryption. I do not. They provide ultimate security, but at the cost of fragility. And when you are thousands of kilometres from home, that's not the time you want to have a small glitch stop you dead in your tracks from using any part of your laptop at all.
[*]I advise setting up an encrypted Private directory. Move all of your sensitive files into said directory. Then symlink back to where the system expects to find them. The big caveat about this strategy is that some countries immediately tag you as a security risk if they catch you using encryption. This is based on the ridiculous premise that most people are too stupid to secure their devices properly. If you do, then this means that you can only be up to no good. You will have to balance this risk against the risk that your laptop will get stolen.
[*]Harden your browser properly. This is especially important when browsing from public places. Properly configured noscript, ghostery, a cookie manager, some form of ad blocking and proper patching are good starts.
[*]If your browser's and email client's main and .cache files are moved into encrypted Private, then this is far better. In fact, I would argue that it is required.
[/LIST]
None of the above is uber secure. Each individual step can be defeated by a sufficiently trained and motivated hacker. However, taken together, they take on significant security weight. They also leave enough convenience that you won't be pulling your hair out. The whole hardening concept can be taken much further, but this usually comes at the cost of usability. In security as in other aspects of life, perfection is the enemy of good.

Hope this helps.

Bon Voyage and Happy Ubuntu-ing!

Edit: ninja'd by TheFu

---

### Post by TheFu on 2018-01-21
The EFF has guidelines for traveling with computing devices.  
* [https://www.eff.org/press/releases/digital-privacy-us-border-new-how-guide-eff](https://www.eff.org/press/releases/digital-privacy-us-border-new-how-guide-eff)
* [https://www.eff.org/issues/travel-screening](https://www.eff.org/issues/travel-screening)
* [https://ssd.eff.org/en](https://ssd.eff.org/en) - Privacy Counter measures

They have a few other guides.

Lifehacker did a good overview: [https://lifehacker.com/how-can-i-make-sure-my-laptop-is-secure-while-i-travel-1495527128](https://lifehacker.com/how-can-i-make-sure-my-laptop-is-secure-while-i-travel-1495527128)

A cheap chromebook is probably the most secure computer for travel that I know.  Google has joined software AND hardware security together making for a highly secure device. They aren't for everyone and have some huge limitations, but for security and travel, I don't know any better platform, google spying aside. ;)

---

### Post by Pat201 on 2018-01-21
I'll just be in the US and no data going with me.  Just the HP Stream for web browsing.  I may fire up some notepad app to take some notes, etc, but nothing I'd have to worry about.  How do the VPN routers work that companies sell?  Same as setting up OpenVPN on a box at home?  Meaning, I'd still have to pay for a service on the other end to connect to if I'm sitting in a hotel room somewhere connecting to their wifi.  Or if I bought two of them, I could put one of them at my house and then use one in the hotel to tunnel back to my house?  This is very confusing, but very interesting to me.  That's one of the reasons I've stayed with Linux over the years is because I love a good challenge and digging into the guts of things to make them work on a budget.  :)  I'm just starting on this topic however which is where most of my confusion is coming from.  Plus it helps that I hate Microsoft's guts and livers for how they've manipulated the market over the years.  Anyway.....   What do you think of these two little boxes?  The cheap one I'm a little worried about because in the setup video you can choose between English and Chinese which sends up a red flag for me.  Nothing against Chinese folks, but you know where I'm coming from.  

[https://www.amazon.com/GL-AR150-Converter-Pre-installed-Performance-Programmable/dp/B015CYDVG8?psc=1&SubscriptionId=AKIAINYWQL7SPW7D7JCA&tag=aboutcom02lifewire-20&linkCode=sp1&camp=2025&creative=165953&creativeASIN=B015CYDVG8](https://www.amazon.com/GL-AR150-Converter-Pre-installed-Performance-Programmable/dp/B015CYDVG8?psc=1&SubscriptionId=AKIAINYWQL7SPW7D7JCA&tag=aboutcom02lifewire-20&linkCode=sp1&camp=2025&creative=165953&creativeASIN=B015CYDVG8)

[https://www.amazon.com/UTT-HiPER-518-Business-Firewall/dp/B01A9GKOFU?SubscriptionId=AKIAINYWQL7SPW7D7JCA&tag=aboutcom02lifewire-20&linkCode=sp1&camp=2025&creative=165953&creativeASIN=B01A9GKOFU](https://www.amazon.com/UTT-HiPER-518-Business-Firewall/dp/B01A9GKOFU?SubscriptionId=AKIAINYWQL7SPW7D7JCA&tag=aboutcom02lifewire-20&linkCode=sp1&camp=2025&creative=165953&creativeASIN=B01A9GKOFU)

---

### Post by Pat201 on 2018-01-21
Oh and thanks for those links Fu! I'll dig into them when I get a second.

---

### Post by DuckHook on 2018-01-21
If you are intent on setting up your own OpenVPN, then I'll have to leave that to TheFu.

If you are okay with commercial VPN, then I can tell you that you needn't make this overly complex. No machinery needed. Most VPN providers will have a client app that you can download onto your laptop. Sign up with them, download and install the app, fire it up, login, and voilá. If you don't trust closed-source apps, then some VPN providers will have instructions on how to fill in Ubuntu's VPN settings. This has the advantage of avoiding third party apps. It's disadvantage is that if not set up properly, it could bork your network settings thus preventing you from accessing the net at all. Rare, but it happens and is worth mentioning.

BTW, if you are worried about Chinese boxes, then you may as well give up computing and check into a monastery. Everything is from China these days including probably the very laptop you are using.

---

### Post by TheFu on 2018-01-21
I'm not impressed with HW that isn't needed.  Chances are that your home router can be a VPN server and your desktop/laptop/android/iOS devices can be a VPN client.

But I'm unclear as to which solution you want.  VPN or ssh?
I'm also unclear if you want to run the server on your home internet connection or want to pay someone else (which is less secure, IMHO).

Regardless, using a VPN/ssh-tunnel whenever away from home/work, is smart. Never trust networks that anyone else can use. A VPN/ssh-tunnel will solve most untrusted, local, network security issues (but not all).

---

### Post by Pat201 on 2018-01-22
> **DuckHook said:**
> If you are intent on setting up your own OpenVPN, then I'll have to leave that to TheFu.

Oh, I'm not, trust me.  :)  I'd like to set one up, because I like "doing", but not when I need something fairly reliable and have one week left to do it.  :)  I agree something commercial is probably the only choice I have at this time and I understand about something being made in China....  Hardware, I'm ok with.  Software I'm sometimes skeptical of.  I guess there could still be tons of stuff in firmware IN the hardware, but.....   :)  I'm really not that paranoid and I have absolutely nothing against Chinese or Russian folks, I'm just wary in situations where governments can be involved.  I don't trust mine either (US) for what it's worth.  Maybe I am paranoid.  LOL

---

### Post by Pat201 on 2018-01-22
> **TheFu said:**
> Regardless, using a VPN/ssh-tunnel whenever away from home/work, is smart. Never trust networks that anyone else can use. A VPN/ssh-tunnel will solve most untrusted, local, network security issues (but not all).

I was just interested in those little "travel routers" because I thought they provided some type of VPN protection without needing an additional service.  I guess they can if I already have a VPN on my home network for them to tunnel to.  I don't however, and reading their user reviews and questions I understand now that they would not be necessary.  

I don't know whether I need a VPN or ssh.  I wanted to securely pay bills from my hotel room and I didn't know how you did that.  I wasn't sure if I used a VPN client and a VPN add-on in my browser to go directly to my bank's web-site or if I VPN'd to my home network and fired up a browser on my home desktop.  With time running short and my ignorance level so high, I'm thinking I should take my checkbook, a stack of envelopes and a book of stamps with me, have my son go to the post office for the mail, take a picture of the bills and text them to me.  Just pay them the old fashioned way.  :)  He'll just have to turn off his google cloud sync or delete the photos as soon as he sends them.  When I return home, I can continue my quest for VPN and network security knowledge.  

The two commercial services I was looking at were NordVPN.com and privateinternetaccess.com.  Both got high marks from PCMagazine and CNet.  I don't stream movies or anything like that on the road, I mostly just read linux stuff and about model airplanes and trains at night.  Sometimes I might google stuff about the surrounding area to find restaurants, shops or whatever we're looking for, but nothing really compromising.  But if I need to pay a bill, handle an insurance problem or handle a problem with my wife's business (I'm her book-keeper), sometimes I might want to log onto a web-site with personal information and I'd like to be able to do that without having my life destroyed.  :)  So if I can do that with a commercial service (understanding why you don't trust them, but not really having a better option at this time), that's probably the best route.  I really have no need to access my home network unless it's just easier to set that up to access the outside world.  

Have you guys worked with (probably not because you're way beyond the need for such) or heard anything good about the Turnkey Linux distributions?  I just set up their file server and it was pretty seamless.  They don't have any way to easily add their other "modules" right now, so I could ditch the file server and set up their VPN server.  Maybe with a couple tweaks, their out of the box solution would be more reliable than a commercial service for me to tunnel into my home network.  I kind of understand what ssh does, but unless it can give me my Ubuntu desktop, I'm not much of a Linux command-line commando.  Even if I could reach my home desktop, I don't know what I could do with it if I couldn't access my browser.

---

### Post by Pat201 on 2018-01-22
Oh, and I checked on the three routers on my network and none of them offer VPN options.  I did find dd-wrt.com and I think a couple of them are on the list that the software can be replaced to provide VPN services, but I'd hate to do that and break them on the way out of town and our home internet connection be down for two weeks.  That would *not* make my family happy.  :)

---

### Post by TheFu on 2018-01-22
I don't trust the US govt either, and I used to work for them!  A healthy skepticism against the local/state/country govt is smart, IMHO.

Is there a reason you want openvpn and not ssh? ssh is about 10 minutes of effort and you can use a client SOCKS proxy to connect from any browser.  [https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel](https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel) is one how-to.  

On the remote side (a computer in my home), I run sshd with fail2ban and have remote access into it available from the internet.  Fail2ban watches log files and dynamically makes temporary firewall rules when X number of failed access attempts happen. It effectively blocks brute force attacks, but we don't use passwords for ssh anyways, so it is highly unlikely someone could present a 2-4K ssh-key correctly and get in.

Then on the client (my laptop), I run an ssh connection script to setup the local encrypted channel to my home network.  Then configure a browser to use a "SOCKS" proxy.  There are GUIs for this, but I just have chromium-browser with a command line option telling it to do so.  This way my connections can be automatic and I don't need to type much, ever.  They are also consistent and don't assume some settings file hasn't been tampered.  My local script:
$ more ~/bin/fireproxy-home.sh 
```
#!/bin/bash

# Only start SOCKS proxy if necessary
if  [ $(ps -eaf |grep ssh |grep -c 64000) = 0 ] ; then
   # Setup SOCKS proxy through home server
   echo "Starting ssh SOCKS Proxy"
   ssh -f -C -D 64000 remote.myhouse.com -NT 
fi 

# Start private firejail with chromium, going through 
# just setup SOCKS proxy
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:64000"; 
firejail --private chromium-browser \
         --proxy-server="socks5://localhost:64000" &
```

I'm running chromium inside a private firejail setup for added security.   "remote.myhouse.com" could be a public IP address or dynamic DNS name from no-ip.com or dyn.org or any of the other DNS providers.  Many home routers have a way to manage these as IP addresses on DHCP ISPs change from time to time.

Clear as mud?

---

### Post by TheFu on 2018-01-22
> **Pat201 said:**
> <snip>

Have you guys worked with (probably not because you're way beyond the need for such) or heard anything good about the Turnkey Linux distributions?  I just set up their file server and it was pretty seamless.  They don't have any way to easily add their other "modules" right now, so I could ditch the file server and set up their VPN server.  Maybe with a couple tweaks, their out of the box solution would be more reliable than a commercial service for me to tunnel into my home network.  I kind of understand what ssh does, but unless it can give me my Ubuntu desktop, I'm not much of a Linux command-line commando.  Even if I could reach my home desktop, I don't know what I could do with it if I couldn't access my browser.

ssh is a general purpose system-to-system connection. It is a swiss army knife for connecting Unix/Linux systems together.  That is what a VPN is too, just more about connecting computers to a LAN, not to another computer.

You can use ssh to provide a secure network connection to your Ubuntu desktop running at home.  THAT is the solution I'd recommend for online banking - though I'd never use my normal Linux desktop for banking. I use a read-only ISO for that.  x2go is the remote desktop solution I prefer. It leverages ssh as part of the setup, but ssh has to be setup and working first.  x2go has a nice GUI on the client side.  It likes simple desktops - so Unity and gnome3 aren't good. Use xfce or LXDE or Mate for the DE and all will be fine.

That is my recommendation.  ssh + x2go.  

I've used PIA before, but only when I want to appear to be in a different place.  I use their client on Android, but not on Linux. They are just using openvpn with less-great security settings.  To get acceptable security, some extra steps are needed to use stronger encryption - AES-256 is what you want. That means installing different 4096 CRT and PEM files.  Don't know how to force that on Android or iOS. I assume all VPN exit nodes are on highly watched subnets.  PIA deletes logs, but while the connection is active, there are logs.

I wouldn't do online banking from someone else's network.  Just wouldn't.  BTW, I was a CFO at a small corporation for 5 yrs.  x2go gets around the local network issues, since those connections would all come from your HOME/office.

Can't say anything good about pre-built Linux solutions.  I've not been impressed with security, even from so-called "security distros" with commercial backing.

---

### Post by DuckHook on 2018-01-22
I hope TheFu doesn't mind my offering a contrary opinion, but here it is:

As much as I wholeheartedly agree with pretty much everything TheFu says, he is doing one thing that many gurus do: he is taking his own high expertise for granted. I imagine that he's been doing this sort of stuff for so long that it's second nature to him. But for a general user, learning how to set up secure ssh keys, then tunneling remote desktop traffic through an ssh connection back to a running home machine configured to host a remote desktop session, all within a span of the few days you've got left before going, is&#8212;ehrmm&#8230; challenging, shall we say?

I've already said it and I'll say it again: perfect is the enemy of good. When you have enough time to figure all of this out, then go nuts. For this trip, my mundane pragmatic advice is: go with something like Private Internet Access. It's not ideal. TheFu's concerns about its exit nodes probably being watched are quite valid. But given the choice between this and a completely unprotected hotel WIFI? There's no question which is the lesser of the two evils. If you are worried about being tracked at the VPN endpoint, cloak yourself in another layer of anonymity with TOR.

I've done online banking remotely using the above setup. I won't do so from a hotel WIFI or an internet cafe, but I've used it from a rental unit's private WIFI network. Between the encryption offered by the VPN plus the encryption offered by HTTPS, I judged it to be an acceptable risk. When you are away from home for a few months, it's impossible not to carry on with life's necessary financial obligations.

A final caveat and then I'll go away: my ISP runs a highly asymmetric network. My upload speeds are 10% of my download's. A home VPN doesn't physically work for me because the uplink would be excruciatingly slow, probably to the point of excessively dropped packets/frames. You must make sure that your physical infrastructure will support whatever IT gymnastics you are trying to pull off.

---

### Post by TheFu on 2018-01-22
DuckHook is correct.  One of my many personality flaws is the inability to determine someone else's skill levels. I've undershot badly before, so I'm trying not to do that anymore.  Overshooting could be an issue too. Sorry.

---

### Post by DuckHook on 2018-01-22
Apologies are not remotely necessary. I learn things from you all the time. This time, it was:

[LIST=1]
[*]The weakness of commercial VPN exit points and VPN keys.
[*]An absolutely empty laptop as a go-to travel appliance.
[*]The uses of a Chromebook.
[/LIST]
I've read your other techniques before, but a refresher is always good.

@Pat201

I'm not saying that TheFu's advice shouldn't be followed. Goodness, no. If you implement his suggestions, you will be more secure than 99.99% of the general population. I was only raising a contrary opinion because you have so little time.

Since you've shown an interest in this sort of security, I would recommend that after your return, that's the right time to start delving into some of these issues in depth. At that point, you won't go wrong implementing TheFu's many excellent strategies.

---

### Post by TheFu on 2018-01-22
There are many smart people here that I learn from too.  
For PIA, I found this chart of ports protocols and ciphers.  
[https://helpdesk.privateinternetaccess.com/hc/en-us/articles/225274288-Which-encryption-auth-settings-should-I-use-for-ports-on-your-gateways-](https://helpdesk.privateinternetaccess.com/hc/en-us/articles/225274288-Which-encryption-auth-settings-should-I-use-for-ports-on-your-gateways-)

---

### Post by Pat201 on 2018-01-23
> **TheFu said:**
> I don't trust the US govt either, and I used to work for them!  A healthy skepticism against the local/state/country govt is smart, IMHO.

Is there a reason you want openvpn and not ssh?

Well, I ssh'd into my Turnkey Linux file server..... got the command prompt.  I was like.... "Hunh.... (rubbing my chin) So what do I do NOW?"  LOL  I'm not afraid of the command prompt, my first experience with MS-DOS was setting up a BBS on a Sanyo 550 with DOS 2.1.  When a friend of my who is VERY Linux/security savvy showed me a network install of Debian off a floppy disk about 15-20 years ago I though "Heyyyy, I like it."  :)    I guess like most of society, I've always used a GUI for Linux (short of some cfg file editing or command line installs, etc here and there) so that's what I've become used to.  I just haven't dug down in there and figured out everything you can do because I haven't had to.  I guess I thought ssh was like opening a terminal and OpenVPN was more like sitting at my desktop.

---

### Post by Pat201 on 2018-01-23
I understand completely Duckhook.  I appreciate both viewpoints.  My short time-frame is why I was trying to look for a "good enough" solution to get me through just this trip.  I'm not worried at all about being tracked, I was more concerned about some bone-head sitting in a van outside my hotel stealing my bank login and emptying us out before I got home or by the next time I received a bill to login and took notice.  We do have a separate bank account that we use just for online purchases, "questionable" retailers, and what-not.  I've never even checked to see if they have bill-pay or not.  I guess I could go the commercial vpn route and transfer just enough money into that account to pay bills and never access my main account while on the road.  My wife could pay the bills, but she is not computer savvy at ALL, nor does she read English, so based on past performance, I'd rather spend 24/7 this week getting something setup than figure out WTH happened when I get home.  LOL  Don't get me wrong, she's a smart cookie and a good business woman, just not good at handling "financial details" when she has no idea what that letter from the insurance company or the IRS says.  :)  

I like the looks of that X2Go, Fu.  I worked with Windows Terminal Server and Citrix a good bit when I was a net admin for a school system, but that was a long time ago.  Educational apps are often very cantankerous running over a network, probably because they're mostly written by educators and not "computer people" and they kind of either worked or they didn't, so we didn't put the Citrix setup into production because we couldn't get the apps working reliably enough.  We could get them working onesy, twosy, but when classes changed and you had a couple hundred kids all logging into the same server at the same time, it just wouldn't happen.  And if y'all are familiar with educational budgets, we just could spring for a different server for every computer lab in the county.  :)  I used to have a good bit of network experience, but I got out about 16-17 years ago and at least in the educational arena, we weren't as worried about security and hackers as you have to be now, so I don't really have any experience with that type of thing.  Once we got a proxy server in and figured out how to keep kids from getting to porn sites, that was about all we had to deal with.  :)

I'll continue researching and fiddling with this the rest of the week and just go from there.  I'll only be gone a couple weeks and with most of the bills a set amount, I'll pay all those before I go and hopefully on the ones with due dates out in the future, I won't have to worry about it until I get home.  My laptop is Linux, my phone is Android and my son's phone is Android.  I don't trust ANY app on a phone, but my backup plan was to set up Skype and let him hold a bill up in front of his phone camera.  Loaded Skype up last night and it came up with a Microsoft logo..... was not aware of that.  Scratch that one off.  LOL  Was trying to avoid the snapping a pic and texting it to me because I know that Google instantly has a backup of that.  <sigh>  Anyway.....  Thank y'all for the advice!  I'll post back as I try various things out and come up with a more definitive plan.

---

### Post by Pat201 on 2018-01-23
Got Chromium installed on server and can SSH in, but when I try to run it I get:

[ATTACH=CONFIG]278296[/ATTACH]

I'm a-googlin'.....  :)

---

### Post by TheFu on 2018-01-23
Try ```
ssh -X {userid}@{server-name} chromium-browser
```
or ```

ssh -X {userid}@{server-IP} chromium-browser
```

Replace the htings in {} with the actual values for your userid and network. 
If the {userid} is the same on both systems, it isn't needed.  
However, this really isn't useful over the internet. Few connections are fast enough.

If you've setup ssh-keys between the systems (ssh-copy-id), then the connection will be 10,000x more secure AND more convenient to use.  That never happens in computing - more secure AND more convenient?  This is the single instance where that is true that I know.


But if you setup **x2go**, then you will have a remote desktop, using encryption and optimized compression for the GUI.  It works nicely from different continents.  I've done it from SE-Asia, Central Asia, South America, South Africa and Europe back to my man-cave in Squidbilly-land.  The only trick is to use the x2go PPA for the client and server installations.

---

### Post by Pat201 on 2018-01-24
Ok, I have absolutely NO idea what I'm doing, but with y'alls help and googling every time I get an error message, I finally have X2Go operational.  :)  Now I've just got to get into it from the outside.  I have a Netgear router and they provide one free login to DynDNS I think it is, so I'll try to figure that out next step.  Fire this bad boy up and we'll be cookin with gas.  :)

---

### Post by TheFu on 2018-01-24
Congrats!

Pro-Tip - Use the router to listen on port 443/tcp on the WAN side, but translate that to port 22/tcp on the desktop running x2go server. That way, hotel internet filters probably won't block it.

Also, you might want to tweak the bandwidth and compression settings in the x2go client to be 1-less than what your uplink from home really provides.  I use "ISDN" from outside and "LAN" inside.  Also disable printing and audio and file transfers, since those are 2-way connections which won't work from any hotel.

This stuff is pretty easy, right?  The hardest part for my Mom was she had a habit of turning off her home PC after use. That means nobody could contact it remotely. So be certain to let anyone at home know NOT to turn off the computer.

1 more question thing.  Please be certain to install fail2ban.  This blocks brute-force ssh attempts on port 22 (on the computer). With port translation happening at the router, the config is handled, but you'll see lots of connection attempts. Fewer than on WAN port 22/tcp, but still more than on some high port like 63400/tcp.

---

### Post by jedi123 on 2018-01-24
TWO ISSUES COME TO MIND : 

1. **Paying bills from a hotel WI-Fi,:  **

A** VPN ** that  has an ip adress server in your city / state ---> so that your bank's Firewall, will not see an international ip address and block you . **ExpressVPN, is very compatible with Linux ** 
( they have a linux command line option  that's easy for a dummy to use).  You can easily choose US/Canadian servers. PS make sure you  use a linux command line to [B]download AND verify from their  
ExpressVPN , PGP keyserver (they give  simple to follow instructions on it for x-hkp:// ) 


2. Border guards going through your LAPTOP AND PHONE. 

[/B]The Canada Border  Service  Agency , as well as   US Customs and Border Protection have the right to search your laptop and phone and its contents  . You can ** encrypt your Ubuntu computer, **however they might take your  computer for "investigating it" and copy its contents of its hard drive. They same is true with your smart phone. They can search it and send it off to be examined somewhere else,[B] if you encrypt your phone. The more sage advice is: 

 -buy an inexpensive computer for travel (walmart you can get great stuff).    
 -delete embarrassing or private pictures or video from your phone,   IE your sex tape
 -delete phone history  (especially of your  pot dealer --lol). 
-delete phone contacts ( again of your pot dealer). 
-delete privacy apps like  wickr /signal etc. ( so as to not be asked about your privacy habits). 
[/B]

---

### Post by TheFu on 2018-01-24
> **jedi123 said:**
> TWO ISSUES COME TO MIND : 

x2go solves all of those issues, since he would be using his desktop back home for everything and doesn't need to bring any data along.

Plus, it has been revealed that he isn't going across any country borders, though within 100miles of a border or port in the USA, I've seen US-Customs agents stopping vehicles. Most recently on I-10 in Mississippi.

---

### Post by Pat201 on 2018-01-25
Luckily, or unluckily, depending on how you view it I guess, I don't have pot dealers, nor sex tapes, nor any such.  Although I'm a pretty boring old dude now and while I'm not up to date on current technology and security measures, I learned a LONG time ago not to have anything you don't want someone to see out there where it can be seen.  :)  Not that I ever did, but my common sense WAY covers my lack of intelligence.  :)  Yep, not travelling across any borders, but if I get stopped by a border or custom agent inside the US,  I won't have to worry about my laptop, I'd probably be arrested for breaking obscenity laws.  

That said, I'll work on those things y'all mentioned and cover as much as I can.  I also don't have to worry about my home stuff getting turned off as it's in "The Cave" and no one comes down here.  I leave all my equipment on 24/7 anyway, except for the laptop I keep our business info on.  The laptop I'm carrying is an HP Stream cheapy, but I really like it.  It has a clean install of Linux Lite on it and two more copies on SD cards I can boot off of to keep things fresh and "wiped" as we move from place to place.  I think I'm nearing "as good as I can get" with my limited experience and I really appreciate everyone's help.  I'll cover my specific questions in the next post.  :)

---

### Post by Pat201 on 2018-01-25
> **TheFu said:**
> Congrats! Pro-Tip - Use the router to listen on port 443/tcp on the WAN side, but translate that to port 22/tcp on the desktop running x2go server. That way, hotel internet filters probably won't block it.

My router at home, right?  I'm not sure it supports going from one port to another.  I *think* I tried that yesterday getting my Q-See cameras working from outside the network, but I can't remember.  I'll check it, though.

> **TheFu said:**
> Also, you might want to tweak the bandwidth and compression settings in the x2go client to be 1-less than what your uplink from home really provides.  I use "ISDN" from outside and "LAN" inside.  Also disable printing and audio and file transfers, since those are 2-way connections which won't work from any hotel.

I remember seeing that on setup, so that one should be easy.

> **TheFu said:**
> This stuff is pretty easy, right?  

Not too bad.  Still have most of my hair.  :)

> **TheFu said:**
> 1 more question thing.  Please be certain to install fail2ban.  This blocks brute-force ssh attempts on port 22 (on the computer). With port translation happening at the router, the config is handled, but you'll see lots of connection attempts. Fewer than on WAN port 22/tcp, but still more than on some high port like 63400/tcp.

That gets installed on the x2go server on on the travelling laptop?

Jedi123 	 	 		 			 				
Yep, I'll probably still pick up a VPN service for a month to try it out and at the very least have it as a backup.  I'll check out ExpressVPN along with those other two.  I'll get one of those configured before I leave so it's installed from a trusted net that's as good as I can get it for now.

As for getting stopped by cops/border guards.....  they better have a damn good reason for stopping us.  I would defer to the guy I work for and follow his wishes, but he and I are pretty much like minded in areas like that.  On the way *to* the job, we'd probably do what we had to to be on our way.  On the way home *from* the job, we'd both probably say, "You have a warrant?  Are we being detained?  Are we free to go?" like in the videos.  LOL  I support cops and their efforts and I'm not an ass to them, but I do believe they have *way* overstepped their bounds when it comes to the "what are you doing, where are you going" line.  Last I checked, I still live in America.  It's none of their damn business where I'm going and what's on my laptop unless they have reasonable suspicion to stop us.

---

### Post by TheFu on 2018-01-25
I've seen a few netgear and linksys routers that didn't support port translation.  Pretty much every other one I've see does.  It isn't labeled, just a few columns on the inbound ports allowed page.  443/tcp --> {internal-IP} --> 22/tcp
It is important the desktop at home on the LAN has a static LAN IP.  Don't want that moving around.

BTW, allowing any camera to be accessed directly over the internet is 99.99999% a bad security choice.  Those things are often used for attacking others if they are accessible to teh outside world.  [https://securityledger.com/2016/09/the-hacked-camera-botnet-not-new-just-big/](https://securityledger.com/2016/09/the-hacked-camera-botnet-not-new-just-big/) - your brand is listed prominently as being hacked.  You don't need to unplug them, but I would block all internet access for them ASAP.  They should only be available on the LAN - but you can use the x2go desktop to see them.  ;)

I had much more hair 10 yrs ago, but still have "most" of it in the places it is desireable. ;) 

Border patrol doesn't need a reason.  They have checkpoints along highways and pull suspicious and ever 4th vehicle over in some places.  Sometimes it is as simple as answering, "Are you a US citizenship." - which you don't actually have to answer. Of course, it depends on your personal stance on being illegally questioned by the Govt without cause or any warrant. Of course, what I believe is a violation of the 4th amendment and what the legal system here believes are often different. Founding fathers stuff, but everyone has to make their own choices.  I'd like to think I'd refuse to answer, but probably would just to avoid hassles.  

When leaving/entering the USA, they can search anything they want. We don't have to agree to those searches and we certainly don't have to provide passwords.  They can force our fingers onto devices, however.

---

### Post by 1clue on 2018-01-25
When I travelled to Colombia, the average person did not have a computer. They had internet cafes, where you rented time on a computer for however long and then used it right there.

You might find it convenient to not bring a computer at all. I would consider bringing a bootable, write-protected USB stick or even dvd or cd. Make a boot device that works with almost anything (system rescue CD?) and then add stuff to get you connected back home. Definitely the VPN in this case.

Go into the internet cafe, reboot off of your device, connect to your VPN, connect to your home, do your stuff, reboot and pull your dvd/cd/usb out while the screen is black.

If it's a non-writable medium then they literally can't pull browser history or any of that from the device on your person. If you boot off a separate media that connects to a vpn on boot, you're most likely protected from whatever is normally running on that computer.  A firmware monitoring software, or a keystroke monitor built into the hardware might be the most you need to worry about.

You might want to consider also getting a Magic Jack. It is an internet device which lets you make phone calls to the US from any Internet connection. Reverse calls are also possible, the people in the USA get a USA number to call, and as long as your device is plugged in and connected you will get the call.

---

### Post by DuckHook on 2018-01-25
This very useful and informative thread is in danger of veering off to the political. For clarity: "XX border services can stop you within 100 miles of a border" is a statement of fact. "Such-and-such government/agency is evil/intrusive/not-to-be-trusted" is an opinion, and a political opinion at that. Please stick to discussion of facts, not political opinions, and everything will be fine.

---

### Post by Pat201 on 2018-01-27
> **TheFu said:**
> Congrats!

Pro-Tip - Use the router to listen on port 443/tcp on the WAN side, but translate that to port 22/tcp on the desktop running x2go server. That way, hotel internet filters probably won't block it.



Well, I broke something.  I got it back working again, but don't know how.  I had port 22 forwarded to a high 50000 number and it was working ok 'til I noticed that I was accessing the 50000 number directly through the client.  I thought, that's not how that's supposed to be, reread your message to confirm and saw the 443.  So in "fixing" it, I changed the 22 to 443 and then changed my client to access 443.  Can't get it to work.  Have tried all kinds of iterations and can't make it work, so everything's just back to 22 for now.  In googling to make sure my router is set up correctly (a small, older Netgear), it looks like there's possibly a conflict with 443 due to the Netgear Genie software that configures the router.  Some folks say it works fine, some say you can't redirect that port due to the software and it's default setting that cannot be changed.  One Netgear tech in an older post on their site said you can't *change* that port because of the router software, but he goes on to say that shouldn't affect accessing the router software on the internal lan because you're not being "forwarded" through the router which makes complete sense to me.  BUT, he says he's not sure if that is the problem or not.  So I'm not sure if I can forward that port or not with my router.  I would like to play with that DD-SRT software sometime just for sport, but that'll have to wait until after my trip!  :)  I have a whole drawer full of old Netgear and Belkin routers I can play with.  So anyway, I hope to get back on this if I have time after I finish up the rest of my "honey do" list.

Oh one other question, I saw where someone said to make sure you change PermitRootLogin yes to no in the sshd_config file.  Is that a good idea, or should I leave that alone?  Right now I can log in as either root or my user name from the x2Go client.

---

### Post by Pat201 on 2018-01-27
> **TheFu said:**
> BTW, allowing any camera to be accessed directly over the internet is 99.99999% a bad security choice.  Those things are often used for attacking others if they are accessible to teh outside world.  [https://securityledger.com/2016/09/the-hacked-camera-botnet-not-new-just-big/](https://securityledger.com/2016/09/the-hacked-camera-botnet-not-new-just-big/) - your brand is listed prominently as being hacked.  You don't need to unplug them, but I would block all internet access for them ASAP.  They should only be available on the LAN - but you can use the x2go desktop to see them.  ;)

You mean attacking others *physically* or using them for some type of network attack?  I'm just running their app on my phone right now (which is all I've had time to mess with), but accessing them through x2Go does make more sense.  Yeah, I'm not big on the "police questioning" thing, but since I don't have anything to hide and 99% of the time it's probably just some guy trying to do his job and go home, I would probably just answer to be on my way.  Plus, even though I'm a pretty ornery old ba*****, I'm basically a nice guy and am polite to everyone I meet.  He would have to be a real tool and tick me off for me to shut down and tell him p*** off and call a supervisor or something.  I'd rather just be "violated" and be on my way.  LOL

Oh wow, yeah reading that article now.....  I did think it was weird that as I was setting the cameras up (haven't used them in 4 years) that there was no upgrade to the firmware or anything.  That was the first thing I checked and I'm still current.  So obviously nothing has been patched, at least on my system.  :(

2nd edit:  I know it's just my opinion and my opinions are sometimes way off base, but I feel as long as the justice system all around the world keeps treating these things as "white collar crime" and "folks just playing around with computer systems" and giving people slaps on the wrist, this is only going to escalate more and more rapidly.  When you steal someone's identity, you can wreck their entire lives.  I hate a freakin thief of any kind and I think when they catch these people, they need to give them *serious* jail time.  And not in some dang country club somewhere, but they need to be on a work gang somewhere.

---

### Post by Pat201 on 2018-01-27
> **1clue said:**
> You might find it convenient to not bring a computer at all. I would consider bringing a bootable, write-protected USB stick or even dvd or cd. Make a boot device that works with almost anything (system rescue CD?) and then add stuff to get you connected back home. Definitely the VPN in this case.


I won't be travelling outside the US, but good points!  That's a good idea for the write-protected boot setup and I encrypted my USB data stick last night.  I'll keep that on the keychain in my pocket.

---

### Post by TheFu on 2018-01-27
Yes, network attacks.  Don't let any "devices" on your network be directly accessible from the internet. PERIOD.  That means security systems, cameras, routers admin, TVs, etc.  If you need to use some special software to access it inside your home, from the outside world, don't trust it.  That means someone else can also access it from that provider/company/group at a minimum and they will be hacked.

OTOH, if you use x2go or a full vpn to gain access, that is fine.  Both of those aren't dependent on 3rd party authentication. There are public keys and private keys. You control both.  This is the flaw of HTTPS websites and people believing they are secure.  There has to be trust in every single CA and every single DNS provider for that system to work.  Both types of providers have proven to be unworthy of our trust. It just takes a few bad CAs to ruin the entire HTTPS trust model.  Eventually, they are caught in our part of the world, but not everywhere.

As for the port forwarding ... you want the LAN side to always point at 22/tcp.  It is the WAN side that 443/tcp (or 59000/tcp or something else) are needed.  Hotels tend to block most ports, so using 443/tcp on the WAN side is probably a good choice if access from hotels, libraries, cafes, restaurants is what you want.

---

### Post by Pat201 on 2018-01-27
> **DuckHook said:**
> This very useful and informative thread is in danger of veering off to the political. For clarity: "XX border services can stop you within 100 miles of a border" is a statement of fact. "Such-and-such government/agency is evil/intrusive/not-to-be-trusted" is an opinion, and a political opinion at that. Please stick to discussion of facts, not political opinions, and everything will be fine.

Point taken.  Good security measures should be learned and practiced, no matter what device you're using and no matter the reason.  I'll try to just stick to learning network security and leave my opinions out of it DuckHook.  :)  Again, I really appreciate everyone's help!

---

### Post by Pat201 on 2018-01-27
> **TheFu said:**
> As for the port forwarding ... you want the LAN side to always point at 22/tcp.  It is the WAN side that 443/tcp (or 59000/tcp or something else) are needed.  Hotels tend to block most ports, so using 443/tcp on the WAN side is probably a good choice if access from hotels, libraries, cafes, restaurants is what you want.

That's how I had it and it was working when I had the client going directly to that port, but quit when I changed it.  I had it like, reconfigured sshd_config to point SSH at port 55322.  Then the router was set to forward port 22 on the outside to port 55322 on the inside.  That was working, but I had the client set to access port 55322.  I don't know *how* that was working, but it was.  LOL  Then I reread your post about port 443.  So I changed the router to port 443 on the outside pointing at port 55322 on the inside and changed the client to access port 443.  Can't get it to work for beans.  Called myself trying every possible configuration until giving up about 1:30AM.  What I *didn't* try was using something other than 443 after I read the deal about some Netgear routers not wanting to forward port 443.  So I'm going to try that today if I get time.

---

### Post by TheFu on 2018-01-27
Don't touch the sshd_config file port setting.  You want 22/tcp to be used internally and 443/tcp to be used from the Internet.

There are only 2 ports, not 3.  How does 443 --> 55322 --> 443 work?
In needs to be 443 --> 22 --> 22

If the router does port translation, 443 will work from the outside.  I think the 443 from the inside is for admin access to the router. That is completely different, using a different network interface, in a different direction.  Routers and firewalls understand which NIC is used and which direction the traffic started.

---

### Post by Pat201 on 2018-01-27
Nope, just two ports.  I thought you changed the 22 to a different port so someone trying to get in wouldn't know what port they were looking for.  That's why I changed that port to 55322.  Then I was trying to port forward 443 on the outside to 55322 on the inside, in other words, 22 was gone.  I didn't realize the inside port always had to be 22.  Ok, I'll change the config file back, set the router back to 443 and 22 and see what I get.  :)

---

### Post by Pat201 on 2018-01-27
Yep.  It's working now.  :)

---

### Post by TheFu on 2018-01-28
> **Pat201 said:**
> Nope, just two ports.  I thought you changed the 22 to a different port so someone trying to get in wouldn't know what port they were looking for.  That's why I changed that port to 55322.  Then I was trying to port forward 443 on the outside to 55322 on the inside, in other words, 22 was gone.  I didn't realize the inside port always had to be 22.  Ok, I'll change the config file back, set the router back to 443 and 22 and see what I get.  :)

It is all relative.  When setting this stuff up, you have to think "I'm coming from the internet, how do the connections need to work"  and then from inside, "I'm on the same LAN, how do I ssh in."  Once you get those 2 thought exercises down perfectly, this stuff will be easy.

Plus, but using a different port from the internet for ssh, you can probably test the internet stuff from inside just ssh'ing to public_IP:443. Some routers have protection against that, but not all do.  I guess it is a way that bad websites trick a router into opening ports for them automatically, so that's why router software often prevents this inside-outside-inside connections.

Anyways, time to get to a library or cafe and test this out like you were in a different city.

Did you setup ssh-keys?  Using passwords over the internet isn't safe.

---

### Post by Pat201 on 2018-01-28
Yeah, I tested it from our shop about a mile away.  Or my son uses his phone as a hot spot sometimes, but he wasn't around when I wanted to test it.  :)  No, I haven't set up ssh-keys.  I've got about a half hour before I get ready, I'll give it a look.

---

### Post by Pat201 on 2018-01-28
Couldn't make it work and I'm out of time.  :(  Once again, I REALLY appreciate everyone's help!  I hope to continue this journey when I get home.  :)

---

### Post by TheFu on 2018-01-28
* Setting up keys can be done while passwords are still left enabled.
* Create the keys - default is **ssh-keygen**.  This makes files in your ~/.ssh/ directory.  The default names are fine. No need to change them today.  I don't remember needing any options for the command.
* Push the public key to the other system - use **ssh-copy-id**.  In the old days, we had to manually push the file over, being careful about owner, group, permissions, and that no newlines were inserted.  *ssh-copy-id userid@server-ip *handles that for us now.

That's it.

You can screw around with ssh-agent so you only need unlock the keys once every few hours or once a day. Or ignore that for now.

ssh-keygen has all sorts of options. ssh will let you pick more secure ciphers, but the defaults are reasonable. If you are really concerned, change to an elliptical cipher.  That can wait.

When you know how to do it, this stuff takes less than 3 min and most of that is waiting for the keys to be created.

NEVER, EVER, share the private keys. NEVER.  The public keys can be shared, but that is only useful for systems you want an easy, remote, connection into.

There is a ssh config file for every user that lets you setup per-connection settings.  For example, with some systems, I only have the IP and a funky userid and connect on an odd port that I don't control.  But I just run **ssh petes** and the different userid, different port, and IP are filled in automatically.  This works for **every** program/tool that uses ssh.  Inside x2go, I say "petes" for the server and it all gets filled in.  And my ssh keys are used.  rsync, ssh, scp, sftp, backup tools, and every GUI app honors the config file.  man ssh_config 
explains the different settings.  They follow the old Windows .ini file style.

Have a good trip.

---

### Post by Pat201 on 2018-02-10
Well I'm back.  Only had to tunnel in one time and everything seemed to work as planned.  I'll work on setting up the keys in case I go on another trip for work and I'll continue on learning about security.   I'll try to keep my netbook as "hard" as I can get it as I learn more.  Again, I really appreciate all the help!  We went through 5 or 6 border checkpoints going and coming and no one even glanced sideways at us as they waved us through even though we were driving a big black van pulling a big black trailer.  :)  I'm guessing all the plate scanners and facial recognition scanners already ID'd us as not suspect as we went through.  :)

---

