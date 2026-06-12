---
title: "FTPd Trouble"
date: 2005-06-18
forum: Server Platforms
---

### Post by deBaas on 2005-06-18
Hello,

Ik would like to share some files with friends of mine. Back in winXP i used Filezilla FTP serer with great satisfaction. Last weeks i have tried different linux ftp servers. Here are the results.

**ProFTPD** ProFTPD is nice, it worked. I used vitrual users with mysql. ProFTPD is hard to configure but has many options. But it doesn't give me an option to limit the IP per virtual user.

**Pure-FTPD** Most easy server to configure. There is a program pureadmin wich allows you to view logs, activities and add/edit/remove users. It is possible to make an IP filter for each (virtual) user. Howerver, I used the InetD to start proFTPD. Due the complex startup options. Pure-FTPd won't run behind Inetd. Another dislike: It won't follow symbolic links, even when they are not out of the chrooted enviroment.

**VSFTPD** Looks nice and should have many options. Runs fine with inetd en real user accounts. However to use virtual users you should creat some kind of database with the Berkeley db program. The readme says:
> 
Many systems have multiple versions of "db" installed, so you may
need to use e.g. db3_load for correct operation. This is known to affect
some Debian systems. The core issue is that pam_userdb expects its login
database to be a specific db version (often db3, whereas db4 may be installed
on your system).
I tried all different versions schipped with ubuntu but none will work.

Can anyone advise me on a FTPd? Or tell me how to fix one of above problems?

---

### Post by LordHunter317 on 2005-06-18
You need to decide on one.  Use whatever one best fits your needs.  You don't need, want, nor care about inetd support.

And no one can help you without error logs, configuration details, etc.

---

### Post by deBaas on 2005-06-18
The one that best fist my needs is Filezilla. So return to Windows? I thought most people here would have some experience with ftp and linux and might want to share this information. If someone has vsftp running with support for virtual users he/her could realy help me out.

---

### Post by Beernut on 2005-06-18
[QUOTE=LordHunter317]You don't need, want, nor care about inetd support.[/QUOTE]


Well why not help him remove inetd support instead of just telling he doesn't need it.

---

### Post by LordHunter317 on 2005-06-18
[QUOTE=Beernut]Well why not help him remove inetd support instead of just telling he doesn't need it.[/QUOTE]Because he hasn't selected which daemon he wants to use yet or post a configuration file?

I can't tell somehow howto do something when they haven't even decided how to do it.

**To The Op:**
My point was that all three of those daemons are basically the same, so it doesn't matter which one you pick.  They all have their ups and downs, but also are have the same basic featureset.  So decide on which one you want to use for this.

If you have a specific set of features you want for this, list them and someone can help you select which daemon is optimal for your usage.

All I see is some inspecific gripes with which one without sufficent details to help you resolve them or even determine if they are resolvable.

---

### Post by deBaas on 2005-06-19
[QUOTE=LordHunter317]
If you have a specific set of features you want for this, list them and someone can help you select which daemon is optimal for your usage.[/QUOTE]
If you would read my post carfully you could have find out my needs:
-Support for symbolic links
-virtual users
-limit ip's per user

---

### Post by LordHunter317 on 2005-06-19
Are those all your needs?  If so, I know proftpd can do all of those (though I'm not quite sure what you mean by the last one).  And if the core can't do it, a plugin DSO certainly ought to be able to.

---

### Post by deBaas on 2005-06-19
[QUOTE=LordHunter317]Are those all your needs?  If so, I know proftpd can do all of those (though I'm not quite sure what you mean by the last one).  And if the core can't do it, a plugin DSO certainly ought to be able to.[/QUOTE]
Simpel, users X may only connect from IP adress xxx.xx.xx.xxx and users y only from yyy.yyy.1.0/24 for example. Using proFTPd with MySQL won't give you this option.

---

### Post by LordHunter317 on 2005-06-19
Why do you want that feature?  It doesn't give you any extra security.  

Anyway, I don't see why the proper <Limit> , AllowUser, and Allow directives wouldn't do what you want.  I didn't try it (as I don't run FTP anymore), but what did you try to do to make it work?  They directives don't say they don't work with mod_sql, and I don't see any reason as to why they shouldn't.

---

### Post by deBaas on 2005-06-20
First jeling all ftp servers do fits my needs and now asking why i need such a feature. Strange wy of problem solving.

You can do this with proftpd but with almost 50 users in a mysql database i sould define 50 classes in my proftpd.conf file. You just can not add a colum IP to your users database and tell proftpd to look over there. PureFTPd has this feature but it seems like it doesn't support symbolic links.

---

### Post by LordHunter317 on 2005-06-20
[QUOTE=deBaas]and now asking why i need such a feature. Strange wy of problem solving.[/quote]Because I'm curious to your reasoning, as I know it doesn't provide any extra real security.  So I want to know why you care: I'm pointing out you may be able to get by without it.

> You can do this with proftpd but with almost 50 users in a mysql database i sould define 50 classes in my proftpd.conf file. You just can not add a colum IP to your users database and tell proftpd to look over there.So write a script to add a user and create a class in the configuration file for him.  If you post the right details I'd be happy to write it for you.

>  PureFTPd has this feature but it seems like it doesn't support symbolic links.I'm not familiar with PureFTPD configuration, but I'm sure it does.  There's probably a configuration option you have to toggle.  If I come up with some free time today I'll poke around for you and try to find it.

---

### Post by jazz on 2005-06-20
Pure-FTPD does support symbolic links ! atleast it did on gentoo, not sure if gentoo's addin some extra patches into it !

I will have a look at it though, i'm facing the same problems with all the ftp servers as mentioned !

Tryin to zero in on a good, easy viable solution...

Lemme know if u get any progress done,,
Thanx,

Jazz

EDIT : The latest release is 1.0.21, whereas the one with ubuntu is 1.0.19, and gentoo installed the latest version all the time., so my bet is if we install the latest version we can get the symlinks to work...

Does anyone have a deb to the latest version ?

---

### Post by jazz on 2005-06-20
Ok, heres the deal.. i finally got it to work.. u have to manually compile it though !

get the source from 
```

ftp://ftp.pureftpd.org/pub/pure-ftpd/snapshots/

```

Then extract, gointo the dir with root priveliges, and then issue the following command..
```

./configure --with-puredb --with-throttling --with-ratios --with-quotas --with-ftpwho --with-welcomemsg --with-virtualhosts --with-virtualchroot --with-diraliases --with-peruseruserlimits --with-privsep --with-extauth CFLAGS=-02

```

Please note that u can change these flags to your personal liking, for a complete list of supported flags, do a
```

./configure --help

```

Once the configuring is done, isuue the following commands:
```

make && make install

```

Ok, well.. thats it folks ! be sure to uninstall any pure-ftpd package u have installed via synaptic.. before performing a install..

Umm, if you know what options to start it with, awesome.. u're set ! if not.. i'll post the options i use..
```

sudo pure-ftpd -S 21 -c 7 -C 1 -B -k 90% -l puredb:/etc/pureftpd.pdb -I 1 -f facility -A -X -G -j -R -B -E

```

Please lookup the documentation to see what all the options mean and do !

Thats it.. install pureadmin, and configure whatever u need !

VOILA.. i hope it helps.

Hey, being a gentoo user does have its own advantages i guess  \\:D/ 

Bye,
Jazz

---

### Post by deBaas on 2005-06-20
Jazz, your my hero. It works like a charm. Hopfully this new version will be in the ubuntu respitories soon. Or is the ubuntu version just wrongly compiled?

Jazz, thank you!

---

### Post by jazz on 2005-06-20
lol, glad it helped !! i was goin insane, cuz of this ! and there arent any ftp servers that really match the functionality of the one's provided in windows !

Ahh well., hope things get good soon.. i'm not sure how the ubuntu deb is compiled, cuz i looked at the changelog, and nothing changed between 1.0.19 and 1.0.21 that had anything to do with symlinks ! so i guess, the deb is not properly compiled or something !!

Besides, now after moving on from gentoo, i realise that the idea behind gentoo was not crap ! Its the greatest learnin curve a noob can get in his way to linux !

Lol, i still use the kernel compiled for gentoo to run Ubuntu, and guess what it runs much much better than the kernels compiled by ubuntu or in ubuntu  :-P , so i'd be keepin gentoo just yet !

Lol.. ahh well, finally i can move on to other issues preventing me to world domination !! like, gettin bluetooth,video streaming,etc.. to work in linux..  ](*,) 

lol, bye,
Jazz

---

### Post by frodon on 2005-06-21
[QUOTE=LordHunter317]Are those all your needs?  If so, I know proftpd can do all of those (though I'm not quite sure what you mean by the last one).  And if the core can't do it, a plugin DSO certainly ought to be able to.[/QUOTE]

I didn't know that proftpd allow symbolic link ! (still not working for me)
Can you tell me how enable it ? (my config file is here : [http://ubuntuforums.org/showthread.php?t=40750](http://ubuntuforums.org/showthread.php?t=40750))

---

### Post by deBaas on 2005-06-21
[QUOTE=frodon]I didn't know that proftpd allow symbolic link ! (still not working for me)
Can you tell me how enable it ? (my config file is here : [http://ubuntuforums.org/showthread.php?t=40750](http://ubuntuforums.org/showthread.php?t=40750))[/QUOTE]
As far as i know proftpd follows symbolic links when they are within the chrooted tree by default.

---

### Post by HAMM3R on 2005-08-02
I like vsftpd

---

### Post by oLMo on 2006-03-23
Many thanks jazz, I spent a lot of time looking for a solution...
However not tested yet :)

---

### Post by benow on 2008-06-17
Thanks jazz.. good stuff.  I think gentoo has a +symlink use flag or something.  A similar feature in ubuntu would be nice in this case.

---

