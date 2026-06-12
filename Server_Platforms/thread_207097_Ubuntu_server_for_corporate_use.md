---
title: "Ubuntu server for corporate use?"
date: 2006-07-01
forum: Server Platforms
---

### Post by wifiabc on 2006-07-01
Would it be recommended to use Dapper Drake server in business environments ? For example, would you run the company's  SMTP server , Web server, DNS server on Ubuntu ?

Are there any good information about what people are using Ubuntu servers for in business and information about its stability, reliability and availability?

---

### Post by vairoj on 2006-07-01
I am planning to use Ubuntu 6.06 Server on Dell PowerEdge 750 as my company development server (Subversion, JIRA, Confluence, CruiseControl, etc.). Therefore, I would like to hear other people's comment on this, too.

---

### Post by beausimon on 2006-07-02
Is ubuntu server robust enough for business critical services?

---

### Post by alamba on 2006-07-02
I've used 5.10 for the following and am currently evaluating moving some of them to 6.06:
1. www
2. Network performance monitoring server (ntop)
3. VPN Server (PopTop - might move this to OpenVPN)
4. DNS
5. DHCP
6. SSH/SCP
7. Vulnerability Scanning (nessus)
8. File Server
9. App Server for a. SugarCRM and b. SQLLedger

A

---

### Post by wifiabc on 2006-07-02
Alamba,
How's the performance and availability of your ubuntu servers so far?

---

### Post by beausimon on 2006-07-02
Looks like not a popular server choice for enterprise use. Only one person tried?

---

### Post by alamba on 2006-07-03
Wifiabc: So far so good. Haven't had any complaints so far. However, most of the installations are in SMB networks rather than large scale enterprise networks.

A

---

### Post by wifiabc on 2006-07-03
Thanks Alamba.

---

### Post by lamego on 2006-07-03
Ubuntu is quite new compared to other distros which are used at the enterprise level, this together with the Ubuntu's main aim so far being the desktop will justify the lack of enterprise level experience.

Ubuntu is quite easy to manage which makes it a good enterprise choice, as for performance/stability questions you should look for the specific applications that you will be using, that is not Ubuntu specific. Also you should have some concern on how good the server hw on the enterprise is/will be supported on Ubuntu.

---

### Post by verbatim210 on 2006-07-03
At the risk of saying something irrelevant, my faith is with ubuntu.

of all the distros i've tried, ubuntu is the only one (so far) that was installed and succeeded (installation, configuration software etc.) first time - one shot.  this tells me two things.

1. its easy and simple.
2. its compatible.

and 3 the online feature is its strength, where at first i assumed it was its weakness.

i know this is broad and that there are countless variables and factors to consider, but hey.. first impressions last huh

---

### Post by faultyCPU on 2006-07-03
LAMP
NAGIOS
vtiger CRM
MAIL (POSTFIX/OPENLDAP/MySQL/webmail)
Bugzilla

trying to put HULA MAIL SYSTEM (looks sexy!!)


I dont see any problem putting it in any environment. Look at your hardware and user requirements first.

---

### Post by kkimmell on 2006-07-03
I've got several Ubuntu versions installed performing various tasks in our enterprise, including:

WWW
VPN
SMTP bridge for web apps

---

### Post by houstonbofh on 2006-07-03
[QUOTE=beausimon]Looks like not a popular server choice for enterprise use. Only one person tried?[/QUOTE]
Most of us who would try it at work... well...  Work.  So we may not be sitting with baited breath to answer every post.  I am using it in two places.  I chose it because I am working on using the desktop in several places.  I wanted continuity in the Linux I would have to document and support.  I have been very happy, and had not availability problems.  And remote updates are very simple.

---

### Post by joehayhurst on 2006-07-18
I've recently installed it running OpenVPN and so far so good. Like most businesses we use Windows for most things but I'm trying to encourage my boss to be open-minded. If nothing else its a great way to develop my Linux skills.

Our only other Linux server is currently Red Hat Enterprise Linux 4, for which we have had to pay £800 for 1 years 'support' - this basically amounts to having to pay for the updates which you get for free in most Linux distros. To be honest I can't see us ever having to contact Red Hat for any actual support so I would view that as wasted money. Interestingly, I recently did the official Red Hat admin course and the trainer there was just about to be moved into a tech support role. Red Hat is actually a much smaller company than you might think (only about 1500 employees globally if I remember correctly), and I doubt that there is much that they can help you with that you couldn't solve yourself by surfing the web and consulting a few forums. It will just depend on how critical it is and how quick you need it fixing.

I guess that once IBM, HP and Dell start shipping their servers with Ubuntu/Debian installations as options on their setup CDs then more people will start to use Ubuntu in business environments. As it is, it appears that most of the hardware companies only seems to support Red Hat and possibly SuSE out of the box.

Lastly I've recently bought the excellent 'Ubuntu Hacks' book which has a few chapters at the back about running Apache, DNS, DHCP, web proxy, firewalls etc on Ubuntu so there's no reason not to at least give it a go, especially for smaller companies who maybe still are running NT4 and don't want to shell out £400 per Windows licence (plus all the client access licence, etc, etc).

---

### Post by Soleil-Raid on 2006-07-18
We use Ubuntu here for all our Linux needs.

We run the following on Ubuntu;
Desktops (most of them on GNOME, with a minority of Windows and Mac desktops for specific apps).
Servers (Apache, Mysql, DNS, DHCP, NFS, LDAP, Kerberos, Samba/PDC, Routing/Firewall, OpenVPN, Email (SMTP and IMAP)

Primarily we develop C/C++, Perl, and PHP.

Compared to Debian (especially for Workstation/Desktop use), I've been very happy with Ubuntu for the way that there's a consistent set of up to date packages for a given release.

The biggest problem I've had has been a lack of documentation for properly implementing an Active Directory type structure (how to tie LDAP, Kerberos, NFS, PAM and NSS together).

---

### Post by fdamstra on 2006-07-18
I don't think it's very popular in corporate settings because it's so new.

Breezy had an 18-month support cycle, which is far too short for a corporate server.  With Dapper Server's 5 year support cycle, it's a lot more tempting.

I'm currently evaluating it at home, and might suggest it for my next server project if it lives up to its promises for a few months.  I'm mainly concerned about updates.

---

### Post by MonkeyNet on 2006-07-24
I am working for an organisation that is currently running quite an outdated version of Mandrake which they are using NFS, Web with PHP/MySQL, Exim, Gateway and VPN services.

I have only been in the job for a couple of days and have ordered a new server to install Dapper Server on. Will be testing thoroughly before going live, but with my previous experiences with Ubuntu, I really don't think that I am going to have any issues at all.

Will make another post though and let you know how everything goes.

Cheers,

Andrew

---

### Post by LordHunter317 on 2006-07-24
I use Ubuntu everywhere else I use Linux in business.

I have a tough time recommending it as an "enterprise" solution due to the following reasons:[list][*]Dapper drake was the first release where it was possible[*]Dell, IBM, HP, et al. don't offer to install it for you on the box.  For that reason, to a lot of business customers, it might as well not exist.[/list]

---

### Post by StickyStyle on 2006-07-24
I just finished up a compleate rebuild of our corprate IT structure, all of our warehouse workstattions are dapper, and all of our linux servers are also dapper (Mail, FIle, Web, database, everything).* 
The five year cycle of the LTS server version fits in perfectly with our server upgrade policy.* Also being that ubuntu uses much newer kernels I was able to get dapper installed on all my servers without having to do -any- changes to the kernal, or going outside the main repos as I have had to with some of my newer servers where I installed debian sarge.

I have confidence in it, even with the distro being "new".* The community base is amazing and the releases are timly and top notch.* Heck, I've got my job riding on it*:D

---

### Post by rick_1010 on 2006-09-15
Well, I actually just did a search on this site for "enterprise level" and this thread came up, it was just what I was looking for.

I am actually in the process of considering using Ubuntu as an enterprise level server (this is for my "small business" though so its not like I'm some large corporation but I do plan to have upwards of 20-30+ machines within this network within the next few months so its not altogether a "light" decision which distro I go with for this)

I am planning to use whichever distro I choose for making individual workstations for employees to work on (they would be working on desktops run off of a cluster which would be openmosix based) and when I decide to move from my 3rd party web hosting provider I want to host the site on the same distro that I am using for the desktops.

Anyways, I don't have much to offer as far as an opinion, although I really like Xubuntu for thin clients and I will always use it I think for laptops that are used to remotely connect to the network (I'm using it on the machine I'm typing this on)

The QUESTION that I have is:

- I know that Ubuntu is debian based. From what I can tell, Red Hat and Suse are not based on a project anything like Debian.. am I right in this? They have basically been taken from the core Linux code to what they are now, basically without much open source involvement, since you can assume the people developing Suse and Red Hat were paid to do this.

I really like the fact that Ubuntu is based on debian which is known to be very reliable, I sometimes wonder about Suse (of which I have tried the desktop only (not enterprise) and thought it was awful in how it made use of my computer's resources.. very slow compared to Ubuntu) and Red Hat as far as where they came from and how well they are really built. It seems that they are always slower running than Ubuntu and I think this is a fundamental flaw (has anyone else noticed this?), I think that one of the main goals of Linux should be to use hardware as best as possible and I just have reservations about the two top distros for enterprise level..

That said, I think I may have to go with Red Hat / Centos as it still seems to be wider supported and documented and I worry that issues may arise that could take weeks to fix if I use Ubuntu.. anyways just my thoughts / questions, I am not an expert but I am at least thinking about using Ubuntu for my business but I am listening to some Linux experts that I know (who, of course, are well trained in Red Hat and seemingly have no experience with much else)

---

### Post by dughutch on 2006-09-21
Today we were discussing our computing environment and my COO pointed out that M$ was part of our problem and asked if we could get rid of it on our clients.  I about fell out of my chair.  I have been wanting to do this very thing and now have the go ahead for a pilot project to prove the concept.  We are just under 50 employees, but spread across 13 locations.  I expect to be tuning in much more frequently to the forums and any advice is welcome.

As for servers, right now we have a SME7 server running, doing qmail, openvpn, web and dns proxy, dns, etc.  SME7 is based on CentOS and has an excellent history.  There has been some discussion in these forums about adapting the work done over to Ubuntu as the core of a SMB server, but it seems to have died out.  SME has worked very well for me for the past many years (first started using it in 2001).  Rock solid and stable.

---

### Post by Glut on 2006-09-21
We have around 20 Ubuntu servers at the moment, slowly replacing debian on our non-critical servers. There haven't been any issues that debian didn't have, so it's going fairly well. Unlike many deployments, we don't generally use Ubuntu as a desktop OS -- Windows is the favourite, followed by OS X and then Debian. From memory we have less than 30 Ubuntu desktops. It will probably replace debian. 
I think Ubuntu is stable enough for most purposes. I haven't tried Canonical's support, so I can't comment on that - but having it available is a comfort. Getting past the public perception of Ubuntu as a desktop distro may be its largest hurdle.

---

### Post by StickyStyle on 2006-09-22
I run all of our servers with Ununtu 6.06, and all of our warehouse workstations (OS X in the office, how cool is that!) are running it as well.
So thats - 
MySQL servers
mail servesr
file servers
ldap servers
workstations.

What i don't understand is these "corprate use" or "is it reliable" questions about servers, all these distros come from the same kernel, they use all the same applications and for the most part are just different in the way they are layed out and what package system they use.  Just pick the style you are most comfortable with and roll with it.

I've used tons of different distros, whent with debian because i liked its style and it fitted me.  Now i have moved to ubuntu because of the LTS version so i can depend on not having to upgrade my servers for five years.

---

### Post by Glut on 2006-09-25
> 

What i don't understand is these "corprate use" or "is it reliable" questions about servers, all these distros come from the same kernel, they use all the same applications and for the most part are just different in the way they are layed out and what package system they use. Just pick the style you are most comfortable with and roll with it.
Different distributions come with different supported packages, unless you're compiling everything yourself. The stability/reliability question usually refers to the supported packages, for instance Debian unstable and Fedora Core are notorious for breakage - Rawhide even more so. At the other end of the spectrum, Debian Stable is incredibly so at the expense of new kernel features and new software versions (XFree being a particular bugbear) So generally you want a distro that supports everything you want while keeping breakage to a minimum. This is where the reliablity question is important.

---

### Post by StickyStyle on 2006-09-27
(I'll expand a bit more on what I was saying/meant)

> Different distributions come with different supported packages, unless you're compiling everything yourself.Different versions. Everyone is going to package in the big apps that are used on a vast majority of servers; Apache, postfix/sendmail, mysql, php... and for the postfix/sendmail thing thats what i mean you go with what works for you.  Big stuff like oracle plays into that also, you need to support it? So you go with what oracle supports.

> Debian unstable and Fedora Core are notorious for breakageSince we are talking about "corprate" servers here, no one in there right mind would run an unstable release on a server.  Sure ubuntu comes from that lineage but after the UVF we start testing and going through the same process as debian does to make stable (dont know how redhat does it) except we are not trying to make it run on everything from BigIron to a caculator so it happens faster (there are other reasons for the speed, but i don't want to start the debian debate).  And the point about debian stable still validates what i was saying,  if you cant work with the older versions, pick something else.  Maybe dapper :-)

> So generally you want a distro that supports everything you want while keeping breakage to a minimumExactly.  

And in the end it all comes down to your admins and i know this has been said before.  Reguardless of what distro you chose for them,  if he/she is not familar with it, or is a total knob, it doesnt matter how much you paid to Red Hat/Novel for your "Super enterprise corprate edition" there will be problems.

Oh and google uses a customized version of ubuntu, is that "corprate ready" enough for everyone? ;-)

---

### Post by Glut on 2006-09-27
> **StickyStyle said:**
> 
Different versions. Everyone is going to package in the big apps that are used on a vast majority of servers; Apache, postfix/sendmail, mysql, php... and for the postfix/sendmail thing thats what i mean you go with what works for you.  Big stuff like oracle plays into that also, you need to support it? So you go with what oracle supports.

Debian stable currently uses mysql 4.0 and postfix 2.1. Let's go back in time a few months to when mysql 5 was released. It was shipped in the next Ubuntu release. A more cautious sysadmin may have avoided mysql 5 on the basis that it hadn't been around long enough to prove stability. *You could argue that MySQL still isn't stable enough for 24x7x365 use. * Same with postfix 2.2 over 2.1. You don't choose a distibution because it ships with the latest and greatest, you choose one that you know works well.
>   
Since we are talking about "corprate" servers here, no one in there right mind would run an unstable release on a server.  Sure ubuntu comes from that lineage but after the UVF we start testing and going through the same process as debian does to make stable 
Etch has been in testing for over a year. It will be released with near 18 months testing. Each Ubuntu release gets 6 months. Except Dapper got an extra couple of weeks. It's not the same. You could say that Debian will be twice or three times as stable as Ubuntu. What you're arguing is that Ubuntu's testing period is enough to make it stable.
 That's up to the sysadmin to decide. One man's stable or 'tested enough' is another's unstable garbage. (not that Ubuntu's unstable, I'm not making that argument.)
> we are not trying to make it run on everything from BigIron to a caculator so it happens faster 

Ubuntu runs on Sun's Niagara arch (T1?)... PowerPC... x64...
Canonical's going after big iron in addition to little(?) iron.

>  it doesnt matter how much you paid to Red Hat/Novel for your "Super enterprise corprate edition" there will be problems. Or your Canonical support for that matter :-)
> 
Oh and google uses a customized version of ubuntu, is that "corprate ready" enough for everyone? ;-)
Google modifies all of its server hardware, but I'm not going to do that. 

FWIW I think Ubuntu's probably ready for most purposes. I'm just not willing to bet my job on it's suitability for mission critical applications.

---

### Post by wildem on 2006-09-27
We are relying on 6.06 for
WWW
MySQL
File Server
Firewall
Software Development

Our focus is development in: Bash,Perl,PHP,C++ 
with have use in AJAX,Python and PHP

So far, there are no problems. One hardware failure(harddisk) but a backup was restored from a tar file and it flies again. Solid.

---

