---
title: "Help choosing firewall, ipcop vs the rest"
date: 2007-01-27
forum: Server Platforms
---

### Post by Barleyman on 2007-01-27
I know this has nothing to do with ubuntu, but....

Currently, I am using a linkys router as my firewall, but I am planning on implementing a firewall with more flexibility to allow for dmz, vpn, bluezone for wireless, etc.

Any opinions on these

ipcop
pfsense
monowall
smoothwall

---

### Post by Ritchstorm on 2007-01-27
I was actually just going to post something like this as well. I am soon going to be opening all ports on zoom router (like i have done on my windows installation) and was just wondering if there was something similar to zonealarm for edgy 6.10.

---

### Post by chrisfay on 2007-01-27
I've used both Smoothwall and IPcop for dedicated firewalls and can say they are both great packages. IPcop's developers were originally devs on the smoothwall project hence the original IPcop software was virtually identical to Smoothwalls. It has since evolved into a very individualized product with some good features. 

I would suggest starting at the Smoothwall and IPcop documentation as its pretty informative. If you need more, the forums and other support options on their sites should provide most everything else. 


As for the other packages you listed, I have not personally tested them....

---

### Post by Bite_me_Bill on 2007-01-28
One that you don't have listed that I am most happiest with is Endian.  I think it's a Smoothwall or IPCop matured version.

---

### Post by chalex on 2007-01-28
My gateway box is regular Debian with two ethernet interfaces, running [Shorewall]("http://www.shorewall.net/").  Then again, I'm a Linux sysadmin at work :)

From what I hear, all those little distros are good and user-friendly.

---

### Post by Wim Sturkenboom on 2007-01-28
> **Ritchstorm said:**
> ... if there was something similar to zonealarm for edgy 6.10.It's called *iptables* and is standard on any Linux distro nowadays.

You can configure it from the commandline (read the manpages) or you can get a graphical frontend (like *firestarter*). Some of the others above are probably also graphical frontends for iptables, but I don't know them and don't feel like doing the research at this moment.

---

### Post by esaym on 2007-01-28
I really think smoothwall is the best.  I have been using it for 4 years now.

Here is a pre loaded iso with a butt load of mods already installed (there are other iso's similar to this one too you just have to search..): [http://community.smoothwall.org/forum/viewtopic.php?t=20262](http://community.smoothwall.org/forum/viewtopic.php?t=20262)

There are alot of mods, almost overwhelming.  I have been there since the beginning so I know my way around pretty good, ask me anything is needed.


Must have mods:
[http://community.smoothwall.org/forum/viewtopic.php?t=8206](http://community.smoothwall.org/forum/viewtopic.php?t=8206)
[http://community.smoothwall.org/forum/viewtopic.php?t=11140](http://community.smoothwall.org/forum/viewtopic.php?t=11140)
[http://community.smoothwall.org/forum/viewtopic.php?t=7138](http://community.smoothwall.org/forum/viewtopic.php?t=7138)
[http://community.smoothwall.org/forum/viewtopic.php?t=8449](http://community.smoothwall.org/forum/viewtopic.php?t=8449)
[http://community.smoothwall.org/forum/viewtopic.php?t=7922](http://community.smoothwall.org/forum/viewtopic.php?t=7922) ( [qos help ,kinda]("http://community.smoothwall.org/forum/viewtopic.php?t=21284") )
[http://community.smoothwall.org/forum/viewtopic.php?t=5698](http://community.smoothwall.org/forum/viewtopic.php?t=5698)
More mods: [http://community.smoothwall.org/forum/viewtopic.php?t=2873](http://community.smoothwall.org/forum/viewtopic.php?t=2873)

If you use snort there is a bug where if your red ip is set to use dhcp.  When smoothwall starts up there will be 2 snort processes running for some reason.  You just have to manualy go into the web gui and stop snort (ids)and then start it again

:guitar:

---

### Post by Barleyman on 2007-01-30
Thanks all for your help,  I think I will give ipcop or endian a try first.  I have a decent dedicated machine to use (512 MB RAM, and AMD 1.2 GHZ).  I was contemplating using a vmware virtual machine, but the whole idea of a firewall on a virtual machine seems a little scary to me,... I guess I am a little old school and would just like to see my network physically separated from firewall.

What does everyone else think?

My only worry about endian, is will it survive.

---

### Post by Bite_me_Bill on 2007-01-30
> **Barleyman said:**
> Thanks all for your help,  I think I will give ipcop or endian a try first.  I have a decent dedicated machine to use (512 MB RAM, and AMD 1.2 GHZ).  I was contemplating using a vmware virtual machine, but the whole idea of a firewall on a virtual machine seems a little scary to me,... I guess I am a little old school and would just like to see my network physically separated from firewall.

What does everyone else think?

My only worry about endian, is will it survive.

Your dedicated machine should run any of them without any problems with a high number of users.  But I am in agreement with your "old school" ways.  A firewall appliance should be a dedicated piece and not a shared.  Though normal users might not think that they are getting alot out of it but those that know the internet is a nasty place can respect the fact that it's dedicated and there are less worries.  Sleeping with one eye open isn't much fun.

---

### Post by Brazen on 2007-01-30
My personal favorite is pfsense.

---

### Post by Toontje on 2007-01-31
When you are looking for a free firewall for home use, you can take a look at [www.astaro.com](www.astaro.com).

This is not open source, but for home use you get a 3 NIC, 10 ip version for free. I use it for over 3 years now and I'm about to upgrade from verion 4 to the current version 7.

---

### Post by esaym on 2007-01-31
The thing I always hated about other firewall distro's was the simple lack of a good support forum.....

---

### Post by Barleyman on 2007-02-01
> **esaym said:**
> The thing I always hated about other firewall distro's was the simple lack of a good support forum.....

Are you implying that ipcop has a good forum?

---

### Post by esaym on 2007-02-01
> **Barleyman said:**
> Are you implying that ipcop has a good forum?

Yes both ipcop and smoothwall.  However, back in the day smoothwall was the only one with a support forum, hence why I went with them ;)

---

