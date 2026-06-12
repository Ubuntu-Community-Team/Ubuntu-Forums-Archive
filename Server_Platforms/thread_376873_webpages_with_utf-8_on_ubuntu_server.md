---
title: "webpages with utf-8 on ubuntu server?"
date: 2007-03-05
forum: Server Platforms
---

### Post by algoe on 2007-03-05
Hi!
I installed the ubuntu server 6.10 with LAMP.
I've managed to get most things to work, but one thing still puzzles me.
I used to have a forum on a old windows-server, and now that i moved it to the new linux box the characters å, ä and ö (very common in swedish, and that's my native language, so...) are all questionmarks. When i look in the database with phpMyAdmin they are replaced with all sorts of strange characters. If i've understood everything right the format that supports these is called utf-8, and at least for the database it says it is.
In the phpbb2-config files it also says utf-8.

When running some programs i sometimes get errors like these:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "sv_SE",
        LANG = "sv_SE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

and
```

svnadmin: warning: cannot set LC_CTYPE locale
svnadmin: warning: environment variable LC_ALL is sv_SE
svnadmin: warning: please check that your locale name is correct
```

I suppose they could somehow be related to my webpage-problem.
Any ideas? :confused:
I should probably mention that I'm still quite a newbie on linux as well, but i try my best ;)

---

### Post by scottfree on 2007-03-09
I am having the same problem with an intranet server.  I am moving it from SLES9 to Ubuntu Server 6.06.1 and so far everything has been smooth.  The only hangup has been accented characters, mostly é, but also some apostrophes and hyphens.  At first I thought it had to do with MySQL because the servers are running different versions, but we pull in an RSS feed and it is also showing question marks on accented characters.  Since we are using Joomla! as our CMS and Apache as our web server the problem could lie with either of these.  I'm still trying to determine which is at fault.  I have read on another post that UTF-8 support is weak in PHP, but it works on my other server.  I'm scratching my head on this one.:confused: 

Let me know if you make any headway, and I'll do likewise.

Scott

---

### Post by phantom32i on 2007-03-25
i am having some problem but i am using Java,
We manage to fix it temporarily by restarting tomcat after the server is booted.
It seems that Tomcat will start last and this causes the problem

Try to do tomcat restart and see if solves your problem.
After that .. i need help as well with seeing if this can be solved using a script.

kk. let me know

---

### Post by Zash on 2007-06-25
I also have this problem. I installed with a 6.10-server-disk (the 7.04 did not support my servers cd-rom-drive), and upgraded to 7.04 with do-release-upgrade.

åäö does not work in ssh-session

---

### Post by Zash on 2007-06-28
installing language-pack-en-base fixet my problem.

---

