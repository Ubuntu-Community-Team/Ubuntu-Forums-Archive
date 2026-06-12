---
title: "vBulletin"
date: 2009-08-30
forum: Security
---

### Post by phillw on 2009-08-30
Hi,

I ask here about vB as this site uses it and, as propriety nature it is not to easy to get answers off them.

My laptop (piglet) is set up as a LAMP server - between FireStarter and ShoreWall I've done my best to set it as accepting http, https, ssh, Cisco-ccp (not too sure why I allowed that one), MySQL to everyone & Webmin to localhost only.

I run 9.04, with all the auto-updates turned on so I have Shiretoko as my browser.

My many passwords are stored by my browser under a master password.

My main (important) passwords are along the lines of 2£pH'@;-_&SQlc^%  Not the easiest to guess with a dictionary attack.

Well, according to the logs, #ID = 3 (Me) logged onto the AdminCP and altered the password of #ID = 1.

Now, I do have the access privalidge to do that, except ....

1)  It showed as my IP address (yeah, so spoofing IP's is nothing new)
2) Evidently I changed the password, and then changed it back.

I thought that it was not really possible to 'guess' a hashed password, you can sort of, try a dictionary attack - I'm not knowledgeable enough to know the ins and outs of that, except that we should keep decently secure passwords.
 
So, spoofing an IP address is not difficult, but how the heck did someone manage not only my password, but be able to change & then re-change a password ? The user of ID = #1 does not use easily guessable passwords - abt 16 chars in length.

The rule I have learnt is that if you think your system is compromised, back up stuff & re-install. 
But, if that occurs, how do we stop it happening again ?

I've thought of making a permanet cookie onto my computer, with a daft encrypted name, such as myphpadmin gives out, with the contents of another of the ones it generates.

As I say, I am security concsious, but faced with logs from vBulletin - "Houstan, we have a problem" 


Your advice on this would be greatly appreciated.

Regards,

Phill.

---

### Post by phillw on 2009-08-31
::SIGH::

I know this is a big ask. Has anyone come across such a thing before, and how did they protect there after.

To my limited knowledge, it should not be possibe - Is the weak link on my laptop or is it server side ?

Thanks, 

Phill

---

### Post by dmizer on 2009-08-31
What version of vB are you running?

Hosting a live site off of a machine you also use to browse the web = very bad.

---

### Post by bodhi.zazen on 2009-08-31
It is hard to know with the information you posted. Could be anything from a problem server side to a bug in vBullitin to an exploit on another application on your box.

Why do you allow connections to mysql from anywhere but localhost ?

---

### Post by phillw on 2009-08-31
I've only just turned on MySQL ( it was turned off at the time). the site was running v3.8.3  It's now on v3.8.5

BTW - as clarification, the site is not run on my laptop, it is hosted by e-nom. I include all my details to ask if someone
could have tunnelled through my computer & onto that one.

---

### Post by dmizer on 2009-08-31
> **phillw said:**
> BTW - as clarification, the site is not run on my laptop, it is hosted by e-nom. I include all my details to ask if someone
could have tunnelled through my computer & onto that one.

But you did say that you were running a LAMP server off of it, and forwarding http. What kind of site are you hosting on your laptop?

---

### Post by phillw on 2009-08-31
my firewall is set thus, under Firestarter, although I have modified stuff with Shorewall.

Allow connection from host

Anyone


Allow Service

HTTP, port 80, Everyone
HTTPS, port 43, Everyone
SSH, port 22, Everyone
cisco-sccp, port 2000, Everyone [I don't think i need this one]
MySQL, port 3306, Everyone [This has only just been added & was not available on 11th August]
Wbmin, port 10000, localhost.

---

### Post by bodhi.zazen on 2009-08-31
I am not following what you are running where.

Are you asking if somebody first cracked into your laptop and then leveraged your laptop to crack into a server ?

What applications are you running on your laptop and what applications are you running on a remote server ?

Second your firewall is iptables. shorewall and firestarter are configuration tools, you should almost certainly use one or the other , but not both. How do you know your firewall is working and what makes you think you need a firewall on your laptop on the first place ? Again what services are you running on your laptop that you want to firewall?

---

### Post by phillw on 2009-08-31
I'm guessing yes, someone got at my laptop. I always fire up the AdminCP for the  site and then pop onto 1st page. I check out what has been posted, catch up with stuff and then open up other tabs to do some work !! (I keep those tabs open & do a periodic check of who's on)

Yes, i do understand about IPtables & that the agents only put  a nice end on to configuring them .... well, that's debateable.

You do not 'run' a firewall on ubuntu - you set it - thus tutorials from you guyz have taught me. I could have 30,000 different front-ends to a firewall - but they all talk to the boss - iptables.

Are you asking if somebody first cracked into your laptop and then leveraged your laptop to crack into a server ?

As it shows my IP address, that would be my 1st thought. But I do not have the skills to know if it was an attack via my laptop, a direct attack upon the server, or a combination of the both of them.


BTW, thanks guyz (and Galz) I'm sorry that you need to ask so many questions of me and I seem not to able to explain what happened !! :-(

Phill.

---

### Post by phillw on 2009-08-31
Scenario ...


There is a forum that I am part of the guide team.

During my learning & getting my skills up to date, I install Ubuntu 9.04 desktop, then add in the rest of LAMP.

I use piglet (my laptop) as my own server, thus i have phpBB3 set up, an e-commerce site, a static & being built dynamic site.

Now in hosting these sites upon my laptop - if one gets 'nuked' or I get hacked - it's no big deal - there is no life threatening data.

It may sound really daft, but I'd like to add that to my knowledge. 

**HOWEVER **it is not my laptop and my LAMP installation, and to the best of my knowledge - my little server may well be secure. 

It is the showing up of my IP, using my password to gain access to a site.

But --- and this for me is the killer --- changing a secure password & then changing it back ?

Without going into the ins and outs - I would not & do not know the password - It is a non dictionary password of about 16 characters. So, how the heck did 'I' alter it and then change it back ?


Thanks for bearing with me.

Phill.

---

### Post by dmizer on 2009-08-31
> **phillw said:**
> I use piglet (my laptop) as my own server, thus i have phpBB3 set up, an e-commerce site, a static & being built dynamic site.

As I said before, hosting a website on the same machine you use to browse the web = very bad.

You are focusing on how your vB site was compromised. I suspect that your laptop was compromised as a result of hosting a website on it, and then once someone pwned your laptop, it was a simple matter to crack the vB site.

Your laptop is the weak link here because you're using it both as a personal computer and as a web host.

Edit:
You also said that you forward SSH to your laptop. Do you have password authemtication disabled?

Either way, your laptop is a prime suspect.

---

### Post by phillw on 2009-09-02
> **dmizer said:**
> As I said before, hosting a website on the same machine you use to browse the web = very bad.

You are focusing on how your vB site was compromised. I suspect that your laptop was compromised as a result of hosting a website on it, and then once someone pwned your laptop, it was a simple matter to crack the vB site.

Your laptop is the weak link here because you're using it both as a personal computer and as a web host.

Edit:
You also said that you forward SSH to your laptop. Do you have password authemtication disabled?

Either way, your laptop is a prime suspect.


my laptop is setup to receive ssh - it is, according to Webmin - this ...

Allow Authentification By Password = Yes
Permit logins with empty Password = No
Allow login by Root = No
Allow RSA (SSH1) Authentification = Yes
Allow DSA (SHH2) Authentification = Yes
Check Permissions on Key Files = Yes
Display /etc/motd = No
Ignore Users known hosts files = No
Pre-Login Message File = None
User Authoration File = Default (~ssh/authorised _keys)
Ignore .rhosts files = Yes

Access Control.
Only allow users = All
Only allow groups = All
Deny Users = All
Deny groups = All

I thought, with Deny Users & groups = All - that this took priority over the allow ?
I'm not sure what you mean by pwned.
I think the above setting does make password authentification = Enabled.

Once again - the vB board is not run on my laptop. So, you are saying that someone could hop onto my laptop, then go onto and hack the remote server, which has it's own firewall / security etc. ?

Once again, thanks for bearing with me.


Phill.

---

### Post by bodhi.zazen on 2009-09-02
I think you really do not know how you were cracked and many things are possible.

You would need to perform forensics on your laptop and, better, the server that was compromised.

Blind guessing in the dark is not very helpful.

If you do not wish or know how to perform forensics you need to at a minimum back up your data and re-install.

At this time your weakest link by far is ssh. Use keys and disable password authentication. Use denyhosts or fail2ban.

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

You next weakness is mysql.

Look, if you wish to install servers you really need to stop and secure them. If they are private servers on your laptop they should listen to 127.0.0.1 and they should be firewalled from outside connections.

---

### Post by dmizer on 2009-09-02
> **phillw said:**
> Once again - the vB board is not run on my laptop. So, you are saying that someone could hop onto my laptop, then go onto and hack the remote server, which has it's own firewall / security etc. ?

Once someone has unauthorized access (pwned) to your laptop, it's trivial to gain access to everything your laptop has access to.

access laptop -> search firefox config for (or wait for you to type) passwords -> gain access to other things like email, remote websites, bank details ... etc.

---

### Post by phillw on 2009-09-02
This is becoming more aparrent as I read more stuff !!!

Me is thinking it's re-instal time. The test sites don't have very much data in them. So, i don't have masses of stuff to back-up.

Do i need to pay any particular checks to the html & php files I already have ?

MySQL databases will be a wrench to lose :-(  - I don't suppose it is safe to just import the databases, excepting schema from back-up into a new MySQL instal ?  

I think my playing with the sites as 'live' has come to an end !!!!
I noticed you said about setting Apache2 up to ONLY allow localhost - If you could point me in the direction of a tutorial for that - I'd be grateful.

Same with MySQL - In the case of MySQL, I can do that under phpMyadmin - is that a safe way to do so ?

I don't see a need for ssh (I think i was confusing it with https - still learning !!!) - my mess up :-\


Thanks,

Phill.

Turning the router back on to Firewall Everything has now been done. Yeah, so closing the stable door after the horse has bolted - but It'll help protect me while i get re-set up. In the meantime - Apache2 is 'stopped' and all stuff setup under webmin has been set to localhost only.

---

### Post by phillw on 2009-09-04
[http://ubuntuforums.org/showthread.php?t=1257770](http://ubuntuforums.org/showthread.php?t=1257770)

---

