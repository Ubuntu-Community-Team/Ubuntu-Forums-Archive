---
title: "Can't su, but can sudo -i"
date: 2012-06-06
forum: Server Platforms
---

### Post by jwright8 on 2012-06-06
I have an interesting problem.  After going through and trying to fix some things Tiger found wrong with my system (looking on forums), I SSH'd in.  

As far as I remember, the major things I did was remove users I didn't need (like www-data since I won't be using Apache/web server capabilities, news, and games users).  I also chowned /usr/bin/at to root:root like it suggested.  I also disabled the message capability of root (I forget how, but it was 'something/mesg n' in ssh to change it).

When I log in with a normal user, it works.  I then type su, and it asks me for my root pass as usual.  It then says "authentication failure."  I tried sudo -i, and it asked me for the pass, and it accepted it and changed me to root.  Thinking somehow my root pass got changed/messed with, I physically went to the machine (which was running with root already logged in), typed passwd, and put in the password to reset it to the password it should be.  It still won't let me su, but it still lets me sudo -i.  

Once I'm sudo'd in as root, I can do su <user> for a normal user and change to it without a problem.

Anyone have any ideas?  Thanks!

EDIT:  I'm running 10.04 LTS Ubuntu Server

I also see this in the logs:

> 
Jun  6 07:00:01 Alatheia CRON[14261]: pam_unix(cron:account): could not identify user (from getpwnam(smmsp))
I looked up and read that I needed to do the following:
```

chmod 644 /etc/crontab
chmod -R 755 /etc/cron.d
/etc/init.d/cron restart

```

Instead of the last line, I did:

```

service cron restart

```

Since that seems to be the newer convention.

---

### Post by snowpine on 2012-06-06
**sudo -i** is the correct and supported way to become root in Ubuntu. (Root password is disabled by default.)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In the future when you make statements such as "like it suggested" or "I read that..." please provide links so we can discuss with you. And **document** the changes you make, don't just say "I did something but I forget what, help me fix it!" ;)

Also if you do choose to enable root login (not recommended or supported on these forums) make sure you have blocked root login in SSH.

Lots of good info on setting up your Ubuntu server here:

[https://help.ubuntu.com/10.04/serverguide/index.html](https://help.ubuntu.com/10.04/serverguide/index.html)

---

### Post by jwright8 on 2012-06-06
I have disabled direct root login through SSH, hence why I was using su(do).  I use sudo -i and/or su for the same fact that I'd imagine most people on this forum do: remembering to type sudo before every command, or the simple fact that it gets annoying and repetitive when you're doing a lot at once.

I suppose I can use sudo -i, but my question was more in relation to what commonly breaks the capability of su.  It wasn't that I couldn't get into root without it; it was that I apparently misconfigured/broke something, and for the sake of learning, I wanted to get an idea of what it **could** be based on general possibilities.  

I'm not the type to post and not search for the answer first.  I've been able to find nothing on the odd problem, and I was hoping someone could point me in the right direction as to why it does what it does.  I'm not interested in just copy+pasting some answer and skimming by, or I'd have just used the sudo -i command and went on about my business.

Most of the (few) modifications that I listed that I did seemed sound on principle before I did them.  While I didn't remember the exact file that I set to "n" as opposed to "y," I had assumed that someone that was familiar with it (which were the people I was asking the question of) would at least be able to glean what I meant by me describing it as disabling the root message capability.  The "as far as I remember" wasn't meant to be a "omg I have no idea what I did so it could be anything out of millions of possibilities."  It was meant to say "I'm 95% sure it is one of these, but there's a slight possibility it's not, so feel free to point me at a link I can read more on in relation to this problem happening."

Thanks for the reply.

---

### Post by snowpine on 2012-06-06
Wow; you're a fast reader, the entire root/sudo documentation and server guide in 7 minutes! :)

I don't know which file or setting you forgot you changed; sorry.

> **jwright8 said:**
> I'd have just used the sudo -i command and went on about my business.

That's exactly what I would do, personally, since it is the recommendation of the Ubuntu developers and the members of this support forum.

---

### Post by jwright8 on 2012-06-06
While your sarcasm is fairly obvious, if you yourself took the time to be as thorough as you hold everyone else to being, you'd have seen on my profile the other thread I started (only about 5 days ago I think?) that openly said that I've already read that documentation (and more on HOWTO forge, links made by mods on these forums, etc.).

Again, in your second line, your sarcasm is completely and totally unhelpful.  I had almost forgotten what it was like to post and have to immediately rape someone just to get a general (see not specific) link and or nudge in the right direction.  As below:

> 
my question was more in relation to what commonly breaks the capability of su
> 
point me in the right direction as to why it does what it does
> 
" feel free to point me at a link I can read more on **in relation to this problem happening**."
I didn't have that problem in the last thread on this very same forum, so I had assumed it wouldn't be an issue this time around; obviously I was mistaken.

In short, if you don't have anything helpful to contribute, and only want to flame/troll, kindly do it to someone that wouldn't tear you to shreds for being a hypocrite.

Thanks!

---

### Post by rubylaser on 2012-06-06
Posting the output of 
```
history
```
could remind you of the exact commands you ran and let others see as well if you have questions.

---

### Post by jwright8 on 2012-06-06
Is there a way to define it to show more lines?  At the moment it looks like this:

```

1  su
    2  su passwd
    3  sudo passwd
    4  su
    5  exit
    6  su
    7  exit
    8  ls
    9  su
   10  exit
   11  su
   12  exit
   13  su
   14  ls
   15  exit
   16  cd
   17  su
   18  exit
   19  su
   20  exit
   21  su
   22  su
   23  su
   24  exit
   25  su
   26  su
   27  exit
   28  su
   29  exit
   30  sudo pico /var/log/auth.log
   31  history

```From when I was trying to see what was going on with su.

I did find the command after all, though.  It was:

```

/usr/bin/mesg n

```But when I set it back to y, it still doesn't let me in su.

EDIT: Nevermind, I was logged in as my user, not root, when I did that.

```

 1030  /proc/sys/net/ipv4/conf/all/accept_redirects
 1031  cat /proc/sys/net/ipv4/conf/all/accept_redirects
 1032  cat /proc/sys/net/ipv4/conf/all/send_redirects
 1033  sysctl -a|grep martian
 1034  echo 1 > /proc/sys/net/ipv4/conf/all/log_martians
 1035  sysctl -a|grep martian
 1036  stat /var/log/btmp
 1037  cat /etc/passwd
 1038  userdel -r games
 1039  userdel -r news
 1040  userdel -r irc
 1041  userdel -r landscape
 1042  userdel -r smmta
 1043  userdel -r smmsp
 1044  userdel -r mail
 1045  cat /etc/passwd
 1046  userdel -r www-data
 1047  userdel -r list
 1048  cat /etc/passwd
 1049  pico /etc/profile
 1050  pico ~/.bashrc
 1051  ./~/.bashrc
 1052  chown root:root /bin/su
 1053  chown root:root /bin/at
 1054  chown root:root /usr/bin/at
 1055  pico /usr/bin/passwd
 1056  ls -l /usr/bin/passwd
 1057  man passwd
 1058  ls
 1059  cat /etc/passwd

```


EDIT:  

After posting that, I see that I did
```

 1052  chown root:root /bin/su

```

Would this have caused it?  Why?  And what is it chowned to by default?

---

### Post by rubylaser on 2012-06-06
You can add more lines to history by changing the HITFILESIZE variable value in your ~/.bashrc file. 

In regards to su, here are it's standard permissions.
```
rubylaser@ubuntu-test:~$ ls -la /bin/su
-rwsr-xr-x 1 root root 36864 2011-02-14 17:11 /bin/su

```

---

### Post by jwright8 on 2012-06-06
Okay, mine says :

```

root@Alatheia:/# ls -la /bin/su
-rwxr-xr-x 1 root root 31100 2011-02-14 17:11 /bin/su

```So the chown shouldn't have broken it, right?  But it seems the number in the middle is different, 36864 as opposed to 31100... what does this number mean?  Is it permissions?

EDIT: 

I just saw the x on mine instead of s in -rwsr in comparison to my -rwxr as well

---

