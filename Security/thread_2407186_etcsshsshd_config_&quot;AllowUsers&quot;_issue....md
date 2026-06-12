---
title: "/etc/ssh/sshd_config &quot;AllowUsers&quot; issue..."
date: 2018-11-30
forum: Security
---

### Post by mglau72 on 2018-11-30
I apologize if this is submitted twice.  I got a message to register when I wrote it up the first time.  I was logged in…
Who’s up for a good laugh?  (I’m not laughing.. but you might)
You’ll read this and think I’m a noob.  Nope.  Been doing this a while.  However- I am really tired and was really tired when I made this idiotic mistake.
I have a virtual Ubuntu Server running on VMWare.  I use Putty to access the server. I’ve been working on this server for about 18 months.  Never an issue.  This is for a client.  They are currently migrating to the Azure.  They requested that I setup 2 servers so that they can be logged into, directly, as root.   I currently have it setup to login as a regular user and then use sudo for root level commands.  They said that the Azure migration can’t do that. 
These are the things I did;

[LIST=1]
[*]Changed the password of root with; sudo passwd root.  I tested it by running sudo –u and was prompted for the root password.  I put in the newly created password and it worked.  I then closed my putty session, opened a new one, and tried to login as root.  “Access Denied.”
[/LIST]
 

[LIST=1]
[*]Started digging through the forums and found that one can go to /etc/ssh and edit the sshd_config file.  Add PermitRootLogin yes  - at the bottom of the file, then save, then restarted the ssh service.   I closed my putty session, opened a new one “Access Denied.”
[/LIST]
 

[LIST=1]
[*]I started digging some more and came across a suggestion… To edit the sshd_config file and add AllowUsers root.  I did this.  The thought that zipped through my mind was “oh- this will allow root to login.”  I didn’t know at that moment that it is actually a security method of just allowing the specified user access to login.  I then closed the putty session, opened a new one.  I tried to login as root and “Access Denied.”  So, I decided to keep working on it and tried to login in as my normal user… Access Denied.  Like a Wrecking ball, it hit me- what I had done- what “AllowUsers” really means.
[/LIST]
 
The Vsphere access is all messed up.I’m trying to gain access to it.I’m not sure if it will even allow me to login via console?It would be swell if they had a snapshot, but I doubt it.
 
If I go to recovery mode >> choose root >> and then get to a shell prompt, will I again be denied access?Because if I could get to the command line, I could easily edit the SSHD_CONFIG file and everything would be good.
 
Right now?The sky is falling.Any suggestions would be GREATLY appreciated.

---

### Post by TheFu on 2018-12-01
Console will let you in.
Professional IT support requires remote console capabilities.

I've locked myself out of sudoers before .... 6 times in a row. It never crossed my mind that the changes I was making to the sudoers wasn't correct and had to hack into the machine over and over and over.

Knowing how to hack into any Linux machine is a basic admin skill.  When you take the RHEL cert test, that is step one to gain access to the VM you'll be working inside.

---

### Post by mglau72 on 2018-12-01
Hey- thanks for the reply.  One of the issues with this client is that their VMware environment is really messed up. that's part of our project- to rebuild it in Azure, but another guy on our team is taking care of that part.  I'll post  what happens when i finally am given access to vSphere and can reboot the server.  I'm not a fan of RHEL, but i think that has more to do with me not getting to work with it as much.  Everyone seems to have Ubuntu.  I'd like to take the Cloud\Linux Microsoft Exam. Anyway- thanks again.  that does settle down my nerve a bit.

---

### Post by TheFu on 2018-12-01
In corporate USA, RHEL is used much more than Debian/Ubuntu.  Ubuntu is used a bunch by developers deploying to the cloud and outside the USA.  It really just depends on the industry that you work inside which distros are primarily used.

Personally, I prefer Ubuntu Server, but that is my bias.  Whatever the client wants, assuming it isn't Azure or VMware or Windows, I'm willing to do it.   Or illegal, of course. Won't do anything illegal.

---

### Post by mglau72 on 2018-12-01
My experience with Red Hat has been that it seems that it is structured a very specific way and you need to follow very specific directions to make things work.  I prefer Ubuntu as well- as it feels like the wild west.

My attempted access into vCenter is failing.  Back in the 90's, when there were still cars that had push down locks, I accidentally locked my door as I got out.  My car running, in the winter, with my only key locked inside.... That's what this situation feels like- except that back in the 90's, i could just laugh it off

---

### Post by mglau72 on 2018-12-03
I had to have the Windows Admin get vSphere to work properly, simply logged in as root and then cleared out all my entries in /etc/ssh/sshd_config, restarted SSH and it worked... all that worry...

---

### Post by mglau72 on 2018-12-03
Resolved

---

### Post by TheFu on 2018-12-03
See the "Thread Tools" button near the top?  Please mark closed to help the community.

---

