---
title: "What should one do in case root account had been enabled?"
date: 2011-09-11
forum: Security
---

### Post by arroy_0209 on 2011-09-11
Without realizing importance of command sudo and due to my previous experience with some other linux OS, I enabled root command sometime after installing ubuntu. I however practically never logged in using command su. After realizing my mistake, I promptly disabled root account using the command: sudo passwd -l root. I notice a directory named /root does still exist (along with dirs bin, cdrom, etc, ..., sys, tmp, usr, var, vmlinuz, vmlinuz.old). Can anybody please tell me what else I should do? Can I check if security problems had arisen due to enabling root account earlier? The command ls -l in the concerned directory gives:
```

drwx------  10 root root  4096 2011-07-11 23:53 root/

```

Second, is there any way to see all commands I have used in terminal starting from first time I used ubuntu after installation? The file .bash_history seems to retain only the recent ones.

---

### Post by HermanAB on 2011-09-11
There is nothing wrong.

Relax and enjoy your Linux system.

---

### Post by haqking on 2011-09-11
> **arroy_0209 said:**
> Without realizing importance of command sudo and due to my previous experience with some other linux OS, I enabled root command sometime after installing ubuntu. I however practically never logged in using command su. After realizing my mistake, I promptly disabled root account using the command: sudo passwd -l root. I notice a directory named /root does still exist (along with dirs bin, cdrom, etc, ..., sys, tmp, usr, var, vmlinuz, vmlinuz.old). Can anybody please tell me what else I should do? Can I check if security problems had arisen due to enabling root account earlier? The command ls -l in the concerned directory gives:
```

drwx------  10 root root  4096 2011-07-11 23:53 root/

```Second, is there any way to see all commands I have used in terminal starting from first time I used ubuntu after installation? The file .bash_history seems to retain only the recent ones.


Root account still exists and owns lots of the system.  Root existing is why you can perform sudo actions.

You have disabled the account again so that is good, but root still exists and always will, which is why lots of files and folders is woned by root.

So dont worry what you see is normail, if it wasnt you wouldnt be able to perform any administrative tasks as elvating using sudo would be useless becasue there would be no root account to elevate to.

cheers

You can type history from the terminal, use the up cursor key.

However there is a limit on this by default which can be changed:

gedit ~/.bashrc

then near the top you should see HISTSIZE=xxxxx

you can change the xxxx value to another number.

also for security you can review all sudo actions performed by viewing the /var/log/auth.log

---

### Post by arroy_0209 on 2011-09-11
Thanks for your suggestions. I have changed both HISTSIZE and HISTFILESIZE to 9999. Earlier these were 1000. This is why I am unable to check when I gave the command to enable root account.

I have also checked /var/log/auth.log but this shows only today's operations. There seems nothing suspicious. But is there any way to find out when I first used the command "sudo passwd -u root"? (or may be I used sudo passwd root, I do not remember.) This must have happened three months ago.

---

### Post by haqking on 2011-09-11
> **arroy_0209 said:**
> Thanks for your suggestions. I have changed both HISTSIZE and HISTFILESIZE to 9999. Earlier these were 1000. This is why I am unable to check when I gave the command to enable root account.

I have also checked /var/log/auth.log but this shows only today's operations. There seems nothing suspicious. But is there any way to find out when I first used the command "sudo passwd -u root"? (or may be I used sudo passwd root, I do not remember.) This must have happened three months ago.


If you are referring to your fist post, there is nothing suspicious.

You have always had and always will have enabled or not root folders and files owned by root and operations carried out under root.

as for 3 months ago, then do you have backups of logs and the such ?

if not then probably not.

Why do you need to know out of interest ? as i said if you think something is wrong because of your first post, then there isnt, it is supposed to be like that

---

### Post by vasa1 on 2011-09-11
> **haqking said:**
> ...
Why do you need to know ...
Actually, I think it's a nice thing :)

We enter commands that help configure Ubuntu the way we want. Having a "log" of these commands, users (who aren't yet experts) can look over their logs and know how they tweaked things the last time and repeat them (if appropriate) after a clean, fresh install of the next Ubuntu version.

---

### Post by haqking on 2011-09-11
> **vasa1 said:**
> Actually, I think it's a nice thing :)

We enter commands that help configure Ubuntu the way we want. Having a "log" of these commands, users (who aren't yet experts) can look over their logs and know how they tweaked things the last time and repeat them (if appropriate) after a clean, fresh install of the next Ubuntu version.


I know, i agree.

I am asking as i think he thinks he needs to know because from the OP he assumes something is wrong.

also asking why someone wants to know, can help the support provided becasue there might be an easier way to do something than the way he refers to ;-)

---

### Post by arroy_0209 on 2011-09-12
vasa1 is correct. I sometimes look back to see what mistake I had done before so that I can avoid that next time. 

I realize that I should have kept backup of /var/log/auth.log too, apart from changing HISTSIZE. the default logfile retains only the most recent changes.

---

### Post by haqking on 2011-09-12
> **arroy_0209 said:**
> vasa1 is correct. I sometimes look back to see what mistake I had done before so that I can avoid that next time. 

I realize that I should have kept backup of /var/log/auth.log too, apart from changing HISTSIZE. the default logfile retains only the most recent changes.


what you can see will depend on what you have done in terms of enabled logging and cleaning up etc.

See here [Ubuntu Community Linux Log Files]("https://help.ubuntu.com/community/LinuxLogFiles")

for a view of various logs which you may be able to get some information from.

Just cos your root account was enabled thats not such a biggie, remember it is on most Linux distros, as long as the password is secure thats all.

As for what you saw in terms of files and such belonging to root, that is not becasue you enabled the root acount, the root account already exists, as does roots ownership of certain files and folders etc.

Cheers

---

### Post by sisco311 on 2011-09-12
Nobody linked to the RootSudo docs? [uhelp]community/RootSudo[/uhelp] :)

Yep, *the root account is disabled* is technically correct terminology, but it's a little bit misleading, especially for new users.

I prefer to use the term: the root account password is locked.

---

### Post by haqking on 2011-09-12
> **sisco311 said:**
> Nobody linked to the RootSudo docs? [uhelp]community/RootSudo[/uhelp] :)

Yep, *the root account is disabled* is technically correct terminology, but it's a little bit misleading, especially for new users.

I prefer to use the term: the root account password is locked.


yeah good point.

and the link is in my signature...i usually point to it, im off my game today ;-)

---

