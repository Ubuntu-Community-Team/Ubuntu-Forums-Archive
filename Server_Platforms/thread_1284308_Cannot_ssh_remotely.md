---
title: "Cannot ssh remotely"
date: 2009-10-06
forum: Server Platforms
---

### Post by tjhart85 on 2009-10-06
Hi,

I have just created a new user on my server, bserocki

This account can ssh locally (on same network), but cannot from an external location.  This same external location allows me to log in using my account though.

The user that can log in, was created at installation by the system.

From the default installation of SSH, does the user need to be a member of a specific group or anything?  I can't find anything online that says it does.

I created the user using the command 'adduser bserocki'

Any thoughts?

Ubuntu Server 9.04

---

### Post by BQAggie2006 on 2009-10-06
> but cannot from an external location. This same external location allows me to log in using my account though.
Can you please clarify this statement? It seems to contradict itself.

---

### Post by tjhart85 on 2009-10-06
> **BQAggie2006 said:**
> Can you please clarify this statement? It seems to contradict itself.

The new account cannot ssh from an external location, but MY account that was created at installation can.

---

### Post by BQAggie2006 on 2009-10-06
Thank you for the clarification, and my apologies for not reading the original post completely. You shouldn't have to add the new user to any additional groups, it should be able to SSH into the system once created. Did you set the password for the new user?

---

### Post by tjhart85 on 2009-10-06
> **BQAggie2006 said:**
> Thank you for the clarification, and my apologies for not reading the original post completely. You shouldn't have to add the new user to any additional groups, it should be able to SSH into the system once created. Did you set the password for the new user?

No problem (you're trying to help me afterall :-])

Yes, there is a password set on the user, using the command 'sudo passwd bserocki'

The main thing I'm confused about is that I can access it on the local network, but cannot from somewhere else, while I CAN access it with my account.  This means the ports are forwarded correctly & everything should be working properly, but for any new users I create, they cannot SSH into it from another location.

I've tried it from my G1 (also works for my user account) and from a friends house.  My user always works, but the new bserocki one does not.

Do new users need to be added anywhere to be authorized to access via SSH?  But that doesn't seem correct, since the user can SSH in on the local network.  As I understand it, when you forward ports, the system really shouldn't care if you are accessing it locally or remotely, but it sure seems to!

---

### Post by BQAggie2006 on 2009-10-06
Users don't have to be added anywhere to be authorized to use SSH. And since it's working locally and one of your accounts is working remotely, it seems that everything is configured properly and in working order. I guess the only suggestion I can offer would be to mimic the groups that your working user account is in to the new user account.

---

### Post by kanikilu on 2009-10-06
Can you clarify what you mean by "can't login"? A more specific error message may help track down the problem. BTW, are you using SSH key authentication?

---

### Post by tjhart85 on 2009-10-06
I get ACCESS DENIED

---

### Post by tjhart85 on 2009-10-07
Well, I copied all of the groups from my user to the bserocki user & it works now.

Thanks for the help everyone

---

