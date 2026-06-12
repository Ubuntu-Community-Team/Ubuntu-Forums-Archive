---
title: "Odd rkhunter reports"
date: 2010-11-08
forum: Security
---

### Post by epz on 2010-11-08
Hello everyone,

I recently ran a rkhunter check and in my log i have found some very odd (to me at least) reports.

/usr/bin/last                                     [ Warning ]
Warning: The file properties have changed:
File: /usr/bin/last
Current hash: 0061d9ec8fcdad3fe69c803bcfcb8ee6a14e65ac
Stored hash : 2528527d90dfd5444dc65deb030ab5ca98a0af25
Current inode: 5244885    Stored inode: 5243495
Current file modification time: 1288629357 (01-nov-2010 17:35:57)
Stored file modification time : 1285352194 (24-set-2010 20:16:34)



/usr/bin/ldd                                      [ Warning ]
Warning: The file properties have changed:
File: /usr/bin/ldd
Current hash: 940d39673059474952bd3e81ea4da0c62b30a885
Stored hash : 38716f3fb2717b91e2fdeb0e6f5605de067ff8bb
Current inode: 5244505    Stored inode: 5243504
Current file modification time: 1287712233 (22-ott-2010 03:50:33)
Stored file modification time : 1284143534 (10-set-2010 20:32:14)
Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.



Warning: The file properties have changed:
File: /sbin/sulogin
Current hash: 8cdaf38b57c9f7b306cb7afbda801820c5895581
Stored hash : 24dbf1248934713c18b82e2faba31f3df2843adf
Current inode: 920742    Stored inode: 917655
Current file modification time: 1288629357 (01-nov-2010 17:35:57)
Stored file modification time : 1285352194 (24-set-2010 20:16:34)


Details:

I reinstalled Ubuntu today (had to wipe hard disk) so i can't say if some update affected it (in case of false positives), all I did while updating the system was watch some videos on youtube with gstreamer so i don't really expect my system to have been compromised like that (that doesn't happen even to windows so i think here im ok).

my kernel is (in case it would ever matter)


2.6.35-23-generic-pae #37-Ubuntu SMP Fri Nov 5 20:57:06 UTC 2010 i686 GNU/Linux

while updating i had ufw enabled my only "weak" setting is dns (mines fail lol but that i know updates are signed so it should be ok)







would anyone help me out understand whats wrong with those? and, if possible post your hashes for those files (sha1) so we can compare them?

thanks in advance


ps: notify me if i skipped any detail you might want to know

---

### Post by cariboo on 2010-11-08
Check the version numbers of the flagged files against the versions in the repositories.

Did you update the rkhunter database before running it? The results look like the normal rkhunter false positives.

---

### Post by epz on 2010-11-08
> **cariboo907 said:**
> Check the version numbers of the flagged files against the versions in the repositories.


this is abit unclear, are you wondering if I used software that is not in repos? Because if so no I didn't else i just misunderstood (awfully) that statement (in case what did you mean?)


> **cariboo907 said:**
> Did you update the rkhunter database before running it? The results look like the normal rkhunter false positives.



sudo rkhunter --update??  yes
sudo rkhunter --propupd?? no


mind giving me your hashes for those ? (i don't think it would be exposing anything personal of  you)

---

### Post by epz on 2010-11-09
bump

---

### Post by street spirit on 2010-11-09
For what it's worth, I've received the same warnings about last and sulogin, with the same hash values and mtimes:

> **epz said:**
> /usr/bin/last
Current hash: 0061d9ec8fcdad3fe69c803bcfcb8ee6a14e65ac
Current file modification time: 1288629357 (01-nov-2010 17:35:57)

File: /sbin/sulogin
Current hash: 8cdaf38b57c9f7b306cb7afbda801820c5895581
Current file modification time: 1288629357 (01-nov-2010 17:35:57)


Not ldd, though.

I think these are normal replacements caused by an "aptitude safe-upgrade", but I decided to look for the hash values just to be safe, which led me to your post.

---

### Post by iponeverything on 2010-11-09
I have see sulogin, last and ldd in rkhunter false positives in reports before.

---

### Post by halj32 on 2010-11-09
if youve updated your system you may need to run this
sudo rkhunter --propupd 

to get rid of the false positives

---

### Post by epz on 2010-11-09
> **street spirit said:**
>  I think these are normal replacements caused by an &quot;aptitude safe-upgrade&quot;, but I decided to look for the hash values just to be safe, which led me to your post.

 google indexed my post lol> **iponeverything said:**
> I have see sulogin, last and ldd in rkhunter false positives in reports before.

 yea i seen them too but it doesn't mean this time it wouldn't be a compromised system   > **halj32 said:**
> if youve updated your system you may need to run this
sudo rkhunter --propupd 

to get rid of the false positives    propupd trusts the checked files, if they are compromised it will still trust them hence before doing so i'd like to be sure they are ok, you have my same hashes? (sha1)

---

### Post by iponeverything on 2010-11-09
fair enough.. 

note the md5's on the files
do a reinstall of packages containing last, sulogin and ldd
and check your new md5's

---

### Post by street spirit on 2010-11-09
> **iponeverything said:**
> note the md5's on the files
do a reinstall of packages containing last, sulogin and ldd
and check your new md5's

I just did that ("sulogin" and "last" are both in the sysvinit-utils package). After reinstalling the package, the hashes are still the same as the "current" ones reported by rkhunter (BTW, they are SHA-1 hashes, not MD5). I guess this means either a) that everything's fine, and it's safe to use -propupd, or b) that the system is compromised, and some clever rootkit is showing me whatever it wants to. My personal paranoia level is currently configured at 3 out of 5, so I'm going to go with (a). ;-)

---

### Post by MechaMechanism on 2010-11-09
sudo dpkg-reconfigure rkhunter

Set rkhunter to auto update the database in cron.  Some updates change the hashes and it can take rkhunter up to 24 hours to update.  I would like to point out that rkhunter database can be fooled this way.  I still use it though.

---

