---
title: "Changing the &quot;Live session user&quot; password"
date: 2012-04-24
forum: Security
---

### Post by dareys on 2012-04-24
Greetings,

I am new to Ubuntu security and am trying to change the "Live session user" password. I believe it is the same as the Ubuntu user. At least that is what it looks like in the password file.

However, in order to change the password, you have to provide the old password, and I have been unable to find it in the book I bought. 

Can anyone tell me what the original Maverick Ubuntu 10.10 password is for "Live session user"?

Thank you.

Jean-Pierre

---

### Post by wojox on 2012-04-24
Live session has no password. Just hit Enter. Unless you have a persistent file to write to, there is no point in changing the username or password. ;)

---

### Post by dareys on 2012-04-24
> **dareys said:**
> 

Greetings,

I am new to Ubuntu security and am trying to change the "Live session user" password. I believe it is the same as the Ubuntu user. At least that is what it looks like in the password file.

However, in order to change the password, you have to provide the old password, and I have been unable to find it in the book I bought. 

Can anyone tell me what the original Maverick Ubuntu 10.10 password is for "Live session user"?

Thank you.

Jean-Pierre

Greetings,

Thank you for the response. In my limited experience as a UNIX Admin, the root account never had a password initially. However, sometimes, it is root. I tried typing in root, Ubuntu, UBUNTU, and just hitting return, to no avail. I tried modifying the password file with VI, to no avail. I could not even do chmod.

This has been going on for a few weeks, and I have been reading to no avail. I had not written before, because in almost thirty years of working with Unix Systems, Solaris, AIX, HP-UX, Linux, the topic is pretty consistent, so I figured it was doing something wrong or need to lean a new feature.

And, I see, nothing has changed. I will try again. Thank you. 

Jean-Pierre

---

### Post by dareys on 2012-04-25
> **dareys said:**
> Greetings,

Thank you for the response. In my limited experience as a UNIX Admin, the root account never had a password initially. However, sometimes, it is root. I tried typing in root, Ubuntu, UBUNTU, and just hitting return, to no avail. I tried modifying the password file with VI, to no avail. I could not even do chmod.

This has been going on for a few weeks, and I have been reading to no avail. I had not written before, because in almost thirty years of working with Unix Systems, Solaris, AIX, HP-UX, Linux, the topic is pretty consistent, so I figured it was doing something wrong or need to lean a new feature.

And, I see, nothing has changed. I will try again. Thank you. 

Jean-Pierre

Greetings,

I tried again after rebooting the machiine, and I was able to change the password from the command line as you indicated. The GUI doesn't let you get away with hitting return.

I am going to apply the same method for the root account. Too many hacking issues.

Regards,

Jean-Pierre

---

