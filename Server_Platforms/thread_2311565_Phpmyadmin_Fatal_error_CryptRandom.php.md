---
title: "Phpmyadmin Fatal error: Crypt/Random.php"
date: 2016-01-28
forum: Server Platforms
---

### Post by opholdings on 2016-01-28
Ubuntu - Phpmyadmin

When accessing localhost/phpmyadmin the following error appears:

Fatal error: require(): Failed opening required '/usr/share/php//Crypt/Random.php' (include_path='.') in /usr/share/phpmyadmin/libraries/session.inc.php on line 16

The Session.inc.php and Random.php files are in the correct folders.

Any ideas?

---

### Post by antonio61 on 2016-01-28
I have the same problem in Ubuntu Server 14.04 LTS. I upgrade apache and phpmyadmin today an I got that error.

Maybe a permission problem?

---

### Post by giordano2 on 2016-01-28
I also have same problem... I changed the permissions to 0777 in /usr/share/php/* but the it keeps the problem....
I dont know what that could be....

---

### Post by clueo8 on 2016-01-28
The latest phpmyadmin 4:4.5.4-1 appears to have caused this error.  I updated this morning and found the same error in my error.log.

I reverted back to the previous version with apt-get using this as a guide: [http://askubuntu.com/questions/138284/how-to-downgrade-a-package-via-apt-get]("http://askubuntu.com/questions/138284/how-to-downgrade-a-package-via-apt-get")

Basically, running:
```
sudo apt-cache showpkg phpmyadmin
```

Will give you all the versions available:
```
Versions: 
4:4.5.4-1~ppa1~trusty1 (/var/lib/apt/lists/ppa.launchpad.net_vincent-c_ppa_ubuntu_dists_trusty_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/ppa.launchpad.net_vincent-c_ppa_ubuntu_dists_trusty_main_binary-amd64_Packages
                  MD5: 20eb9cc7cf4c215c79adaa7566554312
 Description Language: en
                 File: /var/lib/apt/lists/ppa.launchpad.net_vincent-c_ppa_ubuntu_dists_trusty_main_i18n_Translation-en
                  MD5: 20eb9cc7cf4c215c79adaa7566554312

4:4.0.10-1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages
                  MD5: 741cc5619fcb316ac8049f5906394984
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en
                  MD5: 741cc5619fcb316ac8049f5906394984



```

The top one is more recent and is the bad one, which I can see which version I was at with:
```
sudo apt-show-versions phpmyadmin 
phpmyadmin:all/trusty 4:4.5.4-1~ppa1~trusty1 uptodate
```

So I ran:
```
sudo apt-get install phpmyadmin=4:4.0.10-1
```

And kept my current configs, which is the default when prompted.

Then I didn't want to accidentally upgrade to the broken one, so I held it back with:
```
sudo apt-mark hold phpmyadmin
```

So the next time you run an apt-get upgrade, you will see:
```
The following packages have been kept back:
  phpmyadmin

```

I'll give it a few days/weeks before I upgrade phpmyadmin, hopefully they straighten out this issue in a future release... FYI: You can unhold with:
```
sudo apt-mark unhold phpmyadmin
```

Then it should be back to normal when running an apt-get upgrade

---

### Post by giordano2 on 2016-01-28
Perfect... Tks

---

### Post by manifold2 on 2016-01-28
Brilliant, thanks for this catch and the clear examples on how to protect ourselves.  Thanks!

---

### Post by Habitual on 2016-01-28
> **giordano2 said:**
> I changed the permissions to 0777 in /usr/share/php/* Bad, bad habit and as you can see, it doesn't fix anything.
You really should not do that any more. Ever.

[0]777 Never Fixed Anything.

---

### Post by opholdings on 2016-01-28
Thanks Clueo8. Works great.

---

### Post by DaSuperGrover on 2016-01-30
Worked great!

Wonder whether this will be solved quickly, anybody already filed a bug report?

---

### Post by clueo8 on 2016-02-03
It appears the 4:4.5.4.1-1 was released and it fixes this error, source: [http://askubuntu.com/questions/727125/phpmyadmin-not-working-chrome-show-error-500-firefox-shows-nothing](http://askubuntu.com/questions/727125/phpmyadmin-not-working-chrome-show-error-500-firefox-shows-nothing)

I did the unhold on the phpmyadmin package and updated and it appears to be working...

During the upgrade it wanted to upgrade a common db that phpmyadmin uses, but it didn't seem to upgrade cleanly (kept asking me the same thing over and over again)... but I was able to skip that part and the web gui for phpmyadmin appears to work...

---

