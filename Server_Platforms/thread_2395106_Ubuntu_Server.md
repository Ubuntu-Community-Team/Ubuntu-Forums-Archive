---
title: "Ubuntu Server"
date: 2018-06-26
forum: Server Platforms
---

### Post by kanisrj on 2018-06-26
To say I am very green would be an understatement, but I am a senior willing to learn. I got frustrated with trying to set up a server using Windows Server 2016, I don't have access to the simple questions holding me back from setting up a server.

I installed Ubuntu, and it seems pretty much straight forward, I used the virtual machine manager to create a website using "Ubuntu Server 18.04 LTS" but I have questions regarding space. I will be hosting my photo website on it, do I need to add that space during the initial setup, space for the website files or is that not an issue and it can be place elsewhere on the hard drive? My c: drive is 250gb so room is not a problem.

Thanks is advance to anyone who can explain this to a newbie.
RK

---

### Post by TheFu on 2018-06-26
Welcome to the forums.

Running a secure server when you are new to Linux is very hard. There are many subtle aspects to securing a Unix server that point-n-click doesn't teach.

Like with any server, adding more storage later is possible, but it is easiest if added up front, especially for new-to-Unix people.  

Adding storage to a Unix system isn't like it is for desktop Windows. There are multiple manual steps. Many people get confused  when doing things with virtual machines.  The VMs provide virtual hardware to the VM OS.  That means to add more storage, you have to have the VM add another virtual HDD or increase the size of the existing one. Then inside the OS, you have to extend the partitions, resize the LVM, extend the file systems and mount the storage as desired.   Then you'll need to relocate any existing files to the new storage too, while ensuring those files aren't actively used.

 That's much different than on desktop Windows.

So, the best thing you can do is learn how to manage a server, gain some expertise, learn to secure which ever webserver you choose, and ensure whatever webapp you happen to use is constantly, maybe daily, patched to prevent becoming one of the millions of compromised sites on the internet right now.

For security, visit the Security sub-forum here and read all the sticky threads.  Anything that isn't understood needs more research because of the subtle nature of Unix security.  Overall, the rules are simple and apply to every OS:
* don't run any services you don't need.
* don't allow connections from places you don't need to support.
* don't allow brute force attacks after 3-5 attempts.
* stay patched, constantly for internet-facing systems.
* have daily, automatic, networked, backups that "pull" the data, never "push" and never using shared network storage.
* only allow ssh for management uses, but lock down that access to only the IPs you require and only use key-based authentication.

And lastly, when asking questions here, please post the output from commands run, not an interpretation of the output.  We are very familiar with the commands and prefer to see that here than reading long paragraphs which might not actually be factual.

This stuff can be very fun, if you enjoy it. But the learning curve is extremely steep.  Get an Admin Guide that concentrates on using the shell (never a GUI) and work your way through it.  In about 6 months of daily use, you'll be a noob no more and will be entering the "beginner" level.

---

### Post by cariboo on 2018-06-29
Moved to server platforms.

---

