---
title: "unique DNS resolution failure"
date: 2010-09-10
forum: Server Platforms
---

### Post by bobwdn on 2010-09-10
Some where during my past, I remember that I had incorrectly entered a host name in my /etc/hosts file. So, long ago, I had corrected the typo and thought all was well. Until this morning. 

While doing something else, I tailed my syslog file and found the following:
```
user@myserver:~$ tail -f /var/log/syslog
Sep 10 08:49:25 myserver sm-notify[682]: DNS resolution of bob-desktop.mistake,net failed; retrying later
```

Now, notice the comma after the word 'mistake'. I need to find and correct this incorrect comma punctuation. Thereby eliminating this DNS resolution failure.

Anyone know where I should look to find this?

I check my /etc/hosts file to confirm that it does not contain the comma error and it does not. Where is sm-notify finding this entry?

---

### Post by Ryan Dwyer on 2010-09-10
There could be an incorrect domain name configured on your DHCP server. Or if your IP is static then try checking /etc/resolv.conf.

---

### Post by bobwdn on 2010-09-10
Thanks Ryan, I checked /etc/resolv.conf and all is correct there.

What is so weird is that I remember that the error I typed was a comma, instead of a period, before the 'net'. And now, months later I find this log reference to that "old" typo error. 

I guess I don't understand DNS well enough. 

Where could this error be coming from?

---

### Post by terazen on 2010-09-10
I'm not sure where it would be, but if you try below maybe you get lucky...
```
sudo grep -iR "mistake,net" /etc
```
It might take a few, but good place to start.  Most hostname things are in /etc/ afaik.

---

### Post by Ryan Dwyer on 2010-09-10
Is mistake.net your local domain or does it belong to someone else? Maybe you have a bookmark to mistake,net or an email contact saved as someone@mistake,net. Or if you're using a browser such as Chrome, simply vising a page that links to [http://mistake,net/](http://mistake,net/) could cause your browser to do a lookup in advance.

Do other people use your server or just you? Is it running a DNS service? Do you remember what you were doing at 8:49am on the 10th?

---

### Post by bobwdn on 2010-09-11
Thanks both terazen & Ryan Dwyer for your suggestions.

terazen, here is the result from your suggestion:
```
sudo grep -iR "mistake,net" /etc
[sudo] password for administrator: 
grep: warning: /etc/backuppc/pc: recursive directory loop

grep: /etc/blkid.tab: No such file or directory
grep: /etc/fonts/conf.d/30-defoma.conf: No such file or directory
```
The only thing I see interesting is the 'backuppc' reference. But, in looking through backuppc stuff, I do not see a reference to 'mistake,net'.

Ryan Dwyer, 'mistake.net' is my local domain name. DNS is handled by my IPCop firewall. And finally, this server is my in-home file server and only my daughter's computer and my computer are connected to it.

*********
Now, to anyone interested. I returned to tail my current syslog file and find that the questioned entries do not appear. It was during a restart after removing a foldingathome configuration (I had done incorrectly) that I noticed the questioned "mistake,net" entry.

So, with the questioned entries not appearing, I restarted the computer and checked the syslog file again. There they are, only appearing four times during startup.

So, my conclusion is, that if they only appear during startup and then do not continue, maybe I should just ignore the entries.

Now, being VERY inexperienced at this level of system admin, I am curious as to the entries source, but I am thinking that maybe I don't need to concern myself with such a minor issue?

---

### Post by bab1 on 2010-09-11
> **bobwdn said:**
> 
Now, to anyone interested. I returned to tail my current syslog file and find that the questioned entries do not appear. It was during a restart after removing a foldingathome configuration (I had done incorrectly) that I noticed the questioned "mistake,net" entry.

So, with the questioned entries not appearing, I restarted the computer and checked the syslog file again. There they are, only appearing four times during startup.

So, my conclusion is, that if they only appear during startup and then do not continue, maybe I should just ignore the entries.

Now, being VERY inexperienced at this level of system admin, I am curious as to the entries source, but I am thinking that maybe I don't need to concern myself with such a minor issue?

The reference to sm-notify in the syslog is probably the answer to the root cause.  Did/Do you have NFS setup on this host?  The man page for sm-notify shows that the hosts it monitors might hold you erroneous entry.  See [**_here _**]("http://man.he.net/man8/sm-notify")for more info.

---

### Post by bobwdn on 2010-09-13
I found "mistake,net", now what do I do with it?

Following bab1 advice, I looked through the files referenced in 'sm-notify' man page and I found:
```
user@myserver:/var/lib/nfs/sm$ cd /var/lib/nfs/sm.bak
user@myserver:/var/lib/nfs/sm.bak$ ls -alh
total 12K
drwxr-xr-x 2 statd root 4.0K 2010-09-10 08:48 .
drwxr-xr-x 6 statd root 4.0K 2010-09-10 08:48 ..
-rw------- 1 statd root  109 2010-06-23 16:24 desktop.mistake,net
```
There is my "mistake,net" entry.

The primary directory /var/lib/nfs/sm has the correct "mistake.net" entry and the "mistake,net" is found in the /var/lib/nfs/sm.bak directory. I am thinking that this is backup file so, I just 'rm' the file?

---

### Post by bab1 on 2010-09-13
> **bobwdn said:**
> I found "mistake,net", now what do I do with it?

Following bab1 advice, I looked through the files referenced in 'sm-notify' man page and I found:
```
user@myserver:/var/lib/nfs/sm$ cd /var/lib/nfs/sm.bak
user@myserver:/var/lib/nfs/sm.bak$ ls -alh
total 12K
drwxr-xr-x 2 statd root 4.0K 2010-09-10 08:48 .
drwxr-xr-x 6 statd root 4.0K 2010-09-10 08:48 ..
-rw------- 1 statd root  109 2010-06-23 16:24 desktop.mistake,net
```
There is my "mistake,net" entry.

The primary directory /var/lib/nfs/sm has the correct "mistake.net" entry and the "mistake,net" is found in the /var/lib/nfs/sm.bak directory. I am thinking that this is backup file so, I just 'rm' the file?

You don't know what the reaction to removing the file will be.  I would ***move ***the file to a location away from the /var/lib/nfs files.  How about /var/lib/temp/  ?.  Then reboot to see your results.

---

