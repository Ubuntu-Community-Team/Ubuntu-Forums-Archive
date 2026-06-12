---
title: "Ubuntu 11.10 server stops working"
date: 2012-04-25
forum: Server Platforms
---

### Post by Garinil on 2012-04-25
Greetings Community,

Currently, I am using the machine as a LAMP and vsftpd. I believe when I installed the server, I also installed the mail server and DNS, but have not used them. 

I have two issues. I would like to uninstall the mail and DNS software, and then figure out why, after about 2-3 days of the server being online, that it goes offline. The machine, is still on physically, but when I attempt to SSH or to reach the web address connected to the machine, I can not. It is like the OS freezes, thought the physical machine is still powered on.

It is Ubuntu 11.10 server edition.
The machine is an eMachine EL1200 with 3GB ram, recently upgraded from 1GB, AMD Athlon processor.

Please, I am very new to linux OS, and I am very interested in learning more.

Regards,
Garinil

---

### Post by d4m1r on 2012-04-25
You are going to have to provide a better description of the problem. Are you still able to ping the IP? Are you running the server at home and you are trying to connect to it from another PC?

More info please.

---

### Post by slugg007 on 2012-04-25
Seems like you can do a few things.

Is mail or DNS installed?

Run: dpkg-query --list | less
This shows you the list of installed packages.

Run this from your server:
% nslookup google.com YOUR_SERVER
;; connection timed out; no servers could be reached

This shows that even DNS is installed it is not working


Run this from your server:
% telnet YOUR_SERVER 25
Trying <your servers IP>...  (wait a few minutes)
^C

This shows that your server is not responding on port 25 (the typical email port)


If mail and DNS are not responding, do you really care if the packages have been installed?

As far as not being able to reach your server via ssh or something, get console access. Is sshd running? Is your web app running? Can you ssh from YOUR_SERVER to YOUR_SERVER? What happens when you start sshd? Does this give you ssh access from a different machine or from YOUR_SERVER?

Look at the files in /var/log. These usually give you a clue. Do this from the console. the dmesg is often a good place to start.

There must be many ways to debug your issues and I suppose that your problems may not reside in YOUR SERVER but this seems to be unlikely if things work again after a reboot. 

Not to be a wise *** or anything, google helps and so do the man pages. Then there are the ubuntu support pages too.

Hope I have helped in some way.

While you

---

### Post by Garinil on 2012-04-26
> **d4m1r said:**
> You are going to have to provide a better description of the problem. Are you still able to ping the IP? Are you running the server at home and you are trying to connect to it from another PC?

More info please.
I will atempt to ping the IP once the web site and ssh go down again, but as explained it only does it every few days.
> **slugg007 said:**
> Seems like you can do a few things.

Is mail or DNS installed?

Run: dpkg-query --list | less
This shows you the list of installed packages.

Run this from your server:
% nslookup google.com YOUR_SERVER
;; connection timed out; no servers could be reached

This shows that even DNS is installed it is not working


Run this from your server:
% telnet YOUR_SERVER 25
Trying <your servers IP>...  (wait a few minutes)
^C

This shows that your server is not responding on port 25 (the typical email port)


If mail and DNS are not responding, do you really care if the packages have been installed?

As far as not being able to reach your server via ssh or something, get console access. Is sshd running? Is your web app running? Can you ssh from YOUR_SERVER to YOUR_SERVER? What happens when you start sshd? Does this give you ssh access from a different machine or from YOUR_SERVER?

Look at the files in /var/log. These usually give you a clue. Do this from the console. the dmesg is often a good place to start.

There must be many ways to debug your issues and I suppose that your problems may not reside in YOUR SERVER but this seems to be unlikely if things work again after a reboot. 

Not to be a wise *** or anything, google helps and so do the man pages. Then there are the ubuntu support pages too.

Hope I have helped in some way.

While you

I have tried google for uninstalls as well as the crash problem. I don't know the default package names for the DNS or mail server was my problem. 

Now about the crashes, let me be a bit more descriptive.. The server console itself is powered on, but non-responding to input. The screen stays blank with the monitor in sleep. 

Thanks, and I will still atempt both of your suggestions. As I said, I am very new and eager to learn!

Regards,
Garinil

---

### Post by slugg007 on 2012-04-26
> **Garinil said:**
> I will atempt to ping the IP once the web site and ssh go down again, but as explained it only does it every few days.


I have tried google for uninstalls as well as the crash problem. I don't know the default package names for the DNS or mail server was my problem. 

Now about the crashes, let me be a bit more descriptive.. The server console itself is powered on, but non-responding to input. The screen stays blank with the monitor in sleep. 

Thanks, and I will still atempt both of your suggestions. As I said, I am very new and eager to learn!

Regards,
Garinil

I think your server has shutdown or crashed if a directly attached monitor and keyboard get no response. You will have to start reading the files in /var/log and see if you can get a clue.

Can you reinstall ubuntu from scratch?

If you can not rebuild your server or find a clue in /var/log, you are in a tough spot.

---

### Post by Garinil on 2012-05-02
I re-installed ubuntu 11.10 server edition, put only VSFTPD, OpenSSH, and LAMP. 

The server is again not responding to input of any kind, the monitor stays in the "sleeping" state, yet the machine is powered on.

Regards,
Garinil

---

### Post by slugg007 on 2012-05-04
> **Garinil said:**
> I re-installed ubuntu 11.10 server edition, put only VSFTPD, OpenSSH, and LAMP. 

The server is again not responding to input of any kind, the monitor stays in the "sleeping" state, yet the machine is powered on.

Regards,
Garinil

I suppose I missed the sleep state in your earlier posts. There seems to be several ways to make ubuntu sleep - most seem to be related to using the GUI. I normally only use the command line interface for servers and have never had a sleep state problem. I never choose a sleep state when logging off a console. I just log out using the [COLOR=Teal]exit[/COLOR] command.

Look at these threads:

[http://ubuntuforums.org/showthread.php?t=1969314&highlight=server+sleep](http://ubuntuforums.org/showthread.php?t=1969314&highlight=server+sleep)

[http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line](http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line)

[http://askubuntu.com/questions/78907/how-can-i-hibernate-suspend-from-the-command-line-and-do-so-at-a-specific-time-a](http://askubuntu.com/questions/78907/how-can-i-hibernate-suspend-from-the-command-line-and-do-so-at-a-specific-time-a)

[http://ubuntuforums.org/showthread.php?t=1895084&highlight=GUI+sleep+action](http://ubuntuforums.org/showthread.php?t=1895084&highlight=GUI+sleep+action)

Maybe you will find something helpful in one of these. I can not help you much more other than having you look at these threads and encouraging  you to browser search for putting ubuntu or linux to sleep.

Good luck. Post your solution here once you have solved your problem. I am interested in the solution. OR maybe someone else can help you more than I have.

---

### Post by Garinil on 2012-05-04
It crashed again today. Website and SSH became unavailable. The box is powered on, as I can see the light around the power button. Yet, when I use the command line(as this is the server edition, it has NO GUI) the monitor remains on standby as if there is no input from the machine itself. I then have to hold the power button to turn off, and then push again to turn it on. The server has 3gb of ram, which is under the minimum of which the motherboard can handle. 

None of those links I found helpful, though I continue my search for a solution through multiple avenues.

---

### Post by onal on 2012-11-28
Did you every find the solution?  I am having the same issue.

---

### Post by Garinil on 2012-11-28
Greetings,

I just did a new download of the newest server edition and fresh installed. I have had no further problems.

Regards, 
Garinil

Edit- Though, I am stopped using vsftpd, and started using SSH as a file transfer protocol.

---

