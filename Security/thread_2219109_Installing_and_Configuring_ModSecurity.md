---
title: "Installing and Configuring ModSecurity"
date: 2014-04-23
forum: Security
---

### Post by Luft on 2014-04-23
If you're like me, the idea of running your own web server is both appealing and a bit scary.  I love the idea of hosting blogs and on-line gaming for my friends, family and other guests but as with many things, the bad guys are more than happy to drop a giant turd into the punch bowl.  There always has been and always will be a percentage of the world's population that are jerks.  No matter what you present to the world, no matter how good, this group of people can be counted on to try to spoil it in order to enrich themselves or out of a simple mean-spirited nature.  This is where ModSecurity is your friend.

In order for ModSecuity to help you it must be properly installed, configured and rules must be added and activated.  A mistake in any of these steps can, at best, stop your web server from running or at worse, allow your web server to run while at the same time giving you a false sense of security.  Also as new exploits are discovered the rules should be updated so that these exploits fail.

I will try to walk you through the process step by step but I am no expert in this area so please if you have information to contribute please do so.

This article assumes that you have LAMP installed which includes a working web server.  I have found that unlike the articles about ModSecurity already on the Internet, the articles dealing with the installation and configuration of LAMP are adequate.  If you need help you can find it [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").  However, the current package used by Ubuntu 14.04 to install ModSecurity has a number of differences that make using older setup and configuration instructions useless or at least not very helpful.  

In this article I will ask you to type in commands in a terminal window.  Hold down the Control and Alt keys and press the &#8220;T&#8221; key.  Note: I used the upper case &#8220;T&#8221; to make it easier to read but you should not hold down the shift key. i.e. use CNTL-ALT-lower case t.

Enter the following into a terminal:
**sudo apt-get install libapache2-modsecurity**

We have just installed ModSecurity and placed a default package of rules onto our system.

Now we need to place a modsecurity.conf configuration file into the** /etc/modsecurity** directory.  The configuration file is complex but luckily the package comes with a recommended configuration file that we can use as a starting point.  Let's copy the recommended file:
**sudo cp /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf**

We'll make changes to this file later but for now let's check the apache2 log directory:
**ls /var/log/apache2**

You should see three files: **access.log, error.log and  other_vhosts_access.log**.  This is the same as before we installed ModSecurity.  Now let's restart the apache2 service and check this directory again:

**sudo service apache2 reload**
**ls /var/log/apache2**

You should now see four files: **access.log, error.log, modsec_audit.log and other_vhosts_access.log**.
This is a good sign.  A new log called **modsec_audit.log** was created!

When modsecurity is installed it is configured to only detect threats based on it's activated rules and as far as I know, none of its rules are activated which makes the whole thing pretty useless.  We must do three things to get ModSecurity working:

1. Activate the rules.
2. Change the value in modsecurity.conf called SecRuleEngine from DetectionOnly to On.
3. Modify /etc/apache2/mods-available/Security2.conf.

You should ensure that the rules are working properly prior to changing SecRuleEngine from &#8220;DetectionOnly&#8221; to &#8220;On.&#8221;  A bad rule could block the users on your entire network from being able to access important services.  This is what is known as a RBE or "resume building event" in the I.T. sector.  So please, after we're finished, run ModSecurity set for DetectionOnly for a while and check your logs to determine if tweaks are needed.  If there is a rule blocking your entire network it may be wise to deactivate that rule prior to switching the SecRuleEngine value to &#8220;On.&#8221;  (Note: English grammar dictates that I place a period inside the quotes but it is not part of the actual value.  i.e. The value should be &#8220;SecRuleEngine On&#8221; not &#8220;SecRuleEngine On.&#8221; if you want it to work.)

Let's look into the modsecurity-crs direcotry:

**ls /usr/share/modsecurity-crs/**

You should see several directories and a conf file.  What we're interested in right now are the directories **activated_rules, base_rules, experimental_rules and optional_rules**.

Activating a rule is a simple task.  You simply put symbolic link into the activated_rules directory that points to the rule you wish to activate.

We want to activate all of the rules in the base_rules and optional_rules directories so execute the following commands in a terminal:

**cd /usr/share/modsecurity-crs/base_rules**
**for f in * ; do sudo ln -s /usr/share/modsecurity-crs/base_rules/$f /usr/share/modsecurity-crs/activated_rules/$f ; done**

**cd /usr/share/modsecurity-crs/optional_rules**
**for f in * ; do sudo ln -s /usr/share/modsecurity-crs/optional_rules/$f /usr/share/modsecurity-crs/activated_rules/$f ; done**

I tried activating the rules in experimental_rules directory but got an error message when I restarted apache2:  **Could not open geo database "/usr/share/GeoIP/GeoLiteCity.dat": No such file or directory**

I guess that's why they call it experimental.  If you think you might have better luck you can create the symlinks with the following commands:

[I][COLOR="#FF0000"]cd /usr/share/modsecurity-crs/experimental_rules
for f in * ; do sudo ln -s /usr/share/modsecurity-crs/experimental_rules/$f /usr/share/modsecurity-crs/activated_rules/$f ; done[/COLOR][/I]

Next we need to tell apache where to find the activated rules.  Open the /etc/apache2/mods-available/security2.conf file.

**sudo nano /etc/apache2/mods-available/security2.conf**

At the end of the file just before </IfModule> enter the following lines:

[B]Include "/usr/share/modsecurity-crs/*.conf"
Include "/usr/share/modsecurity-crs/activated_rules/*.conf"[/B]

Please note that the order is important.  If you switch them ModSecurity will not block anything.

The first line includes a set of rules that was in the modsecurity-crs directory and the second line tells appache where to find our symlinks .

Save the file by pressing CNTL-O.  (Hold the control key and press alpha O)
Then exit with CNTL-X

We must enable the headers module, this allows ModSecurity to control and modify the HTTP headers for both requests and responses.

**sudo a2enmod headers**

Now restart apache:
**sudo service apache2 restart**

ModSecurity should now be running in detection mode.  After you're sure it would not be blocking legitimate traffic you should do the following:

**sudo nano /etc/modsecurity/modsecurity.conf**

Find this line:
SecRuleEngine DetectionOnly

and change it to:

SecRuleEngine On

Then a final restart:

**sudo service apache2 restart**  (Thanks for catching that Trebacz.)

I hope these instructions help!

---

### Post by Habitual on 2014-04-23
excellent write-up.

---

### Post by Trebacz on 2014-06-28
Great post. You may need a last a "**sudo service apache2 restart**" to enable the rules (after enabling the rules). I assume the config is only read when it's loaded.

---

### Post by Tassos on 2014-08-07
How do I uninstall _**everything**_ by the mod_security ???

---

### Post by Luft on 2014-08-09
I've never tried to uninstall modsecurity but if you used apt-get to install it you can try: sudo apt-get remove libapache2-modsecurity

That will remove the main package.  It will leave any directory that had additional files added so you'll probably have to carefully go through your system to manually remove some stuff.  Maybe someone else will have a better method?

---

### Post by Luft on 2014-08-09
Thanks Trebacz!  I edited my post to include that.

---

