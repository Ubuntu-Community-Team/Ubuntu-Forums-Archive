---
title: "Running a Java application with sudo vs. being root"
date: 2009-06-04
forum: Security
---

### Post by bswilson on 2009-06-04
Friends,

I've come across a situation I'm not sure how to troubleshoot.  Any help or guidance would be appreciated!  The problem is that I am trying to run [RationalPlan Viewer]("http://www.rationalplan.com/viewer-project-management-software.php"), a Java application that can open and export Microsoft Project files.

Now, the weird thing is, even though my userid is the owner of the entire directory (recursively) where the program files and libraries are stored, I can only run the program if I am the root user.  What I mean is, I must actually **be** root!

```
sudo su -
```

When I try to run this application with my own account or with sudo, it fails.  I am launching the program from the command line and so I'm getting seemingly different error messages.  I'm just curious, what is the distinction between sudo and being the root user in this case?

---

### Post by netJackDaw on 2009-06-05
Just would like to say that, if you have to run an application like that you should tell the vendor/distributor/developer that it is broken!!! A normal user application should never have to be run as root! not even as sudo!

When you run with sudo: you are you with privileges elevated to root level. ie you are still you. When you run as root you are root. Things you do can be tracked back using your username when you run with sudo. If you change files that you own when running sudo you can still change them when you're not... Probably not clear enough...

---

### Post by Duckter on 2009-06-05
When you run as root you are root just like Jackdaw said.

When you use sudo you assume the credentials of another user.  Generally speaking and making the usual assumptions (if it is your machine and you haven't been tinkering with the sudoers file) then you will be using root privileges.

su is apparently short for 'switch user' not 'super user' which even I was under the impression until 2 days ago.

And, yep it is all logged back to you.

---

