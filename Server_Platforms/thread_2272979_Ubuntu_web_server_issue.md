---
title: "Ubuntu web server issue"
date: 2015-04-09
forum: Server Platforms
---

### Post by David_Sopczak on 2015-04-09
I am running Ubuntu 14.04 and using it to host Gitlab. The issue that I am having is weird. I have the server connected to a KVM and after I initially login through the KVM I can go to the web page with no problems. I can also SSH once this has been done, but if I end my ssh connection and wait about 10-20 minutes I can no longer access the web page or ssh. I can still ping the IP address of the server from another server and if I go back to the KVM the server is running and I just have to log back in and once this is done everything works again. I have also disabled all acpi functions on the grub and in BIOS. Please help I am racking my brain as to why this is happening. I run 10 other Ubuntu  servers and none of them have this issue...

---

### Post by sandyd on 2015-04-10
*Moved to server platforms*

How did you install Gitlab?

Manual or through Gitlab omnibus?

---

### Post by David_Sopczak on 2015-04-10
I installed it manually.

---

### Post by TheFu on 2015-04-11
Don't know anything about gitlab ... does it put files into your HOME?  Is your HOME encrypted?

---

### Post by David_Sopczak on 2015-04-13
Yes to both.

---

### Post by TheFu on 2015-04-13
> **David_Sopczak said:**
> Yes to both.

That's your answer, probably.  HOME directories are only decrypted when that userid is logged in. That is sorta the point.  So, if any server software needs access to file in a userid's HOME, there is an issue.  The simple fix is to move the git stuff outside your HOME.  You can create a softlink to that new directory from the same place inside your HOME, if you like.  Or use cdpath (shell built-in) to make getting there easy or 20 other solutions.

Clearly the server settings need to point to the new location directly, not going through HOME.

Of course, you could not encrypt the HOME and just encrypt the entire server OS and everything ... then the daemons would have access and the files would still be encrypted when the machine is off.  As a side note, I read last week that whole disk encryption under Linux is faster (noticeably) than HOME directory encryption.

I only use encryption for portable devices - all of them - but I am religious about it and shutting down during travel (even driving to the local cafe), since hibernate and standby are not cryptographically secure to the same degree a completely shutdown system is.

---

### Post by David_Sopczak on 2015-04-13
Have done this and still experiencing the issue?

---

### Post by David_Sopczak on 2015-04-13
Thanks for your help so far.

---

### Post by David_Sopczak on 2015-04-13
okay so update. I was remotely working on the server with SSH and the website went down as did my SSH connection. I went back to the KVM and I was stilled logged in and the server is up. I ran a few commands to check if Gitlab was still running and it was. When I came back to my workstation to see if I could access the site there and SSH I could not... I have restarted Gitlab and got no response from the web page or SSH. I just came back from the server and all I did was look at logs and now I can get to the web page and SSH???

---

### Post by TheFu on 2015-04-13
If there are issues connecting with ssh, you have other problems that need to be solved before worrying about the gitlabs stuff.
Check the log files for anything interesting.  At this point, the issues could be anything - full storage (sectors or inodes), corrupt package install, bad network NIC, plug, cable, switch port, failing PSU, cracked MB, bad RAM, anything.

Oh - and since you are running KVM - are you using the pre-built bridge or did you create your own manually in the /etc/network/interfaces?  I've had issues with the automatic bridges that libvirtd makes, but never had issues with my manually created bridges. Don't know why this is, just that it has been and issue for me and others.

Check the log files.

---

### Post by David_Sopczak on 2015-04-13
Okay thanks.

---

### Post by David_Sopczak on 2015-04-13
So I might have found the issue... I was looking into the config files for Gitlab and I had the server listed as having 8 cores when it only has 4. This created twice the amount of workers. Once I changed this and restarted Gitlab it cut the tasks from 117 to around 58. Hopefully this will fix the issue. If this does I will mark the ticket as closed.

---

### Post by David_Sopczak on 2015-04-13
I created them manually. Thanks for the heads up though.

---

### Post by David_Sopczak on 2015-04-13
Okay it is still down. It was up for about an hour and now I can not SSH or get to the webpage... Also I can not find anything in the logs that shows an error?

---

### Post by TheFu on 2015-04-13
These are all reaches. 

Look for network issues then. Could some other VM/host have grabbed the same IP?
Is it just this VM or are any others on the same VM host impacted?
Swap cables, ports on the server and switch. 

I'd probably reload openssh-server from the repos too - just to be safe. Don't usually see corruption, but an fsck for / might be nice too. 
Is console access impacted or just through the bridge?

---

### Post by David_Sopczak on 2015-04-13
I have 10 other servers and they are running fine. It is just this one after a certain amount of time it will no longer handle requests. You can ping it you just cant access it... I will look into these other fix actions.

---

### Post by David_Sopczak on 2015-04-13
I can access the server through the KVM no problem, just any other way is an issue.

---

### Post by David_Sopczak on 2015-04-14
I have decided that tomorrow I am going to wipe the server and completely re-install Ubuntu 14.04 and see if there was something that was corrupted from the install or persisted from 10.04 desktop that was on there previously.

---

### Post by TheFu on 2015-04-14
Since 10.04, networking/dns/resolvconf has changed, apache2.2 is 2.4 now, and samba has jumped a major release but my samba configs worked under the new version unchanged.

None of those should impact internal ssh connections if the systems can resolve each other, IME.

Last month, I migrated the last 10.04 box here to 14.04. The OS migrations weren't hard, the enterprise app upgrades sucked. ;(

---

### Post by David_Sopczak on 2015-04-14
So.. I might have actually found the issue... I randomly plugged into a wall port that I knew had blazing fast speed 60 down and 60 up. When I checked the IP address it was the same as the gitlab server. I followed the cable from the patch panel and found a small router that was used for a project before I got here. Unfortunately there was no network diagram when I got here and I have had to create one by what I find. I have now changed the IP address of the server and will continue to monitor and check that the site stays active!

---

### Post by TheFu on 2015-04-14
So #15 above helped?  Are you certain that rogue equipment stole the IP?

Do you have monitoring deployed - something like Munin? That will show network issues.

---

### Post by David_Sopczak on 2015-04-14
Yes the site has been up for 7 hours now. The other router was statically assinged. I have a pool of about 14 IP adresses connected to fiber for my servers. I was unaware until today that one had been given to this router. Thanks for your help!

---

### Post by TheFu on 2015-04-14
Please mark thread **solved** ... using the *thread tools* button at the top.

---

