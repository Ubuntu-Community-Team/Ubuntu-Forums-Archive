---
title: "Installing Vmserver with no X on feisty"
date: 2007-05-05
forum: Server Platforms
---

### Post by systimax on 2007-05-05
Hello all !! 

I am trying to install vmware server on 7.04 server with out installing a desktop

I install the server I add to my sources deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

after a sudo apt-get update i then install vmaware

sudo apt-get install vmware-server vmware-tools-kernel-modules

after a few secs it bombs out cause i dont have make installed.

apt-get install make and it picks up and retreis and installs 

when its done I try to open the Vmserver Console app from a win machine to connect to the vmconsole

I get bad username and password with the account i used to install ubuntu with

Port 902 is open and when i telnet into 902 i get this

220 VMware Authentication Daemon Version 1.10: SSL Required, MKSDisplayProtocol:VNC

Anyone else install vmserver on server with out a desktop have any luck?

I tried this
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)


thanks

---

### Post by Chayak on 2007-05-09
Ok, the first point is that VMware doesn't support a .deb package.

The second is that VMware server requires the X server libs so while you don't need to run the desktop you need to have it installed.

To do it you need to install the kernel development and kernel source to your system.  Download the VMware .tar.gz install from VMware and follow the instructions to install it.

Then it's as simple as editing your configs to startup to the CLI rather than X and VMware sever should run fine.

---

### Post by Betelgeuse on 2007-05-09
> **Chayak said:**
> Ok, the first point is that VMware doesn't support a .deb package.

No, the vmware server software is now in the ubuntu commercial repositories so we can install it by 

sudo apt-get install vmware-server

command.

I've installed this one line command and now I have vmware on my Kubuntu Feisty computer. 
But I do not know about the issue on the server installations. I have a server running 4 virtual servers and the host os is windows 2000. I'm now planning to change the host os to ubuntu server, that's why I wa looking on this forums.

---

### Post by Chayak on 2007-05-10
Well why don't you just call up VMware and ask them if they created the .deb in the repository.  The word I got from them was if you don't download it from their site they don't support it.

---

### Post by Betelgeuse on 2007-05-10
I know they do not support a file whic is not downloaded from their web site, so,  Who created that deb file? Ubuntu package maintainers?

---

### Post by Chayak on 2007-05-10
Thats a good question to ask.

---

### Post by masmad on 2007-05-10
I think there is a bug in the Vmware server in the repos that makes it impossible to use it remotely with the Vmware console. Not sure if there are any workarounds, but I'm pretty sure there are other threads about this. Search is your friend.

---

### Post by systimax on 2007-05-10
@Chayak

1 yes there is a bug in the remote console with server 7

2. Yes Vmware supplied the package

here is the response from Canonical

The package information says:
Maintainer: VMware Build Team <vmware-build@vmware.com>


Canonical did the review of the packages for VMWare and we are in
contact with them but please use the official contact information.

Thank you,

 
Name Omitted, Senior Ubuntu Systems Support Analyst

3  Its a bug with Pam and i found the issue

---

### Post by Chayak on 2007-05-10
To each their own.  I never disputed that there was a bug.  I don't know who made the .deb package in the repository but obviously if VMware did they would have a .deb package for download along with the .rpm and .tar.gz.

The solution is for anyone who still in doubt that VMware didn't create the package in the repository it to just call them directly and ask.  They have told me they haven't created or support a .deb install.  I have no doubt there will still be people who will dispute it until they called for themselves so...

Call 1-877-486-9273 which is VMware's toll free number, go to the technical support option and ask a tech if they support a .deb or Ubuntu install, which if the company created they would no doubt support.

Oh and for your official contact information...

>  [email]vmware-build@vmware.com[/email] on 5/10/2007 7:07 PM
            The e-mail system was unable to deliver the message, but did not report a specific reason.  Check the address and try again.  If it still fails, contact your system administrator.
            <MASKEDID #5.0.0 smtp;550 <vmware-build@vmware.com>: User unknown in local recipient table>


---

### Post by systimax on 2007-05-10
In the other thread you responded to  if you would have read the first post it was already stated that the contact info was incorrect. That was part of the issue.

[http://ubuntuforums.org/showthread.php?p=2616441#post2616441](http://ubuntuforums.org/showthread.php?p=2616441#post2616441)

Secondly I think you a little confused about VMware creating a package for a open source community and supporting it officially  There is a difference. By the way you ever hear of a EULA. 
Canonical is not allowed to repackage and distribute it. Thats why the package was built from Vmware and is in the Canonical rep labeled commercial.

So now in addition to the Canonical senior systems admin email that helps maintain the rep 

Im going to now quote the email of a vmware employee that contacted me


"Jxxxxx <jxxxx@vmware.com> wrote:

Hi,

What problem are you experiencing in regards to PAM with the Ubuntu server
package? Out of curiosity, do you know if this problem exists if you use the
regular "tar" installer from vmware.com as well? This would help me figure
out if it's a packaging bug or something more widespread.

Thanks,


2 email after my response to him


Jxxxx

"Hey,

I sincerely apologize that you had such trouble getting in touch with us.  Unfortunately, they haven&#8217;t added commercial packages to Launchpad which is where we normally get our bug reports from.  I&#8217;m correcting the Maintainer field, PAM issues, and updating to 1.0.3.  Please feel free to shoot me any feedback you may have with the package"

Thanks


If you want the private address of the vmware employee feel free to PM me and i will give it to you.

Or you can wait a few days and see that contact info will be corrected the Pam issue fixed and the ver to 1.03

Other wise please take your condescending attitude and go away. It seems to me that your attitude doesnt not represent the Ubuntu spirit of community.

---

### Post by Chayak on 2007-05-11
Well, I stand corrected then.  I was simply going off the word of the techs I deal with on a regular basis.  I would appreciate that email address though.

In regards to how you precieve my attitude I simply want supported facts, and as for your opinions, save them for yourself.

---

### Post by systimax on 2007-05-11
no hard feelings i must have misinterpreted your post. Ill send the email

see yah

---

### Post by Betelgeuse on 2007-05-11
I have a Windows 2000 server running vmware-server and 4 virtual machines in it, one is a debian server. My boss told me to upgrade the server OS so I'm planning to upgrade it to ubuntu server instead of windows 2003 server. :popcorn:  Now I'm waiting for the vmware issue to be solved. i'm using vmware server from the ubuntu repos on my desktop computer (Kubuntu 7.04) but I still did not decide whic server version should I install on the server. That server will run vmware server and DNS service (bind I think) and I'm thinking about installing ubuntu server 6.06 LTS, is there vmware-server in 6.06 repos? or Should I install 7.04? I'm a little bit confused about this. :confused:

---

### Post by systimax on 2007-05-11
If this is for a production enviro go with server 6.06 lts. Long term support. That way its officially supported by vmware if you ever need to pay for support

And install the .tar from vmware.

good instructinos are here.

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

### Post by Betelgeuse on 2007-05-11
> **systimax said:**
> If this is for a production enviro go with server 6.06 lts. Long term support. That way its officially supported by vmware if you ever need to pay for support

And install the .tar from vmware.

good instructinos are here.

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

I know how to install vmware server from those instructions. it was what I do for six months. :) So, I'll go for 6.06 LTS because that server is a production server. I hope it will be better than windows 2000. But I'm a little bit nervous, this is my first linux install on a production server. Now I need info about BIND DNS server because that server has DNS server service too. do you know an how to anywhere about setting up bind dns service on ubuntu 6.06 ? I know how dns works and how to set up on windows servers but I'm a newbie on linux.

---

### Post by systimax on 2007-05-11
much better then  2000. Ubuntu server installed runs around 60mb. Add vmware server to that and it goes up to around 120 or a little higher. You may shave some of by not installing the Web interface peice and not enable host only and nat networks. See if windows can do that

Install webmin and that will help you admin the box  as well as bind

[http://www.mot.is-a-geek.com/web/walkthrough/Webmin_linux.html](http://www.mot.is-a-geek.com/web/walkthrough/Webmin_linux.html)


After the server install if you must have a gui try this

[http://www.xubuntu.org/](http://www.xubuntu.org/) if you go to the wiki it tells you how to add a lightweight gui  after a normal ubuntu server install

as far as bind goes quick google search comes up with this. Im sure you can search more

[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

---

### Post by Betelgeuse on 2007-05-11
I'm not planning to install any gui to that server. I'll install ubuntu 6.06 LTS server edition and vmware server and bind. I can administer vmware-server from my desktop machine (Kubuntu 7.04 with vmware-server installed) using the vmware server console on my desktop. The server has two nics, one is connected to internet and the other is inserted by an ethernet loopback connector to make the nic think it is connected to some network. With this configuration, one nic is on internet and the other is on the local network and I bridged the virtual machines nic to local network nic, that way the virtual servers communicating to eachother like they are on a local network and from the internet nic, I can forward the necessary ports to virtual machines. On windows 2000 vmware host, I'm using routing and RAS service to make this port forwarding. If I install ubuntu on host machine, I think I can forward port and the host machine can act as a firewall to those virtual machines but I do not know about networking in linux yet, so I'm thinking about using a small virtual machine installed ipcop linux to act as a firewall and do the routing and forwarding. I'm using the ipcop linux for two years on my office server and it's working as a vmware virtual machine without problems. When I learn linux networking enough, I'll try the port forwarding on the host machine.  I think adding an IpCop linux firewall into the virtual machines will make this configuration more complex but this is what I can manage for now. I know this is not an optimum solution but I do not have enough time.

---

