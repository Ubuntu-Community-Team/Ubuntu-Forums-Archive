---
title: "Another Swat Question"
date: 2004-11-29
forum: Repositories &amp; Backports
---

### Post by bubber on 2004-11-29
When I try to install Swat with Synaptic I get the following error:

  Depends: samba but 3.0.7-1ubuntu6.2 is to be installed

I am trying to install swat 3.07-1ubuntu6 from universe.  Is version 6.2 available somewhere?  Thanks for the help.

---

### Post by pixelbrain on 2005-02-06
You have to change your repository settings in synaptic. 

settings>>repositories

click on  deb     [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)

type 'universe' in the sections field.

Then hit OK and then the RELOAD button.

Now when you search for swat, 3.0.7-1ubuntu6.3 or greater should show up.

---

