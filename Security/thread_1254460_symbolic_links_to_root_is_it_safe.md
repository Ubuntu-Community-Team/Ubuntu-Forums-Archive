---
title: "symbolic links to root is it safe?"
date: 2009-08-31
forum: Security
---

### Post by r5r4y on 2009-08-31
Hello,
i've a question about the command ln which create symbolic links to, if i use this command for example:

```
sudo ln -s ~/.themes /root/.themes
```

if i put new files in the orginal target the root folder keep updating with the orginal target 
then dosen't this command make an easy access to root somehow? 

i not only speaking about the /root folder, also other folders, this make kinda easy access for viruses no?

---

### Post by bodhi.zazen on 2009-08-31
It is sub optimal yes.

root should not need a /root/.themes you should not be logging in as root.

If you need something in /root, such as a custom .bashrc, put it in /root and keep it owned by root.

---

### Post by r5r4y on 2009-08-31
i'm talking just on the /root folder, is it safe to create symbolic links to / folders anyway? cause the symbolic links keep updating with the orginal target...

if a virus appears in one of the folders? isn't that a risk? cause as i say the symbolic links keep up to date with the orginal target.

---

### Post by bodhi.zazen on 2009-08-31
> **r5r4y said:**
> i'm talking just on the /root folder, is it safe to create symbolic links to / folders anyway? cause the symbolic links keep updating with the orginal target...

if a virus appears in one of the folders? isn't that a risk? cause as i say the symbolic links keep up to date with the orginal target.

I am not sure what you are asking.

1. There are known active viruses in Linux. If you are asking about security please see the sticky.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

2. If you are asking about privilege escalation or limiting damage on a compromised system, you are way beyond symbolic links. You need to look at SELinux or Apparmor.

3. If you are asking about separation of user and system files, yes there is a reason your user files are separate from system files and replacing that system with a bunch of symbolic links to files owned by a user in his or her home is a sloppy practice, regardless of if you are asking about / , /root , /usr/local, etc.

In general system files and things in /root should be owned by either root or the appropriate user (www-data for apache for example). There are exceptions to this rule (~/www for example) but you need to be careful and poor configuration of ~/www can certainly compromise Apache security.

If you have a file or executable for a single user, put it in ~/bin or ~/.themes

If it is for multiple users put it /usr/local/bin or /usr/share and keep it owned by root with ro or rx access by users.

---

### Post by koenn on 2009-08-31
> **r5r4y said:**
> i'm talking just on the /root folder, is it safe to create symbolic links to / folders anyway? cause the symbolic links keep updating with the orginal target...

if a virus appears in one of the folders? isn't that a risk? cause as i say the symbolic links keep up to date with the orginal target.

well, isn't that how you'd *expect* a link to work ?

Besides that, if *you create* a link from /root or any other folder where only root can create files (or links), it's you who opened the door into /root (or an other system folder) and left it wide open. 
I see no reason why you'd want to do that.

---

