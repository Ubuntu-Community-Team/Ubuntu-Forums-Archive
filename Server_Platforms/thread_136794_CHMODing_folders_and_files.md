---
title: "CHMODing folders and files"
date: 2006-02-26
forum: Server Platforms
---

### Post by peanut butter on 2006-02-26
i have to chmod all the files in my webserver to 744 however it wont do files in folders anyone know how to do this?

---

### Post by pestilence4hr on 2006-02-26
chmod -R ?

---

### Post by Sutekh on 2006-02-26
[QUOTE=peanut butter]i have to chmod all the files in my webserver to 744 however it wont do files in folders anyone know how to do this?[/QUOTE]
```
chmod **-R** 744 <your webserver files>
```
The **-R** makes the call recursive through all folders beneath the parent one.

---

### Post by peanut butter on 2006-02-26
thanks so much.
i have another question thow : is there a way so when i upload something via ftp it will automatically be 755. without me having to issue that command every time?

---

### Post by Sutekh on 2006-02-26
Hey that's a good question, thanks for asking!

Well it depends on how you upload.  I don't know much about FTP.

I know if you copy something with the command **cp** you can use the **-p** flag to preserve specified attributes.

```
cp -p <file> <newfile>
```
will copy preserving the mode of access (permissions), ownership, timestamps.

Is that usage applicable to uploading by FTP?

---

### Post by peanut butter on 2006-02-26
idont think so. you see im using ftp to copy files and vnc to chmod.
i think ill just put a cron job for each miniut.
i'm a person who isint too thrilled with the command line.
ill just execuit a bash script.

---

### Post by Sutekh on 2006-02-26
Ah sounds like you have it in hand then!  That's more than I know about FTP I'm afraid

---

### Post by GTvulse on 2006-02-26
[QUOTE=peanut butter]i have to chmod all the files in my webserver to 744 however it wont do files in folders anyone know how to do this?[/QUOTE]

Throw this two lines at cron. These are just the commands, you need to set up times and such, execute as root:
```

find /var/www -type d | xargs chmod 755
find /var/www -type f | xargs chmod 644

```

If you want to make sure everything has the correct webserver user ownership you can throw a line like this in: ```
find /var/www | xargs chown www-data:www-data
```

---

### Post by pestilence4hr on 2006-02-26
If you are using ftp that is initialized in inetd or similar, you can probably change what is called the "umask" that the ftp daemon starts with.  Google "ftp umask" for details.  If you are using scp or sftp, you can either do "scp -p" which will preserve permissions (so if you have them set properly on the machine you are copying from, it will stay proper), or change the umask for the noninteractive shell you run on the remote machine.  Probably .bash_profile, if you run bash.

I should add that this proprosed "cron solution" sounds like a bad idea.

---

### Post by colo on 2006-02-27
Every decent ftp-daemon supporting upload of files and implementing writing-capabilities (like, for example, vsftpd) has an option to chown and chmod uploaded files to custom values.

You should make sure to know how UNIX-style permissions work before possibly f*cking up your whole system with chmod, btw. Applying 744 to everything is NOT the way to administer a system properly, really.

@dradul: "find" has the built in -exec-statement, making your pipe to xargs unnecessary.

---

### Post by GTvulse on 2006-02-27
[quote=pestilence2hr]I should add that this proprosed "cron solution" sounds like a bad idea.[/quote]

It is much better than blindly using "chmod -R", a surefire way of screwing up. Setting up the umask in the FTP server is the proper way to do it, but that can't be done in a ".bash_profile". It has to be done in the actual FTP server configuration files as is the case with vsftpd, the supported ftp server in ubuntu. Or, if that is not possible, in the process spawning the server either with environment variables or execution flags.

On the other hand, using cron to fix this kind of things is a time-honored tradition in Unix and other POSIX operating systems (not in GNU/Linux, so it seems). Furthermore, the OP asked how to chamge file permissions recursively, and that's what I gave an answer for.

---

