---
title: "On login 5 packages can be updated"
date: 2009-07-25
forum: Server Platforms
---

### Post by danking12 on 2009-07-25
I just installed Ubuntu 9.04 Server. After that I installed VMware Server. When I login to my account on the server it prints to the terminal that "5 packages can be updated" and "10 updates are security updates"

I then run "sudo apt-get update" and then "sudo apt-get upgrade"

But it doesn't install any updates. Not really sure what the prompts about package and security updates are for but I would like to solve it.

Thanks for any help.

---

### Post by televisi on 2009-07-28
Hi danking12,
have you resolved your issue?

I just installed Ubuntu server 9.04 and only install the normal packages; after installation finish, I do:
```
sudo apt-get update
sudo apt-get upgrade
```after that, everytime I restart the same message appears:
```
5 packages can be updated.
10 updates are security updates.

```

Does anyone know how to resolve this issue?

---

### Post by danking12 on 2009-07-28
Sorry I haven't figure it out yet but I haven't looked into it at all. If I find a solution I will post back to this thread.

---

### Post by huarewe on 2009-08-12
I also have this issue. I just switched from gui to terminal only -- run the update/upgrade but whatever is placing the message in term isn't updating. 

Any help?

---

### Post by cariboo on 2009-08-12
Try using:

```
sudo apt-get dist-upgrade
```

to see if that solves the problem.

---

### Post by dspeer on 2009-08-18
My name is dietrich, and I had the same issue exactly. 

After running those apt-gets I rebooted the system, and everything was fine.

---

### Post by DigitalRonin on 2009-10-21
You shouldn't have to reboot the system.

The number of packages to update is coming from the message of the day, which is updated by cron. So, it should go away sometime after you update the packages. 

If you're impatient (like me), just run "sudo update-motd" after updating the packages. Then, the message should be different the next time you login.

---

### Post by AsylumDEG on 2010-01-11
Sorry to bump an old(er) thread, but the advice that cariboo907 gave:

sudo apt-get dist-upgrade

was the magic answer for me!  I had done the same - 
sudo apt-get update
sudo apt-get upgrade

many times but had forgotten about updating the distribution itself! Thanks for the reminder and with this post others will be able to hit on a search hit that says the solution works (at least for me)

Did it work for the original poster as well?  If so, it would be nice if they would have confirmed the fix.  If not, was there something else to be aware of?

---

### Post by aphatak on 2010-11-03
I am using Ubuntu Server 10.04 LTS, and I do not really want to upgrade to the next release till the next LTS release.  Does that mean I will keep on getting these package update messages?!?

---

### Post by aphatak on 2010-11-03
I have two servers - uname on each shows -
[INDENT]Linux fsrv 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux[/INDENT]
- on one (this shows packages to be updated but does not update any), and -
[INDENT]Linux vsrv 2.6.32-25-server #45-Ubuntu SMP Sat Oct 16 20:06:58 UTC 2010 x86_64 GNU/Linux[/INDENT]
- on the other (this shows 0 packages to be updated).  Both show Ubuntu 10.04.1 LTS on log in.  I swear I did not run dist-upgrade on the second machine.  How did I get rid of the package update message?!?

---

### Post by rovall on 2011-01-11
This message appears to be in Message Of The Day motd(5) file:
/etc/motd

I don't yet know which program puts it there, but I'm sure its updated periodically and not necesserily after you run aptitude or apt-get.

---

### Post by McLowry on 2011-01-18
Although this discussion is already a few months old, I would like to point out that [here (CLICK ME)]("http://www.linux-archive.org/ubuntu-user/451665-information-login.html") is a short discussion which explains the process.

---

### Post by Denbert on 2011-04-24
> **rovall said:**
> This message appears to be in Message Of The Day motd(5) file:
/etc/motd

I don't yet know which program puts it there, but I'm sure its updated periodically and not necesserily after you run aptitude or apt-get.

I have same problem on Ubuntu Server 10.04 LTS

I've tried all suggested commands including the apt-get dist-upgrade.

uname -a gives me:

[INDENT]Linux server.mydomain.biz 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux

But i still have the following messages after login via Putty:

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Sun Apr 24 09:50:14 CEST 2011

  System load:  0.11                Processes:             167
  Usage of /:   24.7% of 224.59GB   Users logged in:       0
  Memory usage: 1%                  IP address for eth0:   192.168.1.253
  Swap usage:   0%                  IP address for virbr0: 192.168.122.1

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Tue Apr 19 21:10:06 CEST 2011

  System load:  0.0                 Processes:             150
  Usage of /:   24.7% of 224.59GB   Users logged in:       0
  Memory usage: 3%                  IP address for eth0:   192.168.1.253
  Swap usage:   0%                  IP address for virbr0: 192.168.122.1

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

7 packages can be updated.
2 updates are security updates.
[/INDENT]
Any suggestions which can put me in the right direction?

---

### Post by Denbert on 2011-04-24
> **Denbert said:**
> 
Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Sun Apr 24 09:50:14 CEST 2011

  System load:  0.11                Processes:             167
  Usage of /:   24.7% of 224.59GB   Users logged in:       0
  Memory usage: 1%                  IP address for eth0:   192.168.1.253
  Swap usage:   0%                  IP address for virbr0: 192.168.122.1

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Tue Apr 19 21:10:06 CEST 2011

  System load:  0.0                 Processes:             150
  Usage of /:   24.7% of 224.59GB   Users logged in:       0
  Memory usage: 3%                  IP address for eth0:   192.168.1.253
  Swap usage:   0%                  IP address for virbr0: 192.168.122.1

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

7 packages can be updated.
2 updates are security updates.
[/INDENT]


Hmm, I removed the /etc/motd.tail and bingo, the problem was fixed :D - I noted the date on the last part, and it says April, 19 - hence it must have had some problem with an update during the installation as the system was indeed installed on the 19th!

---

### Post by egpetrich on 2011-04-25
It looks like something in a recent update overwrote /etc/motd.tail and introduced confusion. I was able to restore the file with the (automatic?) backup /etc/motd.tail.old.

---

### Post by CharlesA on 2011-04-25
> **egpetrich said:**
> It looks like something in a recent update overwrote /etc/motd.tail and introduced confusion. I was able to restore the file with the (automatic?) backup /etc/motd.tail.old.
Interesting.

Thank you, I just checked and that was the problem.

I was left scratching my head when I ssh'd into my lucid box and it said there were updates available.

I didn't see a backup, so I just edited the file manually.

---

### Post by Denbert on 2011-04-25
> **CharlesA said:**
> Interesting.

Thank you, I just checked and that was the problem.

I was left scratching my head when I ssh'd into my lucid box and it said there were updates available.

I didn't see a backup, so I just edited the file manually.

Did you removed all the lines in the file?

---

### Post by CharlesA on 2011-04-25
I just took out these lines:

```

7 packages can be updated.
2 updates are security updates.
```

Left the blank line between that and the rest of the motd.

---

### Post by Denbert on 2011-04-25
> **CharlesA said:**
> I just took out these lines:

```

7 packages can be updated.
2 updates are security updates.
```

Left the blank line between that and the rest of the motd.

These are last two lines in my file!

```
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Tue Apr 19 21:10:06 CEST 2011

  System load:  0.0                 Processes:             150
  Usage of /:   24.7% of 224.59GB   Users logged in:       0
  Memory usage: 3%                  IP address for eth0:   192.168.1.253
  Swap usage:   0%                  IP address for virbr0: 192.168.122.1

  Graph this data and manage this system at https://landscape.canonical.com/

7 packages can be updated.
2 updates are security updates.

```

---

### Post by CharlesA on 2011-04-25
Those are the two I took out.

I don't think that's motd.tail is supposed to have the updates listed in it. My server has just this (the one I removed the text from was my desktop):

```

charles@Thor:~$ cat /etc/motd.tail
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Thu Apr 21 19:32:52 PDT 2011

  System load:  0.08                Processes:           119
  Usage of /:   18.7% of 441.60GB   Users logged in:     0
  Memory usage: 31%                 IP address for eth0: 192.168.1.2
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/


```

---

### Post by Denbert on 2011-04-25
Great, I'll try it and wait for the next update to see if it will work again.

---

### Post by Turtle.net on 2011-05-03
I just removed /etc/motd.tail and the message is back to normal.
I guess that motd doesn't need motd.tail anymore

---

### Post by Jay86 on 2011-05-06
Thank you guys so much! This just fixed it for me. Same problem, outdated MOTD. Running Ubuntu Server 10.04. All good now :)

---

### Post by Denbert on 2011-05-08
As noticed i removed the /etc/modt.tail file, BUT:

Login to the system says:



[I]Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

0 packages can be updated.
0 updates are security updates.[/I]

Just to check i ran apt-get update and apt-get upgrade and the system found 4 updates to the system.

Therefore something must be broken!

---

### Post by Turtle.net on 2011-05-09
> **Denbert said:**
> As noticed i removed the /etc/modt.tail file, BUT:

Login to the system says:



[I]Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

0 packages can be updated.
0 updates are security updates.[/I]

Just to check i ran apt-get update and apt-get upgrade and the system found 4 updates to the system.

Therefore something must be broken!

I guess that you jumped to conclusion a little bit too quickly.
If you redo "sudo aptitude update" then logoff and log back in that should be fine.

---

### Post by SoFl W on 2011-05-31
I had the same problem as described above.  Renaming/removing the MoTD file "fixes" it but is there a problem.  Will the next time MoTD gets generated will the problem be fixed?

This is a new install of Ubuntu-Server 10.4 installed as a virtual machine.

EDIT:
Never work on multiple problems when you haven't eaten in a while.

---

### Post by zeefreak on 2011-06-06
i had this problem, and this thread helped . . . but not permanently.

it seems like every few weeks i'm having to redelete the /etc/motd.tail file.

it is starting to annoy me that the problem keeps recurring. does anyone have a more permanent solution? i have two servers that are experiencing this issue.

10.04lts.

---

### Post by CharlesA on 2011-06-06
I am puzzled why I am not having that problem on my Lucid server machine.

I removed motd.tail from my Lucid server but it hasn't been recreated as far as I can tell.

It's still happening on my Lucid desktop, where all I did was delete the contents of motd.tail, but left the file in tact. *shrugs*

EDIT: Seems I am having the same thing happen on my Lucid server box now - It said 5 packages could be updated, and I logged off and then back on and the motd wasn't updated.

Guess I'll check later to see if it changes.

EDIT2: The motd file updated as expected later that evening.

---

### Post by programaths on 2011-06-08
Thank you very much ! I was puzzled by this too.

---

### Post by egpetrich on 2011-06-09
Instead of removing "/etc/motd.tail", replace it with an empty file:
```
sudo rm -f /etc/motd.tail
sudo touch /etc/motd.tail
```
From what I have seen of the code associated with this, "motd.tail" is only created if it doesn't exist.

---

