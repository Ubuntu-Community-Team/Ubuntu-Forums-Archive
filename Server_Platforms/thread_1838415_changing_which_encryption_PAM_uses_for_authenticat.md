---
title: "changing which encryption PAM uses for authentication"
date: 2011-09-03
forum: Server Platforms
---

### Post by BrandonSk on 2011-09-03
Hello all,

hopefully someone can help me with this one, as my posts usually end up unanswered.

I managed to get a mail server working. It's a postfix + courier-imap setup. Working means that mail can be sent, received whether it is with webmail (squirrelmail) or other mail clients (e.g. evolution mail).

So far I was adding users via SQL statements:
INSERT INTO mailbox(username, password, *[bunch of other fields]*) VALUES ('userXY@domainA.com',** encrypt('abcd1234'),** *[bunch of other values]*);

Then I started looking at web interface management tools. My winner came to be the [ViMbAdmin]("https://github.com/opensolutions/ViMbAdmin/wiki") which exactly fits my needs. But this is where the problems started.

ViMbAdmin encrypts passwords differently then SQLs encrypt function. Therefore for any user(or mailbox as a matter of fact) which I create in ViMbAdmin I cannot log in as the authentication fails.

For illustration, here is what the two different methods produce:
[B]SQL command:
[/B]```
username           password
test2@domainA.com    grG9NjaqmAayM
```[B]ViMbAdmin:
[/B]```
username           password
test3@domainA.com   e19d5cd5af0378da05f63f891c7467af
```After few days of searching and experimenting I have learned that these different hashes depend on the encryption(or hash) that is applied to the same password.
2 solutions came to my mind:
1) Convince ViMbAdmin to use the same hash mechanism as the SQL encrypt function;
2) Change the authentication when user tries to log in.

[1] was the preferred method, but yielded no result as I could not find any option to force ViMbAdmin to produce the shorter hash.

[2] was more difficult but I found it has to do something with PAM and the files in /etc/pam.d directory.
From different post I understand that the "crypt=x" parameter in these files defines the algorithm used. I further found that what I want is either to have "crypt=3" or "crypt=1 md5".
I tried changing these in files imap and smtp (and all possible cominations) but none of it really worked. I wasn't sure which service I needed to restart after making changes to these files, so I kept restarting postfix and courier-authdaemon. But without any luck.

Now my question is:
1) How can I achieve my goal of using ViMbAdmin which uses the long hash result with the working setup of my postfix and courier-imap?

I you need content of my /etc/pam.d files, or content of my postfix master.cf or main.cf or any other file, please let me know.
Thank you very much!
B.

PS: The error I get in log files while authenticating is that the password provided does not match the encrypted password ...(hash)...

---

### Post by BrandonSk on 2011-09-07
BUMP?

I do not know if I write the posts wrong, in a wrong place or my questions are simply hard? :)
But writing directly to developers has proved to me more efficient so far than posting here :(

Anyway, in case someone runs across this, I received a reply from the developer and ViMbAdmin as of version 0.3.4 (released Sep 6th) supports many different encryption methods.

For my problem that means that solution #1 is now available.

However, if there is someone who knows (solution #2) how to configure postfix to use a stronger encryption (e.g. SHA1 etc.) I would love to know and perhaps a simple guide for what needs to be changed in configuration and how.

Cheers,
B.

---

