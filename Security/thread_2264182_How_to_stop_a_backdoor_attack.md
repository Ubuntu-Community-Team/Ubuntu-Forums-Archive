---
title: "How to stop a backdoor attack"
date: 2015-02-06
forum: Security
---

### Post by shersk on 2015-02-06
Dear forum. How to stop a backdoor attack on a production server? The attacker managed to upload a script to the Wordpress root folder, from where this script (I have read it) probed the system and reported back. The backdoor script provided a login page, and after logging in, a menu over things to do on the compromised system, like upload or move around files. 

A new server was built from scratch, and data transferred to it. After a few days, it became clear that the attacker also had compromised the new system, so his tools had followed with the moving to the new server. The only non-vetted code that was brought over to new machine was the mysql database and the whole wordpress directory structure, with plugins and themes. 

Can anyone give some advice about how to stop this attack? I am now at the stage where I have yet another server ready, but won't bring any code over until vetted. But how to go through all this information and find the malicious items? And most importantly: how did the attacker get access in the first place? Just this morning, he managed to put the backdoor script on the server again. Where, how does (s)he enter? And is there any way to find out exactly what type of malicious script this is, its history, its functionality, etc, from studying the code, or sending it to someone who has time and competency in such things?

---

### Post by TheFu on 2015-02-06
I wouldn't call this a back door if they come into the server using the website. That's the front-door.  Backdoor implies they came into the network some other way, then because they were already inside, didn't have much trouble connecting to the server (i.e. no firewalls to deal with).

If you know where they are coming from  - block that subnet immediately.  If they are going places - block those subnets immediately too.

Check the themes and plugins for hacks. Check the versions of everything - EVERYTHING. Look for known hacks against each. Make a list, check it twice.

Be certain the entire software stack is patched and up to date.  That means the version of PHP used too, not just the OS, themes, plugins and DBMS.

You can engage with security companies to help with this issue.  There are well-known security companies - usually very expensive - or you can contact local "defcon" people and ask for help. Some may have time to do freelance work. Time is money, right?

Some reading: [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)
[http://blog.ircmaxell.com/2014/12/php-install-statistics.html](http://blog.ircmaxell.com/2014/12/php-install-statistics.html)
[http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/) - what a hacker does after getting server access.

Short of checking every version of everything in your software stack, I don't know how to begin.  Of course, if you can see the connections and block those IPs ... web servers have security modules which can be configured for that. As an example, I block many countries from even accessing my websites - people/companies in those countries will never add to our revenue, so why waste bandwidth or allow attacks?

Welcome to the wild west.

---

### Post by Habitual on 2015-02-06
[http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)

---

### Post by wannabe user on 2015-02-06
The main thing to take from the above is keeping the instance up-to-date.

You say you took the whole directory over, well that will most likely contain the malicious files. It's not uncommon to exploit various upload facilities of Wordpress and or installed plugins, I've seen an infected install which had some pretty nice tools, basically a PHP page that allows many features including a shell and DB dump. 

There are tools you can use to help automate checks, there's WPscan [http://wpscan.org/](http://wpscan.org/) which doesn't always give me good plugin detection results, but useful nonetheless. I would however be inclined to port data and themes over to a new install of Wordpress, if that's not possible you need to ensure none of the standard files have been modified and remove any of the malicious files. 

But yeah, Habitual's link is a good starting point.

---

### Post by kpatz on 2015-02-06
I'd reinstall Wordpress from scratch (clear out the php files and reinstall the latest version), so that the malicious scripts are gone.

Then install ZB Block, available here:  [http://www.spambotsecurity.com/zbblock_download.php](http://www.spambotsecurity.com/zbblock_download.php)

ZB Block is a PHP intrusion blocker, that bans many "bad" IP ranges as well as certain behavior-based and user-agent detection and blocking of malicious bots.  It's easy to install and highly configurable.  It'll cut down on wasted bandwidth due to abuse, and will cut down on spam comments and hack attempts as well.

---

### Post by HermanAB on 2015-02-07
A production server - ultimately you got to re-install it from backup.

In the mean time, use iptables to drop the connection to the perp:
# iptables -I -s ipaddress -j DROP

---

### Post by bashiergui on 2015-02-07
+1 to thefu and habitual> A new server was built from scratch, and data transferred to it.Did you transfer clean backups made at a time you know it wasn't compromised? Or did you transfer data from the compromised server? If it's the latter, then it's common for the attacker to upload several malicious scripts, not just one. They might overwrite legit files with malicious ones of the same name. Really they could have done anything as they had root.

Search Google for any recent exploits or vulnerabilities on themes and plugins you're using. Remove the ones that you can't patch or secure.

---

### Post by shersk on 2015-02-11
Thanks to all of you! Taking a break here from the "war" to write an update. 

We ran the WP plugin "**Anti-Malware and Brute-Force Security by ELI", **which found one backdoor script hidden within a theme that hasn't been used for years. It seems to be for uploading some files and move them to another location.

Before, just by chance, I found a tool box type of script, which was much like you described, wannabe user. Like a tool box. It did some scans of the system, and offered a login screen and a menu system for various tasks. This is what I called backdoor script in my first post. 

I have no idea which one of these scripts entered first, but a backup made in October shows that they were not present at that time, and the post-mortem on the abandoned server shows that both scripts were present during the moving.

Next step will be to build a new server, and bring over only one theme and one plugin we have modified, plus the mysql database - the bare essentials. All other code will be installed from trusted sources and latest version.

So the theme, plugin and mysql db should be vetted, although it seems that this particular attacker has lost his means of entry. (There used to be some activity in /tmp when he was active, as well as uploading new backdoors from time to time. There is no such activity visible now, through ordinary means.)

Intrusion detection systems should also be installed, and I am looking at tripwire, ossec and aide. Am now running ossec on the active production server, and satisfied as such, but don't know how well it is able to sniff suspicious activity.

Tried installing WPScan, wannabe user, but got an error message when trying to scan local files, like this:

> ruby wpstools.rb -v --check-local-vulnerable-files /path/to/wp/root/

It says ERROR - "No such file or directory" .../wpscan/data/local_vulnerable_files.xml. What have I done wrong - I installed it with apt-get as prescribed: 

> sudo apt-get install libcurl4-gnutls-dev libxml2 libxml2-dev libxslt1-dev ruby-dev build-essential
git clone [https://github.com/wpscanteam/wpscan.git](https://github.com/wpscanteam/wpscan.git)
cd wpscan
sudo gem install bundler && bundle install --without test



TheFu: Thanks for the reading material.

bashiergui: I transferred data from the compromised server, and the post-mortem shows that the two malicious scripts were present during the transfer. Now they are - scans needed to vet remaining code. How to be sure of this? Reliable scanner applications?

Another direction to work in is like you say, kpatz, blocking strategies. Can you link to an installation guide for ZB Block? Currently, I'm using the Sucuri plugin to block unwanted users in WP, plus manually blocking IPs (using my own ufw script) based on studying the output from ossec. But ZB Block sounds interesting, and I'm like to install it. I'm using Ubuntu 14.04.

---

### Post by Habitual on 2015-02-11
Wordfence is an excellent WP plugin. I **highly** recommend it.

---

### Post by shersk on 2015-02-11
I'm using Wordfence too! :p

---

### Post by bashiergui on 2015-02-12
> bashiergui: I transferred data from the compromised server, and the post-mortem shows that the two malicious scripts were present during the transfer. Now they are - scans needed to vet remaining code. How to be sure of this?Only way to be sure is to start from a clean backup. When one isn't available, I guess have several people review everything and hope for the best.

---

### Post by TheFu on 2015-02-12
> **shersk said:**
> How to be sure of this? Reliable scanner applications?

There is no way to be "sure" of anything in computer security when a network is involved. You can only minimize risks to the level your skill, budget and time available.

If I had a machine that was hacked, and I couldn't prove exactly what was modified, I wouldn't restore from a backup. I'd build a new machine from the best, trusted, sources available and might copy/paste selected files, reviewing each, one at a time, for unexpected differences from believed-to-be-good sources.  Comparing text is very easy on Unix systems.

No scanner is 100% - just like AV on windows is only 50% effective. There are always new methods that the scanners don't know. Always.

In 2002, one of my machines was hacked. Fortunately, they weren't very sophisticated and the hack was seen within a few hours. About 1400 alerts happened. Plus I had an image of the server from a few days prior, which I compared all files against. Found all the changes and remembered all but some changes under /tmp/ ...  Looked in that area closely, saw the owner and immediately knew how they'd gotten in and why they failed to get any further. That account was for 1 purpose only and very limited otherwise.  Because the mirror was current enough, I was extremely confident and didn't rebuild the box. This was the last time any of my servers were hacked.

I like to think I'm better at managing the risks, but it could just be dumb luck. Seems that people who have never been hacked are overly cocky.  Paranoia is helpful when trying to secure a computer.

---

### Post by shersk on 2015-02-17
Oh my god. I built a new server from scratch, secured the server, then installed Wordpress, one theme and one plugin, plus some uploads folders. Then I installed tripwire, following all the required configuration steps, testing it, installed a cronjob.

What happens next is that I start receiving empty emails from tripwire. I file it away at the back of my head that I have to check what's wrong with tripwire one of the next few days, because it's not sending anything.

I log in today, and discover that tripwire does no longer exist on my server. 

Now I'm starting to think that the compromise is not on the hosted server remotely, but perhaps on my local laptop, or somewhere else. What the hell is going on?

---

### Post by TheFu on 2015-02-17
[http://www.linuxquestions.org/questions/linux-security-4/email-alerts-with-tripwire-883839/](http://www.linuxquestions.org/questions/linux-security-4/email-alerts-with-tripwire-883839/)

---

### Post by shersk on 2015-02-17
The whole tripwire is gone. There is no /usr/sbin/tripwire. There is no folder called /etc/tripwire. 

Investigating - in the /var/log/dpkg.log file, it says someone ran 'startup packages purge', and also 'purge tripwire'. This happened three days ago. Could such a command have been issued for innocuous reasons? Am I missing something? I was purging and reinstalling mailutils and postfix a few times, because I couldn't get it to work properly. But I definitely didn't uninstall tripwire.

I guess it means there's still a backdoor hidden among the files I copied from the previous server? Scans with all the scanner programs I have didn't turn up anything. Just one false positive with chkrootkit about Suckit in /sbin/init which is an old bug, according to many posts around the net.

---

### Post by CharlesA on 2015-02-17
Check the auth.log, it should say log anyone who used sudo.

---

### Post by shersk on 2015-02-17
There is nothing in the auth.log. But in the apt-get log, it shows that someone has removed and purged tripwire three days ago. auth.log goes back four days.

---

### Post by bashiergui on 2015-02-17
> Investigating - in the /var/log/dpkg.log file, it says someone ran 'startup packages purge', and also 'purge tripwire'. This happened three days ago. Could such a command have been issued for innocuous reasons?No.

Looks like your adversary still has root. Use the Auth log like Charles suggested to figure out which user ran the commands.

Have you got a backup of the server that predates the one you just used?

---

### Post by bashiergui on 2015-02-17
> **shersk said:**
> There is nothing in the auth.log. But in the apt-get log, it shows that someone has removed and purged tripwire three days ago. auth.log goes back four days.
What do you mean "nothing"? It's empty or chunks of time are missing?

---

### Post by shersk on 2015-02-17
> **bashiergui said:**
> What do you mean "nothing"? It's empty or chunks of time are missing?

The auth.log is present and looks normal, but I tried searching through it for 'tripwire', 'remove' and 'purge', but could not find any command that corresponds to what is stored in the dpkg log, which clearly says purge tripwire.

---

### Post by TheFu on 2015-02-17
> **CharlesA said:**
> Check the auth.log, it should say log anyone who used sudo.

There are hacker tools that clean up the logs and remove that stuff. The only way I know around those is to use rsyslog and send all logs to another, highly secured, log server.

---

### Post by shersk on 2015-02-17
> **bashiergui said:**
> No.

Looks like your adversary still has root. Use the Auth log like Charles suggested to figure out which user ran the commands.

Have you got a backup of the server that predates the one you just used?

No, I have just built the server and not selected backup solution yet. I also though tripwire had things under control now.

---

### Post by TheFu on 2015-02-17
Security is not a checkbox.
It starts with a secure network, smart separation of services, not using passwords, not using vulnerable software versions, and constant vigil.
Think of security as 50 layers, never trust just 1 tool to provide "security."

---

### Post by bashiergui on 2015-02-17
> **shersk said:**
> No, I have just built the server and not selected backup solution yet. I also though tripwire had things under control now.You built the new box from scratch and installed the minimal services?  And you haven't restored any backups to it yet? I suspect user error before another hack here. Edit: unless you're using simple or the same passwords.

Use this opportunity to check all your passwords and make sure they're incredibly long and complex. Disable password auth via ssh, use keys only.

---

### Post by shersk on 2015-02-17
Thanks. I just don't understand - who has time to sit and fiddle with my server like that? Or do these hackers have their scripts / recipes so well organized that it's no effort? 

As far as I can understand, he has sudo'ed, he has manipulated my logs, he has covered the compromise so that it can't be found by chkrootkit and rkhunter etc etc.

---

### Post by bashiergui on 2015-02-17
> **shersk said:**
> Thanks. I just don't understand - who has time to sit and fiddle with my server like that? Or do these hackers have their scripts / recipes so well organized that it's no effort? 

As far as I can understand, he has sudo'ed, he has manipulated my logs, he has covered the compromise so that it can't be found by chkrootkit and rkhunter etc etc.
It's not hard to avoid chkrootkit and rkhunter. 

What I'm wondering is how your brand-new server got hacked, or if it did at all. Is this a physical server on your location or is it in the cloud somewhere? What processes are running? What sockets are open? And did you reuse old passwords? Tell me you don't have ssh accepting password auth.

---

### Post by TheFu on 2015-02-17
> **shersk said:**
> Thanks. I just don't understand - who has time to sit and fiddle with my server like that? Or do these hackers have their scripts / recipes so well organized that it's no effort? 

As far as I can understand, he has sudo'ed, he has manipulated my logs, he has covered the compromise so that it can't be found by chkrootkit and rkhunter etc etc.

Initially, the attack was completely automatic. It is possible for almost any broadband system connected to the internet to scan every IP and every port in 2 days.  That builds a DB for further scripted attacks.  This is all automated.  There are organizations around the world always looking for a Unix box to pwn, because those can be used for so much more useful work later or as phishing repos.  Is it really that hard to understand?

[http://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/](http://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/) - explains how a hacked PC can be used.
[http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/) - explains what a hacker does on a newly hacked box.

Once in a while, a hacker will actually learn tricks from the automated tools and manually try stuff too. That is highly unlikely for a blog, but it isn't impossible.

People is some parts of the world have lots and lots of time on their hands and a computer. Just like a teen in a USA home after school who is bored, people all over the world get bored and find hacking to be entertainment with very little risk. It isn't like you'll fly to confront someone in Indonesia, right?  Heck, even if you report the exact address of someone in your country, state, city to the police, unless the hack has reached a fairly significant dollar amount, they won't help.

BTW - I hope you are scripting this setup by now, so it is repeatable and improvements aren't lost next server build.  A tool like ansible can really make a difference at managing multiple servers more efficiently with repeatable processes.

---

### Post by shersk on 2015-02-17
> **bashiergui said:**
> It's not hard to avoid chkrootkit and rkhunter. 

What I'm wondering is how your brand-new server got hacked, or if it did at all. Is this a physical server on your location or is it in the cloud somewhere? What processes are running? What sockets are open? And did you reuse old passwords? Tell me you don't have ssh accepting password auth.

It's in the cloud. Processes - I'm looking through them with ```
ps aux
```. Not sure what I should look for. I tried ```
netstat -lnp
``` as sudo, and the only ports open to the internet are as expected 22, 25, and 80, plus the NTP port (123). Internally, there are lots of active sockets, but I am not familiar with this and can't tell if anything is out of the ordinary.

I have PermitRootLogin set to 'no', but sshd accepts passwords.

---

### Post by bashiergui on 2015-02-17
> **shersk said:**
> The auth.log is present and looks normal, but I tried searching through it for 'tripwire', 'remove' and 'purge', but could not find any command that corresponds to what is stored in the dpkg log, which clearly says purge tripwire.That's expected. You won't find anything with those key words. What you want to do is determine the timeframe the remove and purge commands were run, then look for the user authenticating around that time. If you're the only user on this server then look for activity when you know you weren't logged in. 

For sockets you want to look for any connections to external IPs that you don't recognize. First watch the established tcp connections for a while, look for unknown IPs or ports.```
sudo watch ss
``` Then watch the services that you have listening for incoming connections. This will tell you if you have odd services listening that shouldn't be.```
sudo watch ss -l
```
For processes you want to make sure all the running processes are expected. Sometimes attackers name their processes suspicious names so maybe you'll get lucky there. It's not unheard of for an attacker to migrate into a legitimate process, or to name their process something that looks legit, those are harder to find.
> I have PermitRootLogin set to 'no', but sshd accepts passwords. That's probably how they got in the first time and again on your new box. Did you reuse the password from the first box?  Don't allow password auth. Use keys.

---

### Post by TheFu on 2015-02-17
Could your cloud access keys have been compromised?
If you are already in the cloud, perhaps paying wordpress.com to manage the infrastructure would be worth it?

---

### Post by shersk on 2015-02-17
> **bashiergui said:**
> That's probably how they got in the first time and again on your new box. Did you reuse the password from the first box?  Don't allow password auth. Use keys.

I reused the password, yes. Until now, I have not thought it possible that my unix account(s) was/were hacked into, I thought the compromise was limited to malicious scripts in Wordpress.

Absolutely understand the thing about automated scanning and probing. I will need something like ansible, so thank you for that. Until now, I am using tutorials offered by the cloud hosting service, which gets a bit complicated now with all these security precautions.

Here are the lines from dpkg.log which shows the moment when tripwire was removed. How do you think it was done, by what command, from reading this?

```
2015-02-14 03:44:42 status installed tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 remove tripwire:amd64 2.4.2.2-3 <none>
2015-02-14 03:44:42 status half-configured tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 status half-installed tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 status config-files tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 purge tripwire:amd64 2.4.2.2-3 <none>
2015-02-14 03:44:42 status config-files tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 status config-files tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 status config-files tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 status config-files tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 status config-files tripwire:amd64 2.4.2.2-3
2015-02-14 03:44:42 status not-installed tripwire:amd64 <none>
```

---

### Post by bashiergui on 2015-02-17
> **shersk said:**
> I reused the password, yes. Until now, I have not thought it possible that my unix account(s) was/were hacked into, I thought the compromise was limited to malicious scripts in Wordpress.When a Wordpress or plugin exploit is successful, the first thing an attacker does is escalate his privileges to be root on the box. 

Look at it from the attacker's perspective: he had root on your old box. It disappeared for a bit while you rebuilt it, but then it appeared again when you were done. He uses the same user, same password to get right back in. A lot of work on your end resulted in zero extra work for the attacker.

Not to belabor the point, but you need unique, complex passwords for everything. EVERYTHING. Get rid of password auth on ssh. 

To TheFu's point, change your passwords and keys to the cloud as well. Check for new users the attacker could have created there.

---

### Post by bashiergui on 2015-02-17
> Here are the lines from dpkg.log which shows the moment when tripwire was removed. How do you think it was done, by what command, from reading this?Look at the auth log at that time and see who was logged in then. Did anyone su or sudo? Who was logged in at that time?
You should be able to see what commands were run by looking at each user's bash history (assuming he didn't delete it). They won't be time stamped, though, unless you configured it to do so. Each user's history is separate so make sure to look at the history for all users logged in at the time tripwire was removed.

---

### Post by shersk on 2015-02-17
Nobody su'ed or logged in around that time, according to auth.log. There are only two users on this system: root and the user I'm logged in as. No-one else than me is authorized to use this server. 

If the hacker has gained root access, he might have manipulated the logs, or the way logs are written, as far as I understand.

---

### Post by shersk on 2015-02-17
> **TheFu said:**
> Could your cloud access keys have been compromised?
If you are already in the cloud, perhaps paying wordpress.com to manage the infrastructure would be worth it?

No. I am using two-factor authentication.

---

### Post by shersk on 2015-02-17
Call off the alarm, I managed to reproduce the incident on a new server. I installed postfix and mailutils, but using a temporary hostname. After switching to the real hostname, and pointing the DNS server to the machine, mail no longer worked, so I purged and reinstalled postfix. After this operation (apt-get), tripwire was disappeared from the system. Just like what happened last. 

How could apt-get remove tripwire when I only asked it to purge postfix?

---

### Post by ian-weisser on 2015-02-17
> **shersk said:**
> How could apt-get remove tripwire when I only asked it to purge postfix?

Because if A ***depends*** upon B, and you remove B, then A cannot be installed anymore.

```
$ apt-cache show tripwire | grep postfix
Depends: postfix | mail-transport-agent
```

When you told the package manager to remove tripwire, it warned you of all the other packages it was about to remove.

---

### Post by bashiergui on 2015-02-17
That's great news. Good news about the 2fa on the cloud, too. Now you can carry on hardening this server. Hopefully you're convinced about using keys and good unique passwords. I'm sick of hearing myself go on about it ;-)

---

### Post by shersk on 2015-02-18
> **bashiergui said:**
> That's great news. Good news about the 2fa on the cloud, too. Now you can carry on hardening this server. Hopefully you're convinced about using keys and good unique passwords. I'm sick of hearing myself go on about it ;-)

I already built a new server and have switched over the domain -> IP. It's good, as now I have a server which has had keys-only logon from scratch. Thanks for reminding me about that. And it doesn't hurt to get some more exercise in setting up a server. I will proceed to harden the server now and perhaps setting up rsyslog, if I can find a place to send those logs to.

---

### Post by shersk on 2015-02-18
> **ian-weisser said:**
> Because if A ***depends*** upon B, and you remove B, then A cannot be installed anymore.

```
$ apt-cache show tripwire | grep postfix
Depends: postfix | mail-transport-agent
```

When you told the package manager to remove tripwire, it warned you of all the other packages it was about to remove.

tripwire depends on postfix, yes, but I wouldn't expect apt-get to remove a package which is dependent on a package I want to remove. But you learn something new every day. 

Thanks for following up my questions in this situation.

---

### Post by shersk on 2015-02-18
As a post scriptum, I ran into trouble with my wordpress configuration now, because I have keys-only authorization in ssh. I wanted to automatically update a few plugins, but couldn't get it to work after entering the location of the rsa keys on the server. 

While I was at it, I went into wp-config.php and secured the keys there with random salts, just to improve security. But for some time, I couldn't log in to wordpress admin. This turned out to be because I lacked curl and curl-support for php5, which I had forgot to install on the new server after last night's migration. curl is needed by the wordfence plugin, which springs into action when someone logs in.

But the plugin update issue was still unresolved. I wanted to enable the use of keys to handle ssh when wordpress automatically updates plugins. It confused me a while that wordpress was asking me for both my private and public keys. THIS private key? The one here, on my laptop? 

Until I realized that these keys are not for connecting from my laptop to the unix server, but from my wordpress to the ftp, which has ssh for access control. Therefore, I logged on the unix server (where wordpress is running) with ssh, and on that server I generated a new key pair with ssh-keygen. I chose to not have any passphrase (is this a security risk?). Then I added the private key (~/.ssh/id_rsa) to my ~/.ssh/authorized_keys file, using a text editor to carefully add the key below key(s) already there, set the permissions (erroneously!) to  ```
chmod 755 .ssh
chmod 644 .ssh/*
``` and entered the full paths to id_rsa and id_rsa.pub on the wordpress plugin update page. That made it work, although the premissions I set was mistaken advice (see below),  described here: [http://wpforce.com/wordpress-tutorial-ssh-install-upgrade/](http://wpforce.com/wordpress-tutorial-ssh-install-upgrade/)

---

### Post by TheFu on 2015-02-18
Whoa there.

* ~/.ssh/ needs to be 700 A-L-W-A-Y-S. Doesn't matter which account.
* ~/.ssh/* needs to be 600 ... except the public key which can have less restrictive settings.
Why?
a) ~/.ssh/ shouldn't work with anything other than 700. That is the first thing to check when ssh key-based connects fail.
b) group and other shouldn't be able to view your private keys, your config file known_hosts or authorized_keys.
I'm shocked if your permissions work.


Yes, having no passphrase to access ssh keys is less secure.

How did you forget to load any packages? Don't you have a script that is repeatable and maintained?  [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) repeatable processes are very important.

Do you think that automatic plugin updates is smart?

---

### Post by shersk on 2015-02-18
Thanks for reminding me and others about the recommended permissions for the .ssh folder. 

> **TheFu said:**
> How did you forget to load any packages? Don't you have a script that is repeatable and maintained?  [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) repeatable processes are very important.

Do you think that automatic plugin updates is smart?

As I have mentioned, we have one theme and one plugin that are both heavily modified. Ideally, we should get them into a public revision system like github, but in both cases this process is stalled because the creator doesn't respond and I am not familiar enough with such programming work to do it myself. There is slight progress regarding the plugin so maybe we will get that sorted out.

Regardless, it is not given that we want to update every plugin immediately a new version is available. There might be many reasons for keeping the current version. Most importantly, updating the plugin may break the webserver, so this has to be a hands-on procedure. 

Whether to use the user-friendly interface offered by wordpress or not is maybe more of a development issue, how wordpress should be designed. There is offered a user-friendly way, and in the hustle and bustle of daily publishing, it's hard not to grab onto all the user-friendliness you can get. But it has to be secure.

---

### Post by shersk on 2015-02-19
TheFu: Maybe you can explain why automatic plugin updates is not smart?

---

### Post by TheFu on 2015-02-19
> **shersk said:**
> TheFu: Maybe you can explain why automatic plugin updates is not smart?

In the end, it is about risk management. Every patch has a risk. Not patching also has a risk.

Ever had any patch that broke a system? Or ever had any patch that broke a tiny, but important part of a system?

When patches are applied, information, issues, problems are usually reported. If you don't see these immediately, the system may be completely broke or partially broke or just incompatible with any customized code installed on the box.  A few times, I've seen *minor updates* corrupt DB tables too.

The smaller a support team is, the more important it is to plan the update time and have plans for contingencies.  I'm part of a 2-man IT team and we both like to travel and sleep at night. Sometimes we are out of touch for multiple days and cannot remote into our systems to fix anything. Traveling for 37 hrs means being disconnected for that time. Some of our destinations don't exactly have broadband. Having a system fail during disconnected time would "bad." Automatic patching drastically increases that risk of failure.

I had a job were I couldn't leave town ... without scheduling it months in advance. They'd freeze all changes weeks before I left to prevent any unknown issues from happening that couldn't be fixed.  It was a government thing and I was on-call 24/7/365. There wasn't any real backup for me and mission support was 24/7. It was an isolated, air-gap, network - no remote access possible.  It sucked and after a few years, I burned out and resigned from a really cool job.  I swore I would never be in a job that required 24/7 support like that again.

Of course, if you have a support team that is available 24/7, constantly monitoring the monitoring tools and everyone has the skills to address any issue from an automatic patch - go for it. That is a mitigation technique we just don't have here.  Automatic updates in a support organization like this could be smart.

OTOH, actually having a backout plan seems to go against the push-fast-and-fix-it-later teams getting all the press today - continuous deployment.  We don't like being the first to try new patches. Much prefer to block any known attack vectors using our network tools/reverse proxy filters and wait a few days for any issues with a critical patch to become known and fixed properly.

Risk management.

---

### Post by shersk on 2015-02-21
Makes sense, TheFu. I guess for us it would be an option to have a test server running as a carbon copy alongside our production server, and let the test server always automatically update. If it doesn't break, also update the production server. 

Another 'post scriptum' here: On my newly created server, the one with tripwire installed right from the start, apt-get told me 7 updates available, 3 of them security updates. I tried updating, but apt-get didn't want to update. A few hours later, apt-get said no updates are required anymore. I understand from reading ubuntu forums that this is to do with dependencies, that apt-get will wait with these updates due to that, and nothing to worry about.

Also a bit difficult to read the tripwire logs, as there are lots of files in for example /usr/sbin that have been modified, and I don't know if this is due to one of my updates or something to be worried about. Would be nice to have a method to directly remove things from tripwire scan when updating, or to send the apt-get output to a file somewhere, so that tripwire can know that this was done by me, not our friend, the hacker.

---

