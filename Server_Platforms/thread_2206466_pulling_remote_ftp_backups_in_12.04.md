---
title: "pulling remote ftp backups in 12.04"
date: 2014-02-19
forum: Server Platforms
---

### Post by michaelebsch on 2014-02-19
I am wondering what the best solution to my most recent undertaking is. I have clients that I am managing websites for, now I do some manual backups of their sites as I make major changes, but these are manual and the files are either stored locally on the hosting server or pulled over to me through an http protocol (browser download).

I currently have a few servers running 12.04, one of which with a 20TB array. is there a relatively simple solution for pulling a backup through ftp from the remote hosting server. The only reason I ask is because while all of them so far have the ability to schedule regular backups, as any good hosting provider should, but less than half have the ability to send this via ftp. 

So what I would like to do is setup the hosting servers regular backup. Then tell my server to access the site over ftp, on a cron schedule,  and pull that backup folder to my local storage. First, is it possible, and second, what would be the best way to go about it if it is? Any assistance is greatly appreciated, thanks!

---

### Post by TheFu on 2014-02-19
> **michaelebsch said:**
> I am wondering what the best solution to my most recent undertaking is. I have clients that I am managing websites for, now I do some manual backups of their sites as I make major changes, but these are manual and the files are either stored locally on the hosting server or pulled over to me through an http protocol (browser download).

I currently have a few servers running 12.04, one of which with a 20TB array. is there a relatively simple solution for pulling a backup through ftp from the remote hosting server. The only reason I ask is because while all of them so far have the ability to schedule regular backups, as any good hosting provider should, but less than half have the ability to send this via ftp. 

So what I would like to do is setup the hosting servers regular backup. Then tell my server to access the site over ftp, on a cron schedule,  and pull that backup folder to my local storage. First, is it possible, and second, what would be the best way to go about it if it is? Any assistance is greatly appreciated, thanks!

FTP should have been killed off in 1995. PERIOD.
[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  So, set up some **ssh** access to the accounts using keys and then we can move onto the "**Best Way**."

That would be **rsync**. Easily scripted. Secure. Doesn't put your userid and password in cleartext over the internet.
All reputable hosting providers support ssh, scp and sftp. From those we can do everything necessary in a secure, efficient manner.

Oh - and stop using FTP.
--
Of the greatest inventions in computing, ssh and rsync are beaten only by UNIX. Those tools are THAT good and make up the core of every UNIX-based backup system.

---

### Post by Lars Noodén on 2014-02-19
+1 to that

If you use rsync, it uses SSH so the connection is secure.  Once you have basic rsync working you can configure it to use keys with SSH to allow unattended backup.

---

### Post by michaelebsch on 2014-02-19
Thanks for the quick responses and I will get something setup through rsync.

---

### Post by TheFu on 2014-02-19
> **michaelebsch said:**
> Thanks for the quick responses and I will get something setup through rsync.

a) get ssh working first.
b) get ssh working using keys next. - ssk-keygen and ssh-copy-id
c) setup rsync  (it defaults to using ssh for connections)
d) setup ~/.ssh/config with the settings/alias/ports/userid for each remote server to make life EASY. Almost every ssh-using tool honors these settings, including rsync.

```
rsync -azv --stats --progress {source} {target}
```
is the start.  Can pull or push - your choice.  Uses the ssh port, so no worries about which port to open or secure. If you "pull" the client doesn't need any open ports.

A real example:
```
rsync -azv --stats --progress romulus:/etc /Backups/romulus/
```
If you want more than a mirror rsync can be used for multiple-versioned backups - great examples here: [https://rsync.samba.org/examples.html](https://rsync.samba.org/examples.html)

BTW, all of this doesn't work as easy if Windows is involved.

---

### Post by kosmokramer314 on 2014-02-27
Fantastic tutorial covering everything needed to do what you are looking for in a secure manner:

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

---

### Post by TheFu on 2014-02-27
> **kosmokramer314 said:**
> Fantastic tutorial covering everything needed to do what you are looking for in a secure manner:

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

Most of the steps in that tutorial aren't necessary.
* **rsync** has defaulted to using ssh for years ... maybe 10 yrs. Haven't needed to use the -e option since the 1990s.
* **ssh-keygen** creates keys - (client side)
* **ssh-copy-id** pushes the public key from the client-side to the remote server, drops it into the authorizedkeys file and makes certain that no file or directory permissions get screwed up accidentally. No need to copy/paste keys or fix EOL-wrap issues anymore.
* setup on the client-side the **~/.ssh/config** if you like for different userid, different ports and easy-to-remember hostnames

This stuff really is very easy and has been for years.  That tutorial was needed in the 1990s, not so much anymore. Just sayin'.

---

### Post by michaelebsch on 2014-03-02
This has all been very helpful, thank you. This turned out to be much simpler than the last time I attempted something similar on 6.04, but being a beginner back then didn't help either.

---

### Post by kosmokramer314 on 2014-03-03
> **TheFu said:**
> Most of the steps in that tutorial aren't necessary.
* **rsync** has defaulted to using ssh for years ... maybe 10 yrs. Haven't needed to use the -e option since the 1990s.
* **ssh-keygen** creates keys - (client side)
* **ssh-copy-id** pushes the public key from the client-side to the remote server, drops it into the authorizedkeys file and makes certain that no file or directory permissions get screwed up accidentally. No need to copy/paste keys or fix EOL-wrap issues anymore.
* setup on the client-side the **~/.ssh/config** if you like for different userid, different ports and easy-to-remember hostnames

This stuff really is very easy and has been for years.  That tutorial was needed in the 1990s, not so much anymore. Just sayin'.


being a beginner and trying to setup keys and all that is not "easy" as you say.  Sure it's no big task once you understand everything that's going on, but that takes time and practice.  Learning how and why each step is necessary gives a better understanding in my opinion.  No offense taken on my side, but to say that this is easy for everyone is not accurate at all.

---

### Post by TheFu on 2014-03-03
> **kosmokramer314 said:**
> being a beginner and trying to setup keys and all that is not "easy" as you say.  Sure it's no big task once you understand everything that's going on, but that takes time and practice.  Learning how and why each step is necessary gives a better understanding in my opinion.  No offense taken on my side, but to say that this is easy for everyone is not accurate at all.

That tutorial is HUGE!  I found it confusing.  Fewer steps means less chance for errors. Easier.

[LIST=1]
[*]create the keys - **ssh-keygen**
[*]push the public key to the other box - **ssh-copy-id userid@remote-server**
[/LIST]
Anything beyond that is *confusing.*  After all, we don't tell beginning users what every GUI config tool does under the covers or how Firefox works or even how logins work.This is no different, IMHO.

Regardless, it is marked as SOLVED, so we did something right. ;)  That's a "win."

---

