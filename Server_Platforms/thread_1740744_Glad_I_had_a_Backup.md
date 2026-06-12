---
title: "Glad I had a Backup"
date: 2011-04-27
forum: Server Platforms
---

### Post by Vegan on 2011-04-27
Today I wrote a new page for my gaming site. The topic was new generation [DirectX 11 games]("http://www.hardcore-games.tk/papers/fpssm5.php"). 

What I did was use an existing document and change the headers and proceed. The problem is I forgot to rename the page and overwrote the old page.

No problem, I hop over to the backups and in seconds the lost file was back.

Because I backup my web folder daily. I did not lose any work at all.

Moral of the story: Backup today.

---

### Post by Usa_Tony_Cuba on 2011-04-27
Congrats @Vegan, happened to me once ... I was running a few scripts in four terminal windows.. went into the execution did enter wrong parameters..  :( almost wipe-up half my /home ...
> **Vegan said:**
> Moral of the story: Backup today.

---

### Post by rubylaser on 2011-04-27
I totally agree, and I'm happy backups saved you.  But, it's never good practice to be working directly on your production website for changes/updates.  It's much better to have a version controlled staging area for tests/new code, and once tested/verified you'd pull a copy over for your production site.  

In this scenario, you'd still have a version in SCM and on your production server, so you wouldn't even have to resort to backups :)

---

### Post by Vegan on 2011-04-28
I use SAMBA and simply make the web folder visible as NAS.

I then use any tool I want to edit the content.

The backup though is a native Linux shell script. I age 90 days so I have versions galore.

I have considered a range of solutions, the simple was all I need. My WRT54G is a good firewall.

---

### Post by rubylaser on 2011-04-28
I hope you do this through rsync and hard links, otherwise, you're unnecessarily saving whole web application backups for no reason (eats up hard drive space).  This is exactly what SCM systems are designed to do for you CVS, Mercurial, SVN, or GIT will happily store all versions of your applications including branches.  Besides, your still not allowing for a test environment before deployment, but maybe that doesn't matter in your case.  Anyways, glad to hear you're covered.

---

### Post by 3L33T on 2011-04-29
> **Vegan said:**
> 

No problem, I hop over to the backups and in seconds the lost file was back.

Because I backup my web folder daily. I did not lose any work at all.

Moral of the story: Backup today.

NICE moral story but you did not specify what technique ("cp", "tar", "cpio", rsync) you used to backup? and you backed up to what medium -- external USB? mounted partition of a different disk?

---

### Post by Vegan on 2011-04-29
I use mysqldump and tar to backups.

I then gzip them and burn them to dvd for archival storage periodically.

script is now over 25 lines long

---

