---
title: "Questions about Ubuntu and having a client/server enviroment  and virtualisation."
date: 2012-08-24
forum: Server Platforms
---

### Post by Jasongtelford on 2012-08-24
Hi there

I have already posted this in another section, but it was suggested that I'd get a better response by reporting it in the server section - so hre goes

I seen on the Ubuntu website that there is a server edition. This is good because I wan to install Ubuntu on a server: specifically this server, "Dell 2950 Twin Quad Core 2.66Ghz 16GB RAM SATA/SAS RAID PowerEdge Server VMware".

However I have three questions that I could not find the answers to.

-----

1: can I install Ubuntu on to my server, create user accounts and then have my client machines connect to the server so the users can login without needing Ubuntu installed on each individual machine.

This is basically what the idea of a server is, but all the stuff ive read talks about web servers, which isn't what I want.

2: will I be able to install Ubuntu onto the server listed above. The lists of servers I saw did not include mine.

3: can I allow my users to access their desktops via the Internet (like a virtual enviroment).

I did this at university with UNIX. Basically, I went to the university website, logged into my student area and then clicked on the link. A login box asked me to login to UNIX and then it loaded a virtual desktop in full screen mode. I then had access to all the program's and files and I was able to interact with the enviroment as though it was a traditional desktop (just accessed via a web-browser using a java applet).

Can I do this with ubuntu so my users can login to their user accounts from any machine by going to the page on my website and logging into their user account using a java enabled browser, such as google chrome or Mozilla Firefox?

----

I think that's it for now, ii hope someone can assist me and thank so much.

---

### Post by SeijiSensei on 2012-08-24
It is easy to set up text-mode remote logins with SSH. For Windows there's a free client called [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").  Macs probably have a native client.

Giving them full graphics environments is a lot harder problem.  [Cygwin](http://x.cygwin.com/) provides an X environment for Windows so it might be possible to use that.

The kind of full-blown environment like that you describe may be a commercial product.  I'd ask your university's IT staff what they use.

As for that server, I've installed Linux on a comparable Dell.  Both Ubuntu and CentOS installed properly with the SAS RAID driver enabled.  However that "VMware" suggests you're really talking about installing to a virtual machine and not to the hardware itself.  Linux on VMware is [well-supported]("http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html").

---

### Post by Jasongtelford on 2012-08-24
> **SeijiSensei said:**
> It is easy to set up text-mode remote logins with SSH. For Windows there's a free client called [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").  Macs probably have a native client.

Giving them full graphics environments is a lot harder problem.  [Cygwin](http://x.cygwin.com/) provides an X environment for Windows so it might be possible to use that.

The kind of full-blown environment like that you describe may be a commercial product.  I'd ask your university's IT staff what they use.

As for that server, I've installed Linux on a comparable Dell.  Both Ubuntu and CentOS installed properly with the SAS RAID driver enabled.  However that "VMware" suggests you're really talking about installing to a virtual machine and not to the hardware itself.  Linux on VMware is [well-supported]("http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html").

So let's see if I understand this right. 

On my server, I would install Ubuntu server edition and then on each client, I would instal ubuntu desktop. Once that was done I would tell ubuntu desktop (installed on the client) to connect via the server. 

So the user turns on the client and Ubuntu loads into the login prompt, the user enters there username and password, the client connects to the server and loads the users desktop (just like it would do if it was loading from its own native drive) - but instead of the users home folders been stored on the clients native drive, they are stored on the server. 

Have I got this right?  And if so, is it easy to set this up and how would I do it. 

I'll forget about distributing the virtual machine over the net for now and just concentrate on fat clients.

---

### Post by SeijiSensei on 2012-08-24
I assumed you were looking to support a mixed environment.

You have a variety of solutions if all the machines are running Ubuntu.  The best thin-client solution is the "[Linux Terminal Server Project]("http://ltsp.org/")" where the sessions run on the server and are displayed by thin clients.

If the clients have a full Ubuntu implementation, you can put the home directories on the server and distribute them to the clients with [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").  This is the time-honored Unix way.  You'll want to examine centralized authentication mechanisms for this solution like [OpenLDAP]("https://help.ubuntu.com/12.04/serverguide/openldap-server.html") or [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo").  

If you just want to let people run applications from a common server, one simple solution is to use [SSH with X tunneling]("http://people.csail.mit.edu/wentzlaf/faq/ssh_X.html").  After logging in with "ssh -X user@server" you can run X applications on the remote server, and the graphical output will appear on your local machine.

---

### Post by LHammonds on 2012-08-24
I have installed Ubuntu Server 12.04 LTS (64-bit) as a bare-metal install on a Dell PowerEdge 2950 which has a PERC 6i RAID controller with five 74GB drives and it worked perfectly.

However, I think you are really wanting to install Ubuntu on that server which probably already has VMware's ESXi server installed.  That means your are installing into a virtual environment.  I have notes on that particular kind of install in my signature.

I cannot comment on delivering a virtual desktop yet but I am very interested in doing this within the next 12 months.

LHammonds

---

