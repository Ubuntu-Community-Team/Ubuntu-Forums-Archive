---
title: "md5sum -c keeps failing"
date: 2009-09-02
forum: Security
---

### Post by methodtwo on 2009-09-02
Hi there
I've just downloaded snort.When i came to do:
```
#md5sum -c snortrules-2.8.tar.gz.md5
```
for the snort rules i got this message:
```
md5sum: ./snortrules-snapshot-2.8.tar.gz.md5: no properly formatted MD5 checksum lines found

```
Does this mean that my box is owned or what?.I don't know what to do next.I've tried deleting both the files and downloading the rules and the md5 files again but got the same result.
Any help would be great

---

### Post by methodtwo on 2009-09-02
I've just tried the same command and got the same results with snortrules-snapshot-CURRENT.tar.gz.md5

---

### Post by cdenley on 2009-09-02
I doubt you were owned. They wouldn't alter the md5 file so it isn't formatted correctly, unless they were attempting to modify it so it would match a maliciously modified copy of snort, but failed. Post the contents of the file.
```

snortrules-2.8.tar.gz.md5

```
I can't seem to download any rules at the moment (403 error). Maybe they are having problems.

---

### Post by methodtwo on 2009-09-02
Here is the contents of snortrules-snapshot-2.8.tar.gz.md5:
```
24d078090790461ebb1993a7d494c961
```
Thank you for your reply

---

### Post by cdenley on 2009-09-02
That is indeed formatted incorrectly. There is no filename, nothing to compare the checksum to. I wonder if it matches.
```

md5sum snortrules-snapshot-2.8.tar.gz

```

---

### Post by methodtwo on 2009-09-02
When i did:
```
#md5sum ./snortrules-snapshot-2.8.tar.gz
```
i got the same string as the one i just posted.Does this mean that it's all O.K?
Thanks for your guidance dude

---

### Post by cdenley on 2009-09-02
> **methodtwo said:**
> When i did:
```
#md5sum ./snortrules-snapshot-2.8.tar.gz
```
i got the same string as the one i just posted.Does this mean that it's all O.K?
Thanks for your guidance dude

Well, the checksum contained in snortrules-snapshot-2.8.tar.gz.md5 matches the checksum of snortrules-snapshot-2.8.tar.gz. This means the file was not corrupted during download. This doesn't verify that the file wasn't maliciously altered, since the hypothetical attacker could easily alter the md5 checksum to match.

---

### Post by methodtwo on 2009-09-02
What could/should i do now then?

---

### Post by cdenley on 2009-09-02
> **methodtwo said:**
> What could/should i do now then?

I suppose proceed with whatever you were trying to do. Is there a reason you couldn't install snort from the repos?
```

sudo apt-get install snort

```

---

### Post by methodtwo on 2009-09-02
I have downloaded the source for snort(wanting to follow [this]("http://ubuntuforums.org/showthread.php?t=919472") thread 
However when i did:
```
#md5sum -c ./snortrules-snapshot-2.8.tar.gz.md5
```
I got an error
My question is would installing from the repos, instead of source, download and install the snort rules as well.Also in the thread i mentioned snort is installed with mysql.How would i set up snort with apache+mysql if i installed from the repos?
Thank you for your time

---

### Post by methodtwo on 2009-09-02
Sorry that this is in the security discussions.It's just that my wanting to install from the repos instead of following the thread i mentioned is security related.Because when i did:
```
#md5sum -c ./snortrules-snapshot-2.8.tar.gz.md5
```
I keep getting an error saying that no properly formatted checksum lines were found.I've tried comparing the string i got from:
```
#cat ./snortrules-snapshot-2.8.tar.gz.md5
```
and:
```
#md5sum ./snortrules-snapshot-2.8.tar.gz

```
and they both match up.
However it has been pointed out to me that although the download might have been uncorrupted that it still doesn't prove that the file wasn't altered along with the checksum.

---

### Post by bodhi.zazen on 2009-09-02
I merged your threads as they seem related.

You may use snort in the repositories and it is a tad more automated, although the version of snort is a bit outdated and same with the rules.

```
apt-get snort-mysql
```

As far as your md5sum error, I would NEVER use anything security related if the md5sum is off like that. The thing to do is report this as a bug to snort.

---

### Post by methodtwo on 2009-09-02
Are you saying that it's safe for me to use snort from the repos but not the snort rules(2.8.tar.gz) that i downloaded?
Will the rules be included if i use the snort from the repos?.I'm guessing yes

---

### Post by methodtwo on 2009-09-02
Dear bodhi.zazen i was following your excellent thread on intrusion detection.If i install snort from the repos at which point do i pick up on your thread.I'm assuming that it's the part after the snort compile right?
Thank you for your time

---

### Post by methodtwo on 2009-09-02
bobhi.zazen
Seeing as though i followed your thread on intrusion detection up to the point of downloading the rules should i uninstall these:
```
libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev
```
Before doing:
```
#apt-get install snort-mysql
```
????

---

### Post by bodhi.zazen on 2009-09-03
You can try to pick up on the how-to after installing (compiling) snort.

As far as the packages, you should probably just leave what you have installed. If you like you can remove everything you installed, remove snort form your system, and start anew by installing snort-mysql from the repositories.

You will need apache for base.

As far as the rules, as I indicated, I would not use the rules if the md5sum is off. You may be able to get an old set of rules form the repositories, I do not know.

Personally I keep my IDS applications and rules as up to date as possible for what should be obvious reasons and so my advice is to compile snort and use an up to date rule set.

If the md5sum is off, you should contact snort.

---

### Post by cdenley on 2009-09-03
> **bodhi.zazen said:**
> 
If the md5sum is off, you should contact snort.

The md5sum wasn't incorrect, the file containing the correct checksum was not formatted correctly since the checksum was not followed by the filename. Also, as I said, you can't even download the rules right now (403 error), so they apparently have bigger problems at the moment.

---

### Post by bodhi.zazen on 2009-09-03
FYI I just downloaded the current snort rules and the md5sum is correct ;

```
bodhi@ufbt:~$ md5sum -c snortrules-snapshot-2.8.tar.gz.md5
snortrules-snapshot-2.8.tar.gz: OK
```

So, as I indicated, I assume there is a problem with the download of your rule set.

---

### Post by cdenley on 2009-09-03
The ruleset must have been fine since he indicated the md5 checksum matched the one contained in the checksum file. The error he received only showed that the file containing the correct checksum was not formatted properly, and the md5sum command failed to parse it. Apparently, if he wants to install manually, he could simply re-download the checksum file.

---

### Post by bodhi.zazen on 2009-09-03
> **cdenley said:**
> The md5sum wasn't incorrect, the file containing the correct checksum was not formatted correctly since the checksum was not followed by the filename. Also, as I said, you can't even download the rules right now (403 error), so they apparently have bigger problems at the moment.

You need to register and use your oinkcode to be able to download rules.

---

