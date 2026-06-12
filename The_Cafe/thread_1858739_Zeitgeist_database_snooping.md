---
title: "Zeitgeist database snooping"
date: 2011-10-12
forum: The Cafe
---

### Post by hkphooey on 2011-10-12
Hi,

From what I gather, zeitgeist was introduced along with Unity. What it does is keep a log of all files you open, all applications you run, and probably some other information as well. 

If you're interested, get an sqlite manager and take a look at the database, which is stored in 
~/.local/share/zeitgeist/activity.sqlite

Here's a partially complete query which you can run on the database
```
SELECT datetime(substr(event.timestamp,1,10), 'unixepoch','localtime'), interpretation.value, actor.value, text.value
FROM event 
  LEFT JOIN interpretation on event.interpretation=interpretation.id 
  LEFT JOIN actor on event.actor=actor.id
  LEFT JOIN text on event.subj_text=text.id
WHERE event.id=1
```

So I'm not sure I like the idea of zeitgeist collecting this information. It would certainly be interesting to anyone interested in seeing what I've been up to. We have the option to clear 'Recent Documents' but none to delete the zeitgeist database. I personally don't use unity, yet the database still starts up when I use Gnome classic. 

How could anyone have thought that collecting this information was a good thing? It helps Unity decide how to arrange your menus. Well why not just let people figure out how to arrange their menus themselves? I'm the best person who knows how to do that. At least give me the option "Do you want to let Unity collect creepy data about you and guess how you like to organize things? No? OK, I won't install it then."

In addition there is the issue of unnecessary processor/disk use -- many people have reported faster systems after disabling zeitgeist -- but I'll let that one slide for the present discussion. 

What do others think?

---

### Post by bodhi.zazen on 2011-10-13
I moved your thread to the cafe as it is more a privacy issue then a security issue.

you might want to look at mounting $HOME in a tempfs or using a kiosk as there are many files in $HOME (such as .bash_history).

Alternately  you can use a private home (chmod 700 $HOME) or encrypt your home directory.

---

### Post by 3rdalbum on 2011-10-13
> **hkphooey said:**
> So I'm not sure I like the idea of zeitgeist collecting this information. It would certainly be interesting to anyone interested in seeing what I've been up to.

If you're worried about people gaining access to your computer and looking at Zeitgeist, then encrypt your home directory and set a BIOS password. An attacker does not need Zeitgeist to gain information about your activities on your computer.

> We have the option to clear 'Recent Documents' but none to delete the zeitgeist database.

There's a program available to blacklist directories and types of files from the Zeitgeist database, or to remove the database entirely.

> How could anyone have thought that collecting this information was a good thing? It helps Unity decide how to arrange your menus.

Unity uses Zeitgeist, but there the relationship ends. Zeitgeist is a Gnome thing, not specifically for Unity. Unity uses Zeitgeist for arranging frequently-accessed programs and doing searches for files.

For example, I have a video somewhere on my hard disk called "The Kinetic King". I watched it yesterday. I can just go to Unity and start typing 'kinetic' and it will pop straight up, even though I can't remember what folder I've put it in.

Zeitgeist's "Activity Log" program is also useful for remembering what you did on a particular day - you can see at a glance what projects you created on Friday, for instance. You can use that information to budget your project, because you can see how much time you spent in that document.

I don't even use Zeitgeist very much, but I know people have already found good uses for it.

Really, it barely logs anything that your system wasn't already logging. But it's more efficient for developers to interact with one encompassing system than to interact with a hundred different log files, meaning that you can do cool stuff with Zeitgeist that you couldn't easily do before.

If you're concerned about security, then you have no reason to be more concerned than previously. Encrypt your home directory and your Zeitgeist log will also be encrypted. Full-stop.

---

### Post by hkphooey on 2011-10-13
Thanks for the clarification 3rdalbum. I agree that encrypting your home directory and setting a BIOS password can do a lot to prevent the misuse of zeitgeist data. However, given that its a database which can be queried by any application, there's nothing to stop someone writing an app which will send the data back to a third party, while the computer is switched on and you're logged in. 

OK, so that's fairly unlikely, but I think what I'm objecting to is the general trend nowadays for applications, companies, organizations, to collect data. Quite often they collect too much through exuberance, and 'just in case they need it later'. Although it seems innocuous at the time, it pretty much always comes around and bites you in the *** later. Just as a small example, think of the developer who thought it would be cool if the Google street view cars collected wifi information as they were driving around. Well that proved to be a big mistake. 

The data of Zeitgeist also seems to be a little big and scary. Its been collecting information on every file I opened, every program I used since I installed Ubuntu 11.04 in April. I'm not sure it actually **needs** that data, and especially so as I don't use Unity. (A personal decision - I just didn't get along with it). Anyway, I was probably a bit alarmed on initial discovery of this cache of information, but with some more insight I'm more relaxed about it. I think I'll probably uninstall it anyway. Couldn't actually find the app you mentioned for limiting zeitgeist information though. Do you have a name for the app, or a URL?

---

### Post by Paqman on 2011-10-13
> **hkphooey said:**
> 
So I'm not sure I like the idea of zeitgeist collecting this information.

You're going to spew when you see /var/log then ;)

Really fine-grained privacy controls for Zeitgeist are in the pipeline, I believe there is a tool you can install already if you're interested in restricting what it logs.

---

### Post by hkphooey on 2011-10-13
I use /var/log a lot. But it's not really personal info, and it only keeps a few days' worth. Zeitgeist keeps information far longer than it needs to .. for ever! 

OK, I understood you weren't entirely serious there ... 

Meanwhile, do you happen to know what this tool is called. I've done a few searches but haven't uncovered it yet.

---

### Post by koleoptero on 2011-10-13
> **hkphooey said:**
> Meanwhile, do you happen to know what this tool is called. I've done a few searches but haven't uncovered it yet.

That's the activity log manager that was mentioned above.

---

### Post by alphacrucis2 on 2011-10-13
activity-log-manager I think is the name of the package. You can always delete the zeitgeist database any time. Kill zeigtgeist. Remove activity.sqlite under ~.local/share/zeigtgeist. When zeigtgeist is restarted it will create a new database.

---

### Post by kaldor on 2011-10-13
It's only local information. Your OS keeps track of things you do all the time and Zeitgeist isn't any different.

---

