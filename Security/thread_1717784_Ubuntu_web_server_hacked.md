---
title: "Ubuntu web server hacked"
date: 2011-03-30
forum: Security
---

### Post by milindras on 2011-03-30
Hi I got a ubuntu 6 installed as a web server which runs many websites. Its uses the webmin control panel. Suddenly today the server was hacked.
What happen here is on all wesites the index.html page was replaced with a hacking page
index.htm, index. html index.php (Turkish attack force something). The owner of the index files are ROOT.
I quickly changed the root password anyway. Then I manually replaced the index.html file from my backups on all site (more than 50 sites!!!)

Where should I start to find how this attack happen?
What should I do this not to happen again?

Appreciate your advice well advance!

Thanks
 **[COLOR=#FFFFFF]u Linux 6.06.2[/COLOR]** **[COLOR=#FFFFFF]Ubuntu Linux 6.06.2[/COLOR]**

---

### Post by lithopsian on 2011-03-30
Start by looking in /var/log/auth and any old copies.  It should log any privileged access such as by root.  You might have to look through a lot of lines since all sorts of things will be happening on a web server but there will be clues in there.  Possibly you will see massive numbers of attempted external logins from a dictionary attack.

---

### Post by Spyderkid on 2011-03-30
im not sure how server ubuntu and desktop differs but if you have a software centre or whatever install Firewall (the icon is a Blue shield) once installed go to system admin > firewall configurator and then prefrences and set it to full.

Also if you want to go the whole 19 yards find an old rotting computer and install IP-COP a linux distro **(the ultimate firewall)** set it up and no one will ever do anything to your server ever again
If you do have an old computer I strongly suggest using IP-COP if you've got a very precious server, all you need to do is install it, then once its set up un-plug the screen and mouses and external stuff, plug it into your router, and just switch it on and slave away

_**LINKS:**_
[IP-COP HOMEPAGE]("http://www.ipcop.org/")
[IP-COP DOWNLOAD]("http://sourceforge.net/projects/ipcop/files/IPCop/IPCop%201.4.19%20_%201.4.20/ipcop-1.4.20-install-cd.i386.iso")

---

### Post by s.fox on 2011-03-30
Thread moved to  [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338")

---

### Post by milindras on 2011-03-30
I have attached the log file. Could you have a look for me? 
Thanks

---

### Post by SeijiSensei on 2011-03-30
> **milindras said:**
> I have attached the log file. Could you have a look for me? 
Thanks

Someone managed to log into the ctcsysadmin account and change root's password. How secure was the password for ctcsysadmin?  How would the attacker know there's an account there named ctcsysadmin in the first place?  Look for the line where the password change for root is reported and explore the attempts above it.  There appear to be a couple of different IPs involved probing a variety of services to find passwords.

No account with even the vaguest of system permissions should have a password that doesn't contain a lengthy mixture of upper/lower letters, numbers, and special characters.

Now let's talk about some other basics.

First, you need to stop using password authentication for SSH and switch to shared keys.  Even better would be to firewall off SSH connections and enable them only for those specific IP addresses that need to connect with those shared keys.

Better yet, set up a tunnel with OpenVPN and always connect over that.  

Even with password authentication disabled, I still only let a couple of machines connect to my public server, and then usually only via OpenVPN.

---

### Post by milindras on 2011-03-30
Sorry it was me. As soon as i found out that the server hacked I chaged the password for more complex ones (It already had complex one) for ctcsysadmin & root.
 
Thanks

---

### Post by dacoolio on 2011-03-30
I just recently switched to public key authentication for my server. I'd really suggest doing that, since not only is it more secure, but it is a lot easier to actually log in and such. 

Anyway, I hope you had backups of everything, since it would make it a lot easier to reestablish the sites. As for the future, make sure you do take backups, the more often the better.

---

### Post by spynappels on 2011-03-30
Ubuntu 6 is quite an old version, was it a LTS version?

Also, did you enable the root account? It is not enabled by default on Ubuntu, and this is for a good reason in that it reduces the attack vector slightly. Key authentication and only allowing access through an OpenVPN tunnel are excellent suggestions.

@Spyderkid: Firestarter is no longer maintained, and only works on GUI systems, server edition is CLI by default. IPTables is comprehensively explained in BodhiZazen's security stickies.

---

### Post by milindras on 2011-03-30
Yes it is Ubuntu 6.06.2 LTS.
This is one of the hacked sites : [http://smallmiracle-srilanka.co.uk/](http://smallmiracle-srilanka.co.uk/) 
Basically it replaced the index.html/php page with their page. The owner of the file is root!

Yes the root acount is enabled but there is a pre login before the root. Both has good passwords.
 
 
Thanks

---

### Post by cariboo on 2011-03-30
Personally I'd probably wipe the server and install the latest LTS version which is 10.04.2 which is available [here]("http://releases.ubuntu.com/lucid/"), and supported with security updates until 2015. The version you are running is only supported until June of this year, so you were probably due for an upgrade anyway.

---

### Post by milindras on 2011-03-31
It's a live web server. I dont think its possible to upgrade while the server is live ????

Thanks

---

### Post by spynappels on 2011-03-31
> **cariboo907 said:**
> Personally I'd probably wipe the server and install the latest LTS version which is 10.04.2 which is available [here]("http://releases.ubuntu.com/lucid/"), and supported with security updates until 2015. The version you are running is only supported until June of this year, so you were probably due for an upgrade anyway.

+1 to this. Make sure that you do not allow root login (this is default) and use sudo for tasks requiring root.

Also make sure you follow SeijiSensei's advice earlier. 

Also you need to check for web browser exploits which allow insertion of files into your document root by passing commands through get or put requests in URLs, that is a way I've been stung before.

---

### Post by CharlesA on 2011-03-31
> **milindras said:**
> It's a live web server. I dont think its possible to upgrade while the server is live ????

Thanks
Would you rather have some downtime or a compromised box?

Let your clients know that you are doing maintenance and will be back up shortly.

---

### Post by milindras on 2011-04-01
This is a dedicated server rented from a Data Center. So there are no physical access to the server. And also it has FTP Backups. have more than 50 websites. Might take days to restore!!
 
Thanks

---

### Post by Grenage on 2011-04-01
> **milindras said:**
> This is a dedicated server rented from a Data Center. So there are no physical access to the server. And also it has FTP Backups. have more than 50 websites. Might take days to restore!!
 
Thanks

Speaking from an administration point of view, and managing a centre that 'must' be running 24/7, I sympathise.  That said, putting suck things off will only cause more problems later on;  schedule it in and progressively update the servers one at a time, your customers will understand.

That's assuming of course that you don't have the facility to temporarily migrate sites to another server whilst you upgrade.

---

### Post by matt_symes on 2011-04-01
Hi

> **Grenage said:**
> Speaking from an administration point of view, and managing a centre that 'must' be running 24/7, I sympathise.  That said, putting suck things off will only cause more problems later on;  schedule it in and progressively update the servers one at a time, your customers will understand.

That's assuming of course that you don't have the facility to temporarily migrate sites to another server whilst you upgrade.

I am in total agreement with Grenage here. 

How do you know that all they did was deface your web pages ?

Kind regards

---

### Post by Jive Turkey on 2011-04-01
Moving the sites to a new server one at a time is probably the best option in terms of uptime.  I'm not 100% sure about the logistics for you on this.

---

### Post by d3v1150m471c on 2011-04-01
honestly, i'd completely reinstall it. setup psad, and if you're running ssh make sure you're using key sharing, and possibly running denyhosts. Also you might want to use iptables to close up all incoming connections unless you absolutely need those ports open, ie port 443, port 80. Before you do anything drastic extract your logs and go through them with a fine tooth comb.

also, if you don't mind what was the website? i could visit it and if i see something that looks exploitable i could point you in the right direction., that is if the site's even up.

---

### Post by tgm4883 on 2011-04-01
For upgrading without needing to reboot, you might want to look into [http://www.ksplice.com/](http://www.ksplice.com/)

---

### Post by CharlesA on 2011-04-01
> **tgm4883 said:**
> For upgrading without needing to reboot, you might want to look into [http://www.ksplice.com/](http://www.ksplice.com/)
Thought that was only for kernel updates?

---

### Post by bodhi.zazen on 2011-04-01
> **CharlesA said:**
> Thought that was only for kernel updates?

It is , but kernel updates are the only reason to reboot, almost everything else can be accomplished by restarting services (rather then a reboot).

---

### Post by tgm4883 on 2011-04-01
> **CharlesA said:**
> Thought that was only for kernel updates?

It is....

> **bodhi.zazen said:**
> It is , but kernel updates are the only reason to reboot, almost everything else can be accomplished by restarting services (rather then a reboot).

Ah, you beat me to it :)

---

### Post by CharlesA on 2011-04-01
> **bodhi.zazen said:**
> It is , but kernel updates are the only reason to reboot, almost everything else can be accomplished by restarting services (rather then a reboot).
That's what I thought. Thanks.

I will have to check to see which packages have been updated next time I am told that my system requires a reboot.

---

### Post by milindras on 2011-04-04
You can have a look at a hacked site by adding a host record to
109.104.72.176        advmilitaria.com

Many Thanks

---

### Post by milindras on 2011-04-05
Could some one tell me a small explantion about the following log:

Many Thanks

Sorry i have attched on the next post!

---

### Post by milindras on 2011-04-05
Could some one tell me a small explantion about the attached log:


Thanks

---

### Post by CharlesA on 2011-04-05
Not sure what it means, but dovecot is a POP3/IMAP server isn't it?

Kinda sounds like someone was trying to bruteforce it, but I'm not all familiar with those logs as I don't use dovecot.

---

### Post by SeijiSensei on 2011-04-05
It's a "dictionary" attack trying to find accounts with poor passwords.  I get these from time to time, too.  I've been thinking of running fail2ban or something similar in front of dovecot to block these, but they haven't managed to do any harm.  I only have a few accounts, and I enforce strong passwords on my users' mailboxes.

Other options include using iptables limit rules or "wrapping" dovecot in xinetd so that rapid multiple connection attempts from a single IP get blocked.

---

### Post by milindras on 2011-04-06
> **SeijiSensei said:**
> It's a "dictionary" attack trying to find accounts with poor passwords.  I get these from time to time, too.  I've been thinking of running fail2ban or something similar in front of dovecot to block these, but they haven't managed to do any harm.  I only have a few accounts, and I enforce strong passwords on my users' mailboxes.

Other options include using iptables limit rules or "wrapping" dovecot in xinetd so that rapid multiple connection attempts from a single IP get blocked.


Many Thanks for the advise...

---

### Post by cprofitt on 2012-04-01
I just completed a red-team blue-team exercise this weekend and one of  the issues that caught the blue-team was the fact that webmin allowed  the following?


port 10000

login user:  admin
password:  blank

check 'remember me'

this allowed the red-team to change the root password and then login via other services.

I still have to test webmin on Ubuntu since I am not sure if this was  the particular setup of the exercise or a default initial configuration.

---

