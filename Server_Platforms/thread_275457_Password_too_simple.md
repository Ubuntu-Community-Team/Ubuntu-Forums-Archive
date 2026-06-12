---
title: "Password too simple?"
date: 2006-10-11
forum: Server Platforms
---

### Post by sgtrock on 2006-10-11
Howdy.

Before you ask, I did search the forums using several different phrases and word combinations, trying to find a solution to this problem.  No joy, unfortunately.  :(

I'm not a Linux newbie, but I am new to Ubuntu.  I've run various flavors of RedHat, Debian, Suse, and Gentoo over the years.  This is the first time that I can remember running into this particular problem.

I'm currently running two instances of Kubuntu 6.06 on two different laptops.  One of them is for work, where we have a policy of rotating all passwords every 30 days.  In order to keep from going stark, raving mad, I need to have a password that I can use on several different systems; everything from Windows to Novell to IBM mainframe to Notes to you name it.

Right now, our local Information Security policy requires us to use a 6 to 8  character password.  Because of the various limitations on the wide variety of systems, I have to choose passwords that are limited to just lowercase and/or numbers.  I always choose a password that is a mix, and is not something simple like a word with a couple numbers tacked on the end.  There's generally at least one number in the middle of a word, for example.  Sometimes two.  In the case that's failing, there's a number in the middle and a number on the end of a short name.  It looks nothing like a word.

IOW, I do not choose simple, easy to guess passwords.  A dictionary attack might succeed in finding them, but I honestly don't see how unless that dictionary is really massive.  :)

Anyhow, here's my problem:  During my last password changing evolution, I was unable to get my Kubuntu desktop to accept the password that every other system in the company accepted.  The error that I got was incredibly cryptic; "Password too simple".  I dropped to the command line and tried just using "passwd".  Same error message.

At this point I'm thinking in terms of a PAM problem.  Now, I am anything but conversant with PAM.  I've used it for years on my Gentoo systems, but I've never had to do anything except accept the default settings when I installed or upgraded it on those.  I've read every PAM man page that I can find and dug through every configuration file in /etc/pam.d.  I've even gone so far as to remove every mention of 'cracklib' in every config file for PAM.  No joy.  :(

So, can anyone tell me where to look to change the password validation mechanisms?  Am I even looking in the right places?

TIA

---

### Post by MJN on 2006-10-11
The **passwd** manpage gives an insight about what sort of default checks are made in order to determine the strength of your password.

However, if you're content that your password strength is sufficient and simply want to force the issue then the easiest way of doing this is probably to set your user password as root e.g. **sudo passwd <username>**. This seemingly doesn't enforce any strength checks.

Mathew

---

### Post by foxylad on 2006-10-11
I did a quick search for the rules that PAM uses, and failed - guess the source is the best place to look.

However, there is a work-around - change the password as root. This doesn't complain when you to change the password to something it considers unsafe:
```
sudo passwd gregf
```

---

### Post by devnulljp on 2006-10-11
> **sgtrock said:**
> So, can anyone tell me where to look to change the password validation mechanisms?  Am I even looking in the right places?
TIA

Sounds like you're using pam_cracklib
Have a look in /etc/pam.d/common-password
Look for a line like

password required       pam_cracklib.so retry=3 minlen=8 difok=3 dcredit=-2 ocre dit=-2

That's looking for at a password of 8 or more characters with at least 2 UPPER CASE and at least 2 !"£$%^&*()}{~@:?>< chars
Both can be changed easily
Good explanation here: [http://www.gentoo.org/doc/en/security/security-handbook.xml?part=1&chap=7](http://www.gentoo.org/doc/en/security/security-handbook.xml?part=1&chap=7)

---

### Post by sgtrock on 2006-11-01
Finally figured it out after much wailing and gnashing of teeth.  I removed the 'obscure' option from this line in /etc/pamd.d/common-password:

password required pam_unix.so nullok obscure min=4 max=8 md5

That got the system to accept the password.

---

