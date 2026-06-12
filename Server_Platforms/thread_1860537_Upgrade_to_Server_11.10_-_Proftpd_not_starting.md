---
title: "Upgrade to Server 11.10 - Proftpd not starting"
date: 2011-10-14
forum: Server Platforms
---

### Post by DaveWut on 2011-10-14
Hi everybody, I'm running Ubuntu server on a virtual machine for about 5 months or more. I didn't have any configuration problem and everything was working before I upgraded to the latest version of Ubuntu Server (11.10). Now, my FTP server won't start again, the console returns the following message : 

```
* Starting ftp server proftpd
- mod_tls/2.4.2: compiled using OpenSSL version 'OpenSSL 1.0.0d 8 Feb 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' library
- Fatal: LoadModule: error loading module 'mod_vroot.c': Operation not permitted on line 74 of '/etc/proftpd/modules.
[COLOR="Red"][fail][/COLOR]
```

As you can see, it seems that I have a problem with my mod_tls for proftpd. It looks like that this module was compiled with an old version of OpenSSL, but I really don't know how I can fix it and/or how I can compile a new version by myself. Another thing I figured out from the upgrade. The installation setup has somehow changed my encryption's configuration. My website, which can be viewed securely, is no more protected with an 256-bit AES protection, but with a Camellia-256 encryption! What does this mean? Does this change can have some impact on my system?

Thanks in advance for your help guys! I hope this is a known bug! 
Dave

---

### Post by botanic on 2011-10-15
Hi Dave

I had the same problem on my local development server this morning, I installed the package "proftpd-mod-vroot" which was listed on my server's package manager but not actually installed.

I am by no means an expert, this may not be the best answer, but it worked for me.  Own risk etc etc! :o)

Alan

---

### Post by macmike on 2011-10-15
I am in a jam now. I tried to upgrade from 11.04 to 11.10 on my Ubuntu Server install. It went through everything and hung when it came to putting MSconfttf I think it was called. I restarted hoping it would pick back. Now the server starts but is after it starts ftp server proftpd. now just blinking cursor. My Ubuntu desktop is not there what can I do to fix this?

macmike
mail(at)mikealrhughes(dot)com

---

### Post by DaveWut on 2011-10-15
> **botanic said:**
> Hi Dave

I had the same problem on my local development server this morning, I installed the package "proftpd-mod-vroot" which was listed on my server's package manager but not actually installed.

I am by no means an expert, this may not be the best answer, but it worked for me.  Own risk etc etc! :o)

Alan

Oh so you say that you had the same problem as me and you fixed it by installing the package "proftpd-mod-vroot"? Oh well, I'll take I try then, thanks for the advice! I'll just take a snapshot of my VM and if nothing works, I'll just go back. 

@macmike : Sorry Macmike, but I can't help you with this problem, we need to know the exact package name. Also, why are you using Ubuntu Server with a user interface?

---

### Post by jconstantino on 2011-10-15
Thank you...install proftpd-mod-vroot solved my problem..

---

### Post by macmike on 2011-10-15
> **DaveWut said:**
> Oh so you say that you had the same problem as me and you fixed it by installing the package "proftpd-mod-vroot"? Oh well, I'll take I try then, thanks for the advice! I'll just take a snapshot of my VM and if nothing works, I'll just go back. 

@macmike : Sorry Macmike, but I can't help you with this problem, we need to know the exact package name. Also, why are you using Ubuntu Server with a user interface?

The reason I am using Desktop with a Server is there are other things I wish to do as well besides it being a server.

---

### Post by DaveWut on 2011-10-15
> **macmike said:**
> The reason I am using Desktop with a Server is there are other things I wish to do as well besides it being a server.
Ok, I was just asking! :) 

Well, installing proftpd-mod-vroot didn't fix the problem. When I'm trying to start proftpd, the same error occured, but I get an additionnal error : 
```
 * Starting ftp server proftpd                                                   
 - mod_tls/2.4.2: compiled using OpenSSL version 'OpenSSL 1.0.0d 8 Feb 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' library
 - mod_sftp/0.9.7: compiled using OpenSSL version 'OpenSSL 1.0.0d 8 Feb 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' library

```

I think the OpenSSL installed after the update is NOT compatible with all proftpd module that requires SSL. Is there's a way to obtained OpenSSL 1.0.0d? 

Thanks!

---

### Post by lokutus25 on 2011-10-17
> **botanic said:**
> Hi Dave

I had the same problem on my local development server this morning, I installed the package "proftpd-mod-vroot" which was listed on my server's package manager but not actually installed.

I am by no means an expert, this may not be the best answer, but it worked for me.  Own risk etc etc! :o)

Alan

Thanks Botanic, it worked for me. I had the same problem, upgraded from 11.04 x64 to 11.10 and proftpd didn't start because of mod_vroot.c.
Now works fine :P

---

### Post by kylecoots on 2011-10-17
>  					Originally Posted by **botanic** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11347425#post11347425") 				
 				[I]Hi Dave

I had the same problem on my local development server this morning, I  installed the package "proftpd-mod-vroot" which was listed on my  server's package manager but not actually installed.

I am by no means an expert, this may not be the best answer, but it worked for me.  Own risk etc etc! :eek:)

Alan[/I]

Thanks! this also worked for me after upgrading from Ubuntu 11.04 to 11.10x64. Didn't like having to SSH all the time so its nice to have my ftp back!

---

### Post by unc0nn3ct3d on 2011-10-18
installed that package, reinstalled proftpd and openssl and the warning messages still persists.

[http://www.proftpd.org/docs/howto/TLS.html](http://www.proftpd.org/docs/howto/TLS.html) - tells us that this si moer of a warning than an error message.. Proftpd starts fine but it'd be nice not to have the warning message

---

### Post by DaveWut on 2011-10-24
Hi guys,
I tried all solutions, but nothing works. The problem is that the compiled version of mod_tls and mod_vroot is not compiled with the newest version of OpenSSL installed by default on Ubuntu Server 11.10. I saw this [subject]("https://bugs.launchpad.net/ubuntu/+source/proftpd-dfsg/+bug/873984") and it seems I'm not the only to have this problem. 

I would like to know if someone here is able to make a compiled version of both modules? In that case I could try to run this FTP once more! 

Thanks!

---

### Post by slez-e on 2011-10-26
I was able to get proftpd-basic running using the proftpd-mod-vroot 0.9.2-1 package from Synaptic package manager. 

Before I ran proftpd-mod-vroot 0.9.2-1, I ran 'sudo apt-get build-dep proftpd-basic' to update all dependancied after the upgrade to 11.10. I figured that given all of the problems, proftpd was left behind during the update. It installed/updated a lot of packages during the process.

My kung-fu isn't very strong but I hope this helps.

---

### Post by DaveWut on 2011-10-26
This hadn't fix the problem, but thanks for the sharing. I still have the same message which says the compiled version of both TLS and mod vroot module are not from the OpenSSL version 1.0.0e.

---

### Post by Metaphysical on 2011-11-04
Just ran into this problem, and the proftpd-mod-vroot package fixed it all for me too. Thanks!

---

### Post by Lokifaer on 2011-11-26
Hello everyone, it seems I have the same problem.
 I didn't understand how to add the mod-vroot in my proftpd.
 So I >disabled it in the configuration file.</span>
 But now I have exactly the same messages as DaveWut.
        
@DaveWut:
 as-tu réussi à redémarrer proftpd finalement ? (j'ai vu ton post sur le siteduzero=)
        
Did anyone succeed in restarting proftpd with this kind of problem ?

---

### Post by sanitycheck on 2011-12-15
If you can get away with no SSL-based modules, I posted a work-around on bugtracker [*here*]("https://bugs.launchpad.net/ubuntu/+source/proftpd-dfsg/+bug/873984").  At least this way it runs.  I'm just using FTP to move files across the LAN, so I can get away with no sftp.

---

### Post by JoeChen150 on 2012-01-05
I started having the same problem after upgraded from Ubuntu 10.XX to 11.10.  After reading post sin this thread, I gathered the following procedure, and it solved the problem for me:

$ sudo apt-get build-dep proftpd-basic
$ sudo apt-get install proftpd-mod-vroot
$ sudo /etc/init.d/proftpd restart

---

### Post by DaveWut on 2012-02-24
@JoeChen150
These commands are good indeed. I'm just posting here to say the problem is solved now. Why my proftpd server did not start after these command is because other configurations in my server were wrong. 

Thanks to everyone! :) 
Dave

---

### Post by iansane on 2012-05-08
I installed 11.04 LTS and have this issue right out of the box.

I did the steps listed here and am guessing the dep-build just installed a bunch of stuff I may not need since it didn't fix the issue.

My sftp is working but I still get the warnings about openssl and mod_tls etc.

I also get a warning that memcache support is not enabled.

Anyone find out another fix for this?

Thanks

---

### Post by DaveWut on 2012-05-08
> **iansane said:**
> I installed 11.04 LTS and have this issue right out of the box.

I did the steps listed here and am guessing the dep-build just installed a bunch of stuff I may not need since it didn't fix the issue.

My sftp is working but I still get the warnings about openssl and mod_tls etc.

I also get a warning that memcache support is not enabled.

Anyone find out another fix for this?

Thanks

These warnings will appear each time you will start your proftpd server and it's normal. The compiled headers version of OpenSSL embedded in both plugins (Mod  TLS and mod sftp) are older than the installed version of OpenSSL on your system. For memcache, I don't know and I haven't tried to fix the problem, it's a good question.

EDIT : I hope you talk of Ubuntu 12.04 LTS and not 11.04.

---

### Post by iansane on 2012-05-08
DaveWut,

yeah sorry about that. I meant 12.04.

I also went and read that bug report and see that it's not going to be fixed since it's just a warning.

Seems strange though to get warnings about versions on a completely fresh install.

I've got all my issues worked out and have tested sftp on different machines so I guess it's just something to ignore. Like you say, I will only see it when I'm ssh'd into the server and restarting proftpd for some reason.

Thanks

---

