---
title: "Not finding PHP.ini file"
date: 2019-07-25
forum: Server Platforms
---

### Post by amandainjames on 2019-07-25
I want to increase upload size in WordPress. I have done everything and now I am finding the php.ini file but it's not there what should I do? Create a new one because if I am having issues in searching and If I create  a new file then the previous one I think will be overwrite. I have gone through a tutorial to <URL snipped> increase upload size in WordPress and there I have seen that selecting Show hidden files will enabled the php.ini file but still I am not finding the file. Any help please? I want to updated the code in PHP.ini file.

*upload_max_filesize = 20M*
*post_max_size = 25M*
*memory_limit = 30M*

---

### Post by SeijiSensei on 2019-07-25
Ubuntu creates two different versions of php.ini, one tied to Apache, and one for the command-line php program. Installing PHP on my 19.04 system created
```

/etc/php/7.2/apache2/php.ini
/etc/php/7.2/cli/php.ini

```
On older versions of Ubuntu "7.2" would be replaced with whatever PHP version you're running. These files are owned by the root user, so you will need to use sudo to edit them, e.g, "sudo nano /etc/php/7.2/apache2/php.ini".

For WordPress, you obviously need to modify the version in the apache2 directory.

The handy utility "locate" is your friend and installed by default. Typing "locate php.ini" will show you the locations of all files or directories with "php.ini" in their full paths.

```

$ locate php.ini
/etc/php/7.2/apache2/php.ini
/etc/php/7.2/cli/php.ini
/usr/lib/php/7.2/php.ini-development
/usr/lib/php/7.2/php.ini-production
/usr/lib/php/7.2/php.ini-production.cli

```

However the database for locate is only updated once each day. Files created since the last update will be missed. You can force an update with the command "sudo updatedb" before running locate to find more recent files.

---

### Post by coffeecat on 2019-07-25
The Tutorials section is for posting tutorials, not for requesting help.

You don't specify your operating system, or release, but making the assumption that you are using Wordpress on an Ubuntu server: *thread moved to **Server Platforms**.*

If you provide details of the system you are using, forum members will be in a better position to help.

---

### Post by SeijiSensei on 2019-07-26
Hello, Amanda???

None of us is paid to provide help here, and it is rude to ask a question and not reply to any suggestions you receive.

Did you read my "signature" at the bottom of my post?  Here it is again:

---

### Post by coffeecat on 2019-07-26
@SeijiSensei, agreed. 

In case this is blog spam, I have now removed the link from the OP. It's certainly a drive-by and I will be surprised if the OP comes back again.

I suggest all forum members desist from responding unless and until the OP posts again.

---

