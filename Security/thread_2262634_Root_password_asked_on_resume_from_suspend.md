---
title: "Root password asked on resume from suspend"
date: 2015-01-26
forum: Security
---

### Post by Andrew_Lucas on 2015-01-26
Hi all,

I use the suspend feature quite a bit. Lately, I've noticed that after I've logged in again (LightDM is the login manager in Xubuntu, I believe), something asks for my root password (with a message about accessing user data).

I've consistently clicked cancel, with seemingly no ill effects - but I'd welcome some help in trying to track down which program is asking for root access and, more importantly, why.

Initially, I wondered if it was some malware (the vestiges of a Window mindset!). I've come away from that idea, but I'd still like to know what's doing what on my system.

Cheers!

EDIT: Screenshot of dialogue box attached.

---

### Post by TheFu on 2015-01-26
When that window is up, look at the process table. What is running?
I'd use something like **xwininfo -root -tree** to find it.

Considering that Ubuntu systems don't have a root password, it is likely whatever program is asking - the exact, exact, exact message would be helpful - is not a primary Ubuntu program.  Did you google that exact message already?

BTW, it would be fairly easy to convince someone new to Linux to install and run a tool that required escalated privileges ... from that point on, they'd own the box. I've thought about how to do it. Just a few lines of scripts and a generated .desktop file would be all it needed.  People who only point-n-click could get into trouble that way.  I don't know of any attacks that happen in this manner, but that's just because they'd be trivial to trace, once the damage were done.

---

### Post by Andrew_Lucas on 2015-01-26
> **TheFu said:**
> When that window is up, look at the process table. What is running?
I'd use something like **xwininfo -root -tree** to find it.

Considering that Ubuntu systems don't have a root password, it is likely whatever program is asking - the exact, exact, exact message would be helpful - is not a primary Ubuntu program.  Did you google that exact message already?

BTW, it would be fairly easy to convince someone knew to Linux to install and run a tool that required escalated privileges ... from that point on, they'd own the box. I've thought about how to do it. Just a few lines of scripts and a generated .desktop file would be all it needed.  People who only point-n-click could get into trouble that way.  I don't know of any attacks that happen in this manner, but that's just because they'd be trivial to trace, once the damage were done.

Thanks for replying. I've uploaded a screenshot.

Googling the (as you suggested) exact message reveals various postings, it seems to be a known issue, but none of them seem to explain it. I've confirmed it's something affecting at least one other user ([http://askubuntu.com/questions/562355/seemingly-random-authentication-is-required-to-change-your-own-user-data](http://askubuntu.com/questions/562355/seemingly-random-authentication-is-required-to-change-your-own-user-data)) on Utopic.

Yes, I realise and considered that, but considering (1) I know no one with, let alone have given them access to, my laptop (2) The install is only a few weeks old (3) Relative rarity of Linux malware (4) I've enabled UFW (I know there's a debate about the point of it if you're not operating a server, but I feel it certainly won't do any harm and doesn't affect the PC negatively AFAIK). I've also not changed my browsing habits much - so I think if there *was *a malware issue, I'd have picked it up before now.

I'm wondering if it's something to do with the fact that I've a separate /home partition, or a separate home partition that's encrypted? Maybe a problem with (re)mounting/accessing the data at login?

---

### Post by TheFu on 2015-01-26
a) I can't read the small words on the image.
b) Don't think it is asking for the root password - looks like it is asking for a sudo password.
c) I think the warning may have happened due to a setting file being owned by root, not your normal userid.  That probably happened by using sudo to run a GUI application and it created, them saved some settings.

**sudo chown -R userid.userid $HOME/** should fix it.  Just change the "userid" to match yours.  Oh - and don't get the directory wrong - trashing permissions across the entire partition would be bad - like reload the OS bad.  This command won't be bad and might fix the issue.

If it isn't clear - don't run GUI programs with sudo.

---

### Post by Andrew_Lucas on 2015-01-26
> **TheFu said:**
> a) I can't read the small words on the image.
b) Don't think it is asking for the root password - looks like it is asking for a sudo password.
c) I think the warning may have happened due to a setting file being owned by root, not your normal userid.  That probably happened by using sudo to run a GUI application and it created, them saved some settings.

**sudo chown -R userid.userid $HOME/** should fix it.  Just change the "userid" to match yours.  Oh - and don't get the directory wrong - trashing permissions across the entire partition would be bad - like reload the OS bad.  This command won't be bad and might fix the issue.

If it isn't clear - don't run GUI programs with sudo.

a) It reads: "An application isattempting to perform an action that requires privileges.Authentication is required to perform this action." Then a password field. Then Cancel/Authenticate.

b) Yeah, sorry. Lazy language. I don't bother to distinguish (because sudo provides root access). The root account hasn't been enabled.

c) I install all applications etc by the command line :S. How could that have happened?

Is there a command to print the permissions of a directory before setting the permissions?

The thing about control of sudo goes without saying. ;)

---

### Post by bapoumba on 2015-01-26
Any message listed if you click on "details" (bottom left) ?

---

### Post by TheFu on 2015-01-26
> **Andrew_Lucas said:**
> a) It reads: "An application isattempting to perform an action that requires privileges.Authentication is required to perform this action." Then a password field. Then Cancel/Authenticate.

b) Yeah, sorry. Lazy language. I don't bother to distinguish (because sudo provides root access). The root account hasn't been enabled.

c) I install all applications etc by the command line :S. How could that have happened?

Is there a command to print the permissions of a directory before setting the permissions?

The thing about control of sudo goes without saying. ;)

Being exact with error messages is very important.  sudo isn't just used to gain root. There are many, many other uses.

c) Ever run **any** GUI program with sudo?  gedit, nautilus, pcmanfm, Thunar?  Perhaps a GUI backup program?

**ls -l **- time for this? [http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything) 

You'd be surprised.  Lots of folks who don't understand file/directory permissions decide it is just easier to always use sudo for everything and get into all sorts of issues. Only you know the level of understand of this stuff. It is a basic part of UNIX/Linux system security, definitely worth knowing, as I'm sure you already know.

---

### Post by mc4man on 2015-01-26
As mentioned expanding "Details" may prove informative
(the auth. box appears to be a pkexec auth

Does anything open if you actually provide auth?

---

### Post by Elfy on 2015-01-29
Funnily enough I've seen this off and on recently when coming back from a lock screen. Running dev version.

I'll try  xwininfo -root -tree next time it happens.

>  If it isn't clear - don't run GUI programs with sudo. Certainly not the root cause of this here.

---

### Post by TheFu on 2015-01-29
> **Elfy said:**
> Certainly not the root cause of this here.

My though is that some GUI program settings were created by root and are still owned by root inside the user's HOME.

Under a HOME, I can't think of many files that should be owned by root.root.
I have only things in ~/.aptitude/ with that on 1 system, not all of them.

---

