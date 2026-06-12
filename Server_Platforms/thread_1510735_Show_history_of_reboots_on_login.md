---
title: "Show history of reboots on login"
date: 2010-06-15
forum: Server Platforms
---

### Post by braunshedd on 2010-06-15
i wanted to know what script i would put where that would tell me the last 5 times the server rebooted whenever i logged on. any help?

---

### Post by CharlesA on 2010-06-15
You can try using uprecords, but that really only keeps track of uptime between reboots.

Would that work?

---

### Post by braunshedd on 2010-06-15
> **CharlesA said:**
> You can try using uprecords, but that really only keeps track of uptime between reboots.

Would that work?
no, im trying to get it to where i would be able to tell upon login if the server crashed or rebooted so that i could figure out what caused it.

---

### Post by CharlesA on 2010-06-15
You could login and check the uptime, that would tell you if there was a reboot or not.

uprecords displays something like this:

```
charles@thor:~$ uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    19 days, 23:57:52 | Linux 2.6.32-22-server    Wed May  5 21:31:57 2010
->   2    11 days, 08:55:09 | Linux 2.6.32-22-server    Fri Jun  4 11:31:50 2010
     3     8 days, 06:56:28 | Linux 2.6.32-22-server    Wed May 26 06:01:24 2010
     4     0 days, 22:32:16 | Linux 2.6.32-22-server    Thu Jun  3 12:58:43 2010
     5     0 days, 08:29:56 | Linux 2.6.32-22-server    Tue May 25 21:30:39 2010
     6     0 days, 00:32:34 | Linux 2.6.32-22-server    Wed May  5 20:00:36 2010
     7     0 days, 00:06:52 | Linux 2.6.32-22-server    Wed May  5 20:57:21 2010
     8     0 days, 00:06:48 | Linux 2.6.32-22-server    Wed May  5 20:33:49 2010
     9     0 days, 00:06:15 | Linux 2.6.32-22-server    Wed May  5 21:12:12 2010
    10     0 days, 00:01:20 | Linux 2.6.32-22-server    Wed May  5 20:45:42 2010
----------------------------+---------------------------------------------------
no1 in     8 days, 15:02:44 | at                        Thu Jun 24 11:29:41 2010
    up    40 days, 23:46:23 | since                     Wed May  5 20:00:36 2010
  down     0 days, 00:40:00 | since                     Wed May  5 20:00:36 2010
   %up               99.932 | since                     Wed May  5 20:00:36 2010
```

uptime displays this:

```
charles@thor:~$ uptime
 20:27:13 up 11 days,  8:55,  1 user,  load average: 0.22, 0.09, 0.12

```

I haven't ran into any time when the machine would reboot itself unless it was a hardware issue. I have mine set to install security updates automatically and the worst thing it does is state "System Restart Required" when you login, if it needs to be rebooted to apply an update.

---

### Post by braunshedd on 2010-06-15
> **CharlesA said:**
> You could login and check the uptime, that would tell you if there was a reboot or not.

uprecords displays something like this:

[code]charles@thor:~$ uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    19 days, 23:57:52 | Linux 2.6.32-22-server    Wed May  5 21:31:57 2010
->   2    11 days, 08:55:09 | Linux 2.6.32-22-server    Fri Jun  4 11:31:50 2010
     3     8 days, 06:56:28 | Linux 2.6.32-22-server    Wed May 26 06:01:24 2010
     4     0 days, 22:32:16 | Linux 2.6.32-22-server    Thu Jun  3 12:58:43 2010
     5     0 days, 08:29:56 | Linux 2.6.32-22-server    Tue May 25 21:30:39 2010
     6     0 days, 00:32:34 | Linux 2.6.32-22-server    Wed May  5 20:00:36 2010
     7     0 days, 00:06:52 | Linux 2.6.32-22-server    Wed May  5 20:57:21 2010
     8     0 days, 00:06:48 | Linux 2.6.32-22-server    Wed May  5 20:33:49 2010
     9     0 days, 00:06:15 | Linux 2.6.32-22-server    Wed May  5 21:12:12 2010
    10     0 days, 00:01:20 | Linux 2.6.32-22-server    Wed May  5 20:45:42 2010

thats exactly what i need. but what file would that command be put into to execute it when i logon?

---

### Post by CharlesA on 2010-06-15
Are you logging in via SSH or console?

---

### Post by braunshedd on 2010-06-15
At the moment, console since i just finished fixing a hardware problem, but usually i use ssh

---

### Post by WinstonChurchill on 2010-06-15
The 'last' command shows you the user login history, but it also has entires like this:
```
reboot   system boot  2.6.32-22-server Sun Jun 6 22:39 - 22:32 (8+23:53) 
```... which show you when the server was rebooted.

---

### Post by CharlesA on 2010-06-15
I added this to the end of ~/.profile:

```
uprecords
```

This is what it looks like when I connect via SSH:

```
login as: ubuntu
ubuntu@192.168.1.9's password:
Linux ubuntu-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010                                                                                                                                i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1     0 days, 00:06:14 | Linux 2.6.32-22-generic   Tue Jun 15 20:36:01 2010
     2     0 days, 00:02:00 | Linux 2.6.32-22-generic   Tue Jun 15 20:42:29 2010
->   3     0 days, 00:00:53 | Linux 2.6.32-22-generic   Tue Jun 15 20:45:22 2010
----------------------------+---------------------------------------------------
1up in     0 days, 00:01:08 | at                        Tue Jun 15 20:47:09 2010
no1 in     0 days, 00:05:22 | at                        Tue Jun 15 20:51:23 2010
    up     0 days, 00:09:07 | since                     Tue Jun 15 20:36:01 2010
  down     0 days, 00:01:07 | since                     Tue Jun 15 20:36:01 2010
   %up               89.088 | since                     Tue Jun 15 20:36:01 2010

```

The last command would probably work, but it's a bit much info wise:

```
ubuntu@ubuntu-laptop:~$ last
ubuntu   pts/1        odin.asgard.lcl  Tue Jun 15 20:46   still logged in
ubuntu   pts/0        :0.0             Tue Jun 15 20:45   still logged in
ubuntu   tty7         :0               Tue Jun 15 20:45   still logged in
reboot   system boot  2.6.32-22-generi Tue Jun 15 20:45 - 20:46  (00:01)
ubuntu   pts/0        :0.0             Tue Jun 15 20:42 - 20:43  (00:00)
ubuntu   tty7         :0               Tue Jun 15 20:42 - down   (00:01)
reboot   system boot  2.6.32-22-generi Tue Jun 15 20:42 - 20:44  (00:01)
ubuntu   tty8         :0               Tue Jun 15 20:42 - 20:42  (00:00)
ubuntu   pts/0        :0.0             Tue Jun 15 20:36 - 20:41  (00:04)
ubuntu   tty7         :0               Tue Jun 15 20:36 - 20:41  (00:05)
reboot   system boot  2.6.32-22-generi Tue Jun 15 20:36 - 20:42  (00:05)
ubuntu   tty7         :0               Tue Jun 15 15:58 - down   (00:11)
reboot   system boot  2.6.32-22-generi Tue Jun 15 15:58 - 16:09  (00:11)
ubuntu   pts/0        :0.0             Tue Jun 15 13:06 - 13:18  (00:11)
ubuntu   pts/0        :0.0             Tue Jun 15 13:04 - 13:06  (00:01)
ubuntu   tty7         :0               Tue Jun 15 12:36 - down   (00:41)
reboot   system boot  2.6.32-22-generi Tue Jun 15 12:36 - 13:18  (00:41)
ubuntu   tty7         :0               Tue Jun 15 07:58 - 08:34  (00:35)
reboot   system boot  2.6.32-22-generi Tue Jun 15 07:58 - 08:34  (00:35)
ubuntu   pts/0        :0.0             Tue Jun 15 06:50 - 06:51  (00:00)
ubuntu   pts/0        :0.0             Tue Jun 15 06:40 - 06:42  (00:01)
ubuntu   tty7         :0               Tue Jun 15 06:27 - down   (00:24)
reboot   system boot  2.6.32-22-generi Tue Jun 15 06:27 - 06:51  (00:24)
ubuntu   pts/0        :0.0             Mon Jun 14 22:03 - 22:05  (00:01)
ubuntu   tty7         :0               Mon Jun 14 22:03 - down   (08:23)
reboot   system boot  2.6.32-22-generi Mon Jun 14 22:03 - 06:26  (08:23)
ubuntu   tty7         :0               Mon Jun 14 21:14 - down   (00:47)
reboot   system boot  2.6.32-21-generi Mon Jun 14 21:14 - 22:02  (00:48)

wtmp begins Mon Jun 14 21:14:23 2010

```

If you don't need that much info about the records of uptime, you can just add this to the end of the ~./profile file.

```
uptime
```

---

### Post by braunshedd on 2010-06-15
> **CharlesA said:**
> I added this to the end of ~/.profile:

```
uprecords
```This is what it looks like when I connect via SSH:

```
login as: ubuntu
ubuntu@192.168.1.9's password:
Linux ubuntu-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010                                                                                                                                i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1     0 days, 00:06:14 | Linux 2.6.32-22-generic   Tue Jun 15 20:36:01 2010
     2     0 days, 00:02:00 | Linux 2.6.32-22-generic   Tue Jun 15 20:42:29 2010
->   3     0 days, 00:00:53 | Linux 2.6.32-22-generic   Tue Jun 15 20:45:22 2010
----------------------------+---------------------------------------------------
1up in     0 days, 00:01:08 | at                        Tue Jun 15 20:47:09 2010
no1 in     0 days, 00:05:22 | at                        Tue Jun 15 20:51:23 2010
    up     0 days, 00:09:07 | since                     Tue Jun 15 20:36:01 2010
  down     0 days, 00:01:07 | since                     Tue Jun 15 20:36:01 2010
   %up               89.088 | since                     Tue Jun 15 20:36:01 2010

```The last command would probably work, but it's a bit much info wise:

```
ubuntu@ubuntu-laptop:~$ last
ubuntu   pts/1        odin.asgard.lcl  Tue Jun 15 20:46   still logged in
ubuntu   pts/0        :0.0             Tue Jun 15 20:45   still logged in
ubuntu   tty7         :0               Tue Jun 15 20:45   still logged in
reboot   system boot  2.6.32-22-generi Tue Jun 15 20:45 - 20:46  (00:01)
ubuntu   pts/0        :0.0             Tue Jun 15 20:42 - 20:43  (00:00)
ubuntu   tty7         :0               Tue Jun 15 20:42 - down   (00:01)
reboot   system boot  2.6.32-22-generi Tue Jun 15 20:42 - 20:44  (00:01)
ubuntu   tty8         :0               Tue Jun 15 20:42 - 20:42  (00:00)
ubuntu   pts/0        :0.0             Tue Jun 15 20:36 - 20:41  (00:04)
ubuntu   tty7         :0               Tue Jun 15 20:36 - 20:41  (00:05)
reboot   system boot  2.6.32-22-generi Tue Jun 15 20:36 - 20:42  (00:05)
ubuntu   tty7         :0               Tue Jun 15 15:58 - down   (00:11)
reboot   system boot  2.6.32-22-generi Tue Jun 15 15:58 - 16:09  (00:11)
ubuntu   pts/0        :0.0             Tue Jun 15 13:06 - 13:18  (00:11)
ubuntu   pts/0        :0.0             Tue Jun 15 13:04 - 13:06  (00:01)
ubuntu   tty7         :0               Tue Jun 15 12:36 - down   (00:41)
reboot   system boot  2.6.32-22-generi Tue Jun 15 12:36 - 13:18  (00:41)
ubuntu   tty7         :0               Tue Jun 15 07:58 - 08:34  (00:35)
reboot   system boot  2.6.32-22-generi Tue Jun 15 07:58 - 08:34  (00:35)
ubuntu   pts/0        :0.0             Tue Jun 15 06:50 - 06:51  (00:00)
ubuntu   pts/0        :0.0             Tue Jun 15 06:40 - 06:42  (00:01)
ubuntu   tty7         :0               Tue Jun 15 06:27 - down   (00:24)
reboot   system boot  2.6.32-22-generi Tue Jun 15 06:27 - 06:51  (00:24)
ubuntu   pts/0        :0.0             Mon Jun 14 22:03 - 22:05  (00:01)
ubuntu   tty7         :0               Mon Jun 14 22:03 - down   (08:23)
reboot   system boot  2.6.32-22-generi Mon Jun 14 22:03 - 06:26  (08:23)
ubuntu   tty7         :0               Mon Jun 14 21:14 - down   (00:47)
reboot   system boot  2.6.32-21-generi Mon Jun 14 21:14 - 22:02  (00:48)

wtmp begins Mon Jun 14 21:14:23 2010

```If you don't need that much info about the records of uptime, you can just add this to the end of the ~./profile file.

```
uptime
```
im a noob for asking this but where is the profile file. when i cd to ~/ it says there are 0 files. is it in the etc directory?

---

### Post by CharlesA on 2010-06-15
That file is located in yer home directory. :)

If you do cd ~/ it takes you to your home directory, usually /home/username/. Any file with a "." at the beginning is hidden.

You can still find it using ls and edit it using nano.

```
ls ~./profile
```

```
nano ~./profile
```

---

### Post by braunshedd on 2010-06-16
i need a step by step here because when i add uprecords to the end of the .profile file nothing happens upon next login. Im using zsh as my shell, and the file mentioned something about it being invaild if bash was being used, and zsh i think is related to bash. I dont know.

---

### Post by CharlesA on 2010-06-16
You probably need to install uptimed like so:

```
sudo apt-get install uptimed
```

Once that's installed, log back in and see what happens.

I've not used zsh, so I don't know if it'll work or not.

---

### Post by braunshedd on 2010-06-16
i already have it installed. ill switch to bash to see if it will work

---

### Post by braunshedd on 2010-06-16
yep it works if i use bash. thats weird. oh well, thank you so much

look at my logon now

you can probably tell by looking at the picture that im 12, which is why i seem so incompetent. Im trying to get better though :)

---

### Post by CharlesA on 2010-06-16
It looks like you would need to add it to .zprofile for it to work with zsh as per this:

```
This is the Z Shell configuration function for new users,
zsh-newuser-install.
You are seeing this message because you have no zsh startup files
(the files .zshenv, .zprofile, .zshrc, .zlogin in the directory
~).  This function can help you with a few settings that should
make your use of the shell easier.
```

I did this to get it working:

```
nano ~/.zprofile
```

Added *uprecords* to .zprofile and saved it.

Logged in via SSH:

```
login as: ubuntu
ubuntu@192.168.1.9's password:
Linux ubuntu-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Tue Jun 15 21:33:18 2010 from odin.asgard.lcl
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1     0 days, 00:06:14 | Linux 2.6.32-22-generic   Tue Jun 15 20:36:01 2010
     2     0 days, 00:05:08 | Linux 2.6.32-22-generic   Tue Jun 15 21:20:12 2010
     3     0 days, 00:03:05 | Linux 2.6.32-22-generic   Tue Jun 15 20:45:22 2010
     4     0 days, 00:03:02 | Linux 2.6.32-22-generic   Tue Jun 15 21:27:00 2010
     5     0 days, 00:02:01 | Linux 2.6.32-22-generic   Tue Jun 15 21:30:42 2010
     6     0 days, 00:02:00 | Linux 2.6.32-22-generic   Tue Jun 15 20:42:29 2010
->   7     0 days, 00:01:14 | Linux 2.6.32-22-generic   Tue Jun 15 21:32:45 2010
----------------------------+---------------------------------------------------
1up in     0 days, 00:00:47 | at                        Tue Jun 15 21:34:44 2010
no1 in     0 days, 00:05:01 | at                        Tue Jun 15 21:38:58 2010
    up     0 days, 00:22:44 | since                     Tue Jun 15 20:36:01 2010
  down     0 days, 00:35:14 | since                     Tue Jun 15 20:36:01 2010
   %up               39.218 | since                     Tue Jun 15 20:36:01 2010
ubuntu-laptop%

```

The % means you are running zsh. :)

---

### Post by braunshedd on 2010-06-16
i had to edit the zshrc file to get it to work, but it did. I should have paid more attention to that when it showed up...
anyway, thanks so much for your help, i would have never figured it out. you guys should get paid

---

### Post by CharlesA on 2010-06-16
Don't forget to mark the thread as solved.

Also, if you want to limit the number of uptimes displayed, you can use the -m switch (it defaults to 10)

---

