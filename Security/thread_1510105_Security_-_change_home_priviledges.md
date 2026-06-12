---
title: "Security - change home priviledges"
date: 2010-06-15
forum: Security
---

### Post by Peter09 on 2010-06-15
I have read that to improve security in Ubuntu a good fix is to make the /home folder tree non-executable by default. This would mean that malware could not run in the /home tree without changing the setup.
 
Is this a viable change, or is it just icing on the cake, any one any thoughts on this.

---

### Post by Bachstelze on 2010-06-15
What do you mean, "non-executable by default"? A directory *must* have the executable bit set. Otherwise, you cannot access its contents.

---

### Post by FuturePilot on 2010-06-15
I think the OP is referring to making /home/$USER 700. This will only prevent other users from accessing your home directory. It has nothing to do with malware.

---

### Post by rookcifer on 2010-06-15
I think OP is talking about mounting /home noexec.  Yes, it can be done, but you would have a non-functioning system since there are scripts that must execute from /home.

---

### Post by bodhi.zazen on 2010-06-15
I think the OP is asking about mount options.

Yes, if you use a separate /home partition it can help to mount it with the noexec and nosuid and nodev options. You can mount /tmp with these options as well.

See

[http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents)

[http://www.debianhelp.co.uk/security.htm](http://www.debianhelp.co.uk/security.htm)

---

### Post by bodhi.zazen on 2010-06-15
> **rookcifer said:**
> I think OP is talking about mounting /home noexec.  Yes, it can be done, but you would have a non-functioning system since there are scripts that must execute from /home.

What scripts would those be ?

---

### Post by rookcifer on 2010-06-15
> **bodhi.zazen said:**
> What scripts would those be ?

Any scripts in autostart directories, as well as any miscellaneous scripts one might have written or downloaded elsewhere.  I have several scripts I use (as well as a directory  I use for development) and mounting /home noexec would be impossible.  Moreover, if the user decides to download a package from outside the repos and run it in userland, it obviously wont work.  

If I had a noexec /home, my system would be useless.  But that's just my experience.  Perhaps others can successfully run a /home with nothing whatsoever ever being able to execute from it.

---

### Post by bodhi.zazen on 2010-06-15
> **rookcifer said:**
> Any scripts in autostart directories, as well as any miscellaneous scripts one might have written or downloaded elsewhere.  I have several scripts I use (as well as a directory  I use for development) and mounting /home noexec would be impossible.  Moreover, if the user decides to download a package from outside the repos and run it in userland, it obviously wont work.  

If I had a noexec /home, my system would be useless.  But that's just my experience.  Perhaps others can successfully run a /home with nothing whatsoever ever being able to execute from it.

Well, you answered your own question.

If you have user scripts you can not mount /home noexec

My guess is that there are probably 30-40 % of users here who run scripts from /home, but that is just a guess.

Most of the "auto start" stuff is going to be system scripts/bin files, so they will mostly work.

---

### Post by linux-hack on 2010-06-15
If you rely want to secure your /home directory why not juste encrypt 'it ??

And what about .profile and so on scripts on the /home folder ? they need to be executed so I think it's not a good idea the noexec

---

### Post by bodhi.zazen on 2010-06-15
> **boogy9 said:**
> If you rely want to secure your /home directory why not juste encrypt 'it ??

And what about .profile and so on scripts on the /home folder ? they need to be executed so I think it's not a good idea the noexec

That helps protect your data from physical access, but it would not help in the OP user case.

The OP is specifically wanting to increase security by preventing users from executing scripts from /home.

In that user case , mounting /home noexec is very reasonable.

It may not work for you, but the OP is not asking what works for you.

---

### Post by Peter09 on 2010-06-15
Hi,
thanks for all the input, I suppose I was interested in the potential increase in security that mounting noexec gives. 

Does it actually help prevent malicious software or is it the case that once something is able to set up an executable script then it potentially can do that from anywhere.

---

### Post by bodhi.zazen on 2010-06-15
> **Peter09 said:**
> Hi,
thanks for all the input, I suppose I was interested in the potential increase in security that mounting noexec gives. 

Does it actually help prevent malicious software or is it the case that once something is able to set up an executable script then it potentially can do that from anywhere.

It may help security in that users can not download and run malignant scripts. As this is a rare problem in Linux it probably does not help you much.

There are a number of variables here, it kind of depends on what exactly we are talking about here. Some crackers, once they have shell access, will download things to various locations where they have write access, for example /home or /tmp . In that event having /home and /tmp mounted noexec helps.

In environments where you need to lock down your users you may want to prevent them from running applications from /home, so again noexec helps.

As a general rule, in terms of security, you may increase security by limiting what is executable by users. If a user can write or download a script they can cause mischief ranging from minor irritants to rootkits.

This must be weighed against usability. As has been mentioned, if your users are programing they would expect to be able to run executable code.

---

