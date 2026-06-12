---
title: "Postfix"
date: 2007-01-20
forum: Server Platforms
---

### Post by lugos on 2007-01-20
Hello,

I am not too familiar with postfix or mailutils, but after doing some research, I figured I would need the two to send e-mails from my web server.

I have installed and set up postfix on my web server, and I have also installed mailutils.  I am trying to send e-mails using PHP through a contact form on my website.  If the mail() function returns a true, I display a success message, otherwise I display a failed message.  Ever since I installed postfix and mailutils, I have been getting the success message.  Before that I was always getting the failed message.  However, I do not see the e-mail in my hotmail account inbox.  I also tried sending an e-mail using the command line.  I didn't see any errors, and I didn't receive a mail delivery error from the system; whereas before, with only mailutils installed, I was receiving the mail delivery error emails.  I don't know if mailutils is needed for postfix to run or vice versa.  I don't know where else to go from here; I'm really at a loss.  I followed the guide here [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5) to set up postfix.

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by MJN on 2007-01-20
What does your /var/log/mail.log say?

Mathew

---

### Post by lugos on 2007-01-20
Hello,

I just ran it again from my contact form and here is what I got in the mail.log file:

Jan 20 13:11:07 localhost postfix/postdrop[8094]: warning: unable to look up public/pickup: No such file or directory

---

### Post by MJN on 2007-01-20
It sounds like all the components of Postfix aren't running. Try **sudo /etc/init.d/postfix restart **and see if the logs say anything. Also try **sudo postfix check** for any obvious errors.

Mathew

---

### Post by lugos on 2007-01-20
Hello,

I did a restart and then saw this in the log file:

Jan 20 13:53:12 localhost postfix/master[8232]: fatal: bind 0.0.0.0 port 25: Address already in use

---

### Post by MJN on 2007-01-20
That's it then - Postfix can't start because something else is already listening on port 25 (SMTP).

Have you installed Sendmail by any chance? (and see if it's running with **ps aux |grep -i sendmail**)

If not, try installing **lsof** and running **sudo lsof -i :25** - this will tell us who/what is listening on 25.

Mathew

---

### Post by lugos on 2007-01-20
Hello,

I ran sudo lsof -i :25 and got this:

COMMAND  PID        USER   FD   TYPE DEVICE SIZE NODE NAME
exim4   4594 Debian-exim    3u  IPv4  11311       TCP localhost:smtp (LISTEN)

---

### Post by MJN on 2007-01-20
That means you've got Exim installed (and running) which, as you've probably guessed by now, is an MTA just like Postfix. Hence running both of them (at least on the same standard SMTP port of 25) is a no-go.

Remove one of them (Exim, Exim, although I'm sure some others might say otherwise! Friendly rivalry between those two...) then restart Postfix and you should be up-and-running!

Mathew

---

### Post by chrisfay on 2007-01-20
As a side note, mailutils installs exim (or a lightweight version of it) as part of its package. So installing both Postfix and Exim, as you've found, will not work.

---

### Post by MJN on 2007-01-20
You sure? It looks like it depends on exim4 **or** mail-transport-agent (of which Postfix obviously is).

Of course, if the OP had installed mailutils prior to Postfix then it would've installed Exim by default, but that doesn't it can't be removed now that Postfix is installed.

Mathew

---

### Post by chrisfay on 2007-01-20
> Of course, if the OP had installed mailutils prior to Postfix then it would've installed Exim by default, but that doesn't it can't be removed now that Postfix is installed.

Correct.... Removing the Exim package would obviously solve the problem. I hadn't realized that the mailutils dependency was satisfied by 'any' mta, so had Postfix been installed originally it wouldn't have caused any issues to install mailutils as well.

Suppose I coulda checked....:biggrin:

---

### Post by lugos on 2007-01-22
Hello,

Problem resolved.  It looks like it was a conflict between postfix and exim.

Thanks again!  You guys are awesome!

---

