---
title: "vsftpd won't restart"
date: 2005-11-22
forum: Server Platforms
---

### Post by msodrew on 2005-11-22
The server I'm using is actually running debian and I'm hoping (since ubuntu is a derivative of debian) that I can be helped here.

My vsftpd server was up and running fine... then I made small trivial changes to vsftpd's conf file (involving umask). I wanted to try out the changes, so I tried to restart vsftpd.

The program itself is located at /etc/init.d/vsftpd

everytime I do
```
datamonkey1:/etc/init.d# vsftpd restart
```
i get
```
500 OOPS: vsftpd: cannot open config file:restart

```

I was like "wtf".... so I just tried vsftpd alone and got:

```
datamonkey1:/etc/init.d# vsftpd
500 OOPS: could not bind listening IPv4 socket

```

the server IS running... im connecting to it and uploading files as i type this so i know its currently ON. Whats going on? is there a seperate command to control it? (like i know for apache is "apachectl" and not "apache")

---

### Post by ruffneck on 2005-11-22
Are you running, editing the config. file when you try to restart vsftpd? Make sure you save and close out of the config. file once you're done editing. Also have you tried doing ```
sudo vsftpd restart
```

I've been using vsftpd for sometime and after making changes to the config. file I usually do a killall -HUP "vsfptd PID" 

"vsftpd PID" being the process ID of the vsftp daemon. You can find what it is by doing  a #ps -ed# 


I think there is also a vsftpd restart command also like you tried but i've never used it.

---

### Post by nordmann on 2005-12-27
I saw this exact same thing on my Ubunu machine, a Breezy Badger install.  For a while I resorted to killing the process and running vsftpd start.  Later on, I stumbled upon the realization that if I invoked the script with a fully-qualified pathname, it worked correctly even for restarting.

Does anyone know why this might be the case?  What is the difference between calling a script using its full pathname and calling it by its file name only when both commands are issued from the file's parent directory?

Also, does anyone know whether the behavior described below is the way it is supposed to work, or is it a defect?

Thanks,
--Erik

---

### Post by jmirick on 2006-01-19
I had all of these problems, including the "could not bind" response, and I pass on my experience:

First, the syntax "vsftpd restart" is not allowed in talking to vsftpd, it takes this to mean "start me with an override configuration file called 'restart'".  And, if you just try to enter "vsftpd" it takes that as a start command, and says, "I can't, somebody else owns that port" which is correct since an existing instance owns it, its already running (as you note).

Second, for all you long-term Unix personages, remember that Ubuntu is very highly GUI-oriented and so the way to shut off a major service (like Ubuntu, or Apache, or whatever) is to use the System | Administration | Services menu rather than the command line.  I can't figure out how you do anything at all with vsftpd at the command line except start it, but that's OK because checking / unchecking the box in Services does it just fine.

---

### Post by darth_vector on 2006-01-19
when i have problems i restart vsftpd with```
/etc/init.d/vsftpd restart
```and if that fails with```
/etc/init.d/vsftpd stop
/etc/init.d/vsftpd start
```

---

### Post by jmirick on 2006-01-23
Ah!  I think you're running it as a service, I'm running it standalone.  It must take its inputs differently; maybe you're talking to the service manager.

---

### Post by MJN on 2006-01-23
[quote=jmirick]I had all of these problems, including the "could not bind" response, and I pass on my experience:

First, the syntax "vsftpd restart" is not allowed in talking to vsftpd, it takes this to mean "start me with an override configuration file called 'restart'". And, if you just try to enter "vsftpd" it takes that as a start command, and says, "I can't, somebody else owns that port" which is correct since an existing instance owns it, its already running (as you note).

Second, for all you long-term Unix personages, remember that Ubuntu is very highly GUI-oriented and so the way to shut off a major service (like Ubuntu, or Apache, or whatever) is to use the System | Administration | Services menu rather than the command line. I can't figure out how you do anything at all with vsftpd at the command line except start it, but that's OK because checking / unchecking the box in Services does it just fine.[/quote] 
Some good guesses there, but all way off the mark... ;) 

The vsftpd script in /etc/init.d accepts start, stop, restart and reload as valid options - they each do distinct things.

The reason you're getting some odd errors when trying to execute 'vsftpd restart' whilst in /etc/init.d/ is nothing to do with it trying to read in a config file called 'restart' it is because **the current directory is not in your PATH** - this is by design**[Footnote 1]**. Thus, when you're typing 'vsftpd' it's actually trying to execute /usr/sbin/vsftpd (because /usr/sbin/ is in root's PATH).

Hence, to execute the script properly do one of the following:

1) If you're already in /etc/init.d/ enter ***./**vsftpd <option i.e. start|stop|restart|reload>*

or 2) If you're elsewhere enter */etc/init.d/vsftpd <option>*

This applies to all scripts and executables - if you're in the parent directory you need to prefix it by **./**

Mathew

P.S. I won't even comment on your claim that services under Ubuntu need the GUI to control them - that *really* is nonsense..! ;)

**[1]** If you're interested why, it is thus: Suppose someone left bits of malicious executable code around and named them the same as common system commands. Then, as a user with sudo privileges, you happened to be in a directory containing (unknowingly) one of these executables - called 'ls' for example. If you wanted to see the directory listing you'd type 'ls'... however the malicious code would instead get run. Thus, by removing the current directory from your PATH this risk is mitigated somewhat because you have to explicitly request the executing of the 'ls' in the current directory by either calling ./ls or /full/path/to/ls - 'ls' alone would not suffice (it would run the 'proper' system 'ls').

---

