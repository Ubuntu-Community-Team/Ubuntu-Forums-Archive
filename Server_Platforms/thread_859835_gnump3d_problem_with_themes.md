---
title: "gnump3d problem with themes"
date: 2008-07-14
forum: Server Platforms
---

### Post by zenoran on 2008-07-14
Does anyone use the apt-get package of gnump3d?

I have it installed and seems to be working other than the themes... when I select a theme it shows a bunch of broken images for that them and whenever you click off the page it reverts back to the default...

anyone seen this and/or know how to fix it?


Thanks

---

### Post by zenoran on 2008-07-16
so no one uses gnump?

are there other decent streaming apps I'm not aware of?

I'm halfway tempted to write my own :(

---

### Post by cariboo on 2008-07-16
I use gnump3d and don't have any problems. Have you looked in /usr/share/gnump3d to see if anything is amiss. That is where all the theme files are located.

Jim

---

### Post by zenoran on 2008-07-16
> **cariboo907 said:**
> I use gnump3d and don't have any problems. Have you looked in /usr/share/gnump3d to see if anything is amiss. That is where all the theme files are located.

Jim

Yup they're all there

```
root@orion:/etc# cd /usr/share/gnump3d/
root@orion:/usr/share/gnump3d# ls
Avalon   Clean    dotNET    LaFrere  Musicus   Nomad   redgrey        simple   Thexder
BlueBox  default  handheld  Liquid   nausicaa  README  SchwartzNGrau  Tabular
root@orion:/usr/share/gnump3d# 
```

It's the strangest thing... images don't work AT ALL and the pref always reverts back to whatever is in the config file.. im not too worried about that because I can always keep the same theme but most of them use images and it would be nice if I could see 'em :(

My brother has gnump installed too on ubuntu and he has the same problem.. not sure how everyone else is working?

---

### Post by SMGauna on 2008-09-30
[https://bugs.launchpad.net/ubuntu/+source/gnump3d/+bug/201013](https://bugs.launchpad.net/ubuntu/+source/gnump3d/+bug/201013)

This problem exists in debian stable as well.  I checked my error logs and it showed :
Header: HTTP/1.0 200 OK
Connection: close
Server: GNUMP3d 3.0
Content-type: text/html
Set-Cookie: theme=Tabular;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;


The cookies are expired as soon as they are set, so they are never used.

gnump3d v3.0 [CVS Info: gnump3d2 1.156 (2007/10/16)] on Perl v5.008008
Line 1349 of /usr/bin/gnump3d reads :
```
        $header .= "Set-Cookie: " . $key . "=" . $val . ";path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;\r\n";
```

If you change the date, the problem is fixed.  It already has the bug filed against it, so expect a patch... eventually. :)

---

### Post by cariboo on 2008-09-30
It seems that all of a sudden I have the same problem, thanks for the fix.

Jim

---

