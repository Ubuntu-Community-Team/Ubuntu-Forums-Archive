---
title: "Group Policy in Linux?"
date: 2007-12-08
forum: The Cafe
---

### Post by Black Mage on 2007-12-08
Is there anything like group policy in Linux where users can be managed, permissions set, and software easily deployed onto user computers?

---

### Post by toupeiro on 2007-12-08
mmmm...  Not in such a direct way.  By the sounds of it, you have an Active Directory Domain with some linux or UNIX servers or workstations. :)

There is a lot you can do with Active Directory in linux, even have accounts in Active Directory log into Linux (though I do this now and I don't much care for it for different security reasons which I am in the process of proving)

GPO In Windows is a set of objects based around Windows API and domain archtype.  for a GPO to work in Windows, a machine account would first have to be created for that Linux machine, but the much more difficult task is that a GPO would have to be written for a linux OS, which I have never seen before.

Your best approach, in my opinion, is NIS.

with NIS, you can create a machine database from an NIS metafile with whatever information you want in it, and query it it with the ypcat command.  This you can use to set your execution scope in your NIS domain.

If we aren't talking about a lot of machines though, another option is to setup a .rhosts file on each linux machine and give yourself a trusted host that you can execute commands as root.  Then, setup some cron jobs for the various things you want to perform.

edit:
oh yeah, if you do NIS, you will still need the trusted host.  NIS just makes it easier to administer multiple machines, and gives you the ability of network logins.  Make your NIS server that trusted host.

---

### Post by Black Mage on 2007-12-08
It sounds like your suggesting a Windows/Linux combination?

I'm trying to  go pure Linux and am basically looking a way to manage accounts on a DNS and deploy software/setting to these Linux Computers.

.rhost does not sound practical because that would mean mean manually going to each computer and configuring it.

---

### Post by toupeiro on 2007-12-08
:) no, that is not what I am suggesting.  That is what it sounded like you already had. (GPO and Linux)


here is the deal though, even in a Microsoft world,  you couldn't just "do GPO" without configuring machines to be on a domain.  Same thing applies to linux.

If you want a Linux domain, I would run NIS.  run DNS on the same box.

setup your .rhosts file to point to your NIS server (think of this as your domain controller where you are going to inforce policy from)  you can use rcp (remote copy) to deploy these files.

for inital deployment, you have a ton of options.  

If you use redhat, you have kickstart which allows you to do unattended installs of an OS.  You also have traditional methods such as ghost or True Image.  even [G4L (ghost for linux)]("http://sourceforge.net/projects/g4l")

There are other things too, like Suns UCE product, which is more like Microsoft SMS for Linux, but that costs money :)

If you have an unstructured environment already, it is going to take some extra steps in the beginning to get centralized.

---

### Post by lostchain on 2008-12-13
sure with lnux you can get ur dreams :guitar:
samba server gets ur dream up :)
where samba3 completely replace windows NT4 and coming samba 4 which will replace windows 2000 & 2003 it has built in active directory services and GPO for controlling windows machines same as windows server does just try samba4 it is still in alpha release and u will get what u want :lolflag:
sorry for my bad English

---

### Post by Gallows on 2009-03-10
Have a look at [this]("http://www.centrify.com/directcontrol/grouppolicy.asp") 

Centrify Group Policy for UNIX, Linux and Mac

[LIST]
[*]Centrally configure the policies that the DirectControl Agent uses to enforce authentication and authorization to that system.
[*]Apply consistent updates to the sudoers file, defining privileged commands that specific users can execute.
[*]Efficiently control crontab files, firewall settings, screensaver password lock, and other properties.
[/LIST]

It's a AD integration / GPO module for Linux.  Comes at a cost though...

---

