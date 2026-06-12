---
title: "Windows SBS 2003 Alternative?"
date: 2007-08-13
forum: Server Platforms
---

### Post by hchristian on 2007-08-13
Hello all,

I am running a small business in Indonesia. We have about 7 Windows workstations running. The server is an IBM xSeries 100 (most basic one) running Windows Small Business server 2003. The server is mainly used for file sharing, printer sharing and serving a database (firebird). 

The cost for each SBS 2003 license is getting to prohibitive and I am thinking of switching to Ubuntu server. I have successfully dual booted Ubuntu on a machine and played with it for a while.

Is it possible for the Ubuntu server to serve as a domain controller where the clients can log on to it? (ctrl+alt+del and log on to server)
On the SBS 2003, clients connect to the server using IE and typing "ConnectComputer" in the address bar. How can I do this using Ubuntu?
I have been trying to look for a tutorial but none address this too well. I am on a limited budget (no test machines) and I can't risk installing the Ubuntu on the server machine to find out that I can't make it run. Can someone enlighten please? All help greatly appreciated. Thank you.

Howard

---

### Post by jrusso2 on 2007-08-13
> **hchristian said:**
> Hello all,

I am running a small business in Indonesia. We have about 7 Windows workstations running. The server is an IBM xSeries 100 (most basic one) running Windows Small Business server 2003. The server is mainly used for file sharing, printer sharing and serving a database (firebird). 

The cost for each SBS 2003 license is getting to prohibitive and I am thinking of switching to Ubuntu server. I have successfully dual booted Ubuntu on a machine and played with it for a while.

Is it possible for the Ubuntu server to serve as a domain controller where the clients can log on to it? (ctrl+alt+del and log on to server)
On the SBS 2003, clients connect to the server using IE and typing "ConnectComputer" in the address bar. How can I do this using Ubuntu?
I have been trying to look for a tutorial but none address this too well. I am on a limited budget (no test machines) and I can't risk installing the Ubuntu on the server machine to find out that I can't make it run. Can someone enlighten please? All help greatly appreciated. Thank you.

Howard

I think you can use it for a domain controller with samba for an NT network but not active directory AFAIK

---

### Post by Anteaus on 2007-08-13
I've recently switched to a samba server from W2000, and the setup was quite tricky but now it's running smoothly I don't think I'd even consider going back. The main problems I hit concerned filesystem permissions, which are admittedly tricky to get right if you want collaborative working.

Changing a domain-controller is always a traumatic event, even when migrating from one Windows domain-controller to another. 

Other point, Linux provides no equivalent of Exhange Server, so if you are using the full SBS setup that might be an issue. There are obviously alternatives, but none that provide exact-replacement functionality.

From what you say about connecting with IE, it sounds as if you're not actually using a domain logon, or the SBS client. In that case, MyLogon might be a simpler and more flexible approach to connecting to the Samba server. [http://mylogon.net](http://mylogon.net)

---

### Post by Brazen on 2007-08-13
I'm also not quite understanding what all features of SBS you are actually using?  Is it being used as a domain controller? email server?  file server?  What is this "clients connect to the server using IE and typing "ConnectComputer" in the address bar"?  If it is a domain controller, you should not have to do any extra steps to log in to the domain, unless maybe that is a shortcut to get to OWA.

For a simple file server, you can use OpenFiler or FreeNAS.  For an email server, with web interface, you can use eGroupware (really tons of options in this area).  For a domain controller, you use Samba (unfortunately, this is the one thing you will lose a LOT of features from Windows domain controller, if you use those features).

For trying things out, if you can get ahold of one box, and pack it with a gig of RAM or more, you can install VMWare Server on it and pack in probably 3 or 4 or more virtual machines with decent performance for trying out things on Ubuntu.

For more detailed answers I think we need a more thorough explanation of what your are wanting out of this.

---

### Post by hchristian on 2007-08-13
Hello all,

Thank you for the help. Sorry if I wasn't too clear on what I was asking. Let me get detailed. Let's hope it doesn't bore you.

Background :
When we first started, we only had 3 computers on a peer-to-peer network. The programs we run are basically only word and excel (for giving price quotations and price lists). The other software that we use is an accounting software based on the Firebird database server (open source so the software don't cost too much). 
The Firebird server was run on computer A with computer B & C getting data off A. The person using computer A complained that his system often lags.

When our budget allowed, we purchased an IBM xSeries 100 computer to act as the server and 5 more client computers. Budget being the constraint, we went on to get the Windows SBS 2003.  I am not an IT person, however, I went on to read some materials on the net and set up the SBS 2003. 

Problem :
The system is still running fine as of now. What I am concerned is when we get more machines. The licenses alone for the SBS 2003 is quite expensive.   I am looking to switch to the Linux server.
We only run word processing programs with file sharing and the accounting program with Firebird on the server (I dont even know to to use Exhange, run an Email server...etc..we use webmail) . Is it possible for the Linux server to provide this? What I meant earlier by "ConnectComputer" earlier was that, when I set up the SBS 2003 server, joining client computers was as easy as type "ConnectComputer" in the IE address bar and everything was set. As simple as that. With Linux as the server, how am I supposed to join the XP clients to the server?

Thank you all.

---

### Post by SteveHillier on 2007-12-07
> **hchristian said:**
> As simple as that. With Linux as the server, how am I supposed to join the XP clients to the server?
.

I don't know if this thread is still live but this bit is very simple to deal with.
On XP go to control panel -> system.  Click on the name tab.  THere are two buttons.  If you click <change> then there is an option to make that computer a domain member.
You will need your domain name.  You will need to have a user name and password.  You will need to have the domain server administrator username and password to authorise adding the machine to the domain.
You will also have to make sure you have set up the user in Active Directory to allow full domain logon.
Like other responders to your enquiry it seems you are not using anywhere near the full features of SBS.
Hope this helps.  email direct if you wish.

Sorry I might have got the wrong end of the stick.  forgive me if I have.

---

### Post by sciurus on 2007-12-07
One of the easiest ways to get the domain server and file sharing set up is to use [http://ebox-platform.com/](http://ebox-platform.com/) . This [should be]("https://blueprints.launchpad.net/ubuntu/+spec/ebox") an optional part of the next version of Ubuntu server; it was supposed to be in Gutsy but the integration work wasn't finished in time.; For now the easiest way to set it up is with their[ custom debian installation cd]("http://ebox-platform.com/get/ebox_installer.iso"),

---

### Post by perfecttao on 2008-02-01
Wow - Ebox looks like a platform that could ACTUALLY compete with MS SBS :)

This is just what I've been looking for for a faster and easier method of installing Samba, LDAP + some form of messaging server :)

Thanks sciurus - you've made my week!!!

---

### Post by HermanAB on 2008-02-01
The best documentation for running  PDC on Linux is on the Samba web site.  Read the Official Howto Guide.  There is also a howto guide specific to Ubuntu.

Cheers,

Herman

---

### Post by perfecttao on 2008-02-04
Bizarrely I've just been reading your howto for Active Directory integration here: [http://aeronetworks.ca/LinuxActiveDirectory.html]("http://aeronetworks.ca/LinuxActiveDirectory.html") Herman - a very well written guide :) Thanks :)

---

### Post by LRT on 2008-02-05
Samba is not for the faint of heart. Make sure you read all documentation and set up a test box before going live. ...luckily you don't have many users...

---

