---
title: "corrupt syslog file"
date: 2010-04-20
forum: Security
---

### Post by ubuchignome on 2010-04-20
I went to open the log file viewer, and it seem like the log file has been corrupted. This is the error I received.


"/var/log/btmp this file is not a regular file or is not a text file. "


It looks like the /var/log file has been replaced by the file listed.Any ideas as to how this could happen? 



Thanks much!


:confused:

---

### Post by cdenley on 2010-04-21
As the error says, /var/log/btmp is not a text file. Nor should it be.
```

sudo last -f /var/log/btmp

```

---

### Post by Rubi1200 on 2010-04-21
I had exactly the same thing happen after a recent system update (I think it was after the one that included the update for sudo, but cannot be sure). Anyway. I found that resetting the desktop settings fixed the problem. If this is a better way to do it, let me know because resetting Gnome obviously reset everything (oops!)
Thanks.

btw, this seems to be a recurring bug because it has happened to me twice after updates.

---

### Post by lensman3 on 2010-04-21
Try a "cp /dev/null /var/log/btmp".  See if that will truncate the file.  This "trick" used to be the way to truncate a log file on Sun's that grew and grew.  The problem was that the file was opened using inodes.  This was the only way to get around the problem.

---

### Post by ubuchignome on 2010-04-21
Thanks all. I figured that it had something to do with an update, I had just updated prior to checking the log files. I know it not a text file as well. I was wondering why the update was causing this. 
Be well!

---

### Post by cdenley on 2010-04-21
> **ubuchignome said:**
> Thanks all. I figured that it had something to do with an update, I had just updated prior to checking the log files. I know it not a text file as well. I was wondering why the update was causing this. 
Be well!

I still don't understand what the problem is. Your complaining that this:
```

gksu gnome-system-log /var/log/btmp

```
gives you
> /var/log/btmp this file is not a regular file or is not a text file.
Is this not correct? Is it supposed to be able to parse that binary log file?

Then you said
> 
/var/log file has been replaced by the file listed


How can a directory be replaced by a binary file contained within that directory? I'm assuming that was a typo? What is the update causing?

---

### Post by Rubi1200 on 2010-04-21
Hi cdenley,
unfortunately I did not take a screenshot when this occurred so all I can do is try and explain it as best I can.
After a system update I went to System > Administration > Log File Viewer to check something. The file does open, but there is a block of text at the top with the message that /var/log/btmp this file is not a regular file or is not a text file.
Clicking ok makes it go away and it is possible to view the logs.
However, this happens each time one opens the viewer again. I have noticed this occurs after certain system updates (again, I should have tracked when exactly but didn't).
I found that using the code rm -rf .gnome .gnome2 .gconf .gconfd .metacity reset the log file viewer to the original default without the error message we have been experiencing.
Of course, it also reset ALL my desktop settings too!
In any event, I think the real question here is whether or not this is really a bug or if you can suggest a simpler workaround to get rid of the error message without having to reset the whole desktop.
Your input is much appreciated.
Thanks in advance.

---

### Post by cdenley on 2010-04-21
So this happens when you simply open the log viewer? I assumed that you actually attempted to open that log file.
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/401499](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/401499)

---

### Post by Rubi1200 on 2010-04-21
ok here is the funny thing: what I am getting is actually a combination of the two things you linked to: I get the message 
/var/log/btmp
 You don't have enough permissions to read the file.
with the box you see in the screenshot. Closing the dialog box makes it go away and I can view the logs normally. However, next time I open the log file viewer; same thing, same message. It is an annoyance more than anything else, but it does seem to happen after certain updates.
As I said before, resetting the desktop gets rid of the message completely, but it would be nice to find a workaround that does not require resetting the entire desktop!
Since this has been reported before and since there seem to be some workarounds shall we call this solved?
Also, would this, as one user suggested, work sudo chmod +r /var/log/btmp ? 
Thanks

---

### Post by cdenley on 2010-04-21
> **Rubi1200 said:**
> Also, would this, as one user suggested, work sudo chmod +r /var/log/btmp ? 

That would get rid of the permissions error, but not the binary file error. Perhaps if you have no failed logins, the file will be empty, and you won't get the binary file error. Or you can truncate it, as suggested in this thread.

---

### Post by Rubi1200 on 2010-04-21
Ok, thanks.
:)

---

### Post by ubuchignome on 2010-04-21
I wasn't complaining, I was asking why, when I go to System > Administration > Log File Viewer, I am getting this file (/var/log/btmp)  insted of the proper log files. But I think that has been cleared up already.

---

### Post by cdenley on 2010-04-21
> **ubuchignome said:**
> I wasn't complaining, I was asking why, when I go to System > Administration > Log File Viewer, I am getting this file (/var/log/btmp)  insted of the proper log files. But I think that has been cleared up already.

I'm guessing it attempts to scan all the files in /var/log when it starts, but then I'm confused why I don't have the same issue in 9.10 with a non-empty /var/log/btmp and restricted read permission. What version do you have?
```

cdenley@ubuntu:~$ sudo apt-cache policy gnome-utils
gnome-utils:
  Installed: 2.28.1-0ubuntu1
  Candidate: 2.28.1-0ubuntu1
  Version table:
 *** 2.28.1-0ubuntu1 0
        500 http://lug.mtu.edu karmic/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by ubuchignome on 2010-04-21
9.10

---

### Post by cdenley on 2010-04-21
> **ubuchignome said:**
> 9.10

I meant what version of gnome-utils package which provides the log viewer.
```

sudo apt-cache policy gnome-utils

```

---

### Post by ubuchignome on 2010-04-21
2.28.1-Oubntul

---

### Post by cariboo on 2010-04-21
You do realize that /var/log/btmp is a listing of last logged in users, and can be read by entering **last**, or **sudo lastb** to see the last bad login attempt.

---

### Post by ubuchignome on 2010-04-21
Is this a security threat?

---

### Post by cariboo on 2010-04-21
No, it's been around as long as I've been using a Linux variant. Have a look [here]("http://linux.about.com/library/cmd/blcmdl1_lastb.htm").

---

### Post by Rubi1200 on 2010-04-22
Personally, I think this is a bug in the gnome-utils package, but since there seem to be ways around it, and since it is more of an annoyance than anything else, I am not too worried. And the last and lastb commands are very useful; thanks!
:)

---

### Post by ubuchignome on 2010-04-22
Thanks much!

---

### Post by Squideshi on 2010-05-02
> **Rubi1200 said:**
>  
/var/log/btmp
 You don't have enough permissions to read the file.


[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---

### Post by cariboo on 2010-05-02
I don't know why there is a bug about btmp and wtmp, you aren't supposed to read the file directly, use last and lastb to read it.

Here's a snippet of the contents of wtmp:

```
cat wtmp
~~~reboot2.6.32-21-generict&#65533;K&#65533;&#65533;2~~~runlevel2.6.32-21-generict&#65533;K.&#65533;tty44LOGINt&#65533;Ktty55LOGINt&#65533;KQtty22LOGINt&#65533;KRtty33LOGINt&#65533;KWtty66LOGINt&#65533;Ktty11LOGINt&#65533;K&#65533;tty7:0jimk:01t&#65533;K<(62~~~runlevel2.6.32-21-genericsw&#65533;Kx&#65533;&#65533;tty7:0:0sw&#65533;K&#65533;~~~shutdown2.6.32-21-genericuw&#65533;K~~~reboot2.6.32-21-generic&#65533;KO2~~~runlevel2.6.32-21-generic&#65533;K&&#65533;tty44LOGIN&#65533;K&#65533;tty55LOGIN&#65533;K&#65533;tty22LOGIN&#65533;K&#65533;tty33LOGIN&#65533;K&#65533;tty66LOGIN&#65533;K|tty11LOGIN&#65533;K&#65533;tty7:0jimk:0&#65533;w&#65533;KXC	gVpts/0/0jimk:0.06&#65533;&#65533;K&#65533;&#65533;gVpts/2/2jimk:0.0&#1996;&#65533;K&#65533;@
```

---

### Post by cdenley on 2010-05-02
> **cariboo907 said:**
> I don't know why there is a bug about btmp and wtmp, you aren't supposed to read the file directly, use last and lastb to read it.

Here's a snippet of the contents of wtmp:

```
cat wtmp
~~~reboot2.6.32-21-generict&#65533;K&#65533;&#65533;2~~~runlevel2.6.32-21-generict&#65533;K.&#65533;tty44LOGINt&#65533;Ktty55LOGINt&#65533;KQtty22LOGINt&#65533;KRtty33LOGINt&#65533;KWtty66LOGINt&#65533;Ktty11LOGINt&#65533;K&#65533;tty7:0jimk:01t&#65533;K<(62~~~runlevel2.6.32-21-genericsw&#65533;Kx&#65533;&#65533;tty7:0:0sw&#65533;K&#65533;~~~shutdown2.6.32-21-genericuw&#65533;K~~~reboot2.6.32-21-generic&#65533;KO2~~~runlevel2.6.32-21-generic&#65533;K&&#65533;tty44LOGIN&#65533;K&#65533;tty55LOGIN&#65533;K&#65533;tty22LOGIN&#65533;K&#65533;tty33LOGIN&#65533;K&#65533;tty66LOGIN&#65533;K|tty11LOGIN&#65533;K&#65533;tty7:0jimk:0&#65533;w&#65533;KXC	gVpts/0/0jimk:0.06&#65533;&#65533;K&#65533;&#65533;gVpts/2/2jimk:0.0&#1996;&#65533;K&#65533;@
```

The bug is that the log viewer would attempt to read those files when it was started. Nobody was trying to read them, the error would just pop up when the application was started.

---

### Post by cariboo on 2010-05-02
I never use the log file viewer, so I guess I've never seen the message.

---

