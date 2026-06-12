---
title: "HP Proliant Support Pack?"
date: 2006-07-19
forum: Server Platforms
---

### Post by jodeet on 2006-07-19
Has anyone installed part or all of HP's so-called 'Proliant Support Pack' on Ubuntu?  HP only releases the software as RPMs for RedHat ESL and SuSe.  I'm interested in doing so but have had only limitted success.  If anyone has tried this, would you share your experience?  The rest of this post describes my experience.

Thanks

1) the 'Pack' is normally installed via a shell script.  The script is 1978
   lines long.  I tried hacking the script to work for Ubuntu, but
   soon gave up due to the length of time needed.

2) I converted 4 of the 'Pack's RPMs to deb's via the alien command.  I was
   able to install them after some hacking of the preinst scripts.

3) even after installing the deb's, some of the programs installed by the 
   deb's didn't work, due to missing shared libraries.  I found the shared
   missing shared libraries and installed them (they were in other deb's,
   available from multiverse, which were not already installed).

4) the 'System Management Homepage' deb didn't create /etc/init.d/hpsmhd.
   I would have to hack some files that are delivered as part of the
   deb itself.  I.e. script files that are not part of the preinst or
   postinst, but are used only during the installation.  The postinst
   script calls them and then deletes them when done.

5) i started the 'System Management Homepage' by manually running
   /opt/hp/hpsmh/sbin/smhstart.  I could login, but there was nothing I
   could do once inside.  No active links.

---

### Post by magicfab on 2006-09-18
Hi,

I have a ML370 system. I haven' t managed to make hpasm work, for similar reasons you described. Did you manage to install HPASM ? On which system(s) ? My primary reason is to be able to control the fan which makes a very loud noise (and of course use it optimally instead of 100% all the time).

Thanks for any details , I will be posting more infor about my trials in another post.

---

### Post by etcpool on 2006-09-20
i found this : [http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1045112&admit=-682735245+1158766390589+28353475](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1045112&admit=-682735245+1158766390589+28353475)

including installing the fakeroot package $sudo apt-get install fakeroot

then run the script followed by the link it should work fine on Dapper

(i had this worked fine on my ubuntu dapper installation from the x86cd sent from ubuntu and i just installed it with x to work it as my home lan server , the service work fine fan start to slow down after gnome booted sucessfully, the fan may spin faster again but only during the boot progress. ;) )

---

### Post by baastie on 2006-09-20
Hi,

[http://debian.catsanddogs.com/forum/index.php](http://debian.catsanddogs.com/forum/index.php)

Sorry for the redirect to another forum,

But we got our hp agents working on debian sarge after thanks
to this site. I also saw some ubuntu users there..

Cheers,

Baastie

---

### Post by etcpool on 2006-09-20
in my situation the redhat package didn't work (these may cause of too much differences of filesystem structure, as if u look into the configuration files)

but with Debian HP script and the suse's package downloaded by it and the fakeroot package, it worked !

---

### Post by baastie on 2006-09-21
good to know,

thanks for the update...

---

### Post by magicfab on 2006-10-27
I confirmed this is working OK with Dapper, but not Edgy. Fakeroot seems to do the trick :)

---

### Post by Pixxa on 2007-04-19
wrong topic :(

---

