---
title: "Comcast DNS is haxored"
date: 2005-04-13
forum: The Cafe
---

### Post by dermotti on 2005-04-13
Ive been noticing the last couple of days ive been getting dns errors like crazy, and at sometimes my internet is totally unusable.

So i do a search an google and found that comcast has been the subject of hacker attacks and dns poisoning (filling hte dns with craploads of bogus data)

I have now switched my dns server to verizon 4.2.2.2 and its been mach fast. First time ive seen it this bad for a long time.

---

### Post by electroglas on 2005-04-13
Me too!

---

### Post by dermotti on 2005-04-13
i reccoemnd trying to changing yoru secondary dns to 4.2.2.2 or any other good dns server you know of

---

### Post by jerome bettis on 2005-04-14
[QUOTE=dermotti]i reccoemnd trying to changing yoru secondary dns to 4.2.2.2 or any other good dns server you know of[/QUOTE]
 how exactly do you do that?

i've been having the same issues.

---

### Post by dataw0lf on 2005-04-14
Use your /etc/resolv.conf :
nameserver <ip>   

Where <ip> is the IP you wish to query for DNS info.

---

### Post by oddabe19 on 2005-04-14
we actually changed our DNS in our router to another comcast DNS address.  It's been working great since.  That way, i can leave my compy at DHCP and let the router do all the work.

---

### Post by dermotti on 2005-04-14
yup, i put the secondary dns of my router to 4.2.2.2 so i could leave my linu computer on dhcp

---

