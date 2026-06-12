---
title: "Subversion repository browser"
date: 2005-05-24
forum: Server Platforms
---

### Post by fng on 2005-05-24
Which program do you guys recommend for viewing and browsing a subversion repository.  I'm looking for something you can use with a browser.

---

### Post by deuce868 on 2005-05-24
trac is a great SVN viewer/program management app.

---

### Post by mendicant on 2005-05-24
Also check out the ones listed under Web Views here:
[http://www.subversionary.org/subversionary.cgi/SubversionProjects](http://www.subversionary.org/subversionary.cgi/SubversionProjects)

---

### Post by fng on 2005-05-25
trac is not an option at work
We allready have a helpdesk with ticket tracking.
But i'm certainly gonna use it at home.

After some trail and error, I succeeded to get viewcvs working (multiple svn repositories).  Im quite happy with the result.  Now i only need to make me a company template for it :)

---

### Post by rich on 2005-05-25
Excellent. CVS is on my list of things to do - despite there being no comprehension that such a thing might be useful.

It sounds like it may be a bit late, but there is an article here :

[http://www.onlamp.com/pub/a/bsd/2005/05/12/FreeBSD_Basics.html](http://www.onlamp.com/pub/a/bsd/2005/05/12/FreeBSD_Basics.html)

The server side is BSD, but 

"This week's article demonstrates how to create a secure repository using Subversion. The next installment will show how to train your users to access the repository using a GUI client."


Rich

---

### Post by jdong on 2005-05-25
viewcvs (deceptively named, yes) also does SVN, and works quite well.

---

### Post by yentingchen on 2005-06-07
[QUOTE=fng]trac is not an option at work
We allready have a helpdesk with ticket tracking.
But i'm certainly gonna use it at home.

After some trail and error, I succeeded to get viewcvs working (multiple svn repositories).  Im quite happy with the result.  Now i only need to make me a company template for it :)[/QUOTE]
Could you provide the detailed process of  how to setup the ViewCVS on Ubuntu?

Best Regards.

---

### Post by flurdy on 2005-06-09
Do you need more functionality than the buildt in web dav support?

it doesnt give you any log information, but you can browse and see which is the current version for each branch. 

And since it comes with subversion it is no hassle to set up.

---

