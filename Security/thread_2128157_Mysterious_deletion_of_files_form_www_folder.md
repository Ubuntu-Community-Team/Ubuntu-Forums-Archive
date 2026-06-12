---
title: "Mysterious deletion of files form www folder"
date: 2013-03-22
forum: Security
---

### Post by adillraza on 2013-03-22
Hi,

We are running a small local server for our office. We have LAMP configured, and there are 20 people using locally deployed php application. Few of the users use FTP to access the designated folders to upload files directly to the server.

Yesterday, the system suddenly stopped, and the application page was not accessible at the clients computers, instead, the application directory was listed on the brower when someone tried to access the application.

When I check through FTP client, I found that almost all files from the www/application folder were deleted (code + images/audio/video files). There were also some other foldres in www, which were also deleted. We had backup to restore the lost files, so that's done, but I really wanted to know what happend?

We checked all the logs, FTP, Apache, System etc, but did not find any deletion log. There were normal deletion log enteries in the FTP log for time before this big deletion has happend. So appearently, the FTP logs does log the deletion activity, but this particular (almost 4,000+ files) deletion is not logged anywhere.

We have firewall, and all security in place.

Plz help us how to trace what has happend. We are using Ubuntu server 2.6.38.

Thanks,
Adil

---

### Post by TheFu on 2013-03-22
Can't tell from the description, but deleted files don't show up in any logs if performed locally or using a .... er ... compromised php script.

I've be looking for unauthorized accesses from all addresses - local and remote.

Are the logs stored on the same machine, or are they pushed immediately to a log server?  Local logs can be modified by an attacker to remove all trace of their activities.

A kernel version is not a version of Ubuntu. Which version is shown in /etc/lsb_release? Is it currently supported and fully patched?

A firewall is good, but not enough. Running a multi-user OS in a secure way is much more complex. Allowing multiple users to read-write to the same directory can be a risk.
FTP is not secure. If the company cared about security, then FTP would be against policy and not even loaded on servers.

---

### Post by mr-woof on 2013-03-23
I agree with theflu, id start to look for unauthorized accesses, files dont delete themselves.

Can you access the website on the internet? do you have ssh enabled and can you access that from outside?

have a look in /var/log/auth.log

---

