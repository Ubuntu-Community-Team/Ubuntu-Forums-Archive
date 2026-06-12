---
title: "Perfect setup"
date: 2006-10-27
forum: Server Platforms
---

### Post by Jeeevs2001 on 2006-10-27
OK, Where to start. 

I currently have a Ubuntu server set up at home as a file server, however due to 'messing about' with it when I first set it up it has lots (well a few) open ports and I am not sure what all of these are for. As a result of this I am looking at doing a clean install and wanted some advice on the different packages I should use to set up my 'perfect' server. 

Currently I use Webmin to help put a ‘friendly face’ on the server but am happy to use the command line if it is necessary. 

I want to be able to: 

1) Share files across the network. 

2) Check my email on this 'server'. To explain this I would like to be able to remote in (probably with ssh) to my server (from the internet) and be able to check my email, probably with Pine or Mutt (which ever is easiest!). 

3) Easily enable 'ad hoc' file sharing. To explain this, if a mate pops round and wants to download a file from my 'server' I would like to be able to quickly set up a 'guest' account so he could log in and copy the file from a network drive (this would only be on the local network not across the internet) then I would like to 'disable' the access - for security. 

4) have FTP access as a backup to the file sever / 'ad hoc' file sharing. 

5) The 'server' currently has 2 internal and 1 external hard disk. I am looking to set up an additional external hard disk to serve as a 'backup' for all data. 

6 ) I currently have a MacBook laptop which would need to be able to ssh in and mount all the drives as shared (for file sharing). My partner has, or will have, a windows laptop which will need to be able to do the same, possible with our own network drive space. 

7) I would also like some advice on setting up file permissions as I would like to have areas for each of the users (i.e. privet areas, not accessible to the other user), shared areas for both users (i.e. to store shared music / data) and a 'public' area (for ad hoc file sharing (point 3). Currently the process of assigning and changing permissions seams overly complicated. 

8 ) If possible I would like the server to email me with any problems and to run a nightly backup of all data onto the 'new' external drive, and let me know of any problems. 

9) Make the server as secure as possible. I am currently trying to find an ISP who will give me a fixed IP so I can ssh in remotely but would like advice on the best way of making it as secure as possible. 

This sounds like allot when I write it all out but I have been using the current setup for a while and would like to get it perfected. 

Any help / advice would be great! 

Jeeves

---

### Post by MJN on 2006-10-27
> **Jeeevs2001 said:**
> OK, Where to start. 
 
You're telling me!
 
I'll have to quote each of your queries or else we'll soon get lost. Here's my 2p worth (and arguably overpriced at that) however if I can make one suggestion, it's don't whatever you do try and achieve this in one go! Let it grow! You can be rest assured that your requirements will also benefit from the inevitable refinements that building is slowly will bring!
 
> I currently have a Ubuntu server set up at home as a file server, however due to 'messing about' with it when I first set it up it has lots (well a few) open ports and I am not sure what all of these are for. As a result of this I am looking at doing a clean install and wanted some advice on the different packages I should use to set up my 'perfect' server. 
 
No such thing as 'perfect' - too subjective. But I agree let's at least aim as close as possible...! ;)
 
> Currently I use Webmin to help put a ‘friendly face’ on the server but am happy to use the command line if it is necessary. 
 
Very good idea. Start at the grass roots level and you won't look back. If you know how the engine works you'll be in a better position to know why it won't when it doesn't!
 
I want to be able to: 
 
> 1) Share files across the network. 
 
**Samba** is the obvious answer here. Get reading the HowTo's and forum discussions...
 
> 2) Check my email on this 'server'. To explain this I would like to be able to remote in (probably with ssh) to my server (from the internet) and be able to check my email, probably with Pine or Mutt (which ever is easiest!). 
 
Are you planning on running a mail server? I'm guessing you are. In which case, my recommendation is **Postfix** for the SMTP server, and **Dovecot** for an IMAP server. An IMAP server will allow you seamless, synchronised, acccess from multiple places/clients with a single view of your mailboxes. To make matters easier, particularly when 'out and about' on the Internet I would suggest a webmai solution too (I recommend **Squirrelmail**, and you'll of course need a web server - **Apache**) as you will not be able to rely upon having SSH access from anywhere and everywhere whereas given web access is ubiqitous it's a safe bet. Still use Pine/Mutt if you want - indeed use whatever client is handy at the time - that's the beauty of IMAP - your mailboxes are held server side so any client can be used without having different views/messages on each.
 
> 3) Easily enable 'ad hoc' file sharing. To explain this, if a mate pops round and wants to download a file from my 'server' I would like to be able to quickly set up a 'guest' account so he could log in and copy the file from a network drive (this would only be on the local network not across the internet) then I would like to 'disable' the access - for security
 
Samba can happily allow guest access however you probably need to refine your requirement here a bit. If your mate is after a file from, say, your home directory then no amount of acceptable 'guest' access will be sufficient (short of giving him your password). Hence, you may be better off having a 'guest area' in which these files can be dropped into as and when required - with full access to anyone on your LAN to it.
 
Many ways to skin this cat really so start out with simple file sharing and progress from there.
 
> 4) have FTP access as a backup to the file sever / 'ad hoc' file sharing. 
 
I wouldn't recommend FTP - it's all too easy to be insecure and can be a right pain in the rear through firewalls (certainly doable but little to be gained from perservering). Given you'll be having SSH available stick to that - run whatever you need over it. **SCP** (amongst many other tools - **WinSCP** on Windows is very good) can copy files over it and for a more robust backup solution, I'd recommend **Rsync** (running over SSH) for safe/fast/secure/incremental backups (local or over the Internet - see next point).
 
> 5) The 'server' currently has 2 internal and 1 external hard disk. I am looking to set up an additional external hard disk to serve as a 'backup' for all data.
 
Good idea. Even better, as mentioned above, consider backing up your data to a trusted partner over the Internet - to put it bluntly if your house burns down you'll still have your cherished digital photos etc. I back my machine up to my brother PC (in a different country but that's down to his choice of living location as opposed to a backup requirement!) using rsync - it can start/stop as and when required. A perfect-as-possible solution in my book.
 
> 6 ) I currently have a MacBook laptop which would need to be able to ssh in and mount all the drives as shared (for file sharing). My partner has, or will have, a windows laptop which will need to be able to do the same, possible with our own network drive space.
 
No experience with Macs but do have a smattering of Windows machines on my LAN which are more than happy doing this.
 
> 7) I would also like some advice on setting up file permissions as I would like to have areas for each of the users (i.e. privet areas, not accessible to the other user), shared areas for both users (i.e. to store shared music / data) and a 'public' area (for ad hoc file sharing (point 3). Currently the process of assigning and changing permissions seams overly complicated.
 
If you get this far you'll already be well on your way to managing permissions with ease... plenty of guidance available however I'm not sure it should be started here. Suffice to say, it's all doable.
 
> 8 ) If possible I would like the server to email me with any problems and to run a nightly backup of all data onto the 'new' external drive, and let me know of any problems. 
 
I run **Logwatch** every night which parses the logs and, thanks to its built-in log-recognition scripts, can extract relevant info and format it into a more concise and digestable format. All the key events reported, stats provided etc and all e-mailed to me ready for a quick morning perusal.
 
> 9) Make the server as secure as possible. I am currently trying to find an ISP who will give me a fixed IP so I can ssh in remotely but would like advice on the best way of making it as secure as possible. 
 
Can you elaborate on your reasoning behind why you want a static IP. I have a dynamic one which is chased by a dynamic-IP compatible DNS provider (**Zoneedit** in this case) hence I access my machine(s) by name - if the IP address changes the name still stays the same so I need not know about it. The security side of things is a discussion-and-a-half by itself but suffice to say SSH is very secure out-of-the-box and so as long as your using decent passwords and don't fiddle with what you don't understand then I can't see you having a problem. You might prefer 'additional' security from disallowing password access but instead using public/private keys but you've got enough to learn about already so leave that one for the next rainy day!
 
> This sounds like allot when I write it all out but I have been using the current setup for a while and would like to get it perfected. 
 
It is a hell of a lot, and you're not going to get anywhere by asking for a discussion on every topic on the one thread! Split it up and start small.
 
I'm sure someone will point you to a single HowTo that covers a million-and-one packages to produce a single all-dancing machine setup. Follow it and it'll work, but you won't have learnt anything along the way and you can at best hope to only achieve what they considered to be 'perfect' - unless you wrote the HowTo then it's unlikely to fit yours.
 
> Any help / advice would be great! 
 
Jeeves
 
How about 'Rome wasn't built in a day'. ;) Or, perhaps more helpfully, don't ask for too much from one thread - it ain't going to happen! :)
 
Mathew

---

### Post by twistedtwig on 2006-10-27
Hey Mathew,

could i ask why the ftp could be so insecure.. completely new to ftp and thinking about setting one up for the just in case situation.

cheers

p.s... cnames still working and all DANDY setting up another today :) :) :)

Twiggy

---

### Post by MJN on 2006-10-27
It's simply that 'standard' FTP sends usernames/passwords in clear text hence could be sniffable. Indeed, the files themselves are transferred as-is which might be equally undesirable.
 
Not that I've got anything against FTP - it's perfect in the right environment. Sending files and backing up machine over the Internet however is not one such environment!
 
If you've already got SSH available, which many have, then running something over that is infinitely preferable. I personally use SCP (with the WinSCP client from Windows machines) - see [http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy) for a nice overview. If SSH works then you'll find SCP (or even SFTP) will also work without any additional configuration.
 
Mathew

---

### Post by twistedtwig on 2006-10-27
ahhhhhhhhhhhhhhhhhhhhhhhhh ic wicked thx, knew that things were sent as plain text just hadnt got as far in the tutorial readings as doing it over ssh (which is up and running :) )

thx again mate

---

### Post by Iowan on 2006-10-27
> **twistedtwig said:**
> could i ask why the ftp could be so insecure.. completely new to ftp and thinking about setting one up for the just in case situation.
No encryption - passwords sent in plain text.
SSH is worth the extra nickel (IMHO).


AWWW... do I type THAT slow???

---

### Post by Jeeevs2001 on 2006-10-27
Hi, 
thanks for your reply Mathew, 

"I run Logwatch every night which parses the logs and, thanks to its built-in log-recognition scripts, can extract relevant info and format it into a more concise and digestable format. All the key events reported, stats provided etc and all e-mailed to me ready for a quick morning perusal."
 
I have tried installing logwatch and it emails the 'admin' account of the server  but could you elaborate on how to make it 1) a bit more specific on the info it pulls out and 2) email it to a real email address once a day, rather than to the admin account. 

I have tried the logwatch website but it seems to be down? 

Thanks again 

Jeeves

---

### Post by MJN on 2006-10-28
My logwatch scripts are as per the default, and find it's displaying sufficient detail to my liking. Was there anything in particular that you want it to pick up on that it isn't currently?

On a 'standard day' I'm getting the following:

Cron: Summary of all jobs run (and how often)
Apache: Amount of data sent (and what types), known hack attempts, errors and number of robot crawls
Kernel: Kernel messages
Pam: Relevent security events/info
Postfix: Relay attempts, numbers of messages failing the spamtrap (RBLs), messages to forbidden accounts
SMARTD: Details of any SMART data changes on my hard disks
SSHD: SSH connections, attempted connections stopped by Denyhosts
Sudo: Summary of sudo executions
Disk: Snapshot of the state and space of the hard disks

This is with the **Range** set to 'yesterday' and **Detail **set to 'Med' in logwatch.conf. You could always increase the latter if the above is insufficient (although it might not change some parts of the report) however it's plenty for me. I'm reading this every day so don't want it to take any longer than 15/20 seconds for me to check for anything amiss - the server is meant to be working for me, not the other way around!

With regards to the e-mailing of the report, just set the **Mailto** directive in /etc/logwatch/conf/logwatch.conf to be an external address.

Mathew

---

### Post by Jeeevs2001 on 2006-10-28
Mathew, 

I can not find this file: 

"With regards to the e-mailing of the report, just set the Mailto directive in **/etc/logwatch/conf/logwatch.conf** to be an external address."

If I look in /etc/logwatch/conf/ the folder is empty. 

However I have managed to get it to email an external address using the Logwatch --mailto comand. 

I would like to be able to configure which of the system logs I get reports from. I get: 

 --------------------- Cron Begin ------------------------ 

Some usefull stuff

--------------------- Kernel Begin ------------------------

This is a massive list of things, most of which I don't understand, is this stuff important / relevent and if not how do I remove it from the report? 

 --------------------- Named Begin ------------------------ 

Again, short summary and usefull

 --------------------- pam_unix Begin ------------------------ 

This bit I am slightly confused on, it looks like a report of any opened sessions and by which user. Useful to see who is accessing the system?

-------------------- postfix Begin ------------------------ 

Usefull

--------------------- samba Begin ------------------------ 

Usefull list of users to access the samba share

 --------------------- Connections (secure-log) Begin ------------------------ 

Again I am not really sure what this is telling me?

--------------------- SSHD Begin ------------------------ 

Usefull list of log-ins or attempted log-ins

--------------------- Sudo (secure-log) Begin ------------------------

Commands issued by Sudo? If yes very useful. 

 --------------------- Disk Space Begin ------------------------ 

Usefull summary of disk space. 

------

Most of this seems useful (assuming I am reading it right!) except the ---Kernel--- bit. Can I safely stop it looking at this log and not loose any important info? 

Jeeves

---

### Post by MJN on 2006-10-28
Are you using Dapper? If so, that might be why logwatch.conf is missing - I'm using Breezy and so I can only assume our packages are different. Try **locate logwatch.conf** and you may find it (then copy it to /etc/logwatch/conf/)

The Kernel section on mine is usually empty - my rarely gets rebooted (i.e. 6 months or more) so there's usually nothing in it... I'm guessing yours is on/off everyday hence filling with a whole load of stuff each time? If so, you could always remove the Kernel reporting by (I think) removing the **kernel** 'script' from /usr/share/logwatch/scripts/services/

Mathew

---

