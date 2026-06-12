---
title: "Ubuntu 18.04 LTS &quot;Bionic Beaver&quot; Auto Updates Not Working"
date: 2019-01-31
forum: Security
---

### Post by sunrise718 on 2019-01-31
We have two computers with Ubuntu 18.04 LTS "Bionic Beaver" and neither of them are getting automatic updates.  

One of them is just getting a "no updates available" or "system is updated" message with no evident updates.

The other computer gets a message prompt about needing a Thunderbolt XPS Update.  Nothing else.

This is trying to use the automatic update feature and not updating through the command line.

Does anyone have any suggestions on what is missing or what could be done to fix any updating issues?

---

### Post by Frogs Hair on 2019-02-16
What are your settings in software & Updates?

---

### Post by deadflowr on 2019-02-16
Look at the unattended-upgrades and apt logs in /var/log.

---

### Post by sunrise718 on 2019-03-05
I appreciate your response and am sorry for the delay in replying.  I don't see any settings in software and updates.  Perhaps my installation is missing detailed options.

---

### Post by sunrise718 on 2019-03-05
Thank you for your response.  I apologize for the delay in responding.  I finally navigated to /var/lib/apt/lists and outputted information.  I have no idea what to do with that information as a newbie.

It starts off with:

auxfiles
lock
partial
security.ubutunto.com_ubutntu_dists_bionic-security_InRelease
  ... Bionic_universe_binary ... Etc.

... and us.archive.ubuntu.com_ubuntu_dists_bionic_multiverse ... Etc.

Not sure if it's updating behind the scenes very quickly since I'm not logged on for long or I need to manually update the packages or if I can set it to automatically update because it's not doing so.  

Help?

---

### Post by Dennis N on 2019-03-05
Check "Software and Updates" utility. Look at the "updates" tab. Settings should look like the attached screenshot in the original installation. This will get you 'unattended upgrades' for security updates and a weekly notification of non-security updates. You are not notified that unattended upgrades have been done for you. If you are curious about what the unattended upgrades were, look at the entries of /var/log/apt/history.log which are all dated.

---

### Post by sunrise718 on 2019-03-06
Okay, I found the Software and Updates menu and it matches your photo.  I am unable to check the log because permission is denied.  I tried entering sudo at the prompt and my regular and then my super pw but that is not working.  How do I resolve that?

I am not logged on for long so it seems odd that I am up-to-date as it claims when I check for updates. 

In the old days, you used to be able to see the updaates being installed but I guess that changed.

---

### Post by Dennis N on 2019-03-07
>  I am unable to check the log because permission is denied. I tried entering sudo at the promot and my regular and then my super pw but that is not working. How do I resolve that?

You can check the permissions on history.log with the command used here:

```
dmn@Tyana-vm:~$ ls -l /var/log/apt/history.log
-rw-r--r-- 1 root root 124661 Mar  7 05:37 /var/log/apt/history.log

```
If you don't know how to interpret this, it shows anyone can read the file, which is the correct permission setting. Yours should have the same set of dashes and letters (-rw-r--r--) at the front. 

The unattended upgrades on my Ubuntu system begin within a minute or so of logging in. You can read history.log in the terminal with:
```
cat /var/log/apt/history.log
```
Newest are at the end.

---

### Post by sunrise718 on 2019-05-07
Thanks for the feedback.  At the Terminal prompt, I entered:

```
ls -l /var/log/apt/history.log
```

and it returned:

```
-rw-r--r-- 1 root root 0 Apr 1 11:48 /var/log/apt/history.log
```

Then, at the prompt, I entered:

```
cat /var/log/apt/history.log
```

but nothing happened.  

So, it appears that I have the correct permissions but no access to the history.log yet.

Is the 0 after root root a problem?  You have 124661, which probably indicates the log size, so 0 means that nothing is writing to the log if I'm correct and, therefore, it is not accessible. 
 
**UPDATE:**

I followed the instructions at: 

[https://www.linuxuprising.com/2019/01/how-to-show-history-of-installed.html](https://www.linuxuprising.com/2019/01/how-to-show-history-of-installed.html)

```
 grep "upgrade " /var/log/dpkg.log 
```

did not output anything (as with history.log not showing anything).

However, 

```
 zgrep "upgrade " /var/log/dpkg.log.2.gz 
```

outputted a long string of results.  The date at the top was 2019-03-12.  

I have not checked log.1.zg or others.

Now what?  How come I cannot view anything at **history.log** or at **"upgrade " /var/log/dpkg.log**?  

Does this mean that updates are being zipped and stored but are not properly installed?

If so, can this be corrected?

---

### Post by sunrise718 on 2019-05-11
Help? (See above.)

---

### Post by deadflowr on 2019-05-11
No logging output in history or dpkg means nothing new has been written.
What does the output for
both of these command show.
```
sudo apt update
sudo apt full-upgrade 
```
Please post back results.

---

### Post by sunrise718 on 2019-05-11
Thanks for your response.  

At both:

```
 sudo apt update 
```

and:

```
 sudo apt full-upgrade 
```

I get get:

[sudo] password for (my-non-sudo-account-name):
Sorry, try again.  (At sudo password.)

And when I enter my regular password:

(My-non-sudo-account-name) is not in the sudoers file.  This incident will be reported.

That is messed up!  

I just manually updated the Firefox browser and deleted the older version.  That should be automated with everything else, shouldn't it?  Ugh.

---

### Post by deadflowr on 2019-05-11
Well yeah, a non-sudo user won't be in sudoers.

Did you create a new user as a new user does not get administrator access by default?
If so then just logout and switch to the admin account and login.

If not and somehow along the way you change your user from the administrator to a standard non-administrator account 
then you might need to reboot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode") and reset it.
In recovery mode after you reset the file system read/write (recovery mode opens as read-only and you would need to change it in order to make any changes stick)
Run
```
adduser username-here sudo
```
change username-here with your user's name.
Then reboot. Just type reboot to reboot, that should still work.

---

### Post by sunrise718 on 2019-05-11
I used the GUI method of creating new accounts and do not recall denying a new user admin access by default.  This seems tricky.

---

### Post by deadflowr on 2019-05-11
> **sunrise718 said:**
> I used the GUI method of creating new accounts and do not recall denying a new user admin access by default.  This seems tricky.

Not a trick.
That's the way it works.
First user you created during the installation is made an admin.
Any user created after defaults to a non-admin.
Even in the User Accounts system setting gui.

To change a non-admin user to a admin user (either when you create the user or after) you simply toggle the account setting to administrator.
(This requires you have an admin account that can make the changes, though. You cannot make that change as a non-admin user)
Probably explained better here:
[https://help.ubuntu.com/lts/ubuntu-help/user-admin-change.html.en]("https://help.ubuntu.com/lts/ubuntu-help/user-admin-change.html.en")

---

### Post by sunrise718 on 2019-05-11
I have two accounts.  One is a standard account and the other is an administrator account with special privileges.  I never log in with the administrator account, only the standard account.

When I want to do something that requires administrator rights, I should just type the administrator password at the prompt and let it temporarily access that administrative privilege.  

I should never have to log in as an administrator, especially if I'm online.  That would make my system too vulnerable. Right?

I guess I could log on as the administrator while offline and check the settings for the regular user ...

---

### Post by uRock on 2019-06-28
You can be on the internet while using the admin account in Linux.  At least long enough to get this troubleshooting completed. I've always used just an admin account. Linux doesn't act the same as Windows.

---

