---
title: "Possible keylogger, rootkit?"
date: 2010-06-25
forum: Security
---

### Post by burton247 on 2010-06-25
Im running ubuntu 10.04, pretty standard install. This morning my girlfriends email account has taken over and the password changed, and security question/location. Anyway the point in she's locked out and it's not anyone we know cause the security question was changed to Chinese...

I wouldn't have thought it would be my Linux computer but she has logged into her emails here recently so I wanted to check. She has 3 windows computers at hers. I did some research and decided to give my computer a rootkit scan using chkrootkit. 

I have some things come up and I've checked a few and they appear to be fine. I don't really want to google everything so if someone with experience can see anything suspicious in the following that would be great:

<code>
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/xulrunner-1.9.2.3/.autoreg /usr/lib/pymodules/python2.6/.path /usr/lib/eclipse/.eclipseproduct /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/profileRegistry/PlatformProfile.profile/.lock /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/profileRegistry/PlatformProfile.profile/.data /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/.settings /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/65/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/61/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/73/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/31/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/74/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/94/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/103/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/78/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/124/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/75/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/71/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/127/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/14/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/28/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/15/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/144/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/.bundledata.3 /usr/lib/eclipse/configuration/org.eclipse.osgi/.state.2 /usr/lib/eclipse/configuration/org.eclipse.osgi/.lazy.2 /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager/.fileTable.8 /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager/.fileTable.7 /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager/.fileTableLock /usr/lib/eclipse/plugins/org.eclipse.jdt.debug_3.5.0.v20090526/.api_description /usr/lib/eclipse/plugins/org.eclipse.ui.workbench.compatibility_3.2.0.I20090429-1800/.api_description /usr/lib/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.300.v20090526/.options /usr/lib/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.300.v20090526/.api_description /usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility.registry_3.2.200.v20090429-1800/.api_description /usr/lib/eclipse/plugins/org.eclipse.pde.build_3.5.2.R35x_20100114/.options /usr/lib/eclipse/plugins/org.eclipse.pde.build_3.5.2.R35x_20100114/.api_description /usr/lib/firefox-3.6.3/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo
/usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/profileRegistry/PlatformProfile.profile/.data /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/.settings /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/65/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/61/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/73/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/31/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/74/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/94/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/103/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/78/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/124/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/75/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/71/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/127/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/14/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/28/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/15/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/144/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager
</code>

Most if it all does appear to be eclipse based. I installed the add-on for C++ so could that be the reason it's throwing these up as suspicious? just because it doesn't know them?

Any help would be really appreciated, I think I'll run rkhunter too. Also, any ideas of another way to help my find a hole or keylogger would be great.

---

### Post by burton247 on 2010-06-25
rkhunter gave me:
<code>
[11:01:52] Checking the local host...
[11:01:52] Info: Starting test name 'local_host'
[11:01:52]
[11:01:52] Performing system boot checks
[11:01:52] Info: Starting test name 'startup_files'
[11:01:52]   Checking for local host name                    [ Found ]
[11:01:52] Info: Starting test name 'startup_malware'
[11:01:52]   Checking for system startup files               [ Found ]
[11:01:52]   Checking system startup files for malware       [ None found ]
[11:01:52]
[11:01:52] Performing group and account checks
[11:01:52] Info: Starting test name 'group_accounts'
[11:01:52]   Checking for passwd file                        [ Found ]
[11:01:52] Info: Found password file: /etc/passwd
[11:01:52]   Checking for root equivalent (UID 0) accounts   [ None found ]
[11:01:53] Info: Found shadow file: /etc/shadow
[11:01:53]   Checking for passwordless accounts              [ None found ]
[11:01:53] Info: Starting test name 'passwd_changes'
[11:01:53]   Checking for passwd file changes                [ None found ]
[11:01:53] Info: Starting test name 'group_changes'
[11:01:53]   Checking for group file changes                 [ None found ]
[11:01:53]   Checking root account shell history files       [ OK ]
[11:01:53]
[11:01:53] Performing system configuration file checks
[11:01:53] Info: Starting test name 'system_configs'
[11:01:53]   Checking for SSH configuration file             [ Not found ]
[11:01:53]   Checking for running syslog daemon              [ Found ]
[11:01:53]   Checking for syslog configuration file          [ Found ]
[11:01:53] Info: Found syslog configuration file: /etc/rsyslog.conf
[11:01:53]   Checking if syslog remote logging is allowed    [ Not allowed ]
[11:01:53]
[11:01:53] Performing filesystem checks
[11:01:53] Info: Starting test name 'filesystem'
[11:01:53] Info: SCAN_MODE_DEV set to 'THOROUGH'
[11:01:53]   Checking /dev for suspicious file types         [ Warning ]
[11:01:53] Warning: Suspicious file types found in /dev:
[11:01:53]          /dev/shm/pulse-shm-2786481481: data
[11:01:53]          /dev/shm/pulse-shm-931637456: data
[11:01:53]          /dev/shm/pulse-shm-1441134836: data
[11:01:53]          /dev/shm/pulse-shm-2627456189: data
[11:01:53]          /dev/shm/pulse-shm-2782141927: data
[11:01:54]          /dev/shm/pulse-shm-2808876141: data
[11:01:54]          /dev/shm/pulse-shm-2149920972: data
[11:01:54]          /dev/shm/pulse-shm-1981829828: data
[11:01:54]          /dev/shm/pulse-shm-2013804589: data
[11:01:54]          /dev/shm/pulse-shm-160451670: data
[11:01:54]   Checking for hidden files and directories       [ Warning ]
[11:01:54] Warning: Hidden directory found: /etc/.java
[11:01:54] Warning: Hidden directory found: /dev/.udev
[11:01:54] Warning: Hidden directory found: /dev/.initramfs

</code>

At the end it day say nothing was found though

---

### Post by Rubi1200 on 2010-06-25
For general security information please read the security sticky by bodhi.zazen:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

chkrootkit:

[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)

rkhunter:

[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

In general, you should know that things like keyloggers and rootkits can only be installed with user interaction; that means you allowed something to run which you should not have allowed.

Stick to the official Ubuntu repositories, don't install software from untrusted sources, keep Firefox as secure as possible and read the logs.

---

### Post by burton247 on 2010-06-25
Cheers for the reply. I read the general section before I posted. Not quite sure why you linked me to how to operate chkrootkit and rkhunter as it was only a snippet of information explaining how to use.

Yeah I know nothing should have been installed without me allowing and to my knowledge I haven't. I'm always really careful when downloading software and doing anything with root privileges. I stick to the repos unless I know the software is fine.

But you can't be too careful when someone has been using your computer then a couple of days later had their email account compromised by the Chinese.

---

### Post by Rubi1200 on 2010-06-25
The main reason for posting the links for rkhunter and chkrootkit was because bodhi.zazen writes there:

> [COLOR=navy]**Etiquette: If you are going to run these tools, please read the documentation (FAQ / README ) and perform a google search on the results of alerts or warnings before posting on the forums.**[/COLOR]

No disrespect intended, but many people post without even conducting a basic Google search.

That said, your approach seems sensible regarding security.

This might also interest you:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

and this:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

:-)

---

### Post by OpSecShellshock on 2010-06-25
As far as your girlfriend's webmail account, the issue is more likely either malware on her Windows machine, she was successfully phished, or she used the same password for that account as for something else and that got phished. Main point is there are a lot of ways to compromise a free webmail account that don't involve the tedious process of getting unauthorized software installed on a Linux computer without the administrator's knowledge.

---

### Post by burton247 on 2010-06-25
Yeah I know I should have done, but I panicked at the thought that someone might have email password and have got all my paypal, ebay, web hosting etc and thought as the ones I hadn't checked were all eclipse based someone might be able to say it's fine without searching. Or that Something might be an issue and I'd been wasting time searching instead of booting to a different OS and changing passwords :)

I thought apparmor was pretty much deprecated but they may have been something else...

Cheers for the links though, they look good

---

### Post by yeleek on 2010-06-25
> **Rubi1200 said:**
> For general security information please read the security sticky by bodhi.zazen:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

chkrootkit:

[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)

rkhunter:

[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

In general, you should know that things like keyloggers and rootkits can only be installed with user interaction; that means you allowed something to run which you should not have allowed.

Stick to the official Ubuntu repositories, don't install software from untrusted sources, keep Firefox as secure as possible and read the logs.

Spot on.

Me - I'd be going over those 3 wintel machines and see if shes used a public wlan anywhere.

---

### Post by burton247 on 2010-06-25
Well I always thought it would be one of her computers but I just wanted to check. 

It must have happened recently so I'd say no to anything public. I've told her not to use any of her computers till I've looked at them. 

I asked if she "forgot her password" recently but she doesn't think so. Although phishing is the most common cause really

---

### Post by bodhi.zazen on 2010-06-25
If you are going to use tools such as this, read the man page, read the documentation on the web page, and do a google search. 

This advice is not "rtfm", but only you can determine what any warning mean. 

Warning are exactly that, an indication that you need to do a little more leg work.

To some extent you answered your own question with the second post:

> At the end it day say nothing was found though

These tools, rootkit detection, are very generic in that they are written of linux in general and not specific to Ubuntu, so ...

1. Start by running the tools on a known good install. How else would you know what is normal ? You can not start by running the tools on a possibly compromised system with no clue as to normal output of these commands.

2. Google search any warnings.

3. Now that you have done #1 and #2 , try again on the suspect computer.

Are the results the same or different ? What has changed ? What did google tell you about these things ?

This is the general process with any os, this is how you remove a virus on Windows (google search for documentation) and you will need to do the same on Linux.

There are no shortcuts and as we do not know what is normal for your system we can not do this work for you.

If you have a specific question about a specific result you may post that.

---

### Post by rookcifer on 2010-06-25
Avoid rootkit scanners, as they are quite worthless and rarely provide usable information (unless one really knows their system very well) and are subject to manipulation.  If an attacker has compromised your machine to the point where he can install a rootkit, it follows that he will probably alter the rootkit scanner so that it wont find it.  Remember, a rootkit is something that an attacker uses *after* he has already compromised your machine.  It is nothing but a tool the attacker uses to maintain access to the machine and hide his tracks.

A better solution is to setup AIDE or Tripwire directly after a fresh install, put the image on removable media (that has no physical access to your machine) and then run periodic comparisons of the two to see what has changed.  However, just like with rootkit scanners, it still takes a lot of expertise to understand what's going on because many legitimate files will have changed.  The advantage these IDS's have over rootkit scanners is they cannot be manipulated by the attacker if they are used properly (setup right after a fresh install and then stored on physically separate media).

If it were me, I would avoid both IDS's and rootkit scanners on a desktop machine.  They are FAR more trouble than they're worth.  The risk/reward ratio just doesn't compute.

---

### Post by bodhi.zazen on 2010-06-25
> **rookcifer said:**
> If it were me, I would avoid both IDS's and rootkit scanners on a desktop machine.  They are FAR more trouble than they're worth.  The risk/reward ratio just doesn't compute.

+1 on that. IMO your time is much better spent learning apparmor or selinux.

You might like something like OSSEC, lower maintenance then AIDE or Tripwire.

---

### Post by burton247 on 2010-06-25
Oh ok then. I'll have a look, I'm always up for learning something and better understanding my system

---

