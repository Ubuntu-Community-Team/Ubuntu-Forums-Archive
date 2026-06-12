---
title: "A question on Tripwire"
date: 2006-07-12
forum: Server Platforms
---

### Post by Sagotis on 2006-07-12
Hi All,

I have a question in regaurd to how one can read the backups of the tripwire database files or the (hostname).twd.bak files.

I looked through the man twadmin pages and the closest I can get is -m R            --remove-encryption option. 

Would this option then turn the (hostname).twd.bak into a clear text file? It should be known that I am posting this from my place of work, reading the online man pages, and thus cannot test this and would like an aswer from experienced tripwire users.

Thanks,

Sagotis

Disclaimer: I was not sure if this question belongs in the Ubuntu General Forum or the Ubuntu Security Issues forum. If this is the the wrong place to be asking this, (1) I am sorry and (2) please, any mod place post in the forum area you feel it should be. Thank you.

---

### Post by Sagotis on 2006-07-12
Ok I am home now and have tried the tripwire -m R (hostname).twd.bak command but tripwire keeps saying that "Unknown mode specified... Use --help to get help."

What is this mode talk none of the man pages fully explain it, however, I also have used tripwire --remove-encryption, tripwire -R --remove-encryption and tripwire -m --remove-encryption with the same output "Unknown mode specified... Use --help to get help."

Looking into the issue more I found out about the  twprint print command, however, when I issue the twprint --print-dbfile (hostname).twd.bak command I get this "Warning: Object name is not fully qualified; skipping."

However, it seems that the command twprint --print-report --twrfile (hostname)-(date).twr issues the info I was looking for but it dumps the results in the terminal and not a clear text file?

**Now my question is is there a way to dump the results of twprint --print-report --twrfile (hostname)-(date).twr to a text file?**

Any help would be appreciated ](*,)

Sagotis

---

### Post by falcon15500 on 2006-07-13
The -m R mode you are trying to use, is invalid for the **tripwire** program.  However, it is valid for the **twadmin** program - which fits, as you mentioned you got it from the man page for twadmin!

So try:  **twadmin -m R <filename>**

And for the other question...

Try:  **twprint --print-report --twrfile <filename> >> file.txt**

falc

---

### Post by Sagotis on 2006-07-13
> **falcon15500 said:**
> The -m R mode you are trying to use, is invalid for the **tripwire** program.  However, it is valid for the **twadmin** program - which fits, as you mentioned you got it from the man page for twadmin!

So try:  **twadmin -m R <filename>**

And for the other question...

Try:  **twprint --print-report --twrfile <filename> >> file.txt**

falc


falcon15500,

First I would like to say thank you very much. 

The command: twprint --print-report --twrfile /path/to/(hostname)-(date).twr >> /home/user/whatever.txt does infact work as you have stated, and I am grateful for your help :mrgreen:

However, the command: twadmin -m R (hostname).twd does not seem to be necessary in light of this command: twprint --print-dbfile --dbfile /pathe/to/(hostname).twd >> /home/user/whatever.txt (I was able to piece this together from your example and the man pages of twadmin). 

The only problem with printing a dbfile is that it takes a 5.5 meg twd file and creates a txt file that is just over 103 megs :rolleyes: :evil:; a bit impractical (for me anyways).

Thus, it seems then (to me) that all one needs to do is to print out the twr files really, which can and will server as a consistent back knowledge of all changes done to the system since it was created.

falcon15500 **thank you so very much** :D 

Sagotis

---

