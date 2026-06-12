---
title: "Am I Secure?"
date: 2008-04-18
forum: Security Discussions
---

### Post by Kwag on 2008-04-18
I am running Ubuntu Edgy Eft -- no anti-virus running, no additional firewall running other than the fact that Ubuntu closes all ports by default (I didn't change that).  I did edit my hosts (sp?) file and put something similar to the following: 

hosts.deny = all

(I don't remember the precise syntax of the configuration).  Also, I do not have ssh installed.

So, that seems pretty secure.  However, I virtualize Windows XP SP 2 on this machine using Virtual Box.  I have no anti-virus or firewall installed or running on that guess OS.  I have a folder on my Linux /home partition that I share with Windows.  Everything that I am interested in keeping from my work on windows gets saved to this shared folder.  In this way, I only have to backup my ext3 /home partition.  I don't have to worry about different file system types, backing up the virtual machine, etc.  (although occasionally I make snapshots and backup the virtualized Windows XP file so i can restore it if I have to).  

The point is, if my Windows box gets infected ... I am not overly concerned, since all the files I am interested in from that OS are stored on the shared folder within /home.  

My question is:  Is this safe?  Safe meaning ... can I depend on the files on my shared /home folder being untouched from any viruses that could enter the virtualized windows XP OS since these files are physically stored on a Linux partition ... or are they still at risk?  How safe are they?

Thanks.

---

### Post by pseudo-random on 2008-04-18
For the large part, most malware won't 'know' its on a virtual PC.
That said next generation malware and rootkits like blue pill
[http://en.wikipedia.org/wiki/Blue_Pill_(malware)]("http://en.wikipedia.org/wiki/Blue_Pill_(malware)")
Employ virtualisation to evil effect and can recognize if they're running 'virtually' themselves.
Though I wouldn't worry about them they're all experimental / proof of concept at the moment...
Bottom line is you're already safer than 99% of computer users out there. Especially so since you've got the right idea there about identifying important data and protecting it.

---

### Post by HermanAB on 2008-04-18
Hmm, hosts.deny is a configuration file for tcpwrappers.  Tcpwrappers was designed to work with xinetd and xinetd is deprecated.  The result is that tcpwrappers now only works with programs that has libwrap explicitly compiled in.  Soooo, tcpwrappers doesn't do much anymore.

You are correct that Ubuntu will work fine with no firewall since you know which services you are running.  However, windows in the VM has many poorly documented listeners and is as secure as a Swiss Cheese.  Therefore, you should install Firestarter (however you can disable the 'interactive' part since it doesn't do anything useful).  

Cheers,

Herman

---

