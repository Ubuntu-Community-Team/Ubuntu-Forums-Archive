---
title: "Simple Trouble Ticket System"
date: 2007-05-07
forum: The Cafe
---

### Post by rickyjones on 2007-05-07
Hello,

I'm looking for a very simple, web-based trouble ticket system for my business. Something that I can just upload to my server and configure access to the MySQL DB. Something that can be customized but isn't too "heavy." I know, a lot of requirements.

Does anyone know of anything like this? I simply need a trouble ticket system to make my life easier for managing tasks at my various client locations.

What is in use by the community and can anyone recommend a package to try?

Thanks,

-Richard

---

### Post by kprowell on 2007-05-07
Try this.  Depending on the number of users, it's free.  
[http://manageengine.adventnet.com/products/service-desk/index.html?scp](http://manageengine.adventnet.com/products/service-desk/index.html?scp)

or

[http://www.spiceworks.com](http://www.spiceworks.com)

---

### Post by v8YKxgHe on 2007-05-07
I really like [FlySpray]("http://flyspray.org"), it's a great bug/issue tracker (I take it that's what you need?). I've recently joined the FlySpray team and am working on a new, web2 style theme for it :)

---

### Post by TravisNewman on 2007-05-07
Seconding flyspray! It's a bug tracker but we use it as a support ticket tracker for the help desk. It's great!

It's not *better* than bugzilla but its certainly easier and more straight-forward.

---

### Post by rickyjones on 2007-05-07
FlySpray looks like it can fulfill my needs. I just uploaded it to my server - can anyone explain why it appears as though the stylesheet is not loading?

[http://www.rrcomputerconsulting.com/tt/](http://www.rrcomputerconsulting.com/tt/)

I also have this error at the top: Notice: Undefined offset: 0 in /home/content/r/m/a/rmaloleyii/html/tt/includes/class.tpl.php on line 39        

I'd love to try this out if I can get this fixed. 

Thank you for your recommendations!

-Richard

---

### Post by v8YKxgHe on 2007-05-08
Are you using 0.9.9.1 or the latest SVN? The reason why the stylesheet isn't loading is because the URL is wrong:

```
<link media="screen" href="http://www.rrcomputerconsulting.**com/tt/themes//theme.css**" rel="stylesheet" type="text/css" />
```

I'm not sure why it's like that, but you can easily fix it by editing the template file 

> templates/header.tpl

and changing 

>    <link media="screen" href="http://www.rrcomputerconsulting.com/tt/**themes//theme**.css" rel="stylesheet" type="text/css" />

To

>    <link media="screen" href="http://www.rrcomputerconsulting.com/tt/**themes/Bluey/theme**.css" rel="stylesheet" type="text/css" />

---

### Post by rickyjones on 2007-05-08
Odd - I just redownloaded the package and reinstalled it and not it works fine. Hmmm.

Thanks for the help guys!

-Richard

---

### Post by tom93 on 2008-03-29
I just found [http://16bugs.com]("http://16bugs.com") .
You run it on their site and they gently nag you to upgrade, but the free version can hold 1 Meg of bugs. You can even read the bug list with lynx.

---

### Post by HermanAB on 2008-03-29
PHPsupport is also useful:
[http://aeronetworks.ca/phpsupport.html](http://aeronetworks.ca/phpsupport.html)

---

