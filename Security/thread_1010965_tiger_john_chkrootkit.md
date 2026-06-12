---
title: "tiger john chkrootkit"
date: 2008-12-14
forum: Security
---

### Post by ferd on 2008-12-14
These are my results from a recent tiger john chkrootkit scan. This looks disturbing but I am not knowledgeable enough to know.

<clip>

How bad is it and can I correct it with help?:confused:

Edit bodhi.zazen: Please do not post such large blocks of text to the forums, use attachments.

Second, not to be rude, but you can not seriously expect others to go through hundreds of lines or output and explain it to you line by line ???

---

### Post by albinootje on 2008-12-14
In my opinion you should look at results from tiger with a grain of salt in general.

> # Checking OS release...
> Unreleased Debian GNU/Linux version `lenny/sid' <PRE>

It doesn't know about this Ubuntu or Debian release.

A better application than chrootkit is rkhunter imho.
(sudo apt-get install rkhunter)

But what is strange that you have a /home/dev directory.
Did you create that ?

---

### Post by ferd on 2008-12-14
> **albinootje said:**
> In my opinion you should look at results from tiger with a grain of salt in general.

> # Checking OS release...
> Unreleased Debian GNU/Linux version `lenny/sid' <PRE>

It doesn't know about this Ubuntu or Debian release.

A better application than chrootkit is rkhunter imho.
(sudo apt-get install rkhunter)

But what is strange that you have a /home/dev directory.
Did you create that ?

If so, I don't remember doing it. I expect false positives from security scans, but this seems like a lot. I also do rkhunter and chkrootkit without the tiger john and find less problems.

---

### Post by albinootje on 2008-12-14
Which Ubuntu or Debian release is this ?
And is it plain Ubuntu or Wubi ?

Do you have a separate /home partition perhaps ?
If you do then it's easy to add the nodev and nosuid and noexec mount options.

By the way, the author of rkhunter has released some more tools,
see [http://www.rootkit.nl/projects/](http://www.rootkit.nl/projects/)

---

### Post by bodhi.zazen on 2008-12-14
> **ferd said:**
> These are my results from a recent tiger john chkrootkit scan. This looks disturbing but I am not knowledgeable enough to know.

<clip>

How bad is it and can I correct it with help?:confused:

Edit bodhi.zazen: Please do not post such large blocks of text to the forums, use attachments.

Second, not to be rude, but you can not seriously expect others to go through hundreds of lines or output and explain it to you line by line ???

These tools are as much for education as anything else.

I suggest you start with ;

[http://linux.die.net/man/8/tiger](http://linux.die.net/man/8/tiger)

Now you can get an explination from tiger with tigexp

For example :

```
/usr/sbin/tigexp pass014w
```

pass014w is but one of the messages in the output.

You can include explanations in the report with the -E filag

tiger -E

From there, google is your friend.

Now if you have a specific question on a specific warning or report, that is different.

---

### Post by ferd on 2008-12-14
> **albinootje said:**
> Which Ubuntu or Debian release is this ?
And is it plain Ubuntu or Wubi ?

Do you have a separate /home partition perhaps ?
If you do then it's easy to add the nodev and nosuid and noexec mount options.

By the way, the author of rkhunter has released some more tools,
see [http://www.rootkit.nl/projects/](http://www.rootkit.nl/projects/)

I do have a separate home partition. l am using Ubuntu 8.04. Thanks for the 411 on the additional tools.

---

### Post by ferd on 2008-12-14
> **bodhi.zazen said:**
> These tools are as much for education as anything else.

I suggest you start with ;

[http://linux.die.net/man/8/tiger](http://linux.die.net/man/8/tiger)

Now you can get an explination from tiger with tigexp

For example :

```
/usr/sbin/tigexp pass014w
```

pass014w is but one of the messages in the output.

You can include explanations in the report with the -E filag

tiger -E

From there, google is your friend.

Now if you have a specific question on a specific warning or report, that is different.

Thank you. I need to do a follow up on the report and will.

---

