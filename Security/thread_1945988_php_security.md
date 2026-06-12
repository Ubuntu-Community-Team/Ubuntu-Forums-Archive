---
title: "php security"
date: 2012-03-24
forum: Security
---

### Post by giocos on 2012-03-24
I have a server with a few virtualhost. 
apache is running by www-data user
Every /var/www/site is ftpuser:www-data and every file is ftpupser:ftpgroup

I discover that my server is vulnerable if someone put a phpshell and use it. (like weevely)
so i changed a lot of thing on php.ini
1)safe mode = on
2)disable ```
php_uname,delete,system,etmyuid,getmypid,passthru,leak,listen,diskfreespace,tmpfile,link,ignore_user_abord,shell_exec,dl,set_time_limit,exec,system,highlight_file,source,show_source,fpaththru,virtual,posix_ctermid,posix_getcwd,symlink,popen,system,escapeshellarg,escapeshellcmd,myshellexec,c99_buff_prepare,c99_sess_put,fpassthru,posix_getegid,posix_geteuid,posix_getgid,posix_getgrgid,posix_getgrnam,posix_getgroups,posix_getlogin,posix_getpgid,posix_getpgrp,posix_getpid,posix,getppid,posix_getpwnam,posix_getpwuid,posix_getrlimit,posix_getsid,posix_getuid,posix_isatty,posix_kill,posix_mkfifo,posix_setegid,posix_seteuid,posix_setgid,posix_setpgid,posix_setsid,posix_setuid,posix_times,posix_ttyname,posix_uname,proc_open,proc_close,proc_get_status,proc_nice,proc_terminate,phpinfo,pcntl_exec,eval
```
3)open_basedir in every virtual host
4)installed mod_security and activated the core rules
5)installed suhosin

Before the hardening the phpshell connect with www-data privilege and bash shell.
Now with ftpuser and php shell
Any suggestion? i want block this. I already lost 2 day for find a solution


sorry for my bad english

---

### Post by unspawn on 2012-03-24
> **giocos said:**
> Before the hardening the phpshell connect with www-data privilege and bash shell. Now with ftpuser and php shell Any suggestion? i want block this.
Fat chance you are running something in your web stack that is vulnerable to remote file inclusion attacks (may look like "wget%20http://some/remote/file"), so check your system and daemon log files, especially your web server logs. Since you run FTP check the FTP daemon logs as well. If you don't know how to grep for terms or want to generate clues from looking at 200s and 404s first you could run the logs through Logwatch. Easiest, quickest way to generate leads.

Also list and compare the version information for every (homebrewn?) tool and application, including plugins, running in your web stack with what the vendors suggests as latest stable. If an application or plugin, especially PHP-based ones, hasn't been updated in say a year check for vulnerability reports before deciding to move to something supported and maintained.

---

### Post by giocos on 2012-03-24
i just want that my server is protected from php backdoor shell.

---

### Post by unspawn on 2012-03-24
> **giocos said:**
> i just want that my server is protected from php backdoor shell.
Yes, I understand that. Look, it's commendable you did harden the web server but that should have been done in the first place. Also doing it reactively is like treating symptoms. 
What you need to do is *find and treat the cause*.

---

### Post by SeijiSensei on 2012-03-24
Any script you write needs to check the input it receives and only accept valid values.  Somewhere you must have a script which doesn't do this and can be exploited.  This is a PHP programming issue, not really something native to the Apache or PHP stacks.

I have a couple lines of code at the top of most scripts that checks $_SERVER['REQUEST_URI'] looking for strings that reference external resources.  If the REQUEST_URI contains "http:" or "ftp:" I simply have the script echo back an error and halt.  In actuality, those exploits would fail anyway since the passed values don't meet other criteria, but it's more efficient to just reject such requests at the outset.

---

