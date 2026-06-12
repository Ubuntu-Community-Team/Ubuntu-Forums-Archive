---
title: "[IDEA] Install time LDAP / Directory access/autthentication setup"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by elvis on 2007-10-18
My Gutsy Gibbon IDEA thread:
[http://ubuntuforums.org/showthread.php?t=422043](http://ubuntuforums.org/showthread.php?t=422043)

Same request for Hardy Herron.  

SuSE, RedHat and other "corporate-focussed" distros all offer directory access/authentication configuration at install time.

I administrate several medium-to-large networks at the moment, all of which I have migrated over the last 2 years from other legacy Linux systems to Ubuntu.  

Server-side setup is not an issue I believe.  That's what network administrators like me are hired to do.  Building an OpenLDAP system is up to the competence of the network admin, and simplifying that IMHO is a moot point.

Connecting to this server and authenticating a local client machine should be something more automated - something power users or helpdesk staff are capable of doing via a simple GUI.  Again, go through a RedHat or SuSE install, and you'll see the same thing.

"authtool" and "authtool-gtk" in Gutsy are in a very early stage at the moment, and need a great deal more polish.  Likewise they are standalone applications, and not an optional part of the install-time config.

This GUI would needd to install the various pam-ldap and  libnss-ldap files, add in the URI for the desired LDAP / Microsoft Active Directory / Apple Open Directory / etc server, and perhaps even have additional sections to configure automatic mounting of the user's home folder via the network as an option.

---

### Post by socceroos on 2007-10-18
I couldn't agree more. I've been looking for this feature in Ubuntu for over 3 years now. Everyone is talking about the need for it, noone wants to do it.

I am currently not capable of writing the necessary software myself, but oh please, if any one can - PLEAAASE consider doing this! Its been a sticking point for me for sooo long.

I believe its time that something was done about this. No more, 'Oh, just follow this howto.', or, 'This piece of crappy software will give you a half-baked solution...'. We need the real deal.

---

### Post by Zdravko on 2007-10-19
If something didn't make it in Gutsy, then why do you think it can make it in Hardy?

---

### Post by bethaviv on 2007-10-19
> **Zdravko said:**
> If something didn't make it in Gutsy, then why do you think it can make it in Hardy?

They're just asking for it, this is an IDEA pool.

It was the same thing with C-F... people had been asking for integration and they finally got it in Gutsy.

---

### Post by Zdravko on 2007-10-19
Aah, yes - here you caught me.
Btw, what is C-f?

---

### Post by bethaviv on 2007-10-19
> **Zdravko said:**
> Aah, yes - here you caught me.
Btw, what is C-f?

Compiz-Fusion...

---

### Post by Zdravko on 2007-10-19
> **bethaviv said:**
> Compiz-Fusion...
I've never used this thing. Does it taste good? How much computer resources does it take?

---

### Post by bethaviv on 2007-10-19
> **Zdravko said:**
> I've never used this thing. Does it taste good? How much computer resources does it take?

If you're using Gutsy you have it. It's all the special desktop effects (wobbly windows, etc...)... something you mentioned you didn't care for in another post.......

---

### Post by Zdravko on 2007-10-19
I don't use Gutsy. I will start using (seriously) Ubuntu with Hardy Heron (Alpha 4) somewhere in the beginning of February 2008.

---

### Post by elvis on 2007-10-20
> **Zdravko said:**
> If something didn't make it in Gutsy, then why do you think it can make it in Hardy?

In all seriousness, I find this mentality a little puzzling.

Ubuntu and indeed GNU/Linux moves at the speed of light.  New features and tools are being added all the time.

If new features didn't appear, then there would only have ever been one release of Ubuntu.  There would be nothing new EVER upgrading from one version to the next.

If something didn't make it to Gutsy, I assume it didn't for a number of reasons.  Whether it be that the software wasn't mature enough, or developers just didn't have the time.  I don't *EXPECT* my ideas to be incorporated either.  All I'm doing is throwing out ideas into a public space so hopefully the Ubuntu developers will hear them, and decide for themselves if that's the direction they want to take Ubuntu in.

Ubuntu in my opinion is the best general-purpose desktop distribution around.  It's Debian roots make it a fantastic server distribution also.  I think the "last frontier" for Ubuntu will be to gain corporate approval.  That market is sewn up by and large by RedHat and Novell/SuSE (and of course, Microsoft). 

I believe Ubuntu has the power to dominate in that field.  Why?  Because Ubuntu is dead simple to administrate on mass, due mostly to APT (something neither RedHat nor Novell/SuSE use - their tools in my opinion are far more frustrating and time wasting, speaking as someone who actually administrates medium-to-large Linux networks).

But in order to break into this market, some corporate-focussed tools are needed.  The big one I think is centralized authentication, which needs to be set up consistently through both GUI and command-line tools (and perhaps eventually web-based setup with eBox, but that can come later).

From here, other tools can extend on this.  Once the base authentication systems are set up, any system requiring authentication can be set up - remote desktop management (VNC with PAM auth), mass package administration, user/group/network grouped software rollouts, etc, etc.

As mentioned, I've already replaced quite a great deal of RedHat and SuSE/Novell boxes out there in the real world with Ubuntu.  I love it, my clients love it, the users love it.  But there's still a few ideas that can be suggested to help it  turn from a "good" system into a "great" system.  

Hence the whole point of an IDEAs forum. :)

---

### Post by stijngysemans on 2007-10-20
+1
Same need here.

@ my workplace we use a windows server 2003. I would like to change to Ubuntu on my work-laptop but it causes me some trouble
-exchange server
-login on the AD

Ubuntu can have a tremendous potential!

---

### Post by brickbat on 2007-10-20
Zdravko are you trolling?

Comments like "If something didn't make it in Gutsy, then why do you think it can make it in Hardy?" are not helpful.

Many things are in Gutsy that were not in Edgy  Thats the whole point.

---

### Post by Zdravko on 2007-10-20
> **brickbat said:**
> Zdravko are you trolling?

Comments like "If something didn't make it in Gutsy, then why do you think it can make it in Hardy?" are not helpful.

Many things are in Gutsy that were not in Edgy  Thats the whole point.

No, I am not. I am trying to conquer this forum.
I apologize for what I said. Of course Hardy will be the very best of what we expect!

---

### Post by sunburst on 2007-10-26
Hi.This was Ubuntus last chance to get Ubuntu on the server map. I’ve been locking for a setup that give you the same features as MS Win2003 and Ubuntu was my last hop. I’m not willing to spend heaps of money on any linux server dist. I’ve tried them all and none of them have worked 100%, there is always something that doesn’t work or stop working. Even if they work you get an NT4 domain at best, this is 2008 not 1988. A Samba domain is not god enough, you get hacked in a heartbeat. As I said this is 2008 and I think Ubuntu should bee on the frontline here. Apparently they are not interested so bay bay Ubuntu.

---

### Post by elvis on 2007-10-29
> **sunburst said:**
> Hi.This was Ubuntus last chance to get Ubuntu on the server map. I’ve been locking for a setup that give you the same features as MS Win2003 and Ubuntu was my last hop. I’m not willing to spend heaps of money on any linux server dist. I’ve tried them all and none of them have worked 100%, there is always something that doesn’t work or stop working. Even if they work you get an NT4 domain at best, this is 2008 not 1988. A Samba domain is not god enough, you get hacked in a heartbeat. As I said this is 2008 and I think Ubuntu should bee on the frontline here. Apparently they are not interested so bay bay Ubuntu.

I think you need to remember that Gutsy was a desktop-focussed release.  And indeed, the request I am making in this thread is a Desktop feature.

Server-side improvements will no doubt be a focus of 8.04, given that it will be the next LTS (Long Term Support) release of Ubuntu which makes it more favorable for a server install than a normal release.

As for your comments on Samba:

1) Samba3 can become a client in an Active Directory Domain.  

2) Samba3 can act as a non-ADC "member server" in an AD domain, and include support for extended ACLs.

All the other complaints about "Ubuntu" not being good enough because of Samba are a little short sighted.  For starters, Ubuntu and Samba have two different development teams.  The lack of support is not Ubuntu's fault, and changing to another distro won't help you (as all distros currently on the market will use Samba3 as well)

Secondly, Samba4 is in development at the moment, and will be a complete Windows 2000/2003 Server Active Directory replacement.

And finally, if you want a Windows AD Domain Controller, you can always go and buy Windows.  Linux is a lot more than just a "low cost Windows replacement".  A whole lot more.

And with that, lets please get back on topic...

---

### Post by teamanx on 2008-01-11
Mandriva and PCLOS have an excellent auth tool, called drakauth, that can set up an authentication against almost everything. It is all open-source, and is developed in GTK, so maybe it would not be very difficult to port it to Ubuntu.

---

