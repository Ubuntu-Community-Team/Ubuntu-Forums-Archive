---
title: "Which Forum Software ( &amp; perhaps in Ubuntu Server repsitories)"
date: 2008-03-30
forum: Server Platforms
---

### Post by luvit on 2008-03-30
I know there is a large thread on this, but it's been dead for over 2yrs.
[LIST]
[*]So I don't get over my head for daily maintenance & etc...[LIST]
[*][COLOR=Blue]Free[/COLOR] - Source not required...[/LIST][LIST]
[*][COLOR=Blue]Feature Rich[/COLOR][/LIST][LIST][LIST]
[*]I have no experience or interest in writing code for customizations.[/LIST][LIST]
[*]I probably won't worry about skins.[/LIST][/LIST][LIST]
[*][COLOR=Blue]Simple installation[/COLOR] or possibly in (Ubuntu Server repositories)[LIST]
[*]I can live with a complicated install with excellent instructions.[/LIST]
[*]I like vBulletin, but your recommendations don't have to reflect vBulletin style.[LIST]
[*]My only forum experience is as a member of Ubuntu Forums and another vBulletin-based forum. I've not been observant of other forums I've briefly visited.[/LIST][/LIST][/LIST]My first forum will be a **small** closed forum with invites from Mods or Users.

---

### Post by dmizer on 2008-03-30
i've employeed [simple machines forum](http://www.simplemachines.org/) (SMF) in a variety of implementations and it's served faithfully for at least 3 years now.

installation is cake if you follow the well written directions.  upgrades can be easily done via the admin interface, and releases are fairly regular.

user interface is familiar enough to most users, and it uses standard bbcode.  admin interface will probably take some getting used to, and i found the board permission settings to be a bit frustrating to get used to, but otherwise it's a great piece of software.

pick your skin carefully, or if you're good enough ... write your own.  skin creators find it difficult to keep up with the SMF release schedule, and sometimes updates will break because the skin isn't compatible.

it's also being integrated with most open source CMS like drupal.

it's quite resistant to attack, and none of my production boards have been hacked since i moved to SMF.  Every other free board i've used has been hacked at one time or another.

edit:
just remembered this fantastic resource - [http://www.opensourcecms.com/](http://www.opensourcecms.com/)

the site lists most free CMS including forum software, and has sample installs of all the listed software which allow you to log in and play with the forum both as a user and an admin to see how things work.

---

### Post by hyper_ch on 2008-03-31
SMF is good software, constantly being evolved... however if you don't like the licence then maybe phpBB3... I heard it's a huge improvement (also in security related areas) but I haven't tested it yet.

---

### Post by rickyjones on 2008-03-31
I'm used to using PHPBB. It is free, open source, and very simple to install and customize.

-Richard

---

### Post by hyper_ch on 2008-03-31
well, phpBB2 has a terrible security record ;)

---

### Post by luvit on 2008-03-31
> **dmizer said:**
> edit:
just remembered this fantastic resource - [http://www.opensourcecms.com/](http://www.opensourcecms.com/)
I don't know if you realize how often you find my posts and give me great recommendations. Thank you.
I am considering a derivative of SMF: [[COLOR=RoyalBlue]_SMF Appliance_[/COLOR]]("http://www.rpath.org/rbuilder/project/smf")
It's a minimal Linux install with SMF in hopes of supporting a celeron server. (closed community, 120members, 5 or 10 active users at once).

This is where I'll begin the sandbox unless you think a celeron processor with 512MB of RAM 40GB HD is a pipe dream to run a small volunteer organization forum.
I have two of these celeron servers, so I'll count on the 2nd server to provide a cold spare backup.

---

### Post by Dr Small on 2008-03-31
[MyBB]("http://mybboard.net") is pretty good, and somewhat similar to vBulletin

---

### Post by dmizer on 2008-03-31
> **luvit said:**
> ... unless you think a celeron processor with 512MB of RAM 40GB HD is a pipe dream to run a small volunteer organization forum.
I have two of these celeron servers, so I'll count on the 2nd server to provide a cold spare backup.

i ran a full fledged website with forum and 500+ pictures photo gallery on a 700mhz pIII with 256meg of ram.  i think you'll be fine.

glad to hear you find my posts helpful. :)

---

### Post by luvit on 2008-04-01
I got some thanks in, dmizer... :)

[SIZE="1"][COLOR="Red"]I think the below info is solved[/COLOR][/SIZE]
[SIZE="1"][COLOR="Silver"]I got Ubuntu Server v7.10 (LAMP) installed.
I haven't installed SMF, just yet.
I'm stuck on installing GD Graphics Library if you will see my thread: ht tp://ubuntuforums.org/showthread.php?t=742292[/COLOR][/SIZE]

---

### Post by Deathrend on 2008-04-01
phpBB3 for Free, a few years ago, I would have said avoid it like the plague (Otherwise known as WindowsMe), however it's a lot more secure than the past versions.  (Don't get me wrong, it was as secure as others, ore probably more.. however it was also one of the most popular, leading to more found exploits).

However for Paid, hands down Invision Power Board, I've used it for years, however just recently broke down, and upgraded to the paid version (Mine was very..very out of date.. yet I loved it to much to get rid of it).

I've put my Ubuntu LAMP server through everything you could immagine, and it fights back like a champ, pretty much any forum that you can run on Apache/PHP/MySQL will run on it.  If you're missing an add-in file, that's easy enough to fix with the packages ;)

---

### Post by hyper_ch on 2008-04-01
still running IPB 1.3.1 myself ;)

---

