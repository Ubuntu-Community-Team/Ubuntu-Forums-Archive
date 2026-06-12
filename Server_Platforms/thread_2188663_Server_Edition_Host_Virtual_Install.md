---
title: "Server Edition Host Virtual Install"
date: 2013-11-18
forum: Server Platforms
---

### Post by ibjsb4 on 2013-11-18
I am getting prep up for yet another install.  This time I am using the server edition of 12.04 and doing a virtual install to be turned into a desktop.

I have mention this in two other threads, but no one agreed with this approach.

I know that sound will not be installed and doc's will be gone.

This is just another attempt to lower my installed package count.

I posted in servers because only the server install offers the virtual install.

Any thoughts?

---

### Post by TheFu on 2013-11-18
What do you mean by "virtual install?"  JeOS or something different?

I load Ubuntu Server, then a window manager or LXDE for my desktops to limit bloat myself. I run these desktops mostly inside KVM virtual machines and use ssh mainly to access the VMs, but either Spice or NX for remote desktop access from around the world as well.  My blog has about 5 articles about this.

I would not consider using JeOS for a desktop. The number of missing functions would not be my recommendation for a desktop.

---

### Post by ibjsb4 on 2013-11-19
Hi TheFu

> What do you mean by "virtual install?"  JeOS or something different?

If you go to F4 at the beginning of the install, there is the option to do an install just for running VMs. And I am only doing this for the low package count.

Anyhow, I went ahead a did it last night.  Got startx running and my basic classic/fallback desktop.  Package count stands at 505 installed packages.  Of course this is a bare bones desktop.

---

### Post by TheFu on 2013-11-19
Firewall?  Every desktop needs to run a firewall.
If you just want a small OS, take a look at **TinyCore**.  12MB including X/Windows.

---

### Post by capscrew on 2013-11-19
> **TheFu said:**
> Firewall?  Every desktop needs to run a firewall.
I have a Firewall at the edge of my network that seems to stop everything.  Am I missing something here?  I'm not arguing the point.  I'm interested in learning new stuff and protecting my desktop users the best I can.  They're all Ubuntu desktops if that matters.

---

### Post by TheFu on 2013-11-19
> **capscrew said:**
> I have a Firewall at the edge of my network that seems to stop everything.  Am I missing something here?  I'm not arguing the point.  I'm interested in learning new stuff and protecting my desktop users the best I can.  They're all Ubuntu desktops if that matters.

Why does every desktop need a firewall even if there is another firewall at the edge?
[LIST=1]
[*]Any Windows machines on the network?  'nuff said.
[*]Do you allow javascript/flash on the machines?
[*]Are any ports opened to the outside world? Any?
[*]Inbound ssh, ftp, sftp, webDAV, calDAV, email, torrents, and 500 other things?
[/LIST]

I think the only one of those that is not obvious is the javascript.  Javascript is a complete programming language including commonly used network features. Javascript is designed to be contained within the browser on the system it runs on, but what about all the other machines on the internal network?  Well, javascript can be used to launch attacks against those ... don't forget that letting a remote website run javascript is just asking them to use that for purposes you do not necessarily agree with AND those sites will almost always trust another 4th party for advertising.  Malware has been delivered using both javascript and flash from trusted websites ... after the ad network was cracked.

Most people are NOT paranoid enough when on the internet.

---

### Post by ibjsb4 on 2013-11-21
I would prefer to stay out of the firewall conservation :) but I do have one last question for you before I put this thread to rest.

As stated I have startx.  Its setup identical to my other install, but this new install takes an extra 15 seconds to boot.  This has been going on since installing startx.

I have ~/.xinitrc in place just like the other install.

I have ~/.profile in place (auto X start scrip) just like the other install.

I have gone through init and xinit files, they are all the same.

The other install was done with the mini iso and of course this one is not.  I might add that I went ahead and turned it into a 90% complete desktop without problems.  Total install takes 2.5GB to date.

---

