---
title: "Ubuntu Novice Needs Advice"
date: 2016-10-18
forum: Server Platforms
---

### Post by huskerphil on 2016-10-18
Hi everyone.  My company has asked me to build a server with Ubuntu on it to test an application in our dev environment.  Having never worked with Linux before I'm finding that to be a bit of a challenge.  I currently have Ubuntu Server 16.04.1 LTS installed with the Ubuntu Desktop GUI.  Here is what I need the server to do next.

[LIST]
[*]Join our dev Windows Server 2012 R2 domain
[*]Have domain groups/users be able to log into the server and be in the sudo group
[*]Have those same domain groups/users remote desktop into the server from a Windows 7/Windows 10 machine
[/LIST]

I have done lots of trial on and error with these three things, but can't ever get them all to work correctly.  I've read a ton of guides and posts, but each one seems to go about this a different way.  I want to scratch everything I've done and start with a fresh install.  Does anyone know the best guides I can use for this?  Or any other thoughts/ideas?  

Appreciate your help and feedback with this.  Thank you!!!

---

### Post by darkod on 2016-10-18
Stop on the first step. Ubuntu Server with Ubuntu Desktop GUI??? I know you said you have almost no linux experience and probably that makes you dependent on a GUI, but I would reconsider the approach.

Why don't you try installing the ubuntu server as it's supposed to be, only with command line? Can this application work on linux server without GUI? The basic stuff you need to set up are not that difficult to do in the command line too. Trust me, if you can't manage to do that, the GUI won't help you much. In fact it might turn things even more complicated.

The rest of the stuff you mentioned, joining a windows domain and have domain users logging in is not too complicated. You should be able to do it.

---

### Post by QIII on 2016-10-18
> **darkod said:**
> Stop on the first step.

^^ This.

Server + GUI is a Windows-ism.  Not that that is bad.  It works perfectly well for Windows and if you use Windows you do it that way.  There is absolutely nothing wrong with a Windows Server, despite what some of the more "purist" (read "zealous") Linux users may say.

However, the general case for a server in a Linux environment is a non-graphical (command line) interface, often administered remotely via SSH.  The idea of a server is to present very limited and specific services for a clear purpose.  A GUI is composed of a large number of services that consume resources and detract from the intended services.  In a server exposed to the web, a GUI's running services also multiply the attack surfaces.

I run websites on command-line-only servers, administer them over SSH, don't use Control Panels and don't have anything like phpMyAdmin installed.  Of all the attempted hacks on the servers, the last service is the one most often tried at by ne'er-do-wells.  Trying to use the servers as a proxy is a close second.

There is a learning curve, no doubt.  But you are in a position to learn things as they are most often done, rather than trying to "un-learn" later.

---

### Post by huskerphil on 2016-10-18
Thank you for the response.  If it were my choice I would go the command line route, I have already found it much easier to work with that.  However, it was requested that a GUI interface be made available.  Even after I suggested a command line interface could be used instead.  Hands are kind of tied there.

---

### Post by QIII on 2016-10-18
So long as those with the rope realize it is also tangled around their necks.  :)

---

### Post by huskerphil on 2016-10-18
Ha ha ha, we will have to see on that.

---

### Post by mastablasta on 2016-10-19
> **huskerphil said:**
> Thank you for the response.  If it were my choice I would go the command line route, I have already found it much easier to work with that.  However, it was requested that a GUI interface be made available.  Even after I suggested a command line interface could be used instead.  Hands are kind of tied there.

Have a look at Zentyal distribution, [http://www.zentyal.com/zentyal-server/](http://www.zentyal.com/zentyal-server/)


see if that helps you set it up. Ubuntu based and by default it will install with GUI, but "expert mode" will let you install a webgui only.

since you will probably want some LTS and if you do not want to spend money on Zentyal, then have a look at Nethserver. Centos based, nice webgui. Another similar option is ClearOS.

another option is to install ubutnu and then add a simple GUI like Ajenti, to help you do what you need it to do. 
 
do they want deskotp GUI or would webgui do for them? i mean with webgui oyu can control it from mobile phone. same goes for SSH by the way.

---

### Post by huskerphil on 2016-10-19
> **mastablasta said:**
> Have a look at Zentyal distribution, [http://www.zentyal.com/zentyal-server/](http://www.zentyal.com/zentyal-server/)


see if that helps you set it up. Ubuntu based and by default it will install with GUI, but "expert mode" will let you install a webgui only.

since you will probably want some LTS and if you do not want to spend money on Zentyal, then have a look at Nethserver. Centos based, nice webgui. Another similar option is ClearOS.

another option is to install ubutnu and then add a simple GUI like Ajenti, to help you do what you need it to do. 
 
do they want deskotp GUI or would webgui do for them? i mean with webgui oyu can control it from mobile phone. same goes for SSH by the way.

Thank you for the feedback.  Since this is on a dev environment and we aren't sure if we will be purchasing this software they don't want to spend any money.  I was under the impression Ubuntu Desktop would work for this???  I'm probably wrong there.

---

### Post by TheFu on 2016-10-19
Ubuntu Desktop is meant for desktops. It generally doesn't include "server management" things.

There is a server guide document for 16.04 (google finds it). Take a look at that.  I avoid the web-guis, since as software is more complex, they also have more bugs which attackers can use.  Allowing developers ssh access to a web server is a not-so-great idea.  Depending on the complete software stack, it might be best to setup a CI environment and only have the servers grab the deployment code directly from the DVCS.  This should happen after all the automatic testing has been performed.  Hopefully, your devs are already using TDD.  Then the devs won't need **any** server access. This is the best option.

For each dev, they probably want to use a virtual machine on their own systems to do initial development and testing.  Vagrant is popular for this.  If you do allow them access to the production server (or even control on the pre-prod test server), it will be common for them to demand more and more access and screw up OS security settings.  Preventing developers from doing less-than-smart things on a *nix system is very hard unless you know more than they do about it.  *nix security is full of subtle settings that take time and experience to understand.  Letting devs on the box at all will dig a hole that you'll probably never get out from.

Purchasing software?  That usually isn't necessary on a Linux stack unless you just want to pay someone. Support often isn't any better than forums provide unless it is extremely specific and from the actual software developers. There are only a few tools I'd pay for on Linux.

So, let's assume you lose the login battle and are forced to allow ssh for devs. Allowing developers unlimited sudo access is a really bad idea. Just sayin.  Even allowing editors so they can edit system files is very dangerous.  You want to know exactly what they want with sudo and lock their specific users down to just those commands with exactly those options. sudo allows this level of control.  Also, the power to mount is the power to take over (or destroy) a system, so be cautious with that as well.  Be very careful - looks like a no-win situation based on the requirements.  You should warn your boss about this.  Would be good to get to some official Linux training ASAP if you are the admin. If you don't have much time, the redhat training (3-levels) is probably the best, but There is a huge learning curve and it is probably best left until after you've been a full-time user for 6 months without a GUI.  I don't think **any** Linux admin classes use a GUI. It just isn't done that way.

Linux is not Windows. The way software is used on it is very different. There is a different culture. Linux systems tend to have zero paid software installed.  The community around each project is really where the support comes. We see Windows admins coming to Linux all the time here trying to apply the stuff they were taught from the Windows ecosystem which just doesn't apply.  It is a completely different culture - not a customer/supplier relationship. For that, you need to be running commercial RHEL or SuSE as the OS. Debian/Ubuntu just isn't that way.

The stock desktop (Unity) doesn't work with remote desktops - you'll need something like mate, lxde, xfce instead. A desktop is just another program, not the OS on linux. Something lite that doesn't need direct access to the GPU is required for the remote desktops. No local desktop is needed for this to work. Look at either x2go or tightvnc. x2go has ssh tunneling built-in and I think tightVNC still needs either an ssh-tunnel or VPN used to be secure.  Use the --localhost option on the tightvnc-server to force that.

As for joining a domain - not really done on *nix systems.  If you want users and groups to be provided by a differnt LDAP server, that isn't hard, provided the LDAP server has POSIX schema extensions loaded. It would just be for logins. [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) is where I'd start.  It wouldn't be for apache/nginx web logins. For those, the LDAP would need to be setup again. The same if you want CIFS file server support - samba would be setup which only applies to CIFS authentication, not for the entire server. 

Linux is extremely flexible which can also make it very challenging. Plus there are multiple methods to setup things. We commonly say there are 50 different ways to solve any issue.  Different methods are best under different situations.  For example, the way I'd setup LDAP authentication for 5 people is different from how I'd do it for 100-5,000 people.

---

### Post by darkod on 2016-10-19
+1 for the last post by TheFu.

I don't know how you plan to set up the environment, but developers shouldn't need "remote desktop" access to the server. They develop their code and upload it by something like sftp/scp session. They can easily do that from any windows using the free WinSCP program.

Is the idea for them to use this server to do the actual development on? Because if they develop on their workstations, then no server access is needed in fact apart from the upload which they can do themselves or through the IT administrator.

---

### Post by SeijiSensei on 2016-10-20
> **huskerphil said:**
> 
[LIST]
[*]Join our dev Windows Server 2012 R2 domain
[*]Have domain groups/users be able to log into the server and be in the sudo group
[*]Have those same domain groups/users remote desktop into the server from a Windows 7/Windows 10 machine
[/LIST]


Do you really need to have the Ubuntu box join the Windows domain?  Why?  It is possible, but not really necessary as we'll see in a minute.  If you must do this, read [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto).

If you don't go for the full-blown integration with the Windows domain, you can simply add the users to the system directly with the same passwords they use now.  Another possibility might be using LDAP authentication against the Windows domain controller: [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

Next, why do the developers need to have root privileges?  In my mind, that's a recipe for potential disaster.  If they don't have any Linux experience, why would you give them the ability to blow up the box by mistake?  There's no need to have root privileges to develop or test code.  Only the system administrator (you, presumably) should have root privileges.  Everyone else should be an "ordinary" user.  I'd begin with that security model and open it up only if there is some functionality that the developers cannot employ without root privileges.

As for remote desktops, consider installing an X server on the Windows machines like [Xming]("http://https://sourceforge.net/projects/xming/") or [Cygwin/X](http://x.cygwin.com/).  That will let users run graphical applications on the Ubuntu box and have the output display on their Windows machines.

Finally, for moving code between the machines, run [Samba]("https://help.ubuntu.com/community/Samba") on the Ubuntu box.  Then you can map shares on that box from Windows just like you would do with a Windows network.

---

