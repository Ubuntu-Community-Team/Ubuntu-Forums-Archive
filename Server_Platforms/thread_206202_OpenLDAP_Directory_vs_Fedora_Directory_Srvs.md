---
title: "OpenLDAP Directory vs Fedora Directory Srvs"
date: 2006-06-29
forum: Server Platforms
---

### Post by pbowrin on 2006-06-29
Can  OpenLDAP Directory or Fedora Directory services be install on Ubuntu Server or does it already come installed with a directory app.   I would like to use Ubuntu server as an authentication server like Active Directory.

Thanks

---

### Post by herald on 2006-06-30
OpenLDAP can most certainly be installed on Ubuntu, Fedora DS I'm not so sure about, but I can't imagine why it couldn't...as long as the supporting dependencies are met, and the Kernel requirements are met, Linux is Linux, be it Debian or RedHat.

---

### Post by pbowrin on 2006-06-30
[QUOTE=herald]OpenLDAP can most certainly be installed on Ubuntu, Fedora DS I'm not so sure about, but I can't imagine why it couldn't...as long as the supporting dependencies are met, and the Kernel requirements are met, Linux is Linux, be it Debian or RedHat.[/QUOTE]

Thanks for your prompt response ... I'm truly impressed with the community support.   Can you provide steps for me to install and run Open LDAP?

Thank you.

---

### Post by Iowan on 2006-06-30
[http://www.ubuntuforums.org/search.php?searchid=6436391]("http://www.ubuntuforums.org/search.php?searchid=6436391")

Anything in here that will help?

---

### Post by herald on 2006-06-30
In addition to what Iowan has already posted, this link might be of some use.  The best thing to do is to Google "OpenLDAP" and to visit your local bookstore.  LDAP is somewhat complex depending on what kind of schema you need to implement, and I don't know of any quick and dirty implementation that's worth its salt.

---

### Post by LordHunter317 on 2006-06-30
If this is a serious LDAP deployment, don't even bother with OpenLDAP.  Seriously.

---

### Post by NewbieNik on 2006-07-06
LordHunter317, can you explain why? I am hoping to replace my W2K3 server at home with Ubuntu and would like it to handle my log-ons on both windows and Linux platforms and am trying to learn OpenLDAP to achieve this, but if you have other information, please share it.
Or is it that you have had problems and just don't like OpenLDAP?

---

### Post by pclancy on 2006-07-06
I found some relatively helpful references for the Fedora directory server:[LIST]
[*][https://help.ubuntu.com/community/FedoraDirectoryServer](https://help.ubuntu.com/community/FedoraDirectoryServer)
[*][https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto](https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto)
[*][http://directory.fedora.redhat.com/wiki/Howto:DebianUbuntu](http://directory.fedora.redhat.com/wiki/Howto:DebianUbuntu)
[/LIST]

Even with the guides I found it fairly annoying to install, and I didn't have much luck with the LDAP authentication.  Has anyone else been successful with Fedora directory server?

---

### Post by Useless on 2006-07-07
OpenLDAP is def possible on an ubuntu box, but the managability is much easier on an AD Win2k3 Box.  You have been forewarned, this will be a bit tough on a linux box..haha.  :)  Good luck!  I also have looked in to the fedora directory server but was pretty much turned off by the install alone.

---

### Post by Soleil-Raid on 2006-07-11
> If this is a serious LDAP deployment, don't even bother with OpenLDAP. Seriously.

Heh, I've been coming to this conclusion lately as well. Anyone have any suggestions for an LDAP server I can expect to work, and will handle replication without falling on it's ***?

---

### Post by nkassi on 2006-07-12
Fedora and OpenLDAP both will run on Ubuntu. As far as OpenLDAP sucks argument, i've used OpenLDAP in production and I don't see what all the hate is all about. It works perfectly fine for the 30+ people setup I managed. 

Fedora Directory does have a huge advantage when it comes to ease of management. It has a great web interface that rivals any LDAP directory around. I strongly suggest you look into Fedora Directory considering that your background is in AD on W2k3. 

Just remember, Linux + LDAP + Samba will not completly replace AD but I will do a great job at Authentication, File/Printer Sharing and all other non windows desktop management stuff. ( Thinking of Web, DNS, and BLah!) 

Nic

---

### Post by gruepig on 2006-07-12
> **LordHunter317 said:**
> If this is a serious LDAP deployment, don't even bother with OpenLDAP.  Seriously.

Uh ... there are many, many serious OpenLDAP deployments, including numerous large universities.  See discussions on [email]openldap-software@OpenLDAP.org[/email].  Or, for quite a bit of info about Stanford's (slightly-dated) LDAP assessment: [http://www.stanford.edu/services/directory/openldap/history/choice.html](http://www.stanford.edu/services/directory/openldap/history/choice.html).

---

### Post by oly on 2006-07-12
openldap is also best used with phpldapadmin which supplys a nice interface, however you still have to configure it yourself.

[http://www.digitaloctave.com/files/server/PDC-Server1.0.tar.gz](http://www.digitaloctave.com/files/server/PDC-Server1.0.tar.gz)

you can get a script from there which might help just edit settings.sh and run setup from the terminal and it will setup samba ldap and phpldapadmin automatically hopefully.

worked fine here used it to setup our schools domain server.
if you hit problems feel free to pm me, as there might be bugs which i do not know about due to me continually modifyuing the script.

---

### Post by jporpilla on 2006-07-12
Is there any other way on how can a W2k3 AD can manage Ubuntu Desktop?

---

### Post by LordHunter317 on 2006-07-12
> **nkassi said:**
>  It works perfectly fine for the 30+ people setup I managed.Which is tiny, FWIW. 

> Fedora Directory does have a huge advantage when it comes to ease of management.Which is the core issue.  Active Directory isn't the best LDAP server around because it's the most scalable, or because it's replication works best, or any other reason like that.  It's the best LDAP server because it's tools are infinitely superior to everyone else's.

OpenLDAP is also missing quite a few features from FDS like the Active Directory bridge, and multi-master replication (yadaya it's bad, bad, but needed, so provide it).  Until 2.3, they didn't support password polices in the default distribution, it was an overlay you had to pull and build from CVS.

[quote=gruepig]Uh ... there are many, many serious OpenLDAP deployments, including numerous large universities.[/quote]And?  There are many, many serious deployments of IISv5 but that doesn't make it a good choice.

---

### Post by nkassi on 2006-07-12
> Which is tiny, FWIW. \
Oh well I know of a couple of setups with more than a couple thousand users. I personally know the admins and I have played on there network. 

But please, could you elaborate on issues with openldap that you know off. I would really like to know.

> Is there any other way on how can a W2k3 AD can manage Ubuntu Desktop?

Short answer: Yes it can. 
Long answer:You will need to add some schema extension to support unix related things. Last time I look into this, there was a commercial package Not sure if it is commercial but whatever) called AD4Unix that did all the setup you need. In any case I only suggest it if you really need to keep AD running since the switch to a unix based LDAP directory will have lots of advantages.


Nic

---

### Post by nkassi on 2006-07-15
[http://directory.fedora.redhat.com/wiki/Howto:DebianUbuntu](http://directory.fedora.redhat.com/wiki/Howto:DebianUbuntu)

This might be useful to people trying to install Fedora Directory on Ubuntu.

Nic

---

### Post by compbrain on 2006-07-15
> **LordHunter317 said:**
> Which is tiny, FWIW. 

Which is the core issue.  Active Directory isn't the best LDAP server around because it's the most scalable, or because it's replication works best, or any other reason like that.  It's the best LDAP server because it's tools are infinitely superior to everyone else's.

OpenLDAP is also missing quite a few features from FDS like the Active Directory bridge, and multi-master replication (yadaya it's bad, bad, but needed, so provide it).  Until 2.3, they didn't support password polices in the default distribution, it was an overlay you had to pull and build from CVS.

And?  There are many, many serious deployments of IISv5 but that doesn't make it a good choice.


So, Im not sure how extensive your experience with OpenLDAP is, but I can say that it is A) Stable, and B) High Performance. I can cite a few large .com's that are using OpenLDAP for 100% of their enterprise directories. (We're talking well over 200,000 entries, over 8k users, and maintaining about 500qps/server, with low latency).

OpenLDAP may be a bit more difficult to setup (depends on your background), but it is high performance, and it *IS* enterprise ready.

---

### Post by LordHunter317 on 2006-07-15
> **compbrain said:**
> So, Im not sure how extensive your experience with OpenLDAP is, but I can say that it is A) Stable, and B) High Performance.**And?  Did you bother to read my post?**   I specifically stated that stability and performance mean almost nothing.  What I said was that OpenLDAP isn't production-ready because it has poor administration tools and because its is lacking features almost ever other LDAP server says, including FDS.

No one cares about stability or performance.  They **all** have that.

---

### Post by compbrain on 2006-07-15
They do not "all have that". FDS and Sun One Directory Server are very similar, and their query response times are completely different than OpenLDAP. OpenLDAP is much faster for indexed queries on the same hardware, and yes, it does make that much of a difference. 
As for administration tools, ldapadd/ldapmodify are more than enough for most large deployments. Take those, and write some site specific scripts, and you will be much happier than a generic point and click GUI. 
I dont see what features OpenLDAP is lacking, perhaps besides the GUI admin, and the NT Sync tool, both of which are easily replaced by other more functional alternatives. [http://www.jxplorer.org/](http://www.jxplorer.org/) is a great LDAP browser/editor, and for AD Sync check out [http://acctsync.sourceforge.net/](http://acctsync.sourceforge.net/). Neither of those tools are perfect, but out of the box probably will not work in a large scale deployment. 
So, atleast from my point of view, Production Ready *is* measured by stability and performance, and not by Administration tools and featureset. If that was the case, every Windows service and application would be "Production Ready".

---

### Post by LordHunter317 on 2006-07-15
> **compbrain said:**
> As for administration tools, ldapadd/ldapmodify are more than enough for most large deployments. Take those, and write some site specific scripts,You just contradicted yourself.  Thank you for proving my point.  If I have to wrap them with scripts, the tools are insufficent.

> I dont see what features OpenLDAP is lacking, perhaps besides the GUI admin, and the NT Sync tool, both of which are easily replaced by other more functional alternatives.And Multi-master replication, which is a show-stopper for a lot of corporate deployments.  LDAP modifications don't stop simply because the master had to go down.

More importantly, you're seemingly forgetting the simple fact: the sys/LDAP admin is usually not the one making modifications to the data in the directory.  It's usually either helpdesk-level people (resetting passwords, enabling accounts, updating whatever) or people outside the technical department altogether (HR fixing names and updating other such data).  

Which makes admin tools a big deal.

> So, atleast from my point of view, Production Ready *is* measured by stability and performance, and not by Administration tools and featureset.The industry as a whole clearly disagrees with you.  If that were true, then AD would not be the most popular LDAP server.

> If that was the case, every Windows service and application would be "Production Ready".Uhh, no, not quite.

---

### Post by compbrain on 2006-07-15
> **LordHunter317 said:**
> You just contradicted yourself.  Thank you for proving my point.  If I have to wrap them with scripts, the tools are insufficent.

And Multi-master replication, which is a show-stopper for a lot of corporate deployments.  LDAP modifications don't stop simply because the master had to go down.

More importantly, you're seemingly forgetting the simple fact: the sys/LDAP admin is usually not the one making modifications to the data in the directory.  It's usually either helpdesk-level people (resetting passwords, enabling accounts, updating whatever) or people outside the technical department altogether (HR fixing names and updating other such data).  

Which makes admin tools a big deal.

The industry as a whole clearly disagrees with you.  If that were true, then AD would not be the most popular LDAP server.

Uhh, no, not quite.

Ok, Im not going to bicker about admin tools any longer; we clearly have different goals for our LDAP deployments. I may just  kick in that I've never been to a large scale deployment that hadn't written their own tools for HR and such, with ANY ldap soloution (AD, Sun ONE, OpenLDAP, etc)

Multi-Master is a touchy issue though. I can point people at [http://www.watersprings.org/pub/id/draft-zeilenga-ldup-harmful-02.txt](http://www.watersprings.org/pub/id/draft-zeilenga-ldup-harmful-02.txt)
Live multi-master situtations tend to indroduce data-consistency issues. A more logical choice is a Master with a hot spare (A slave that can be promoted to a master).

---

### Post by jnegro1176 on 2006-07-27
[www.ebox-platform.com](www.ebox-platform.com)

We've been playing with this one in our test lab.  Seems to be fairly stable and easy to install.  Otherwise check out these two links to build an ldap/smb server of your own.

[www.majen.net/smbldap](www.majen.net/smbldap) contains some bleeding edge scripts for Ubuntu.  They're still a bit buggy, but seem to work.

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/LDAP](http://wiki.ltsp.org/twiki/bin/view/Ltsp/LDAP) is a set of howto instructions that are step by step similar to the scripts above.  We had better luck with the how-to and are currently working on a script for ubuntu/kubuntu servers and clients.  I will post it once it is complete.

I've played with the Fedora Directory Server, and although it was very clean and stable, it was missing the samba features I need for the few windows clients we still have on our network.  I'm sure there are many people on here who know alot more detail when it comes to this product.

Hope this was of some interest :)

---

### Post by quad3d@work on 2006-09-28
Just going over FDS installation and it required Apache2 MPM 'worker' model... now, I already have 'prefork' installed due to PHP5 isn't quite thread safe yet and package doesn't deal with Apache2 worker model.

I'm wondering why is Apache2 worker model required for FDS? Any way around that to get it working with prefork model? Thanks.

---

### Post by compbrain on 2006-10-01
> **quad3d@work said:**
> Just going over FDS installation and it required Apache2 MPM 'worker' model... now, I already have 'prefork' installed due to PHP5 isn't quite thread safe yet and package doesn't deal with Apache2 worker model.

I'm wondering why is Apache2 worker model required for FDS? Any way around that to get it working with prefork model? Thanks.

If my memory serves me, FDS uses Apache for its Pseudo administrative web interface. IIRC, this is not required for operation, but an optional feature.

---

