---
title: "someone's storing files on my ubuntu virtual box"
date: 2012-04-26
forum: Security
---

### Post by anotherlinuxnewbie on 2012-04-26
I've got an ubuntu 10.04 client virtualbox on a windows 7 host.  I log into my machine today, and get a low storage level warning, and so I click "examine".  Long story short, I find that there's a bunch of files -- movies and games -- stored in /tmp/tmp/.files.  This is a machine at home, and nobody here has the tech savvy to do this.  This machine has no ports exposed on my sonicwall router.

Any help/leads/ideas would be greatly appreciated.

---

### Post by unspawn on 2012-04-26
> **anotherlinuxnewbie said:**
> Long story short, I find that there's a bunch of files -- movies and games -- stored in /tmp/tmp/.files.
- Who owns the directory and when was it last modified ('stat /tmp/tmp/')?
- Which user accounts did access the machine ('sudo lastb; sudo last; sudo lastlog')?
- What processes ('sudo ps axfwww') does the machine run and what 'net-facing services ('sudo netstat -ntulpe') does the machine provide?
- Do any system, firewall or daemon logs show reconnaissance followed by successful requests?
- Anything else "odd" or interesting in any logs? (Try running Logwatch?)

---

### Post by anotherlinuxnewbie on 2012-04-26
Thanks for your reply.

> - Who owns the directory and when was it last modified ('stat /tmp/tmp/')?
According to stat, I do.  When I go into the properties of the files, they also show me as the owner.
> - Which user accounts did access the machine ('sudo lastb; sudo last; sudo lastlog')?
I'm a newb with this stuff, but as far as I can tell, only my id has logged in 
> - What processes ('sudo ps axfwww') does the machine run and what 'net-facing services ('sudo netstat -ntulpe') does the machine provide?
attached as ps_axfwww.txt and netstat.txt
> - Do any system, firewall or daemon logs show reconnaissance followed by successful requests?
don't really know what I'm looking for
> - Anything else "odd" or interesting in any logs? (Try running Logwatch?)
attached as logwatch.txt

Sorry I"m not more help, but like my name says...  If you can instruct me specifically on what to check, I'll do that.

Thanks for your help.

---

### Post by lisati on 2012-04-26
/tmp is usually used for storing temporary files, and is sometimes populated when browsing stuff on the net. It is usually emptied out when you reboot. 

Things to check for include whether the files relate in some way to websites you have been visiting and projects you have been working on.

---

### Post by anotherlinuxnewbie on 2012-04-26
Thanks for your response.

This machine is only used for an app I'm developing.  The only sites I go to are ones that relate to that project, e.g., javascript development.  I'm thinking either chrome or ff have been compromised on that machine.  I can't  think of any other way this could happen, and none of my other machines here have been affected.

---

### Post by anotherlinuxnewbie on 2012-04-26
My bad: in my haste to post, I put the wrong folder up, it's actually /var/tmp/tmp/.files

---

### Post by anotherlinuxnewbie on 2012-04-26
I also found this: /var/tmp/tmp/Driver, which contains something called [iroffer]("http://iroffer.org/"), which is evidently a file-sharing program.  No idea how it got there.   

Interestingly, I just searched the file I attached earlier, ps_axfwww.txt, and it does contain this entry: 

> 2306 ?        S      0:03 ./Driver m.m -b

and this folder, /var/tmp/tmp/Driver, DOES contain an executable called Driver, and a file call m.m, which is of type 'Objective-C source code', according to Nautilus.

I'm thinking I must have installed an IRC client a few years back that had this bundled into it.

---

### Post by unspawn on 2012-04-28
Sorry for the late reply.

> **anotherlinuxnewbie said:**
> According to stat, I do. When I go into the properties of the files, they also show me as the owner.
...meaning the directory was created and files were uploaded through a service that runs under your UID or gives access to your account. 


> **anotherlinuxnewbie said:**
> I'm thinking I must have installed an IRC client a few years back that had this bundled into it.
When asked to run commands like 'stat' returning actual data helps as for instance time stamps tell you when items were last modified, accessed or changed and if that would support your hypothesis or not.


> **anotherlinuxnewbie said:**
> as far as I can tell, only my id has logged in
(* And while I should be concentrating on facts and avoid any signs of bias using Windows as virtualization host means one should factor in the effects of malware which could for instance lead to credentials having been leeched from the virtualization host. Also using Linux as development machine often means it would be an exception if it has been set up with security in mind as developers usually want things quick and hassle-free...)
- When you list logins can you trace each of them back to you actually logging in? 
- Are any of the logins from a location outside of your LAN?
- Do they coincide with service access or logins on the guest or virtualization host? 


> **anotherlinuxnewbie said:**
> attached as logwatch.txt
Unfortunately in my haste to post too I've made some errors: 'ps' should have been run as 'ps axf -opid,ppid,uid,cmd' (as that would also show what user a process runs as), Logwatch as 'logwatch --detail High --service All --range All --archives --numeric --save /path/to/logwatch.log' (because otherwise it will only analyze logs using the default "yesterday" setting) and I forgot to have you run 'sudo lsof -Pwln'. Like you noticed you run "iroffer", a DCC file sharing service, with PID 2306, in the background ("-b") with "m.m" being the configuration file (located in the directory the binary is located in: run 'grep -v ^# m.m|grep .' there to see how it's configured) but it (at the time you listed connections) didn't show up in the network connection table. That's good. What I can also see from the nfo you posted (thanks) is that your Ubuntu machine runs a full GNOME desktop and exposes NTP, Samba, web server, SSH and Vino services. What it doesn't tell, interesting since the directory is "/var/tmp/tmp", is 
- what homebrewn scripts, web-based management panel, forum, web log or other software the web server runs and what if the web server logs show signs of recon, and
- what machines and or services your router (if any) exposes to the 'net. (If you have no idea and you do not have access to a remote machine outside of your LAN you can run nmap or OpenVAS on against your router see one of the free on-line services like nmap-online.com, or more in-depth: securityspace.com, provide.)

Right after running 'lsof' you should make your router stop forwarding traffic to the virtualization host and guest, stop the guests web server, kill the iroffer process (if it restarts automagically check crontab files) and delete the movies and games but not iroffer or related files.

---

### Post by OpSecShellshock on 2012-04-28
> **unspawn said:**
> What I can also see from the nfo you posted (thanks) is that your Ubuntu machine runs a full GNOME desktop and exposes NTP, Samba, web server, SSH and Vino services.

Well, Samba had a highly critical vulnerability patched recently, and seeing Vino listening is never a good sign. SSH is also a good target if the credentials are weak.

Given those listening services and the mysterious appearance of files that shouldn't be there, I would personally take that as an indication that at least the virtual machine has been popped and would wipe it out and rebuild. At this point I would also highly suspect the host system and would wipe and re-install that one as well just for good measure.

---

### Post by unspawn on 2012-04-28
> **OpSecShellshock said:**
> at least the virtual machine has been popped and would wipe it out and rebuild. At this point I would also highly suspect the host system and would wipe and re-install that one as well just for good measure.
That may well be the outcome but I favor performing proper analysis *first*.

---

