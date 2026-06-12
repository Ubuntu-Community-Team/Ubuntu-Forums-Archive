---
title: "[SOLVED] rkhunter log analysis"
date: 2008-09-15
forum: Security
---

### Post by lovinglinux on 2008-09-15
I need some help to understand these results:
> ...
[20:38:42] /bin/egrep                                        [ OK ]
[20:38:42] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
...
[20:38:43] /bin/fgrep                                        [ OK ]
[20:38:43] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
...
[20:38:48] /usr/bin/groups                                   [ OK ]
[20:38:48] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
...
[20:38:49] /usr/bin/ldd                                      [ OK ]
[20:38:49] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
...
[20:38:52] /usr/bin/sudo                                     [[COLOR="Red"]** Warning**[/COLOR] ]
[20:38:52] Warning: The file properties have changed:
[20:38:52]          File: /usr/bin/sudo
...
[20:38:55] /usr/bin/lwp-request                              [ OK ]
[20:38:55] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
...
[20:38:58] /usr/sbin/adduser                                 [ OK ]
[20:38:58] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.

---

### Post by Dave_Connor on 2008-09-15
Sudo was recently updated, "sudo rkhunter -propupdate" and run rkhunter again.

---

### Post by ayenack on 2008-09-16
Just a quick heads up that should be.

**sudo rkhunter --propupdate**

May also be an ideal to run these.

**sudo rkhunter --update** (Will update rkhunter.)
**sudo rkhunter -c -sk** (sudo rkhunter -c will run rkhunter and -sk will skip the pause screens.)

---

### Post by lovinglinux on 2008-09-16
> **ayenack said:**
> Just a quick heads up that should be.

**sudo rkhunter --propupdate**

Thank you both. I assume this means the sudo binary was update from the repository right? Nothing to fear?

And what about those files with "Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check." What does this means? Sounds like something that is trying to bypass a check :)

---

### Post by ayenack on 2008-09-16
> **lovinglinux said:**
> Thank you both. I assume this means the sudo binary was update from the repository right? Nothing to fear?

And what about those files with "Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check." What does this means? Sounds like something that is trying to bypass a check :)

Yes it was. So nothing to fear from the sudo. 

As for egrep check the md5checksum.

**md5sum /bin/egrep**

This is mine.

[B]ayenack@ubuntu:~$ md5sum /bin/egrep
5bc0f4598a8cd6b33740b240fe5fbaf7  /bin/egrep[/B]

Yours should match. If they are the same then alls well. If they are not then one of us may have a problem :(

You could also use this (I think) to see if the results are the same or not.

**sudo rkhunter --check --pkgmgr dpkg**

---

### Post by lovinglinux on 2008-09-16
> **ayenack said:**
> This is mine.

[B]ayenack@ubuntu:~$ md5sum /bin/egrep
5bc0f4598a8cd6b33740b240fe5fbaf7  /bin/egrep[/B]

Yours should match. If they are the same then alls well. If they are not then one of us may have a problem :(

The md5checksum match :)

> **ayenack said:**
> You could also use this (I think) to see if the results are the same or not.

**sudo rkhunter --check --pkgmgr dpkg**

With this command the result log does not show those lines with "it is whitelisted for the 'script replacement' check."

What is the difference from "sudo rkhunter -c -sk"?

---

### Post by skew on 2008-09-16
> **ayenack said:**
> 

As for egrep check the md5checksum.

**md5sum /bin/egrep**

This is mine.

[B]ayenack@ubuntu:~$ md5sum /bin/egrep
5bc0f4598a8cd6b33740b240fe5fbaf7  /bin/egrep[/B]

Yours should match. If they are the same then alls well. If they are not then one of us may have a problem :(

Maybe you could help me out at the same time. Is their a master list somewhere that I can refer to that'll show what the correct md5checksums should be for programs that are found in the
repository?

 If not how do you check the md5sum results returned for authenticity?

thx

---

### Post by ayenack on 2008-09-16
> **lovinglinux said:**
> The md5checksum match :)



With this command the result log does not show those lines with "it is whitelisted for the 'script replacement' check."

What is the difference from "sudo rkhunter -c -sk"?

As I understand it.
It's using [dpkg]("http://en.wikipedia.org/wiki/Dpkg") **P**ac**k**a**g**e **M**ana**g**e**r** to compare the files so if there are no flags everything should be fine. If you are using  -c -sk it's checking against its own logs. By the way -sk just stands for skip and makes it so rkhunter does not pause and wait for you to press return.

---

### Post by ayenack on 2008-09-16
> **skew said:**
> Maybe you could help me out at the same time. Is their a master list somewhere that I can refer to that'll show what the correct md5checksums should be for programs that are found in the
repository?

 If not how do you check the md5sum results returned for authenticity?

thx

Not that I know of. If you want to check each package you've installed then you could md5sum each package something like this.

md5sum /bin/egrep /usr/bin/firefox /usr/sbin/adduser

And so on but it'd take an age. Then you could ask other people to paste there md5sums to compare or where appropriate check out the package home page for each program and check the md5sum.

It's easier to check the distro md5sum when you download Ubuntu. Check out this link.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This needs to be run on your install cd/dvd. Then just check each time you install a program that the md5sum matches that which is on the home page of the program.

These are the hashes for each Ubuntu distro.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Basically if you install something from the repo's then you'll have no problems. If there was a problem found with one of the programs in the repo's a fix would come down the line pretty soon afterwards. Or some sort of warning would be submitted. As far as I know this has not happened.

You could run a command something like this.

**md5sum /home/your_user_name_here/*/***

Or as root.

**sudo su**

Then.
**md5sum /*/***

Then try to check them with individual sites. But this would generate huge amounts hashes.

---

### Post by lovinglinux on 2008-09-16
> **ayenack said:**
> As I understand it.
It's using [dpkg]("http://en.wikipedia.org/wiki/Dpkg") **P**ac**k**a**g**e **M**ana**g**e**r** to compare the files so if there are no flags everything should be fine. If you are using  -c -sk it's checking against its own logs. By the way -sk just stands for skip and makes it so rkhunter does not pause and wait for you to press return.

Thank you very much for the explanation. Everything is clear for me now, so I will mark the thread as SOLVED.

---

