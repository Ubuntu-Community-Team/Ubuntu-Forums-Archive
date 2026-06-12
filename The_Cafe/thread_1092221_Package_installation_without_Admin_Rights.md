---
title: "Package installation without Admin Rights"
date: 2009-03-10
forum: The Cafe
---

### Post by newbe5 on 2009-03-10
Forgive me if this has been gone over a thousand times, but I'm going to ask anyway :P

Is there a way fro me to set up a "Trusted APT repository" from which users can install software without the need to enter a sudo password? This is so I can distribute software in an enterprise-like environment without giving users access to install software from ordinary repositories.

Also, while I'm on the subject, can anyone reccomend good tools for use with Ubuntu in an enterprise managed environment? This isn't for production machine currently, I'm just testing the software out to see what it might be capable of. 

Thanks in advance!

newbe5

---

### Post by MaxIBoy on 2009-03-10
I don't know if you can configure apt differently for different users, but why would you want to? Seems like asking for trouble to me. Stick with requiring root access for all installing, it's safer that way.





UNIX was designed for enterprise (invented before personal computers) and with shared mainframe computers (so permissions policies become way more important.)

Linux's UNIX heritage means that it has a very good toolset for creating secure permissions policies. 
[http://www.zzee.com/solutions/unix-permissions.shtml](http://www.zzee.com/solutions/unix-permissions.shtml) 
Essentially, if you want to make sure no one can mess with anything, add a user, and don't allow the user to run anything with sudo or change any settings. Then, keep the admin user's password a secret.

---

### Post by Yashiro on 2009-03-10
Yes, but how do you keep machines patched with security updates without admin intervention, is what he's really asking.

---

### Post by MaxIBoy on 2009-03-10
Use [cron-apt]("http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html") to automatically update packages. Just change the default settings so that it will download *and *install the packages instead of just downloading, disable the "mailon" option so you don't get spammed by email notifications that the computer is updating itself, and you're good to go.

---

### Post by Johnsie on 2009-03-10
Maxi, I've been wanting to do that for my server and also so I don't have to manually update packages every couple of days on the desktop. Do you think you could explain in more detail how to go about doing these automatic updates? After 3+ years using Ubuntu I'm starting to get a little fed up having to manually update. things every time I notice the 'updates available' icon appearing.

---

### Post by MaxIBoy on 2009-03-10
First, install cron-apt. 

Then, as root, edit /etc/cron.d/cron-apt to suit your needs. The file is commented with explanations by default.

---

### Post by newbe5 on 2009-03-11
Great information, thanks guys :) But what about distributing software to the client machines once they are out in the field? Is there any easy tool to do this, something that works like SMS for windows maybe?

---

### Post by Johnsie on 2009-03-11
Someone could probably write an application that does this. The application would need to  be running as a root owned background process. The application would detect if new packages were available on your web server, automatically download the debs and then install them. If the application was already running as root then it wouldn't need a password to process the debs.

Security-wise this might not be a good idea, but it is do-able.

---

### Post by bigbrovar on 2009-03-11
> Johnsie  	
Re: Package installation without Admin Rights
Someone could probably write an application that does this. The application would need to be running as a root owned background process. The application would detect if new packages were available on your web server, automatically download the debs and then install them. If the application was already running as root then it wouldn't need a password to process the debs.

Security-wise this might not be a good idea, but it is do-able. 
This is probably not a good idea for an enterprise setting. where stability is most important over anything else. setting unattended updates for systems is always a bad idea. where i work we use apt-cacher so all systems download packages and updates via the caching server. for managing and administering the systems i use systemimager. which allows me to maintain a golden image. where updates are first installed and tested. before their are pushed out to the clients. this way. all my clients are centrally controlled and monitored. with tools like cluster-ssh adminitering systems in updating my clients to the latest image is a breeze .. i can also set a cron for the client to alway fetch the latest image from the image server. this way i on top of what goes in and out of each computer . and if there is a patch that needs to be applied. i can apply it to all over 200 computers. within 10mins without leaving my sit.

---

### Post by toupeiro on 2009-03-11
I recommend you look into a tool called pssh and do a little reading up on ssh keys.

you can share a root ssh key of one system with other systems which is basically another way of making it a "trusted host" which is another methodology you could follow to install software from a central location.

Once you share your root key from the system you will run pssh from, simply supply it a list of your other machines by name or ip address and the command you wish to run.

---

### Post by MaxIBoy on 2009-03-11
> **newbe5 said:**
> Great information, thanks guys :) But what about distributing software to the client machines once they are out in the field? Is there any easy tool to do this, something that works like SMS for windows maybe?
Look into [creating a custom debian repository on your LAN]("http://www.debian.org/doc/manuals/repository-howto/repository-howto") and [adding it]("https://wiki.ubuntu.com/Repositories/Ubuntu?action=show&redirect=AddingRepositoriesHowto") to all your installations. 

You could remaster the Ubuntu CD so that the repository is set up correctly on the installation image. That way, you don't have to change this for every computer you deploy.

---

### Post by kk0sse54 on 2009-03-11
> Forgive me if this has been gone over a thousand times, but I'm going to ask anyway 

Is there a way fro me to set up a "Trusted APT repository" from which users can install software without the need to enter a sudo password? This is so I can distribute software in an enterprise-like environment without giving users access to install software from ordinary repositories.

Also, while I'm on the subject, can anyone reccomend good tools for use with Ubuntu in an enterprise managed environment? This isn't for production machine currently, I'm just testing the software out to see what it might be capable of. 

Thanks in advance!

newbe5

You don't enter your sudo password to gain access to the repo, you enter it so that the installer has write permission to your root filesystem.

---

### Post by UbuWu on 2009-03-11
For security updates use the unattended-upgrades package. For other programs, you can configure sudo to allow people to run e.g. only gnome-app-install with sudo rights.

---

### Post by gnomeuser on 2009-03-11
Install packagekit, then setup policy using policykit over what users are allowed under which conditions and using what methods of verification.

Yay packagekit

The trusted apt repo part of the problem could, probably, be done by setting up your own local mirror and forcing all clients to use that.

---

