---
title: "Ubuntu 14.04 LTS issue setting up multiple sites on different ports"
date: 2015-06-03
forum: Server Platforms
---

### Post by Adam_Shearman on 2015-06-03
Hey all.

I'm currently in the process of putting together a 14.04 server to host reposado, margarita, munki, and eventually puppet (moving services from an OSX server to a dedicated server). 
Problem is i'm having to have a few of the web apps listening on different ports, for example hostname.local:8089 will point towards margarita, hostname.local:8088 will point towards reposado, and hostname.local will point to munk.

Now, obviously i've got these set up as virtual hosts pointing to different document roots, but is there any way i can clean up my URLs? like maybe margarita.hostname will point to port 8089, reposado.hostname to 8088 and so on?
I've had a quick attempt at using namevirtualhost but can't seem to get that to work.....

Anyone able to point me in a general direction of how to go about it?

Cheers

---

### Post by volkswagner on 2015-06-03
Yes you can.

What you're looking for is setting up a reverse proxy. You can use Nginx or Apache2 as the reverse proxy server.
I created a small [how to]("http://ubuntuforums.org/showthread.php?t=1920715") for doing this with Apache. Check it out and come back if you have questions.

Reverse proxy works great for hosting various sites with different software/ports. This can point to the same machine (ie: 127.0.0.1) or another machine.

---

### Post by Adam_Shearman on 2015-06-04
Ahhhh thankyou kindly. I had a little look in to reverse proxy-ing but couldn't quite get my head around it, this seems a lot more informative :) will get back to you with my findings!

---

### Post by Adam_Shearman on 2015-06-04
> **volkswagner said:**
> Yes you can.

What you're looking for is setting up a reverse proxy. You can use Nginx or Apache2 as the reverse proxy server.
I created a small [how to]("http://ubuntuforums.org/showthread.php?t=1920715") for doing this with Apache. Check it out and come back if you have questions.

Reverse proxy works great for hosting various sites with different software/ports. This can point to the same machine (ie: 127.0.0.1) or another machine.


Whoop! it worked for margarita with a bit of a play about (Y) now time to add all the rest!

---

### Post by volkswagner on 2015-06-04
Glad you got it working.

Please mark thread solved, using "Thread Tools" at top of post # 1.

---

### Post by Adam_Shearman on 2015-06-05
Also though, before closing down:

If the fqdn of my server is ps01.domain.local with an A record set in the DNS of my domain controller pointing to that server for PS01, am I right in thinking I must then set DNS on PS01 itself to do the final resolution? Just asking as at the moment [http://margarita.PS01.domain.local](http://margarita.PS01.domain.local)  works (had to set server name to that in my vhosts config file with the proxy-ing) but [http://margarita.PS01](http://margarita.PS01) doesn't....

---

### Post by darkod on 2015-06-05
If you want to reach the machine only by ps01 you have to also set such A record in your dns server (domain controller if that's the same). A new record, don't replace the other one.

---

### Post by Adam_Shearman on 2015-06-05
Hmmmm.
Well at the moment, on our windows domain controller (2008) i have a Host (A) record for PS01.domainname.local pointing to it's IP address, then i added extra Host (A) records for margarita.PS01.domainname.local reposado.PS01.domainname.local and munki.PS01.domainname.local (this is what it fills in when doing the add Host (A)) all pointing to PS01's IP address.... 
As i said, if i type in the fqdn then i get where i need to be, but the whole point of this exercise was simplifying URL, not lengthening them. hehe.

---

### Post by SeijiSensei on 2015-06-06
If you mean you just want to type "margarita" instead of "margarita.ps01.domainname.local" then you need to create a DNS search entry on the client machine that looks in "ps01.domanname.local".  If your machine gets its configuration via DHCP, you can configure the DHCP server software to pass that search string to the client at boot time.  If you use static addressing via the file /etc/network/interfaces, you can add a "dns-search" parameter like this:
```

auto eth0
iface eth0 inet static
address ...
netmask ...
[etc.]
dns-search ps01.domainname.local

```
Now Linux will automatically append that string to the end of any "unqualified" hostname like just "margarita."

The graphical NetworkManager application offers this option as well.

---

