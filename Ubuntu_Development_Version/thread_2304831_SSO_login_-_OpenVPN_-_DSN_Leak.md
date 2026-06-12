---
title: "SSO login - OpenVPN - DSN Leak"
date: 2015-11-30
forum: Ubuntu Development Version
---

### Post by sammiev on 2015-11-30
Running Ubuntu-gnome 16.o4 and in the last 4 or 5 days I started having trouble staying login to this forum.

I have it tracked down to the OpenVPN.

I noticed this [thread]("http://ubuntuforums.org/showthread.php?t=2304547") a day or two after I started having the same problem.

I noticed whenever the leak takes place, I loss connection or login to this site.

Tested the DNS leak using a few programs and both programs show there is a DNS leak.

When running without the VPN there is no issues, been testing this for 2 days now.

No issues with Windows OS or Android running the same VPN.

Anyone else?

Thanks

---

### Post by QDR06VV9 on 2015-11-30
> **sammiev said:**
> Running Ubuntu-gnome 16.o4 and in the last 4 or 5 days I started having trouble staying login to this forum.

I have it tracked down to the OpenVPN.

I noticed this [thread]("http://ubuntuforums.org/showthread.php?t=2304547") a day or two after I started having the same problem.

I noticed whenever the leak takes place, I loss connection or login to this site.

Tested the DNS leak using a few programs and both programs show there is a DNS leak.

When running without the VPN there is no issues, been testing this for 2 days now.

No issues with Windows OS or Android running the same VPN.

Anyone else?

Thanks
Thanks sammiev I have complained about that for a couple of months now.
I have since added Arch to my multi-boots and not one minute of problems now.
Not a rant here but merely the facts and this happens on trusty, vivid, and wily to present.
Regards

---

### Post by dave205 on 2015-12-28
> **runrickus said:**
> Thanks sammiev I have complained about that for a couple of months now.
I have since added Arch to my multi-boots and not one minute of problems now.
Not a rant here but merely the facts and this happens on trusty, vivid, and wily to present.
Regards


thanks runrickus for the info. I too have found the leak in 15.10. I see you mention Arch. do you have any pointers to that? I don't believe I've heard of it before.  Also does that fix the dns leak issue?

---

### Post by QDR06VV9 on 2015-12-29
> **dave205 said:**
> thanks runrickus for the info. I too have found the leak in 15.10. I see you mention Arch. do you have any pointers to that? I don't believe I've heard of it before.  Also does that fix the dns leak issue?
Hi dave205 Sorry I have not paid attention to this thread for while, But Arch is another Linux OS(more Info here [http://distrowatch.com/table.php?distribution=arch](http://distrowatch.com/table.php?distribution=arch))
Sorry to get your hopes up.;)
Kind Regards

---

### Post by dave205 on 2015-12-30
> **runrickus said:**
> Hi dave205 Sorry I have not paid attention to this thread for while, But Arch is another Linux OS(more Info here [http://distrowatch.com/table.php?distribution=arch](http://distrowatch.com/table.php?distribution=arch))
Sorry to get your hopes up.;)
Kind Regards

No problem RunRick.  I've heard of the Arch Linux before but for some reason it just didn't occur to me that you were talking about the distrib. I guess I had "package" on the brain. Good news is that I've found the fix for the CLI openvpn but not for the config manager vpn.  If interested you can read about it here - [http://ubuntuforums.org/showthread.php?t=2307975&p=13414596#post13414596](http://ubuntuforums.org/showthread.php?t=2307975&p=13414596#post13414596)

---

### Post by andrew102 on 2016-01-05
Not sure if this is related. But I run a BIND DNS server on my local LAN. I was finding that I was unable to resolve intranet addresses around 9/10 times until I removed secondary DNS servers from the network configuration. BIND is set as a forwarder anyway so it is okay for me to have a single DNS server.

---

### Post by sammiev on 2016-01-05
> **andrew102 said:**
> Not sure if this is related. But I run a BIND DNS server on my local LAN. I was finding that I was unable to resolve intranet addresses around 9/10 times until I removed secondary DNS servers from the network configuration. BIND is set as a forwarder anyway so it is okay for me to have a single DNS server.

I tried a single DNS with no luck over the day of trying many things.

Installed bind9 tonight and still no luck.

Change my DNS to 127.0.0.1 and BINGO, my VPN is passing all the test.

I left the DNS at 127.0.0.1 and removed bind9 and all my problems came back.

Likely play with this over the next few days and see where it goes no I have VPN again. :D
 
Thanks

Edit: Works not too bad but a few sites still show some leak. Will keep on working on it.

---

### Post by sammiev on 2016-01-08
Bind9 and using DNS 127.0.0.1 or 0.0.0.0 corrects all the problems I have been having.

Tested it on [grc]("https://www.grc.com/dns/dns.htm") using Witopia VPN and passed with no issues on many different servers.

Should not have to use bind9 so there is a problem but for now, it's solved.

Edit: change 0.0.0.1 to 0.0.0.0 - sorry typing mistake.

---

### Post by QDR06VV9 on 2016-01-08
> **sammiev said:**
> Bind9 and using DNS 127.0.0.1 or 0.0.0.1 corrects all the problems I have been having.

Tested it on [grc]("https://www.grc.com/dns/dns.htm") using Witopia VPN and passed with no issues on many different servers.

_**Should not have to use bind9 so there is a problem but for now**_, it's solved.
+1 Thanks..

---

### Post by sammiev on 2016-01-08
> **runrickus said:**
> +1 Thanks..

Made an edit to one of the addresses, made a typo. :( 

Should have been 0.0.0.0 not 0.0.0.1

---

### Post by QDR06VV9 on 2016-01-08
> **sammiev said:**
> Made an edit to one of the addresses, made a typo. :( 

Should have been 0.0.0.0 not 0.0.0.1
:DYea I caught that, I had already tried the fix that he sent in his post..
Thanks sammiev:D
Edit:I went with Cuttlefish(On Arch)

---

### Post by davehenson on 2016-01-14
Just to mention this is an issue that's over 2 years old now. :(  Hard to believe something this important (privacy) is still open. tracked in bugtracker [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1211110](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1211110)

---

### Post by sammiev on 2016-01-14
I was able to get around it for now, but it needs to be fixed.

---

