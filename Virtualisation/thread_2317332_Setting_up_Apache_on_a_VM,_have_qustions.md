---
title: "Setting up Apache on a VM, have qustions"
date: 2016-03-15
forum: Virtualisation
---

### Post by mattig89ch on 2016-03-15
Hidy ho all,

I have a windows 10 machine at work.  And, instead of surfing the internet while I wait for something to do, I figured it would be a good idea to start brushing up on my linux skills.

So I have a Virtual Machine running Ubuntu 15.10 32 bit.  I installed apache on that system, and have it sharing my local machines NIC. Now I want to work on making sure I know how to remotely access this machine, and make changes via the CLI.

So my first question, how do I setup that machine for remote access?

Second question, is there a special way to remotely access an Ubuntu machine from a windows machine?

Edit:Third question, while I wait for those two up there.  Where does apache2 put its web pages?  So I can play around with creating basic html documents

---

### Post by bab1 on 2016-03-15
> **mattig89ch said:**
> Hidy ho all,

I have a windows 10 machine at work.  And, instead of surfing the internet while I wait for something to do, I figured it would be a good idea to start brushing up on my linux skills.

So I have a Virtual Machine running Ubuntu 15.10 32 bit.  I installed apache on that system, and have it sharing my local machines NIC. Now I want to work on making sure I know how to remotely access this machine, and make changes via the CLI.

So my first question, how do I setup that machine for remote access?

Install openssh-server on the Ubuntu VM.  
> 

Second question, is there a special way to remotely access an Ubuntu machine from a windows machine?

Install PuTTY on the Windows machine and ssh to the Ubuntu machine from Windows.  This will give you a Ubuntu CLI in a PuTTY window.
> 
Edit:Third question, while I wait for those two up there.  Where does apache2 put its web pages?  So I can play around with creating basic html documents
You can configure any location you like as the DocumentRoot. It is configured in the /etc/apache2/sites-available/<domain.conf> file.  You create that file using the /etc/apache2/sites-available/000-default.conf file as a template.  Just copy that file to file with the name you want to use and edit that.  The line to set the DocumentRoot is```

DocumentRoot /var/www/html

```
I have all of my web page DocumentRoot set to /srv/data/www/<domain>

---

### Post by oldos2er on 2016-03-15
Moved to Virtualisation.

---

### Post by SeijiSensei on 2016-03-16
I use VirtualBox for VMs.  To make the VM visible to the rest of the network, the easiest solution is to use "bridged" networking.  That puts the VM in the same network as the host.  Then machines on the rest of the network should be able to connect to it directly.

As for how they connect, that depends on whether you have a DNS server running locally or not.  If you do, then just add an A record for the server's name and IP address.  If not, you can either use IP addresses in the URL like [http://10.10.10.10/](http://10.10.10.10/),  or add an entry to each client machine's [hosts]("https://en.wikipedia.org/wiki/Hosts_%28file%29") file.  The problem with the IP-based approach is that you cannot use Apache's name-based virtual hosts feature if you want to run multiple sites on the same IP.  That requires unique hostnames for each virtual host.

---

### Post by mattig89ch on 2016-03-24
My apologies for not posting this sooner.  Using putty worked!  I only used putting to configure cisco routers before now, I had no idea what else it can do.  still don't actually, since I'm only using it for this other purpose.

But its working!

Now to...um...hm.  I guess create a web page, and copy it to the servers folders?  Are there any guides to creating a web page via the command line?

---

