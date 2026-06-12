---
title: "Replicating Server Settings"
date: 2009-03-21
forum: Server Platforms
---

### Post by Marcelo Santos on 2009-03-21
Hello All,

In my company, we have a bunch of Linux Distros, and my boss came to me with a project to replace all of these distros with Ubuntu Server 8.10 64.

In a general, every server will be almost identical, running a Samba Server, and have installed (and not running) LAMP configuration.

My question is: what is the best method to replicate the first configuration that I've done in the first server and replicate this settings on the others?

The only changes that I will face probably will the hard disks configuration, motherboard and network settings.

I' thinking to use Ghost, but I am not sure of the Ubuntu behavior in face of these hardware changes.

Is there a software or command that I can save the Ubuntu Settings to a media, and replicating these settings in a new installation?

Any help would be very appreciate.

Regards,

Marcelo.

---

### Post by sgla1 on 2009-03-21
Have you considered using cobbler and puppet?  It appears that cobbler now supports debian installs
 [http://fedorahosted.org/cobbler/wiki/DebianDeployment]("http://fedorahosted.org/cobbler/wiki/DebianDeployment") 
even though it is a fedora-sponsored program.  After install puppet can be used to deploy software and manage configs across a large server farm.

I'd be very interested in your results using cobbler with Ubuntu.

---

### Post by hyper_ch on 2009-03-22
well, server-wide settings are in /etc... basically copying that should clone most settings. However some stuff needs then still manual change.

Hardware changes are not a big issue on linux - as long as the hardware is supported directly.

---

### Post by Marcelo Santos on 2009-03-24
I'm thinking to make a copy of all settings in a working ubuntu box, and, in the instalation process these settings will be replayed to new server....

It's a kind of "unattended instalation" in Windows... You configure the settings, machine name, and so on, save this to a inf file and use the method that I spoke above.

In a few minutes, the server is installed, with no issues at all.. Just only rename the machine name, and it's ready to work.

Marcelo.

---

### Post by doogy2004 on 2009-03-24
A simple idea might be to use rsync to update the servers from a master configuration server.

---

### Post by sgla1 on 2009-04-05
> **Marcelo Santos said:**
> I'm thinking to make a copy of all settings in a working ubuntu box, and, in the instalation process these settings will be replayed to new server....

It's a kind of "unattended instalation" in Windows... You configure the settings, machine name, and so on, save this to a inf file and use the method that I spoke above.

In a few minutes, the server is installed, with no issues at all.. Just only rename the machine name, and it's ready to work.

Marcelo.

If you want to clone a large number of machines, you might want to look into System Imager.  

However system imager doesn't address the problem of rolling out changes to a large number of machines in a uniform fashion after they are installed.  Neither does copying/rsyncing /etc imho.  You can deploy new settings across your farm that way, but how do you install updates and new software?

Cheers
Steve

---

### Post by Marcelo Santos on 2009-04-06
> **sgla1 said:**
> If you want to clone a large number of machines, you might want to look into System Imager.  

However system imager doesn't address the problem of rolling out changes to a large number of machines in a uniform fashion after they are installed.  Neither does copying/rsyncing /etc imho.  You can deploy new settings across your farm that way, but how do you install updates and new software?

Cheers
Steve

I'm thinking about a kind of to save the /etc dir, and other files that contain the machine configuration.

The idea is automate the deployment of new servers across the enterprise, but some settings will never be the same: like the servers that will be installed in remote locations, were the network and subnet mask is different from the headquarters...

Well, if I can minimize the effort to deploy these guys... I guess every minute saved is worth the effort.

Let's try the the Tip Steve, and I will post here the results... But this will not fast as I want...

Regards,

Marcelo.

---

### Post by OmegaBLK on 2009-04-20
> **sgla1 said:**
> If you want to clone a large number of machines, you might want to look into System Imager.  

However system imager doesn't address the problem of rolling out changes to a large number of machines in a uniform fashion after they are installed.  Neither does copying/rsyncing /etc imho.  You can deploy new settings across your farm that way, but how do you install updates and new software?

Cheers
Steve

Your cobbler & puppet/scripting recommendation is the way to handle this situation and I agree especially if the hardware varies.  When using automated install files + scripts it is much easier to deal with changes when deploying and push them out to clients then using imaging software and cloning.

As for system management, I guess cfengine/puppet/scripting most likely is the answer then.  You could also glue some tools together thru scripting (like pssh/cluster ssh, expect, etc.) and it should be snap to get clients to pull new apps/updates down and to apply config changes.  

FYI to the OP:  The Ubuntu/Debian equivalent to unattended install is called preseed.  But Ubuntu can also utilize the RedHat/Fedora kickstart files for automated installs also.  Cobbler using PXE installs can customize dhcp and dns for you and push out installs automatically across the network to the systems that you want to install on.  And Cobbler also allows one to setup in-house mirror repositories for both RPM and DEB packages and keep them in sync with the original repo server.  You can setup different profiles/roles for specific systems.  I would really take a look at [https://fedorahosted.org/cobbler/wiki](https://fedorahosted.org/cobbler/wiki) and give it a spin.  Puppet/scripting is great for pushing out config changes.

Also don't forget to check up on Canonical's Landscape as that is specifically for Ubuntu, but I have not been keeping track of it lately.

Some links:
[Preseed](https://help.ubuntu.com/8.10/installation-guide/amd64/appendix-preseed.html)
[Puppet](http://reductivelabs.com/trac/puppet)
[Landscape](http://www.canonical.com/projects/landscape)
[cfengine](http://www.cfengine.org/)

---

