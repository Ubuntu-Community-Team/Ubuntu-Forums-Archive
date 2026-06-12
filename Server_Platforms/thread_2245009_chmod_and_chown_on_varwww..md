---
title: "chmod and chown on /var/www/."
date: 2014-09-20
forum: Server Platforms
---

### Post by irv on 2014-09-20
What is the best settings for ownership and access on the /var/www/ directory and all the files and directories under it?

---

### Post by Lars Noodén on 2014-09-20
If you are the only user on that machine you can chown it to yourself.  If you are sharing it with a group, then there are other options involving group permissions.  The important thing, from the web server's perspective, is that o=rx for directories and o=r for files and  (except for fairly unique exceptions) there is no write access by the web server or its child processes.

---

### Post by irv on 2014-09-20
I have mine set like this
> drwxr-xr-x 38 irv    www-data 4096 Sep 17 07:59 www
I am the only user on the server so I changed owner from root to irv and am using the group www-data. I have all rights the group has executing and reading rights and others executing rights. I am thinking this should be about the way it should be setup.

---

### Post by Lars Noodén on 2014-09-20
You can use your own regular group, too, not just the user.  Having www-data there is a bit risky because then it is one step away from giving write access to those files to the web server.  Nothing bad is going to automatically happen but it peels away another layer of security.  The user www-data exists to provide an unprivileged user for the main activities of the web server, the group www-data is largely an artifact of creating that user.  The idea is to give the server the least amount of privileges needed to get the job done.  

Here you can see that a root process is started and then one or more under www-data is launced by that root process.

```

ps -efjH | sed -n '1p;/apache2/p'

```

Some CMS tools might need write access to specific directories or files, but those can be dealt with on a case by case basis.  In general, www-data should be kept from getting write access to the pages it is serving.  Again, that's just one more layer.

---

### Post by irv on 2014-09-20
Are you suggesting I should maybe change my rights on the /etc/www/ and stuff under it? I have a couple of directories under www that I have audio files kept that I want other to be able to listen to. I saw on other server where group was set to www-data. Just wondering?

---

### Post by Lars Noodén on 2014-09-20
> **irv said:**
> Are you suggesting I should maybe change my rights on the /etc/www/ and stuff under it? I have a couple of directories under www that I have audio files kept that I want other to be able to listen to. I saw on other server where group was set to www-data. Just wondering?

I would propose not using the www-data group for anything, leaving it instead for the web server's own exclusive use.  At least one of the BSDs labels these special groups with an underscore at the start of the name so they are easier to spot, but the Linuxes don't do that, so it's harder to notice.  There is some vague mention in the Apache2 documentation about setting [User](https://httpd.apache.org/docs/2.4/mod/mod_unixd.html#user) and Group but it does not cover the reasons.  Again the idea is that the web server should not be able to gain write access to anything that it publishes, this is kind of a variation of the principle of Write XOR eXecute (W^X).  

If the audio files are under /var/www somewhere, presumably they are going to be readable by anyone already so no additional changes with groups are needed.  The defaults for /var/www are world-readable.  Otherwise, it is easy to add a joint group.  

There are a few cases where files and / or directories can be in the www-data group, but they are not so common.  One case would be where you have some portion of the web server behind a password and you don't want the regular shell users to be able to read those files if they log in.  Another would be when running a CMS, they sometimes want to write to a file or two, in which case SuExec in Apache2 can be used.

---

