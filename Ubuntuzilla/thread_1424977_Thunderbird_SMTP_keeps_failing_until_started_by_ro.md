---
title: "Thunderbird SMTP keeps failing until started by root"
date: 2010-03-08
forum: Ubuntuzilla
---

### Post by liancheng on 2010-03-08
Hi, everyone,

I installed thunderbird-mozilla-build tonight, and it excited me until I found I couldn't send out any mail (SMTP error occurred all the time). And it had taken me hours to figure out that I must start Thunderbird 3.0.3 with root privilege.

I tried "[FONT=Courier New]chown -R user:user /opt/thunderbird[/FONT]" where "[FONT=Courier New]user[/FONT]" is my username, but nothing changed. I also [FONT=Courier New]chown[/FONT]-ed my Thunderbird 3 profile directory, and things kept the same. Seems that something odd other than file I/O must be done with root privilege. It's really weird.

I confess that I haven't go through the FAQ and the forum, because it's already 2 a.m. here and I've got no time. Sorry for being annoying if anyone else had posted this problem before :(

---

### Post by nanotube on 2010-03-09
Hi
there should be no need to start thunderbird as root in order for it to work. 

i suggest you fix all the permissions, as follows:
```
sudo chown -R root:root /opt/thunderbird
```
```
sudo chown -R yourusername:yourusername /home/yourusername/.thunderbird
```

then start thunderbird normally, see if it works, and if not, post exact text of any error messages you get. (just "smtp error" is not very useful for diagnostic purposes).

try also starting with a fresh profile, in case your profile is borked (make sure to back up your existing profile - you can then restore your messages back to into a fresh profile).

---

### Post by liancheng on 2010-03-10
Hi, nanotube, thanks a lot for reply :)

As I mentioned in the first post, I've already [FONT=Courier New]chown[/FONT]-ed [FONT=Courier New]/opt/thunderbird[/FONT] and [FONT=Courier New]~/.thunderbird[/FONT], but nothing better.

The exact error message is:
[INDENT]Sending of message failed.
The message could not be sent because connecting to SMTP server email.baidu.com failed. The server may be unavailable or is refusing SMTP connections. Please verify that your SMTP server settings are correct and try again, or contact the server administrator.
[/INDENT]Also, I tried to analyze SMTP packages sent by Thunderbird by Wireshark. But actually no SMTP packages are captured at all. Then I [FONT=Courier New]strace[/FONT]-ed Thunderbird and found out that no socket APIs were called. So it seems that something went wrong before any network interactions.

I attached the [FONT=Courier New]strace[/FONT] output.

---

### Post by liancheng on 2010-03-10
Oh, forgot to mention, fresh new profile doesn't help either... I just cannot figure out what operation must be done with root privilege to sent a mail? I also tried to move the whole /opt/thunderbird folder to ~/local/opt, nothing changed. Weird :(

---

### Post by liancheng on 2010-03-10
I also tried start Thunderbird with -safe-mode argument, no effect. I removed the thunderbird-mozilla-build package and replaced it with the tar.bz2 package downloaded from Mozilla site, no effect either.

---

### Post by nanotube on 2010-03-13
did you notice that /opt/thunderbird has to be owned by root, but your profile has to be owned by your user, not by root? 

and then run thunderbird as regular user, not root?

also, are you sure it's not just the email server being down? can you connect to it with any other email client?

---

