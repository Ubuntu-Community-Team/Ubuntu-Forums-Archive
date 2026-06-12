---
title: "File writing permissions on Apache"
date: 2009-07-07
forum: Server Platforms
---

### Post by Zyndrof on 2009-07-07
Hey there,

I use Apache2 as my development server and need it to allow file writing for my project folder. Security is not an issue since this is only a local server for testing purposes.

I made it work with this command:
sudo chown www-data.www-data <mydir> -R

However that locked the folder from access which is not that convenient. How can I activate mkdir etc. while still keeping normal persoal access?

Thank you!
Chris

---

### Post by Wim Sturkenboom on 2009-07-07
I don't see a reason why apache needs to be able to write the full tree. I use a setup where apache can write into one subfolder of the documentroot.

My setup is as follows. '*tacinc*' is one of my websites and the documentroot is the subdirectory '*web*'. There is one subdirectory where apache (in this case the user/group nobody) can write and that is the subdirectory '*files*'.
```

tacinc
|-- inc
|   |-- handover
|   |-- incident
|   |-- report
|   |-- schedule
|   `-- users
`-- web
    |-- **files**
    `-- images

```
```

wim@btd-techweb01:~$ ls -ld tacinc
drwxr-xr-x  4 wim develop 96 2007-03-27 06:41 tacinc/
wim@btd-techweb01:~$ ls -ld tacinc/web/
drwxr-xr-x  4 wim develop 1320 2007-10-12 07:54 tacinc/web//
wim@btd-techweb01:~$ ls -ld tacinc/web/files
drwxrwxr-x  2 wim nobody 80 2009-07-07 08:49 tacinc/web/files/
wim@btd-techweb01:~$

```

Hope this helps.

---

### Post by Zyndrof on 2009-07-07
I tried it on the folder that I want to be able to write to. However I still get denied access...

christoffer@christoffer-laptop:~$ ls -ld Website
drwxrwx--- 10 christoffer www-data 4096 2009-07-06 19:16 Website
christoffer@christoffer-laptop:~$ ls -ld Website/user_files
drwxr-x--- 6 christoffer www-data 4096 2009-07-07 13:47 Website/user_files
christoffer@christoffer-laptop:~$ 

Website is the document root and inside lies a folder called user_files which I would like to write to freely.

---

### Post by Wim Sturkenboom on 2009-07-07
```

christoffer@christoffer-laptop:~$ ls -ld Website
drwxr[COLOR="Red"]**w**[/COLOR]x--- 10 christoffer www-data 4096 2009-07-06 19:16 Website
christoffer@christoffer-laptop:~$ ls -ld Website/user_files
drwxr**[COLOR="Red"]-[/COLOR]**x--- 6 christoffer www-data 4096 2009-07-07 13:47 Website/user_files
christoffer@christoffer-laptop:~$

```*Website* only needs _drwxr[COLOR="Red"]**-**[/COLOR]x---_ as apache does not have to write there, so no write for the group. *Website/user_files* needs write permissions for apache, so _drwxr[COLOR="Red"]**w**[/COLOR]x---_.

---

### Post by Zyndrof on 2009-07-07
> **Wim Sturkenboom said:**
> ```

christoffer@christoffer-laptop:~$ ls -ld Website
drwxr[COLOR="Red"]**w**[/COLOR]x--- 10 christoffer www-data 4096 2009-07-06 19:16 Website
christoffer@christoffer-laptop:~$ ls -ld Website/user_files
drwxr**[COLOR="Red"]-[/COLOR]**x--- 6 christoffer www-data 4096 2009-07-07 13:47 Website/user_files
christoffer@christoffer-laptop:~$

```*Website* only needs _drwxr[COLOR="Red"]**-**[/COLOR]x---_ as apache does not have to write there, so no write for the group. *Website/user_files* needs write permissions for apache, so _drwxr[COLOR="Red"]**w**[/COLOR]x---_.

I'm not quite following... The command as I understand it is the same for all rows you wrote "ls -ld Website". However you define drwxr[COLOR="Red"]**w**[/COLOR]x. I tried specifying that with ls -ld Website drwxrwx but that didn't do it.

Can you show me the exact commands to write?

Thank you for your time :)

---

### Post by Wim Sturkenboom on 2009-07-07
OK, sorry. The **ls** command (as given) shows you the specified directory and its permissions and some other stuff. You need the **chmod** command to change the permissions.

You did not specify the full path, but let's assume that Website is in */home/christoffer*.

```

chmod 750 /home/christoffer/Website
chmod 770 /home/christoffer/Website/user_files

```
The first command will set the permissions for */home/christoffer/Website* to drwxr-x--- and the second command will set the permissions for */home/christoffer/Website/user_files* to drwxrwx---.

---

### Post by Zyndrof on 2009-07-08
Thank you, that worked just as it should :)

But, access to the new folder my script created with the php-function mkdir('dirname') is restricted. Is this caused by the chmod or is it because I should pass a second argument in the mkdir-function?

---

### Post by Wim Sturkenboom on 2009-07-08
If I understand you correctly, you use a php script to create subdirectories in */home/christoffer/Website/user_files*.

If so, check who owns the new directory (probably *www-data*), to which group it belongs (probably *www-data*) and the permissions of that directory (ls -l will help you there). What I understand from the php help on mkdir (see [http://www.php.net/mkdir](http://www.php.net/mkdir) ), everybody should have access to the new folder as the default permissions are 777.

And what do you mean by restricted. Can you not access it, can apache not access it, ... ?

---

### Post by Zyndrof on 2009-07-08
You understand my correctly. The new directory is owned by wwwroot. However, existing directories are still owned by me and accessible by Apache.

Apache can read the dir fine so I guess there's not really a problem. It sould just be convenient to have write permissions in the folders created by the script.

---

### Post by Wim Sturkenboom on 2009-07-08
The permissions should be 777 and therefore you should be able to access it. Did you read the help page that I linked to above? It tells you how to set the permissions when creating a directory.

OK, and I don't have any idea where wwwroot comes from. You can do a grep through the apache configs as I assume that it will be there.

---

### Post by Wim Sturkenboom on 2009-07-08
Sorry, was a bit in a hurry yesterday.

On my system, files created using PHP are owned by nobody and belong to the group nobody. Pemissions are 644.

I'm running a Slackware server, by the way, and the configs might be different.

My grep results for 'nobody':
```

root@btd-techweb01:/etc/apache# **grep -r nobody ***
httpd.conf:#  . On HPUX you may not be able to use shared memory as nobody, and the
httpd.conf:User nobody
httpd.conf:Group nobody
httpd.conf.default:#  . On HPUX you may not be able to use shared memory as nobody, and the
httpd.conf.default:User nobody
httpd.conf.default:Group nobody
no-subdomain/httpd.conf:#  . On HPUX you may not be able to use shared memory as nobody, and the
no-subdomain/httpd.conf:User nobody
no-subdomain/httpd.conf:Group nobody

```
You can replace nobody in the above command with webroot to check.

---

### Post by Zyndrof on 2009-07-09
Ok, thank you for all your help :)

---

