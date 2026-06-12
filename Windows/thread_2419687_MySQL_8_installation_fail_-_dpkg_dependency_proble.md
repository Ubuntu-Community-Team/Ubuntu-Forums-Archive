---
title: "MySQL 8 installation fail - dpkg: dependency problems prevent configuration of mysql-"
date: 2019-05-24
forum: Windows
---

### Post by rjnfrazao on 2019-05-24
I wasn't able yet to install MySQL 8 in Ubuntu.

[LIST]
[*]Distribution : Ubuntu 18.04.2 LTS (running on windows using WSL)
[*]WSL version : 4.4.0-17134-Microsoft
[*]Mysql-server : 8.0.16-2ubuntu18.04 amd64
[*]
[/LIST]
I am following these instructions - [Steps for a fresh installation of MySQL]("https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#apt-repo-fresh-install")

I have tried some suggestions that I found at the internet, based on similar cases, but none of them worked. 
Example 1 : sudo apt -f install -> In order to fix the dependency problem.
. 
Example 2 : Remove installation -> update distro -> install it again.

Example 3 : Update post installation script for Msql Community Server, in order to manually edit it and add set -e on 2nd line to ignore any error (basically invoke-rc.d/init fails to restart the mysql service). restart it manually after. 

Well all those options failed.

After the installation, I run the command to start the mysql server, but the service isn't recognized, so the installation fail.

Based on my experience, it's very hard to evaluate exactly the root cause of the problem, any suggestion recommendation and suggestion would be really appreciated. I am planning to follow this installation process My SQL Community Server, [https://dev.mysql.com/downloads/mysql/](https://dev.mysql.com/downloads/mysql/), where I can select the packages to be installed.



```
dpkg -l | grep mysql -> Installed Packages


ii  mysql-apt-config               0.8.13-1                           all          Auto configuration for MySQL APT Repo.
ii  mysql-client                   8.0.16-2ubuntu18.04                amd64        MySQL Client meta package depending on latest version
ii  mysql-common                   8.0.16-2ubuntu18.04                amd64        Common files shared between packages
ii  mysql-community-client         8.0.16-2ubuntu18.04                amd64        MySQL Client
ii  mysql-community-client-core    8.0.16-2ubuntu18.04                amd64        MySQL Client Core Binaries
iF  mysql-community-server         8.0.16-2ubuntu18.04                amd64        MySQL Server
ii  mysql-community-server-core    8.0.16-2ubuntu18.04                amd64        MySQL Server Core Binaires
iU  mysql-server                   8.0.16-2ubuntu18.04                amd64        MySQL Server meta package depending on latest version



Installation log


update-alternatives: using /var/lib/mecab/dic/ipadic to provide /var/lib/mecab/dic/debian (mecab-dictionary) in auto mode
Setting up mysql-client (8.0.16-2ubuntu18.04) ...
Setting up mysql-community-server-core (8.0.16-2ubuntu18.04) ...
Setting up mecab-ipadic-utf8 (2.7.0-20070801+main-1) ...
Compiling IPA dictionary for Mecab.  This takes long time...
reading /usr/share/mecab/dic/ipadic/unk.def ... 40
emitting double-array: 100% |###########################################|
/usr/share/mecab/dic/ipadic/model.def is not found. skipped.
reading /usr/share/mecab/dic/ipadic/Adj.csv ... 27210
reading /usr/share/mecab/dic/ipadic/Adnominal.csv ... 135
reading /usr/share/mecab/dic/ipadic/Adverb.csv ... 3032
reading /usr/share/mecab/dic/ipadic/Auxil.csv ... 199
reading /usr/share/mecab/dic/ipadic/Conjunction.csv ... 171
reading /usr/share/mecab/dic/ipadic/Filler.csv ... 19
reading /usr/share/mecab/dic/ipadic/Interjection.csv ... 252
reading /usr/share/mecab/dic/ipadic/Noun.adjv.csv ... 3328
reading /usr/share/mecab/dic/ipadic/Noun.adverbal.csv ... 795
reading /usr/share/mecab/dic/ipadic/Noun.csv ... 60477
reading /usr/share/mecab/dic/ipadic/Noun.demonst.csv ... 120
reading /usr/share/mecab/dic/ipadic/Noun.nai.csv ... 42
reading /usr/share/mecab/dic/ipadic/Noun.name.csv ... 34202
reading /usr/share/mecab/dic/ipadic/Noun.number.csv ... 42
reading /usr/share/mecab/dic/ipadic/Noun.org.csv ... 16668
reading /usr/share/mecab/dic/ipadic/Noun.others.csv ... 151
reading /usr/share/mecab/dic/ipadic/Noun.place.csv ... 72999
reading /usr/share/mecab/dic/ipadic/Noun.proper.csv ... 27327
reading /usr/share/mecab/dic/ipadic/Noun.verbal.csv ... 12146
reading /usr/share/mecab/dic/ipadic/Others.csv ... 2
reading /usr/share/mecab/dic/ipadic/Postp-col.csv ... 91
reading /usr/share/mecab/dic/ipadic/Postp.csv ... 146
reading /usr/share/mecab/dic/ipadic/Prefix.csv ... 221
reading /usr/share/mecab/dic/ipadic/Suffix.csv ... 1393
reading /usr/share/mecab/dic/ipadic/Symbol.csv ... 208
reading /usr/share/mecab/dic/ipadic/Verb.csv ... 130750
emitting double-array: 100% |###########################################|
reading /usr/share/mecab/dic/ipadic/matrix.def ... 1316x1316
emitting matrix      : 100% |###########################################|


done!
update-alternatives: using /var/lib/mecab/dic/ipadic-utf8 to provide /var/lib/mecab/dic/debian (mecab-dictionary) in auto mode
Setting up mysql-community-server (8.0.16-2ubuntu18.04) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
dpkg: error processing package mysql-community-server (--configure):
 installed mysql-community-server package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-community-server (= 8.0.16-2ubuntu18.04); however:
  Package mysql-community-server is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wildmanne39 on 2019-05-24
Hello and welcome to the forum!

*Thread moved to **Windows a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by rjnfrazao on 2019-05-25
I found a useful link : [https://github.com/Microsoft/WSL/issues/3631](https://github.com/Microsoft/WSL/issues/3631), @jw-redpanda put some light in my problem. He mentions a installation problem at MySql 8.0 using WSL in windows. The MySQl doesn´t start. He presents a workaround, well for me I was able to install version 5.7 at least, but I wasn't able to proceed after step 5, when you have the version 8 as candidate.  It worked for others, so good luck for you.

---

