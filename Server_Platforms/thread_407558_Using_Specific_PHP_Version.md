---
title: "Using Specific PHP Version"
date: 2007-04-12
forum: Server Platforms
---

### Post by MilesZS on 2007-04-12
Let me see if I can accurately describe my situation:  I have a VPS (Slicehost.com) running Dapper.  I have a proprietary web app written in PHP that I need to support (using PHP, MySQL, Apache). The web app requires PHP v5.1.4. It seems to fail on any other version of PHP. Unless I am mistaken, 5.1.2 is used by Ubuntu Dapper, and Edgy uses 5.1.6. The Ultimate Question is: What is the best way to handle this situation? I would, of course, prefer to use package management, as it obviously makes everything fairly simple, but this doesn't seem to be possible (in particular, I couldn't find a repository of any type that is still serving 5.1.4).

I can envision possibly building my own deb of 5.1.4, which, if I am not mistaken, would allow me to use the trusted repositories when it comes to Apache, and MySQL, if I also froze the PHP version. However, I am more than a little intimidated by that process, as I've heard it's difficult (to put it mildly).

So far, the default installations of PHP, MySQL, and Apache have not worked. I recently compiled both Apache 2.2.4 and PHP 5.1.4 by hand, which worked, but is not ideal, obviously.  This seems to me to be the 'desperation scenario', but I suppose if it works, it works.

Any other ideas? ... and thanks for reading my verbose question.

---

### Post by Frosty Cold Drink on 2007-04-12
Considering PHP security issues, I'd say update your VPS to 5.1.6 or (maybe) better 5.2.1

---

### Post by MilesZS on 2007-04-12
> **Frosty Cold Drink said:**
> Considering PHP security issues, I'd say update your VPS to 5.1.6 or (maybe) better 5.2.1

Sure, that would be great.  Like I said, though, this web app requires 5.1.4.  I know that's dumb, and I have been trying to figure out why that is, but as it stands, it requires v5.1.4.  

So, knowing I HAVE to have PHP 5.1.4, what do you believe is the best way to do it?

---

### Post by Frosty Cold Drink on 2007-04-12
> **MilesZS said:**
> Sure, that would be great.  Like I said, though, this web app requires 5.1.4.  I know that's dumb, and I have been trying to figure out why that is, but as it stands, it requires v5.1.4.  

So, knowing I HAVE to have PHP 5.1.4, what do you believe is the best way to do it?

I really hate it when I post questions and people refuse to anwser them, so I won't do it :) But could you stand to beat on the app provider? If they don't keep thier code workable on the latest stable minor release, then perhaps another vendor may be a better choice...

Anyway, see if you can force a specific version from whatever tool you use to manage packages. You never know, it might be there. Other than that, you are probably best off just compiling from source. If you are worried about updating, do a CVS chekout, which you can update as needed. Desperate or no, if you are going to break from the repositories, best keep it as seperate as possible.

---

### Post by MilesZS on 2007-04-12
> **Frosty Cold Drink said:**
> I really hate it when I post questions and people refuse to anwser them, so I won't do it :) But could you stand to beat on the app provider? If they don't keep thier code workable on the latest stable minor release, then perhaps another vendor may be a better choice...

It's a long story as to how it's gotten to this point.  I'll spare you.  Unfortunately, it's a CMS that a bunch of small businesses and not-for-profits use, and I'm taking over the hosting.  I have to support it.  You're right though, it's not a good situation.  

> **Frosty Cold Drink said:**
> Anyway, see if you can force a specific version from whatever tool you use to manage packages. You never know, it might be there. Other than that, you are probably best off just compiling from source. If you are worried about updating, do a CVS chekout, which you can update as needed. Desperate or no, if you are going to break from the repositories, best keep it as seperate as possible.

I think you're right, compiling from source is probably going to be the best way.  Thanks for your help, man.

---

### Post by dmclark on 2007-04-12
> **Frosty Cold Drink said:**
> Considering PHP security issues, I'd say update your VPS to 5.1.6 or (maybe) better 5.2.1

For the life of me I cannot figure out how to get 5.1.6 for dapper -- any ideas?

---

### Post by marianom on 2007-04-12
Hi MilesZS. I searched internet to see if I could find a .deb 5.1.4 to no avail.
Anyway, compiling from source it's pretty ease (I've done it with oracle, mysql, imap and gd support and it's working).

Let me know your php specifications and I give it a try to see if I can give you the exact procedure.

---

