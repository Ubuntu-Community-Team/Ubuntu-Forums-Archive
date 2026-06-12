---
title: "Trying to setup an Outbound SMTP mail server with &amp; using Multiple IP Addresses"
date: 2010-03-15
forum: Server Platforms
---

### Post by lcsfsr1 on 2010-03-15
Hello,
This is the current setup that we have:
We have approx 20 clients who pay us to send out a type of e-mail called an E-Blast to their customers.  We currently are using 5 Microsoft Windows Virtual Servers to do this.  The problem is that those machines are starting to break down.  There are times that it will take Microsoft Windows approx 9-10 hours to complete 1 job.  This is way too long.  We want to move away from Microsoft Windows for this particular type of job as it seems there are more customers who are wanting to use this type of advertising.
It seems that using a Linux Server "Command Line or Shell" environment would be the best way to go as there is no GUI like Windows.  Since there is just text...that is something that would/should process very, very quickly.

I am in the process of setting up a new SMTP outbound mail server.  This is the current software & configuration (what is installed on this new machine):

_Ubuntu_ Server 9.04
_Samba_ version 3.3.2 - Installed during/at the end of the initial Ubuntu OS installation
_Postfix_ Mail Server version 2.5.5 - Installed during/at the end of the initial Ubuntu OS installation
_Webmin_ Version 1.510 
_Open SSH_ version 5.1 
_ClamAV_ version - 0.95.3 

All of the customer data (Names, E-Mail Addresses, etc that these e-mails are going to) are currently loaded in a Microsoft SQL Database.

My machine that I am using is plugged into the DMZ.  I have 1 ip address for the 1 network card.  I have also added/bound 4 more ip addresses to that network card.

I have configured Postfix for Multiple IP Addresses.

I can, from the command line, send successful test e-mails and receive them in my  personal account.

As far as I know everything is setup correctly.  I can and will post requested information so that it can be verified that everything is setup correctly.

Here are a couple of my questions:
  
[LIST]
[*]Can someone please help me      ensure that I have my Network / Interfaces file and my Postfix's      Master.cf/Main.cf files setup correctly???
[*]How can I setup this server      to be an Outbound SMTP server and get it to use all 5 of the IP Addresses      to send these e-mails quickly???
[*]What can I use to check and      ensure that this server is in fact sending out emails on all 5 IP      Addresses (I heard that there is a program named "Postal" that      may help in determing this).
[/LIST]
  
Thank you,

Bobby Howerton

---

### Post by KB1JWQ on 2010-03-15
What's the benefit you're looking to gain by using all five IPs simultaneously?  You're going to be I/O or bandwidth constrained; using multiple IP addresses isn't going to do anything to address that.

-- KB1JWQ

---

### Post by lcsfsr1 on 2010-03-16
Well I just thought that if you were sending out an email to a group of   recipients of say 500 and it was all going over 1 ip address then it would be a little slower. But if you split the 500 over 2 ip addresses (250 each) then it would send the email twice as fast because because they are both being sent   simultaneously.  I hope that I am not confusing you.

I am just trying to tweak my servers to get the most out of them.

Thanks for your help!!!

Bobby

---

### Post by KB1JWQ on 2010-03-16
Hi, Bobby.

I understand where you're coming from, but Postfix uses multiple delivery processes simultaneously.  I'd keep going with one IP, and when you eventually hit a wall as far as "can't send any more mail" it'll be time to re-evaluate either the hardware, bandwidth, or tweak your postfix config.  However, this isn't likely to happen until you're sending out close to a million messages a day, at which point using another tool may be the better solution all around.

---

