---
title: "How to share a server amongst friends"
date: 2010-01-13
forum: Server Platforms
---

### Post by mlissner on 2010-01-13
I'm working on a project with a number of friends to build a website. They need to be able to do things like log into the server, edit files,run code, etc.

Is there a scheme people use for this kind of a scenario so that the person has all the permissions they need, but no more?

I'm tempted to make them root, but I don't think I trust them quite that much. It seems like there is probably a better way. 

Any thoughts?

---

### Post by adam814 on 2010-01-13
The best way I could think of would be a custom configuration in /etc/sudoers.  I'd add them all to a group (the name wouldn't really matter), then specify by hand the commands they're allowed to run with sudo.

The line you would need is pretty similar to this one: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo#Granting_Access_To_Specific_Users_To_Specific_Files](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo#Granting_Access_To_Specific_Users_To_Specific_Files)

That way they they can run the commands they need as root, but not the ones they don't and it gets logged to /var/log/auth.log so if anyone abuses it you know who it is.

---

### Post by mlissner on 2010-01-14
That seems like a fairly reasonable approach, though I shudder to think about getting that configuration correct. 

Are there any other ideas out there about more powerful approaches that might work better?

---

### Post by Lars Noodén on 2010-01-14
What do you mean by 'run code' ?  That's the tricky part and sudo is the most powerful solution you can get there.  As to getting that configuration correct, that's a matter of planning, testing and evaluating the tests.

If you want the just to work with the web services, do each have their own [virtual host](http://httpd.apache.org/docs/2.2/vhosts/examples.html)?   Just how much should they be able to edit each other's web sites?  More complex arrangements will best be solved using ACLs, which then allow settings for more than one group per directory to be used.  

Regardless of any of that, use the package openssh-server to provide access to them.  The sftp subsystem is easy to chroot, so that they can only read or write specific directories and sub-directories.

---

### Post by falconindy on 2010-01-14
You can force logins into a chroot with openssh. This means that if you specify the chroot as being /var/www/, then they can never go above that. Doesn't make sense to give them root permissions, either. Look into ACLs.

---

### Post by mlissner on 2010-01-14
Thanks all. I think I'll either do something with the ACLs or just say screw it, and give them root capability. Assuming I have good backups, and that they don't do anything TOO crazy, I think that might work.

---

