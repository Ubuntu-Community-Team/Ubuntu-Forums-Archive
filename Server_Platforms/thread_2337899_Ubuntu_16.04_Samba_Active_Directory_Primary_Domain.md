---
title: "Ubuntu 16.04 Samba Active Directory Primary Domain Controller"
date: 2016-09-22
forum: Server Platforms
---

### Post by blechinger on 2016-09-22
Hello all,

I'd like to open up a big can of worms and ask some questions about AD domains via Samba 4.

First some background:

I've got a very small network and a VM cluster running inside of it. All of the VMs (dev and prod) are linux. Most of the other bare metal boxes I've got are user PCs running windows. I think I'm ready to create a domain and I'd like to do that in a way that allows me to join all of those Linux/Windows machines to the same domain. I do *not* want to start buying Windows Server 2012r2 lics or let Windows have more control than I absolutely have to.

I'm a network admin. I've worked mostly in Windows at the server/admin level. I've worked in linux at a user/dev level for about a decade off and on. Ubuntu Server is still pretty fresh territory for me.

Now the questions:

I've googled around a bit and found a useful [guide]("http://blogging.dragon.org.uk/samba4-ad-dc-on-ubuntu-14-04/") or two walking one through how to setup what I'm talking about, however; they're all for 14.04. Could the same steps from the aforementioned guide be applied directly to 16.04? If not what steps should I take? What pitfalls can I expect when adding a Windows 10 PC to the new domain? What functionality can I expect? Any recommendations on additional tools to aid administration?

Feel free to shout me down about any misconceptions I may have. I assume what I'm looking to do is possible (it seems to be hinted at here and there when I'm surfing around) but I haven't seen any great, concise, central documentation regarding Samba 4/Kerberos/Ubuntu Server/Active Directory and what one's expectations should be for Windows + Linux integration. Any help is greatly appreciated! :) Thank you.

---

### Post by darkod on 2016-09-22
16.04 is fairly new so it will take time for the tutorials to get "translated" over... I would expect that guide to work for 16.04 too.

You can add all windows clients to a Samba AD, not sure what pitfalls you think you might expect... For administration from windows, you can use the standard MS RSAT tools (or called differently over various versions of windows but you get the point). The basic stuff like Users and Computers, DNS and GPO should work from those tools identically like on windows. I haven't tried configuring DHCP with the tools though.

For a basic domain without too much specific MS requirements, Samba AD will do the job perfectly. And with a free license. :)

---

### Post by blechinger on 2016-09-22
@darkod

Righteous. This is pretty much what I figured but I wanted to hear it from you guys. Pretty neat that I can use RSAT for administration. I'm looking forward to playing around with that. :)

Pitfalls I'd expect...? Windows registry is pretty finicky.[I]shrug
[/I]Since I've never done it before I'd expect Windows to fight me tooth and nail! Your comments give me enough confidence to forge forward and give it a whirl though.

Thanks again!

---

### Post by darkod on 2016-09-22
The good thing about Samba AD is that windows clients won't even know the difference. So, expect minimum fighting from them. :)

Where you might have issues are things that reside on the DC in a windows network. Obviously Ubuntu with Samba is not identical to full Windows Server. That's why I said that if you don't need some specific MS requirements, you should be fine.

If I'm not mistaken, Samba guys were able to do this only after a court order making MS to share the AD code (or part of it anyway). That was the missing link that helped Samba create the AD that looks identical (or at least very, very similar) to a windows AD. So the clients have no clue they are talking to a linux server in fact...

---

### Post by blechinger on 2016-09-22
Well that's neat. I figured there was some sort of translating going on but it sounds like it might as well be AD for most normal operations. Very cool.

Would you mind expanding on "specific MS requirements"? What do you think won't work (major Group Policy overhauls/restrictions, multi-domain forests)?

At this point all I'm really looking to accomplish is:

Primary AD DC: DHCP/DNS/AD/SSO
Backup AD DC: DHCP/DNS/AD/SSO/Fail-over

---

### Post by darkod on 2016-09-22
To be honest I wasn't thinking on anything specific. I just wanted to point out that of course we can't expect this server to behave fully like Windows Server.

For what you mention, I would use:
DHCP - I would use either isc-dhcp or dnsmasq (the standard linux packages for dhcp). Of course, you can try the DHCP tool from RSAT (right now I can't even remember if it shows up installed and as I said I have never tried to use it anyway).
DNS - the built-in Samba internal DNS works just fine, but you can use the bind9 alternative too for more complex dns
AD - works
SSO - this would depend more on the applications that you will use, and how they can use the AD logins (or not)

In the last few years I have setup 2 projects with ubuntu+samba domain controllers in network with exclusively windows workstations. They haven't complained on anything major. :) I used 14.04 purely because 16.04 wasn't out yet.

This should work out fine for you, give it a shot. And any problems that you might run into, are probably solvable with the help from google and ubuntu forums.

---

