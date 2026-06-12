---
title: "Log file shows Firefox activity: is this normal?"
date: 2010-05-19
forum: Security
---

### Post by Rubi1200 on 2010-05-19
I see these activities logged on a fairly regular basis in /var/log/auth.log and was wondering if this is normal activity?

firefox: gethostby*.getanswer: asked for "ftp.cs.rose-hulman.edu IN A", got type "DNAME"

The format is always the same, though sometimes the address is a regular Internet site.

Any insights?

Thanks in advance.

---

### Post by Soul-Sing on 2010-05-19
please install htop, or run top in the terminal and show the results here.
could be an add-on phoning home for some reason?

---

### Post by Rubi1200 on 2010-05-19
Here is the output from htop; not sure if there is anything there.
Thanks.

---

### Post by Rubi1200 on 2010-05-19
This kind of activity is also being logged:

firefox: gethostby*.getanswer: asked for "www.unixtutorials.info.nyud.net IN A", got type "DNAME"

There doesn't seem to be any pattern to these messages. Sometimes they will appear in /var/log/auth.log a couple of times in one day, sometimes not for a few days, and then, as above, a different address is shown but always with the format shown here.

Additional information if it helps; no vnc, ssh, or remote desktop. Only cups as a listening service. Default Firefox installation with NoScript. 
That's it; happy to provide more info if needed.
Thanks.

---

### Post by Soul-Sing on 2010-05-19
Do you have any connection with/to Rose-Human  Institute of Technology? via putty or ftp?

---

### Post by Rubi1200 on 2010-05-19
None whatsoever. The only thing I can think of is that it may have been a link for downloading an ISO image. But, the message keeps re-appearing in the log even though I downloaded the image 2 days ago.
I have cleared the cache in Firefox, so I don't think that could be it.

---

### Post by Rubi1200 on 2010-05-19
Update:

I ran tail -F /var/log/auth.log and then went to a few of my regular sites. The message (firefox: gethostby*.getanswer: asked for "ftp.cs.rose-hulman.edu IN A", got type "DNAME") appeared in the log when I went to [www.distrowatch.com]("http://www.distrowatch.com")

This is a bit unusual?

---

### Post by cdenley on 2010-05-19
It looks like firefox is attempting to resolve those domains, but receives an incorrect response from your DNS server. Firefox can sometimes resolve domains which you haven't used.
[https://developer.mozilla.org/en/Controlling_DNS_prefetching](https://developer.mozilla.org/en/Controlling_DNS_prefetching)

You can try changing DNS servers to see if the problem goes away.

Google:
8.8.8.8
8.8.4.4

OpenDNS:
208.67.222.222
208.67.220.220

---

### Post by Rubi1200 on 2010-05-19
Ok, that makes sense. 

Can I assume this is not a serious security concern?

Thanks!

---

### Post by cdenley on 2010-05-19
> **Rubi1200 said:**
> 
Can I assume this is not a serious security concern?


Well I would be suspicious about any invalid DNS response. It may be the result of DNS spoofing or something. More likely, though, you're just using a poorly run DNS server.

---

### Post by Rubi1200 on 2010-05-19
[http://ubuntuforums.org/showpost.php?p=1960622&postcount=7](http://ubuntuforums.org/showpost.php?p=1960622&postcount=7)

Can I use this solution to change the DNS servers?

(Backing up first, of course)

Thanks.

---

### Post by cdenley on 2010-05-19
> **Rubi1200 said:**
> [http://ubuntuforums.org/showpost.php?p=1960622&postcount=7](http://ubuntuforums.org/showpost.php?p=1960622&postcount=7)

Can I use this solution to change the DNS servers?

(Backing up first, of course)

Thanks.

You can try, but I think NetworkManager may overwrite it eventually.
[https://help.ubuntu.com/10.04/internet/C/connecting-wired.html](https://help.ubuntu.com/10.04/internet/C/connecting-wired.html)
I'm not sure NetworkManager will let you assign DNS servers if you use DHCP, though.

---

### Post by teh_drizzle on 2010-05-19
> **cdenley said:**
> You can try, but I think NetworkManager may overwrite it eventually.
[https://help.ubuntu.com/10.04/internet/C/connecting-wired.html](https://help.ubuntu.com/10.04/internet/C/connecting-wired.html)
I'm not sure NetworkManager will let you assign DNS servers if you use DHCP, though.

Yes you can :) 

See here for Google's documentation: [http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

It's pretty straightforward if you edit the connection settings through NetworkManager. :)

---

### Post by cdenley on 2010-05-19
Yes, I just noticed you can select "Automatic (DHCP) addresses only" for "Method" in NetworkManager. Then you can specify DNS servers.

---

### Post by Rubi1200 on 2010-05-19
Thanks for the information and speedy responses :)

I was just wondering if it might be worthwhile turning DNS Prefetching off in Firefox before trying to change DNS servers?

Also, I may have a problem changing DNS servers because I tried it once (back in my Windows days); I wanted to switch to OpenDNS but my ISP seemed to change it back to their servers (is that possible?).

Thanks in advance.

---

### Post by cdenley on 2010-05-19
> **Rubi1200 said:**
> Thanks for the information and speedy responses :)

I was just wondering if it might be worthwhile turning DNS Prefetching off in Firefox before trying to change DNS servers?

Also, I may have a problem changing DNS servers because I tried it once (back in my Windows days); I wanted to switch to OpenDNS but my ISP seemed to change it back to their servers (is that possible?).

Thanks in advance.

Well, your ISP can't change the DNS configuration on your computer unless your it is configured to set your DNS servers according to DHCP. It can always force any DNS requests to be handled by their DNS server regardless of what IP your requests are sent to, though, since they route your traffic for you. I do that for users on my network. I doubt your ISP would do that to you, though.

---

### Post by Rubi1200 on 2010-05-19
Thanks cdenley and teh_drizzle for helping with this issue.

I have changed the DNS servers in Network Manager to the Google DNS servers and the error messages have gone now.

:)

---

### Post by bodhi.zazen on 2010-05-19
> **Rubi1200 said:**
> Thanks cdenley and teh_drizzle for helping with this issue.

I have changed the DNS servers in Network Manager to the Google DNS servers and the error messages have gone now.

:)

I have recently started using opendns

[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

Look at # 5 (nice screen shot) and # 8 

Even if you stay with Google. DNS, nice tips on the above link ^^

---

### Post by Rubi1200 on 2010-05-20
> I have recently started using opendns

[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

Look at # 5 (nice screen shot) and # 8 

Even if you stay with Google. DNS, nice tips on the above link ^^

Thanks for the link and the tips :)

---

