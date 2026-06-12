---
title: "Transparent Proxy + Dans Guardian"
date: 2011-03-02
forum: Server Platforms
---

### Post by 75HUkv4xGlY986i5 on 2011-03-02
Hi all,

I was wondering if the following scenario was even possible. If it is and you have information about it, I would appreciate you passing it on to me.

As an fyi, I am not a very savvy linux user. I am also not a developer, I do not know any programming at all, which seems to make using linux more difficult.

I want to have a content filter that is completely transparent based on ubuntu (I am more comfortable with ubuntu). I assume I will need some sort of transparent proxy/bridge type setup. I have read about squid, but it sounds like TinyProxy would suit me better if it is capable of doing what I want since it is much lighter weight (we are talking 10-15 lan users max). I want to place a VM between my firewall and my network. I want this VM to pass all traffic through an AV like Clam AV or equivalent and dans guardian content filter, as it seems to be the best one out there. I don't want it to be possible to get around this CF either, such as bypassing the CF. I run a packet filter bsd firewall and do not want that to change and don't want to tack these additional services on to my firewall. I also want to to be able to NAT/Port forward to my internal network at leisure without issues with the CF/Proxy. I do not want there to be any client side configuration at all, ie having to set proxy in web browser/other clients.

Is this possible? Are there any well documented instructions that I can follow? The more simple and more spelled out the better, as I am only slightly experienced with Linux, but am capable enough to follow well written instructions. Thanks for your time in helping me out.

---

### Post by rubylaser on 2011-03-02
If you're going to setup a virtual machine anyways, I'd just install IPCOP with the Dansguardian and Copfilter Plugins.  That will do everything you want, without having to edit configuration files and with a simple web GUI to manage it all.  If you don't want to use IPCOP as the firewall, you'll need to enable something like WCCP (Web Cache Communications Protocol) to force all web traffic going to your firewall gateway through the proxy.  That way, there's no way to bypass the proxy, and there's no configuration necessary on the client.

Just my 2 cents.

---

### Post by SeijiSensei on 2011-03-03
Let me suggest that you start by reading up on running a [transparent proxy with Squid]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html").  I'm pretty sure DG uses squid, so you might be able to kick it into transparent mode.

If you're concerned about blocking malware and the like, you can implement filtering by extension in squid, and add [SquidClamAV]("http://squidclamav.darold.net/") to actually scan every object.  Filtering by extension is pretty easy in Squid, though you'd need to learn a bit about "[regular expressions]("http://www.zytrax.com/tech/web/regex.htm")" to write the rules.  For instance, these rules block all downloads of anything ending in .exe:

```

acl EXE url_regex \.exe$
http_access EXE deny

```

(The "\.exe$" is a regular expression that matches any URL ending in ".exe".)  The "acl" defines a pattern that I've arbitrarily named "EXE" against which web requests are matched.  The http_access rule denies downloads of objects that match the pattern referenced by EXE.

---

### Post by 75HUkv4xGlY986i5 on 2011-03-03
@rubylaser
Thanks for the IPCop suggestion, I did think about it before posting, but I already have an excellent firewall that I will not replace. I am also not keen on putting another layer onto my simple network as it doesn't seem necessary (double NAT particularly). I am willing to put in the work to make it a seemless drop in solution that end users won't even notice (unless they of course are being naughty on the net). I ultimately want to be able to clone my vm and drop the same setup into place at friends and family's homes that have expressed interest in having it.

@SeijiSensei
Thanks for the links and advice. Your first link seems to be dead, perhaps it is simply site maintenance occurring as the home page fails to load as well. My concern with Squid was that I read it has a larger footprint which means it requires more resources and sounds like it was slower, but if it is what will work best then I will do it. I try my best to set it up correctly. Thanks also for the SquidClamAV link, I didn't realize there was already something that would work with squid which sounds great. Thanks for the regular expression example too, regular expressions melt my brain and they cause me fear.

Thanks for the input guys. I will continue on my conquest. Any other comments, suggestions, links and whatever else are all very welcome. I will try my best to put together some solid documentation as well since I can't seem to find anything anywhere. I will create a post with all the steps I went through so others in my similar situation can have a resource to turn to.

---

### Post by koenn on 2011-03-03
couple of things to look out for

the general idea of "transparent proxy"ing is that your default gateway (your router and/or firewall) detects traffic going towards any port 80 on the internet, and redirects it to the [NOPARSE] address:port[/NOPARSE] where your proxy lives. 

that means the exact rules will vary with whether the proxy runs on the routing host (and you'd have an iptables REDIRECT), or on a separate machine (which would require a Destination NAT). Note that this needs to be set on the router/firewall, not on the proxy host. 
Otoh, this arrangement breaks the normal HTTP flow, which is why squid needs to be made aware of this, by adding the keyword 'transparent' in its conf. 

I'm pointing this out because the guide is rather unclear on this point. Also, since you already have a firewall and intend to keep it, you'll have to figure out how to configure DNAT on it. 

If you're going to use Dansguardian (recommended, very easy to set up  content filter), you redirect to that; it will expect to be talking to a squid, but that's something you configure in dansguardian's config; squid can be on the same machine as DG, or a separate one. 


lastly,
> I do not know any programming at all, which seems to make using linux more difficult. 
you should get  that idea out of your head as soon as possible. 
You're not doing any programming. Your configuring software. Editing values in a configuration file is a lot closer to entering values in the text box of a wizard than it is to programming.

---

