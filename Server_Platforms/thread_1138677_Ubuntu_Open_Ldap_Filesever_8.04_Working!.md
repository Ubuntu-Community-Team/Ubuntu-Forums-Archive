---
title: "Ubuntu Open Ldap Filesever 8.04 Working!"
date: 2009-04-26
forum: Server Platforms
---

### Post by mitanc on 2009-04-26
Hey All,

Wanted to post my experience with using Ubuntu to replace my windows SBS of 5 years.

First off, I love linux, have played with it for many years and have used it extensively at home as a server for videos / music / etc.  This was the first time I actually decided to use it in a production setting, and while it has not been easy, it is satisfying to see it work.  Here's some of the things I got completed and some of the setbacks.  Also, I have some other questions that hopefully someone with more knowledge can help me with.

I basically used Ubuntu 8.04 server to act a primary domain controller and file server for my company.  This replaced a windows SBS server which was running old and becoming annoying to maintain.  I decided to make the switch for the following reasons:

1.  I get all the benefits of Active Directory and Filesharing used with a windows server, but none of the license fees or support fees.  Also when problems do occur, I can use google and the forums for advice rather than having to call a computer "expert".

2.  Backing up on linux is MUCH MUCH easier in terms of snapshots, timed backups using cron, and rysncing over the internet built in.  No need to use propietery software which also have fees and their own problems.

3.  I can always add more features and scale the server better to handle more functions in the future.  While I would need to learn more about doing those things (such as installing a mail server) it would be free to try and implement and I can act like a huge company without spending the big business bucks.  

4.  SSH to do something is so much easier than remote desktoping in using a slow internet connection.

5.  I like software raid, it gives me control over what I see, and while not the easiest thing to setup (in my case because of some minor overlooked issues) it does give me the most information.  Since this is about important data, its a good thing.  

6.  I love tinkering with technology so its a good fit for me.

Now, with all this currently running, I do have some small issues that I would appreciate your feedback on.  

A.  The main thing I need to solve is saving large excel files onto the samba shares.  For some reason the files can occasionally not save or just act super slow.  If anyone has experience please let me know.

B. How do I make the logon script which runs when a domain user logs into the client PC connect to shared network printers?  I got the drives mapped using net use, but printers don't seem to install the same way.  Can the batch file invoke a vbs script that resides in the netlogon directory?

C.  I would like to install a mail server which uses pop to check all the users on the system's mail and route it to the correct person on the internal LAN.  We send a lot of mails internally, and this would eliminate our mailboxes being full on the POP end.  Secondly I can run a virus scan on incoming and outgoing mail, a junk filter, and all mail can be saved on the server in case a client PC fails.  Any recomendations?

D.  Other things I can do with this server that any of you have implemented?  I am thinking squid as a proxy server so I can cache data and control browsing within the office. 

Overall I am happy with the system and if I can get a few of things above answered I would be extatic.  Thanks for taking the time to read thru this.

Mitan

---

