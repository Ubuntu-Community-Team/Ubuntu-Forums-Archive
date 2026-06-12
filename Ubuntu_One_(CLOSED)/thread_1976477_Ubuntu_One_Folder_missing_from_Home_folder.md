---
title: "Ubuntu One Folder missing from Home folder"
date: 2012-05-08
forum: Ubuntu One (CLOSED)
---

### Post by Senior_Buckethead on 2012-05-08
Hey I have noticed since I have gone to 12.04 that my Ubuntu One folder from my Home folder is missing? How can I get it back?

Glenn.

---

### Post by PhantomTurtle on 2012-05-08
I think that's because the Ubuntu One client is not installed by default(but that might not be the reason, so I might be wrong).

---

### Post by Senior_Buckethead on 2012-05-08
Yeah, I went to Ubuntu Software Centre and installed Ubuntu one, but I still don't have the folder in /home/glenn directory, nor do I have any system settings for it. 
So  I am wondering what other packages are not installed that might be dependencies or such.

---

### Post by PhantomTurtle on 2012-05-08
> **Senior_Buckethead said:**
> Yeah, I went to Ubuntu Software Centre and installed Ubuntu one, but I still don't have the folder in /home/glenn directory, nor do I have any system settings for it. 
So  I am wondering what other packages are not installed that might be dependencies or such.

Have you opened the Ubuntu One control panel and signed in to it yet?

---

### Post by Senior_Buckethead on 2012-05-08
Found it in system settings. But when I launch Ubuntu One, it crashes with the following error:
```

CredentialsError
DBusException(dbus.String(u'Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.'),)

```

---

### Post by oldos2er on 2012-05-09
Thread moved to Ubuntu One.

---

### Post by Senior_Buckethead on 2012-05-12
Can someone please help with the error message:
```

CredentialsError DBusException(dbus.String(u'Did not receive a reply. 
Possible causes include: the remote application did not send a reply,
 the message bus security policy blocked the reply, 
the reply timeout expired, or the network connection was broken.'),)
```What is causing this error and how can I fix it?

---

### Post by Senior_Buckethead on 2012-05-15
bump

---

### Post by Senior_Buckethead on 2012-05-17
bump again ...

---

### Post by Senior_Buckethead on 2012-05-19
```

 p, li { white-space: pre-wrap; }  CredentialsError
 DBusException(dbus.String(u'Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.'),)

```

Can someone please illuminate me on this error message...

---

### Post by Senior_Buckethead on 2012-06-04
Reinstalled 12.04 and fixed problem. Ubuntu One must run on Python, since reinstalling has fixed problem.

---

