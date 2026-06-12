---
title: "Transition from Windows-based network to Ubuntu-based"
date: 2011-02-11
forum: Server Platforms
---

### Post by larynx on 2011-02-11
I am looking to make the switch from a Windows based network to an Ubuntu based one. Currently the network includes a Windows 2003 server which acts as a domain controller and file server, a network shared printer (Canon 2300N) and 7 clients running Windows. Several other Windows-based clients connect remotely via RDP.

I would like to setup a server to act as a domain controller, file server, and (if possible) terminal server. The clients should be authenticated via the server and have access to the files stored on it (via ssh?).

Here are several points that I was wondering about:
[LIST]
[*]All the clients use Outlook, some of the clients run Quickbooks Pro and another program called Tentant File Pro. I was thinking about replacing Outlook with Thunderbird (I contact, calendar, and tasks) and I know that Wine can't run Quickbooks and Tenant File Pro so I may have to use VirtualBox/VMWare because these applications can't be replaced by native Linux versions.
[*]I need an adequate backup solution for the files on the server running as a daily backup.
[*]Should I use webmin to administer the server?
[*]What antivirus / firewall solution should I use for the server and the clients?
[*]How can I allow remote clients the login to the server to be able to run applications (Outlook, Browser, Tenant File Pro, etc.) remotely on the server?
[/LIST]

What is the best solution for this? And what would be the least painful way of making the transition for the users?


I know this is a lot, but any feedback would be appreciated.

Thanks.

---

### Post by garfonzo on 2011-02-11
Well, I don't know the answer to all of these points, but I'll offer what I do know...
> **larynx said:**
> 
[LIST]
[*]I need an adequate backup solution for the files on the server running as a daily backup.
[/LIST]

I would setup rsync to do backups. This is what I use for my personal home server. You can set up a cron job to execute a script and that script would be a simple one line command invoking rsync. It's brilliant because it can be set up to only backup those files that have changed. For every hard drive I have data on, I have an identically sized external drive attached via USB which holds the backup. In the event of a main drive failing, I simply put the external drive inside the box and Bob's your uncle.

> **larynx said:**
> 
[LIST]
[*]Should I use webmin to administer the server?
[/LIST]

That's a tough one. I used Webmin for a bit, but found that I enjoyed administering the server via command line. Webmin does offer an easier way to navigate the plethora of options, but for me, it was too much. I, personally, administer servers via command line only. This is a personal preference. You can install Webmin, try it out, and can it if you don't like it. 

Well, that's all I've got. Hopefully some of the more experienced folks on the forum can help you out with the other questions. Hope this helps!

---

### Post by larynx on 2011-02-13
> I would setup rsync to do backups. This is what I use for my personal home server. You can set up a cron job to execute a script and that script would be a simple one line command invoking rsync. It's brilliant because it can be set up to only backup those files that have changed. For every hard drive I have data on, I have an identically sized external drive attached via USB which holds the backup. In the event of a main drive failing, I simply put the external drive inside the box and Bob's your uncle.

Sounds good, I think I'll go with a rsync running via a cron job.

> That's a tough one. I used Webmin for a bit, but found that I enjoyed administering the server via command line. Webmin does offer an easier way to navigate the plethora of options, but for me, it was too much. I, personally, administer servers via command line only. This is a personal preference. You can install Webmin, try it out, and can it if you don't like it.

I think I'll start with webmin and try to move towards the command line when I'm more comfortable with it.

---

