---
title: "Virtual Mail to RT (via shell pipe)"
date: 2010-12-14
forum: Server Platforms
---

### Post by STOIE on 2010-12-14
Hi all,

I have a bit of an issue here.
Request Tracker is up and running, but, I need to pipe my email aliases through to the rt-mailgate.
Problem is, like most I would imagine, I have my mail server running postfix with virtual aliases (in a mysql DB).
Putting [email]rt@mydomain.com[/email], |/bin/rt-mailgate doesn't work which I can understand, however, I have fiddled with other ways of getting around it and nothing I have read I understand (or they explain) enough to let me fix it. (it's always that missing step that is "assumed" knowledge).

Problem is I am a noob at postfix so I am sure there are thing's I am missing.

Anyway, if someone could explain (in detail) a way around the issue I have would be most most appreciated.

Thanks,
Aaron.

---

### Post by cipherboy_loc on 2010-12-14
> **STOIE said:**
> 
Putting [EMAIL="rt@mydomain.com"]rt@mydomain.com[/EMAIL], |/bin/rt-mailgate doesn't work

I think you need to do this:

```
echo 'rt@mydomain.com | /bin/rt-mailgate
```



Cipherboy

---

### Post by STOIE on 2010-12-14
Sorry cipher,

What do you mean, and you appear to be missing a "'".

On the shell why would I want to echo an address to the mailgate???

---

### Post by cipherboy_loc on 2010-12-14
Sorry about that, yes I was missing a '. 

Echo is, from the man page:

> 
       echo - display a line of text


It allows you to print a line of text, in this case the "rt@yourdomain.com".

The correct command should be as follows:

>  echo 'rt@mydomain.com' | /bin/rt-mailgate

More or less, echo is a utility to print a line of text to the console. But instead of printing it to the console, we print it to /bin/rt-mailgate with the | symbol (called a pipe by some).


Why we use single quotes is to make sure it prints EXACTLY [email]rt@mydomain.com[/email], and not rt mydomain.com or something else.



Cipherboy

---

### Post by STOIE on 2010-12-14
I know what echo and pipe are.

I am asking why would I want to echo an email address to the rt-mailgate...?

The rt-mailgate takes messages and enters them into the rtdb.

The pipe to mailgate needs to be for a message hitting the alias to be redirected to the rtdb through initiation of the perl script (mailgate).

echoing an email address to it seems like echo "blah" >| /dev/null???!?!?

An I missing something here, how does this help me with my question to route virtual aliases to a shell pipe (ie. rt-mailgate).

I believe I need something more like a local transport entry that then routes the message back through with a local entry of /etc/aliases. However, I am not quite sure on the exact way this should be configured.

---

### Post by STOIE on 2010-12-14
Okay now I see how you have become confused... with your first response.

When I wrote I have the database entries (for aliases to postfix) of [email]email@domain.com[/email], |/bin/rt-mailgate

I mean this:

I am speaking about the table data in the database table aliases.
maildb.aliases

name | destination
[email]email@domain.com[/email] | |/bin/rt-mailgate

So it is a bit more complex then me just wanting to pipe something to a script. I should mention I am a unix administrator so I am fine with unix cli just never done much postfix specific things (more than 5 or 10 hours worth anyway).

But, I believe there is a solution where I can use alias in the db to point to a local entry in the /etc/postfix/aliases file which then contains the pipe to rt-mailgate.

Sorry, hope this better explains my situation.

---

### Post by STOIE on 2010-12-14
Fixed!

In /etc/postfix/main.cf
mydestination = localdomain.com

In the mail.aliases table.
[email]rt@domain.com[/email], [email]rt@localdomain.com[/email]

In /etc/postfix/aliases
rt: |/bin/rt-mailgate ... etc.

And it works!

---

