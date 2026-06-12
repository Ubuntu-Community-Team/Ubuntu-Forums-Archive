---
title: "rkhunter warnings and network issue"
date: 2012-02-19
forum: Security
---

### Post by CaptainofCrunch on 2012-02-19
I'm pretty new to Ubuntu so forgive me if I sound like an idiot when you read this.

I have rkhunter installed on my computer. First time i did a --check I go no warnings, next time i got the following warnings. 

[B]/usr/bin/unhide.rb [WARNING]
checking for hidden file directories [WARNING]
[/B]

After I got these warnings I googled each one to see what it meant, can't remember what exactly they said but basically it was not a security risk.

Next scan a few weeks after that I got these warnings.

[B]/usr/bin/unhide.rb
/sbin/ifconfig
/sbin/ifdown
checking for hidden files and directories
[/B]

Again I googled and nothing bad came up.

I did another scan today and I got these warnings.

[B]/usr/bin/url
/usr/bin/mail
/usr/bin/rpm
/usr/bin/unhide.rb
/usr/bin/bsd-mailx
/sbin/ifconfig
/sbin/ifdown
checking for hidden files and directories
[/B]

Can anybody tell me has my machine been compromised or what is going on?

Also I have noticed a couple of times that my network has been uploading and downloading at about 200-300Kbs when i am in the homescreen with not updates or browsers running. When I seen this happen I immediately switched off the internet for a few minutes and when I turned it back on network usage was back to normal.

Again any help with this issue would be much appreciated. I have tried searching for a solution to the second issue but I haven't found anything.

---

### Post by CaptainofCrunch on 2012-02-19
I'm running Ubuntu 11.10

---

### Post by Dangertux on 2012-02-19
These errors have to do with two things.

The first being some of those are scripts or symlinks to programs elsewhere. These are interpreted as sign of compromise, however in Ubuntu it is normal for them to be that way. Rkhunter was designed with a more traditional Linux in mind (RHEL/CentOS/Gentoo) Ubuntu/Debian do things a little bit differently, and link or put wrapper scripts in place to maintain compatibility with these other distros.

Additional errors can be caused if you used rkhunter after an update without rebuilding it's database.

```

sudo rkhunter --propupd

```

Keep in mind this, will normalize your baseline database, and if your system is compromised it will be using the compromised hash sums as a baseline.

You should do a scan prior to updating, then run that command immediately after doing an update before using your system for anything else in order to maximize the effectiveness of rkhunter.

All in all I would say there is probably nothing to worry about.

Hope this helps.

---

### Post by CaptainofCrunch on 2012-02-19
> **Dangertux said:**
> These errors have to do with two things.

The first being some of those are scripts or symlinks to programs elsewhere. These are interpreted as sign of compromise, however in Ubuntu it is normal for them to be that way. Rkhunter was designed with a more traditional Linux in mind (RHEL/CentOS/Gentoo) Ubuntu/Debian do things a little bit differently, and link or put wrapper scripts in place to maintain compatibility with these other distros.

Additional errors can be caused if you used rkhunter after an update without rebuilding it's database.

```

sudo rkhunter --propupd

```

Keep in mind this, will normalize your baseline database, and if your system is compromised it will be using the compromised hash sums as a baseline.

You should do a scan prior to updating, then run that command immediately after doing an update before using your system for anything else in order to maximize the effectiveness of rkhunter.

All in all I would say there is probably nothing to worry about.

Hope this helps.

Ahh ok I understand now so basically I was doing a legitimate change to those files by updating my system but rkhunter didn't know that, so I need to in a way reset rkhunter.

so anytime I do a system update I should 
1)rkhunter --check
2)sudo rkhunter --propupd 
3)update system
4)rkhunter --check

Is this correct?

Do you know anything about the second problem?

---

### Post by Dangertux on 2012-02-19
> **CaptainofCrunch said:**
> Ahh ok I understand now so basically I was doing a legitimate change to those files by updating my system but rkhunter didn't know that, so I need to in a way reset rkhunter.

so anytime I do a system update I should 
1)rkhunter --check
2)sudo rkhunter --propupd 
3)update system
4)rkhunter --check

Is this correct?

Do you know anything about the second problem?

The order should be 

1 - rkhunter --check
2 -  update
3 - sudo rkhunter --propupd
4  rkhunter --check

The second problem is a little odd, and I would be slightly concerned, do you do any torrenting? Bit torrent clients are famous for doing that.

Hope this helps.

---

### Post by CaptainofCrunch on 2012-02-19
> **Dangertux said:**
> The order should be 

1 - rkhunter --check
2 -  update
3 - sudo rkhunter --propupd
4  rkhunter --check

The second problem is a little odd, and I would be slightly concerned, do you do any torrenting? Bit torrent clients are famous for doing that.

Hope this helps.

Excellent thank you very much.

No not tethering at all. No Bit torrent or other torrent programs. It's a wired connection aswell.

It has only happened a few times. Obviously once is too many. 

What was weird was that when it happens the values for sent and received were within about 10Kbs of each other. Could it be a bug in the system indicator. 

I'm using System Monitor for upload and download speeds.

Also I did a reset on rkhunter and then scanned again and I'm still getting these warnings.

/usr/bin/unhide.rb 
Checking for hidden files and directories

---

### Post by CaptainofCrunch on 2012-02-23
> **Dangertux said:**
> The order should be 

1 - rkhunter --check
2 -  update
3 - sudo rkhunter --propupd
4  rkhunter --check

The second problem is a little odd, and I would be slightly concerned, do you do any torrenting? Bit torrent clients are famous for doing that.

Hope this helps.

I'm still getting these warnings

/usr/bin/unhide.rb 
Checking for hidden files and directories

I've reset rkhunter a couple of times and I'm still getting those warnings. 

Any suggestions?

---

### Post by Dangertux on 2012-02-23
> **CaptainofCrunch said:**
> I'm still getting these warnings

/usr/bin/unhide.rb 
Checking for hidden files and directories

I've reset rkhunter a couple of times and I'm still getting those warnings. 

Any suggestions?

You're going to continue to get the unhide.rb warning, and Checking for hidden files and directories isn't a warning so much as an informative update.

Hope this helps.

---

### Post by CaptainofCrunch on 2012-02-23
> **Dangertux said:**
> You're going to continue to get the unhide.rb warning, and Checking for hidden files and directories isn't a warning so much as an informative update.

Hope this helps.

Why will I still get the unhide.rb warning?

I'm still learning, sorry.

---

### Post by Dangertux on 2012-02-23
rkhunter tends to trigger on scripts (ruby, python, perl , bash ..etc) in your /usr/bin /usr/local/bin /bin or /sbin directories.

This is because legitimate programs are often swapped with scripts , that are in the direct path so they are executed when a normal command is run on a compromised system.


Hope this helps.

---

### Post by CaptainofCrunch on 2012-02-23
> **Dangertux said:**
> rkhunter tends to trigger on scripts (ruby, python, perl , bash ..etc) in your /usr/bin /usr/local/bin /bin or /sbin directories.

This is because legitimate programs are often swapped with scripts , that are in the direct path so they are executed when a normal command is run on a compromised system.


Hope this helps.

That makes sense.

Thank you very much for your help.

---

