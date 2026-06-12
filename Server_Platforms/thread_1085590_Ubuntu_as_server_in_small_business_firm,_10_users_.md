---
title: "Ubuntu as server in small business firm, 10 users - roaming profiles"
date: 2009-03-03
forum: Server Platforms
---

### Post by srdjo on 2009-03-03
I am trying to replace my current windows 2003 server setup with ubuntu.

I have he following problem:

How can I make something like roaming profiles in linux ?
I have about 10 users, so I dont wont to do anything over complicated.

I want each user to be able to login to any free computer and get his documents and settings like we can on w03 server.

I tried ltsp, but we dont have the same hardware, and the remote desktop to windows machines on ltsp clients was kinda slow.

What is the optimal solution ?

My client computers use ubuntu and xp.

---

### Post by netztier on 2009-03-03
> **srdjo said:**
> 
How can I make something like roaming profiles in linux ?


One possible solution: 

NFS mounted home directories. All user's Homedirs are on an NFS server, and on whatever PC the user logs in, he is not using /home/<username> off the local disk, but /home/<username> which is the mountpoint for his personal directory on the NFS export of that server. This will include building something with LDAP or NIS and the NFS automounting feature. 

This being said, you'll probably want to look at gigabit connectivity and plenty of RAM for that NFS server, since every read or write access to any file in any user's homedir will result in NFS traffic to and from that server. If a user has a lot of large MP3 or Video files in his homedir and accesses them frequently, you might see increased load on the NFS server.

If you (google-)search for "NFS home directory", you should be able to find a good number of ressources on how to set it up. I for one haven't got any experience in this, because I never found need or time to try this.

Now since every user already has a private directory on the file server, you might be able to us that very directory as repository for the User's roaming Windows profile, provided you share that directory with Samba. This might include that you have to configure Samba do be an (NT4 style) PDC.

regards

Marc

---

### Post by kishore.s on 2009-06-17
you should be able to do it through samba which acts as PDC(Primary Domain Controller)
google out and this should be not that difficult

I do use the same ..;)

---

### Post by v3xtra on 2009-06-17
Our school implements this, but I'm not sure how they do it to be honest.  We have labs that have Red Hat computers and Windows XP computers, and from any computer we are able to connect with a central username and access any documents that we need.  It's a nice setup, and really allows for you to be able to use any operating system that you want to with your work.

I would love to know how you are able to do this if you get everything working!  Thanks!

---

### Post by ghen on 2009-06-18
AFAIK there's no one file/user service that can gracefully accept both linux and windows clients so it looks like you're going to need two different setups. Both can be on the same box, but it will definitely be more complicated than a W2k3 SBS hands down. Not to mention the loss of Exchange!! Are you using that by the way?

You're going to need both Samba and NFS to share out windows and linux files respectively. Also, you'll need authentication with OpenLDAP and make everything play nice together.

Here's one of the walkthroughs I've been using to set up my server. Its slightly more complicated than it has to be, but very good at explaining each step:

[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

It works well under 8.04 as long as you take apparmor into account.


In conclusion: You've already paid for a 2003 SBS license. I say stick with it. Even if its a regular 2003 license and doesn't have exchange you're still better off as far as "don't want to do anything over complicated" goes. Are there any real problems with the current setup or do you just want to change for FOSS?

---

### Post by HermanAB on 2009-06-18
Howdy,

You actually have two separate problems:
a. Centralized authentication (a.k.a. single sign-on).
b. Centralized file store.

You can do both with a Samba PDC.  Or you can use NIS or LDAP plus NFS.  See the Official Howto on the Samba web site for details and examples.

---

### Post by scorp123 on 2009-06-18
> **srdjo said:**
> I am trying to replace my current windows 2003 server setup with ubuntu. [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

### Post by ghen on 2009-06-19
> **scorp123 said:**
> [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

By the way, that contributor has a newer version of that tutorial on his website:

[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

Its extremely verbose and helps a newbie like me to understand each step enough to fell confident customizing it.

---

### Post by whoop on 2009-10-27
> **ghen said:**
> By the way, that contributor has a newer version of that tutorial on his website:

[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

Its extremely verbose and helps a newbie like me to understand each step enough to fell confident customizing it.

Although, the newer version is also quite out dated.
I for one am not happy about the lack of (up to date) documentation on this very important topic. The tutorial you are referring to is the only complete tutorial I could find on the net. It is using an ubuntu server that is not supported anymore, and although it is the most complete way to do it, I don't think it's the easiest way. All the others tutorials are vague, incomplete or outdated. I don't know any tutorial for an ubuntu server that still has support.

There are two companies I know of that are using windows now, after having looked at linux. This issue was one of the important reasons for to use windows.

---

### Post by openfly on 2009-10-27
> **ghen said:**
> AFAIK there's no one file/user service that can gracefully accept both linux and windows clients so it looks like you're going to need two different setups. 

That's not entirely true.  OpenAFS accepts both fine and dandy.

Mind you their concept of grace is a little off kilter.

---

### Post by Lars Noodén on 2009-10-27
> **ghen said:**
> AFAIK there's no one file/user service that can gracefully accept both linux and windows clients so it looks like you're going to need two different setups. Both can be on the same box, but it will definitely be more complicated than a W2k3 SBS hands down. Not to mention the loss of Exchange!! 

Getting rid of the legacy system will save a lot of maintenance work.  Samba PDC works fine for Linux and OS X and even other systems.
As Openfly points out, OpenAFS is an option.  If it's already set up, it's a breeze to set up for OS X and a fairly simple recipe for Linux.  

Getting rid of MS Exchange would be enough of an advantage even by itself to warrant the upgrade.  However, that is separate from the two tasks of single-signon and networked storage.  When he does get to that point, [kolab](http://packages.ubuntu.com/jaunty/kolabd) and [citadel](http://packages.ubuntu.com/jaunty/citadel-suite) are two to look at first.

---

### Post by jason_Xtreme on 2009-10-27
U can try ebox-platform been using it for over a year we have our roaming profiles and the base setup took only a couple of hours. The forums are friendly and you get assistance with probs pretty quickly.

We have 12 computers and 16 staff members so ebox delivery what we needed plus features such as egroupware and built in ldap makes it easy to add other systems. the jabber server does not work but i substituted with openfire.
Sorry for not posting links (have something in my clip board) just Google the names.

Webmin also works great for the areas that ebox dont cover. (you can use the "stressfree" theme to get a cleaner webmin look.

---

### Post by whoop on 2009-10-30
> **jason_Xtreme said:**
> U can try ebox-platform been using it for over a year we have our roaming profiles and the base setup took only a couple of hours. The forums are friendly and you get assistance with probs pretty quickly.

We have 12 computers and 16 staff members so ebox delivery what we needed plus features such as egroupware and built in ldap makes it easy to add other systems. the jabber server does not work but i substituted with openfire.
Sorry for not posting links (have something in my clip board) just Google the names.

Webmin also works great for the areas that ebox dont cover. (you can use the "stressfree" theme to get a cleaner webmin look.

That could be cool, I'll give that a looksy, when I have the time.
In the meantime I've created an ubuntu idea on the general issue that ubuntu domain control sucks and needs to change: [http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)
Please **Vote** for this, as we all should understand that this is a really important feature.
Even if stuff like ebox is the way to go, ubuntu wiki should at least point to this as a possible solution for your (corporate) environment. All current documentation is either incomplete or outdated.

---

### Post by jondecker76 on 2009-10-31
I agree 100% that this should be something that works out of the box and is simple to set up - I've been wanting this for my home setup for a long time now.. Centralized login and user files would be great! (though I wouldn't want this as a thin-client setup)

---

