---
title: "Cannot upgrade from 8.04 to 9.04"
date: 2009-08-06
forum: Server Platforms
---

### Post by reswob on 2009-08-06
OK, I've searched around a bit and I cannot find the exact answer to my question.  I've been trying to use the cli to upgrade my server from 8.04 to 9.04, but I keep getting the same error.  I've tried various commands discovered through searching the forums and the net, but I have not found the correct magic words.

>:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.3 LTS"

>:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
>:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

>:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

>:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The most common solution to this problem is entering the correct proxy information, but we either don't have a proxy or it is in transparent mode (which means, AFAIK, that I cannot enter:

sudo export http_proxy=http://user:passwd@proxy:port/
sudo export ftp_proxy=http://user:passwd@proxy:port/

and suddenly have my upgrade work.

Does anyone know of any other options/ideas?

Thanks.

Craig

---

### Post by trundlenut on 2009-08-06
As far as I know you can't jump releases with an upgrade. i.e. to get from 8.04 to 9.04 you first have to upgrade to 8.10 then to 9.04.

I'm sure I saw a guide on how to do it here but now I can't find it.  Try a search.

---

### Post by running_rabbit07 on 2009-08-06
Yeah, you have to go one at a time. May be easier and way faster to back up your files and settings then do a fresh install of JJ. If you have a /home partition it will be easy to just do a fresh install. If you want to create one before trying a fresh install read [go here]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by Wim Sturkenboom on 2009-08-06
@trundlenut and running_rabbit07
If you're right, how is it possible that I could go from 6.06 to 8.04 (desktop version)?

@reswob
Any good reason why you want to upgrade from a LTS version to a NON-LTS version? 8.04 server is supported till april 2013 while 9.04 server is supported till october 2010.

---

### Post by reswob on 2009-08-06
Security requirements dictate a kernel upgrade to 2.6.30.x and I thought upgrading to 9.04 would be the easiest way to do that.

If there is an alternative method to upgrade the kernel only, please let me know.  My searches for THAT has only led to compiling instructions and/or the same 'sudo apt-get dist-upgrade' instructions I've already tried.

I was really hoping to not compile my own kernel....

Thank 

Craig

---

### Post by running_rabbit07 on 2009-08-06
> **Wim Sturkenboom said:**
> @trundlenut and running_rabbit07
If you're right, how is it possible that I could go from 6.06 to 8.04 (desktop version)?

@reswob
Any good reason why you want to upgrade from a LTS version to a NON-LTS version? 8.04 server is supported till april 2013 while 9.04 server is supported till october 2010.


.....

---

### Post by slakkie on 2009-08-06
```

# see the file itself for comments
echo "Prompt=normal" | sudo tee -a /etc/update-manager/release-upgrades
sudo aptitude update && sudo aptitude safe-upgrade
sudo do-release-upgrade 

```

Then you will hit 8.10. Then you just need to run do-release-upgrade again and you are at 9.04

---

### Post by slakkie on 2009-08-06
> **running_rabbit07 said:**
> Maybe you should explain how to do it then being that you apparently know something that we don't.


6.06 is/was LTS, 8.04 is LTS. LTS to LTS is a supported method of upgrading.. So 8.04.x upgrade to 10.x LTS will also be supported. But 8.10/9.04 to 10.x LTS not, there you have to do a incremental upgrade, passing each intermediate release.

---

### Post by running_rabbit07 on 2009-08-06
> **slakkie said:**
> 6.06 is/was LTS, 8.04 is LTS. LTS to LTS is a supported method of upgrading..

That is what I was figuring. I recently had 8.04 on my laptop and it only went up one at a time via upgrade manager. of course if I had've waited until 10.04 which I think is the next LTS the update manager was going to do the update on it's own. After doing the update that way once, I will never do it again. It took way to long. Much faster to do a clean install, which is why I was recommending it.

BTW, is 6.06 server still being supported? I have seen a few people still claim to have it.

---

### Post by slakkie on 2009-08-06
I only do upgrades since I have plenty of stuff in /etc which I don't want to reconfigure. I make a backup of my full root mount point with clonezilla and then start the upgrade. 

I really doubt if a clean install is quicker, since I don't need to install all additional packages, nor do I need to reconfigure my applications which are used system wide (network/apache/squid/samba/etc).

6.06 server is still supported, desktop not.

> 
Ubuntu 6.06's support will end in June 2009 for desktops and June 2011 for servers. This will mean a lot of desktop only applications will not be supported anymore (see this list of supported packages) but once 6.06 will become EOL expect an update here. 


Taken from [https://help.ubuntu.com/community/EOLUpgrades#Upgrade%20path](https://help.ubuntu.com/community/EOLUpgrades#Upgrade%20path)

---

