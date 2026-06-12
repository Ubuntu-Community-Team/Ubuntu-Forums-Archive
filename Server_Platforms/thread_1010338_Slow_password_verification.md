---
title: "Slow password verification"
date: 2008-12-13
forum: Server Platforms
---

### Post by hardysummer on 2008-12-13
After booting, I sign in, slow verification.  I run a sudo command, slow verification.  I shutdown computer, slow verification.

I noticed a significant delay in the password verification.  It takes like 3 seconds for it to verify the password.

It gets annoying since I type the password and hit Enter and start typing in stuff only to see that the prompt is waiting for the password to be verified.

What is causing this significant delay in Intrepid?  Could it be the Private folder thing I created?  Because this is the first time I created it to see how it worked.  I doubt it is.

---

### Post by skunkbad on 2008-12-13
Was verification ever fast for any action?

---

### Post by hardysummer on 2008-12-13
Hello, did you read the post?

If you do not have an answer, do not reply.

---

### Post by Joeb454 on 2008-12-13
I actually think skunkbad was asking a genuine question...

---

### Post by hardysummer on 2008-12-13
Okay, then, here my answer: Yes.

It takes less than 1 second.  I can type in the password, hit Enter, type in the next command, and before I can hit Enter again, the password is already verified.

Not in Intrepid.  What is causing this?

My current set up is no different from the previous.  Only difference is the Private folder thing that is offered in Intrepid that I wanted to see how well it worked.  Is there a way I can get rid of the Private folder thing for good to see if it is the cause of it?

---

### Post by MJN on 2008-12-14
Could it be a DNS-related issue? Specifically, I'm wondering if the 3-second delay might be a timeout resulting from a failed reverse-lookup - perhaps done to populate a logfile entry and/or security check. That said, I would expect this delay to occur immediately after the initial login (and before the password) as there's little point in delaying such an event (and indeed some reasons why it wouldn't want to).

You could check this by running a packet sniffer (e.g. Wireshark) and seeing if there's any network traffic (DNS queries specifically) at the point of submitting your password.

It's a long shot, but in the absence of any other ideas...

Mathew

---

### Post by cariboo on 2008-12-14
Have you tried putting the server name and ip address in /etc/hosts on the computer you are connecting from eg:

```
127.0.0.1         locahost
127.0.1.1         computername
192.168.1.100     servername
```

Jim

---

### Post by hardysummer on 2008-12-14
It was nothing network related since I just finished installing a clean server when I noticed the delay in password checks.

It was very obvious since I tried to sudo a command and started typing and tab-completion only to find out that part of the command was typed and tab-completion can not be used yet until the password check is finished.

I decided to do another clean server install, but without the Private folder thing.  And yes, it was the cause of it.

---

### Post by skunkbad on 2008-12-15
> **Joeb454 said:**
> I actually think skunkbad was asking a genuine question...

Like many, I am here to help when I can.

---

