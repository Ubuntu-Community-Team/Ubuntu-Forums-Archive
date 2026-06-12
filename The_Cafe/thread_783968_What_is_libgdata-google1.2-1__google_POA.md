---
title: "What is libgdata-google1.2-1 / google POA ?"
date: 2008-05-06
forum: The Cafe
---

### Post by Jags_FL on 2008-05-06
I was updating Ubuntu 8.04 and saw a package name " libgdata-google1.2-1 " was getting updated/installed through "Update Manager". Now, I don't recall installing anything from google. And that makes me wonder what it is and what its doing in Ubuntu by default.

The little info I found under >> Ubuntu  >> Packages  >> hardy >> libs >> libgdata-google1.2-1 says, it's a " Client library for accessing google POA through SOAP interface ". I guess someone here will be able to shed some light on this. ( [http://packages.ubuntu.com/hardy/libgdata-google1.2-1](http://packages.ubuntu.com/hardy/libgdata-google1.2-1) )

Thanks, -Jags

---

### Post by fluteflute on 2008-05-06
It's part of evolution (default email client).

---

### Post by Jags_FL on 2008-05-06
Many thanks fluteflute for the reply.
 
Ok so its a part of Evolution. But what exactly "google-part" does within Evolution ?

As I use web based emails only, would it be ok / safe to remove Evolution ?? (thru Synaptic package manager).

Thanks in advance.

---

### Post by Polygon on 2008-05-06
why does it matter so much to you that there is a package that helps other programs connect to google on your system? its opensource.......

---

### Post by Jags_FL on 2008-05-07
My questions were slightly different and i.e.:

(1) What exactly " libgdata-google1.2-1 / google POA " does within Evolution and
(2) Is it safe to remove Evolution from Ubuntu 8.04 ?

Many thanks in advance.

---

### Post by taylorkh on 2008-05-14
I noticed this one also.  A search for "Google POA" on google.com does not return anything to explain what "POA" is.  I use google every day as a search engine.  However, I do NOT want those nosy bastards poking around on my computer systems.  I do not install google toolbars or any other free programs which google offers to "help me".  Looks like I have to remove evolution and ekiga to remove this library. 

Ken

---

### Post by reyfer on 2008-05-14
> **Polygon said:**
> why does it matter so much to you that there is a package that helps other programs connect to google on your system? its opensource.......
Maybe he/she cares so much about it because, as you yourself stated IT IS HIS SYSTEM?

---

### Post by b3n87 on 2008-05-14
isn't that a library file for Evolution so that it can access your Gmail account or Google calender?

---

### Post by dash86no on 2008-06-18
> **reyfer said:**
> Maybe he/she cares so much about it because, as you yourself stated IT IS HIS SYSTEM?

Good point, I say it's a very healthy sign when people look into and question what kind of files are being added to their systems. 

To me, that's one of the biggest pluses of the open source community over the "Just click ok ok next next" cluture of the closed source OS world.

I wondered about this too, but will leave it on my system for now.

---

### Post by rpineger on 2008-08-04
I was interested in how to track these things back so I've had a go. Every project is different so it can be tricky! 

I believe it is the Google Calendar backend as mentioned on this page of the Evolution wiki:
[http://www.go-evolution.org/Evo2.22](http://www.go-evolution.org/Evo2.22)

Target: 2.21.1
Owner: Harish/Chenthill with GSoc Student
Add a account setup for Google Calendar.
Ability to view/modify/add/send appointment through Evolution
Status: Committed. 

I also found 'bleeding edge' source code in their Subversion repository:
[http://svn.gnome.org/svn/evolution/trunk/plugins/google-account-setup/](http://svn.gnome.org/svn/evolution/trunk/plugins/google-account-setup/)
But I didn't want to download a tarball because I can barely speak C anyway ;-)

I couldn't make the connection though between the final package name 'libgdata-google' and this library. Perhaps the link is with the package maintainer at Ubuntu?
Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>

I've had a look at Ubuntu Package search and found the maintainers - clicking on 'Ask a question' took me to Launchpad so I think I might raise a minor bug to get the description clarified if someone in the know is willing to help.

Richard

---

### Post by mrgnash on 2008-08-04
> **taylorkh said:**
> I noticed this one also.  A search for "Google POA" on google.com does not return anything to explain what "POA" is.  I use google every day as a search engine.  However, I do NOT want those nosy bastards poking around on my computer systems.  I do not install google toolbars or any other free programs which google offers to "help me".  Looks like I have to remove evolution and ekiga to remove this library. 

Ken

Paranoid much?

---

### Post by ssam on 2008-08-04
i think it is also used by totem's youtube plugin.

---

### Post by orawax on 2008-10-10
> **Polygon said:**
> why does it matter so much to you that there is a package that helps other programs connect to google on your system? its opensource.......

A healthy distrust?

Ekiga GTK-standalone (ekiga-gtkonly) comes without the big brother component, but unfortunately it's not functioning: [http://ubuntuforums.org/showthread.php?t=893678](http://ubuntuforums.org/showthread.php?t=893678)

---

### Post by sixerjman on 2008-11-11
This bothered me also as I use webmail almost all the time and don't like 
installing things I don't understand on my systems. 

The package maintainer(s) could have done a better job explaining what exactly 'POA' is.  Nearest definition I could find was 'Post Office Agent' but who knows? 

The package is 'optional' but any attempt to remove it via aptitude wants to take out evolution which is also part of 'gnome-desktop-environment' and I will not do that.

---

### Post by seattleweb on 2009-01-27
> **sixerjman said:**
>  package is 'optional' but any attempt to remove it via aptitude wants to take out evolution which is also part of 'gnome-desktop-environment' and I will not do that.

I will; I want no part of Google on my system :/

/dev/null for evolution

---

