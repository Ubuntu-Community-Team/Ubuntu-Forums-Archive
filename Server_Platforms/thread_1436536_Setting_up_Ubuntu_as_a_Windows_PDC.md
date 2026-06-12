---
title: "Setting up Ubuntu as a Windows PDC"
date: 2010-03-22
forum: Server Platforms
---

### Post by markgilbert on 2010-03-22
I don't want to generate any bad vibes with this, but I'd like to see what peoples opinions are regards setting up Ubuntu as a Windows primary domain controller (PDC).  I know that active directory and it's associated technologies are proprietary Microsoft technologies, however, it is very easy to setup a Windows PDC on an existing Windows Server install using dcpromo.  

There doesn't seem to be any kind of straight forward way to setup Ubuntu, or any other Linux distro for that matter, as a Windows PDC.  Now I know Ubuntu is trying to gain traction with the general public, and the general public is not really interested in running Linux based PDCs, but for sever admins and making tacks in the server arena it would seem like a good idea to have a simple way to configure a Samba & LDAP PDC using some kind of wizard or GUI interface.

If I've missed something really obvious and this is already possible then please enlighten me, but as far as I am aware it's not.  Hopefully this will generate some discussion around the point as I would be interested in other people's opinions.

---

### Post by Lucky. on 2010-03-22
I'm pretty interested in this too, been wondering it for a while.  From what I've heard though, it's pretty much not possible / stable.

In the back of my head I keep planning the following fantasy migration from Windows to Linux...

1.  Keep that Windows PDC going for my Windows Workstations.
2.  Migrate all of the other servers to Ubuntu with Samba and LDAP.
3.  Move Web Services to Ubuntu.
4.  Figure out some sort of Linux Active Directory Alternative, and run that on top of the Samba servers.
5.  Start replacing Windows workstations with Linux Workstations that use whatever alternative we have in Step 4.
6.  After the last Windows workstation is gone, drop the Windows PDC server.  Yay!  100% Linux!

As you can see, there's some holes in my little fantasy world.  I still don't know what a valid Linux alternative is to active directory.

---

### Post by Ryan Dwyer on 2010-03-22
I started a discussion about this about 6 months ago on the ubuntu-devel-discuss mailing list. It turned into an argument about GUI vs CLI.

My idea was to have a product that can do everything that Windows Small Business Server can do (PDC, DNS, DHCP, file sharing, mail server...), as well as bonus features for Ubuntu workstations like being an apt caching server, maintaining a hardware audit with SSH+lshw and managing workstations on mass using SSH. My belief is that if Ubuntu can get into the small business market then people will start using it at work and it will gain popularity.

---

### Post by HermanAB on 2010-03-22
Howdy,

The main problem is that Samba can only do the older Windows 2000 type ADS.

Other than that, it may actually better to use a different technology like MySQL and PAM with NFS (Services for UNIX on Windows) and get away from the whole freaking LDAP, Kerberos, Winbind head-ache.

---

### Post by jrssystemsnet on 2010-03-23
> **HermanAB said:**
> Howdy,

The main problem is that Samba can only do the older Windows 2000 type ADS.No, Samba can only act as an NT4 PDC, which means no AD whatsoever.  Samba can be a *member* of an AD domain with Windows DCs just fine, however.

Samba4 promises to allow having a Samba DC in an AD domain, but Samba4 is not out yet.  For the moment, if you want AD, you're going to need Windows Server to act as the DCs.

Also note: there's no such thing as a "PDC" in an AD domain.

---

### Post by essexboyracer on 2010-03-23
I too am interested in this. Just like the amazing work ubuntu has done to bring linux to the desktop, making it easier to use and friendlier, the same needs to happen in the SME environment. Windows Server is no different to XP/Vista - it still has a GUI and that is what most admins will be familier in dealing with, hence ubuntu server needs to change/adapt to accomodate these potential converts.

I have been given the go ahead to examine and test the possibility of using linux server in our windows XP client network, replacing the SBS2003 server that sits in there at the moment. I am not afraid of the CLI but in our organisation it will not only be me administering the server, therefore it needs a point and click interface to achieve this.

I have tested eBox, which seemed quite good initially and I managed to get XP clients to attach to the domain, open up shared network folders and install large format office network printers. The thing that bugged me with ebox was its annoying navigation menu and I got the feeling that if a config file for a service needed configuring manually, I would need to go back to the CLI to do it, negating the benefit of using eBox.

I am just about to try out webmin, which I know was dropped from ubuntu ages ago, I cant remember the reason, something to do with package management or webmin not being actively maintained anymore (it is maintained BTW). 

Thw whole GUI/CLI argument is boring and old - a focus on providing a solution that relates to the real world scenarios is needed to bring linux servers back into the small business environment.

---

### Post by jrssystemsnet on 2010-03-23
> **essexboyracer said:**
> Thw whole GUI/CLI argument is boring and old

AFAIK, you're the only one who's so much as mentioned that in this thread.

The problem is that right now you *can't* use Samba as an Active Directory DC; you can use it as a member server (with either Winbind or LDAP) of an Active Directory domain, or you can set it up as an NT4-style domain with *no* Active Directory, but you cannot use it as a DC.

Samba4 promises to change this, but Samba4 isn't out yet; if you've got the development skills, you can always go contribute to the project - but aside from that, until Samba4 is released, you're just spinning your wheels.

---

### Post by R.Bucky on 2010-03-23
You might want to try out ClearOS ([http://buckycomputing.net/blog/clearos-an-alternative-to-ms-server/](http://buckycomputing.net/blog/clearos-an-alternative-to-ms-server/)). It is the closest thing that I can find to a complete solution. As the previous post mentions, the next version of Samba should greatly enhance MS compatibility.

---

### Post by markgilbert on 2010-03-23
jrssystemsnet, I thought that NT4 had PDCs, which for a lot of small businesses would probably be adequate.  I think that Server 2000 and onwards used operational master roles.

As far as what else has been said, if Samba and LDAP are not the way to go with this and MySQL and PAM with NFS is a better way of doing this then fair enough, but I still think what's required for this to gain traction in small businesses and smaller IT departments is a simpler way of configuring and administrating the whole thing.

I did look at eBox but wasn't overly impressed with it, I found the navigation rather cumbersome.  Maybe this is because it's just not what I'm used to, but it did seem a bit unintuitive.

---

### Post by jrssystemsnet on 2010-03-23
> **markgilbert said:**
> jrssystemsnet, I thought that NT4 had PDCs, which for a lot of small businesses would probably be adequate.Correct, NT4 domains had a PDC and could have one or more BDCs.  However, an NT4 style domain has no Active Directory; meaning, among many (many, many, many) other things, no GPOs.

The *only* thing you get out of an NT4-style domain is centralized user login and profile storage - that's it.  Which is, frankly, usually not really worth the hassle of having it to begin with.  Particularly as compared to the cost of a copy of SBS server.

Typically, I find that you're better off either working with plain user/pass decentralized authentication, or setting up an actual AD domain.  The "in-between" of an old-style NT4 domain is just not worthwhile.

FWIW, I have set up a Samba3 NT4-style "domain", and it's still in service.  I am not pulling my objections to it out of thin air. :)

---

### Post by markgilbert on 2010-03-23
From what I can gather centralised user login and roaming profiles seems to be what you get with the Samba and LDAP configuration.  So as somebody said earlier, possibly MySQL and PAM with NFS is a better solution, but how far towards an AD replacement solution can be achieved with that kind of setup?  Which then flows back to my original question of, can this be done with a straightforward GUI/Wizard interface.  I would guess not, again unless anyone can point out otherwise.

---

### Post by HermanAB on 2010-03-23
Microsoft Windows 2003 supports two types of Active Directory: Win2000 and Win2003.  Samba 3 support only Win2000 style Active Directory, which should be good enough for most small businesses.

Read the manual!

[http://samba.org/samba/docs/man/Samba-Guide/](http://samba.org/samba/docs/man/Samba-Guide/)

[http://samba.org/samba/docs/man/Samba-Guide/happy.html#sbehap-bldg1](http://samba.org/samba/docs/man/Samba-Guide/happy.html#sbehap-bldg1)

[http://samba.org/samba/docs/man/Samba-Guide/unixclients.html#sdcsdmldap](http://samba.org/samba/docs/man/Samba-Guide/unixclients.html#sdcsdmldap)

---

### Post by markgilbert on 2010-03-23
I absolutely agree, a Windows 2000 type AD setup is adequate for most small businesses, and while it appears that Samba can be configured to replicate this kind of setup, it's all done via CLI rather than a GUI.  As long as Linux is more hassle to setup in this role than a Windows Server box, sysadmins and IT departments are going to continue to buy into the whole Microsoft eco-system.

---

### Post by dfxdeimos on 2010-03-23
> **jrssystemsnet said:**
> Also note: there's no such thing as a "PDC" in an AD domain.
 
Came her to say this, left satisified.
 
There are several accurate and well thought out answers here. You could configure it as a member server, but there is currently no way to make it a full fledged AD DC.

---

### Post by markgilbert on 2010-03-23
A member server is ok, but not good for small businesses where there is only one server and you want the Linux box to be it.

---

### Post by essexboyracer on 2010-03-23
I dont understand enough about Msoft AD to engage in a discussion about the merits of what it and Samba can and can't do. What I do understand is that I see an opportunity for linux to rise to the challenge as a windows server replacement in the small business, windows environment, if it can be done to allow sys admins to do it in a GUI way.

Sure, I could spend months becoming a linux guru setting this up from scratch but I don't have the time (more importantly the company doesn't have the money) and would rather have it setup quickly and then get into the fine tuning at a later stage. In light of this, can I retract my comments about eBox earlier and actually offer support for the fantastic work they have done in trying to simplify the process of integrating a linux server in a heterogeneous environment.

EDIT: Webmin HOW-TO [http://ubuntuforums.org/showthread.php?t=1445655](http://ubuntuforums.org/showthread.php?t=1445655)

---

