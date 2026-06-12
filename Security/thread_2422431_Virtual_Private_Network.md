---
title: "Virtual Private Network"
date: 2019-07-07
forum: Security
---

### Post by cruzer001 on 2019-07-07
This project started out simple enough.  Just wanted a extra layer of security/privacy when using a public internet connection.

The seemingly simple solution is just use a browser VPN plugin and call it good. This could still turn out to be the solution for a single user machine.

But then I started reading about the pro's and con's of vpn servers.  Now its got me thinking that I should install ubuntu vpn server instead of using a plugin. This setup would allow me explore vpn and hopefully acquire enough confidence to one day convert the whole house (4 computers) to vpn.

What I'm looking for is a direction to take, the proper server (free) to start this venture with and keep it as simple as possible.  I know there are other uses for vpn, but the two things I really care about are security (without to much of a performance loss) and privacy.

I'm new to vpn so all input is appreciated.  Thanks for reading.

---

### Post by #&amp;thj^% on 2019-07-07
A couple of good links to start: [https://www.cyberciti.biz/faq/howto-setup-openvpn-server-on-ubuntu-linux-14-04-or-16-04-lts/](https://www.cyberciti.biz/faq/howto-setup-openvpn-server-on-ubuntu-linux-14-04-or-16-04-lts/)
And: [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04)
This will all sound very foreign for a bit of time.
TheFu has some great points also, do a search in the forums. (Trust is an issue for me with paid VPN's research, research, research.)
Good Luck :)

---

### Post by TheFu on 2019-07-07
VPNs only provide security if you run the server on hardware that you control, on a network that you trust.

Other that that, they are for privacy, assuming the VPN provider can be trusted.  [https://www.infosecurity-magazine.com/news/29-vpn-services-owned-by-six/](https://www.infosecurity-magazine.com/news/29-vpn-services-owned-by-six/)  Basically, if it is free, then you don't have either security or privacy.

Browsers can't be trusted, IMHO.  They are extremely complex software and have a history of claiming something in their features which turned out to be less than true. How many times has "private mode" been found to be non-private mode?  7, 10? Sometimes that truth was marketing-speak and other times it was software bugs. Regardless, I don't believe any claims from browsers about security or privacy, addons and plugins included.

As you know, security and privacy aren't the same thing.  If you want security, get a chromebook and run chromeos, just don't expect any privacy.  Privacy is 1000x harder on the internet.  I don't think it is possible today, at least not against a dedicated govt trying to unmask you.

I run a VPN for connections home from the outside world.  I used to run VPNs for very large enterprises with many thousands of concurrent connections.
I have a paid VPN provider with exit nodes around the world for other reasons.  The US-FBI has tried to get their connection records multiple times and failed. They do not retain any records of that type 3 minutes after the connection is closed.  This means that people using a VPN 24/7 have significant risk from govt tracking, if they don't close them from time to time.

Of course, some people think I'm paranoid.  I've just been in the industry a long time and worked in large-scale telecom long enough to know what they can accomplish and what security-vendors can accomplish too.  Most people have never heard of these companies providing network tools for enterprises and govts world wide.

So ... I use openvpn with AES-256-CBC for the VPN server that I run.  I've installed the cert file and use them for the paid VPN service with AES-256-CBC too.  There are other specific, non-default, settings that I changed in the commercial client, since their defaults are good enough for most people. I don't remember them nost, but went through the manpage setting for setting.

---

### Post by cruzer001 on 2019-07-07
As luck would have it, two post from the forum finest :)

@1fallen
Thanks for the links.  I'll give them a proper read tonight when I have some time to myself.

@TheFu
> VPNs only provide security if you run the server on hardware that you control, on a network that you trust.
Public networks of course cannot be trusted, but I thought the added encryption that vpn can provide would be enough when logging onto a untrusted network.  Am I wrong?
> Browsers can't be trusted, IMHO.
I agreed with you.
> get a chromebook
Chromebooks are not allowed in this house :D
> The US-FBI has tried to get their connection records multiple times and failed. They do not retain any records of that type 3 minutes after the connection is closed.
Provider trust is a big issue.  I realize some providers sell or store user information.
> Of course, some people think I'm paranoid.
I use to think that added security was unnecessary for the home user, but times have changed.  Selling information is big business these days.
> I use openvpn with AES-256-CBC
AES-256-CBC - my first thought was "what the hell is that" :)  So I did a quick search and now know what it is, but don't understand why this is a needed package.  Again, need to do a proper read on it tonight.

Thanks guys :)

---

