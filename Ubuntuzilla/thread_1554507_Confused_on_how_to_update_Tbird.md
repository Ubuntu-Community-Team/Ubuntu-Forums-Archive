---
title: "Confused on how to update Tbird"
date: 2010-08-16
forum: Ubuntuzilla
---

### Post by Ralph L on 2010-08-16
I am confused on what is the standard and intended way of installing TB updates.  Under Edit>Preferences>Advanced>Update there is an option to have TB check for new updates and ask me if I want to install them.  I have set that option, but whenever it finds an update, it puts up a window that says I don't have permission to install the update.  TB is installed in /opt, if that makes a difference.  Is this the standard method for updating TB, and am I just having problem with it, or is ubuntuzilla the standard and intended method of installing updates?

Any help appreciated, and if you can tell me how to fix my permission problem that would be helpful.

Also, have the same question for Firefox.

Thanks

Ralph

---

### Post by nanotube on 2010-08-18
Hi,

Ideally you would get your updates from a repository, rather than use individual applications' auto-update mechanisms.

So, if you're using the ubuntuzilla repository, you should just pull the latest versions from that, rather than doing the within-app autoupdate.

There are no 'permission problems' here - the application files are owned by root, as are all application files.

Did you use the ubuntuzilla repository, or the old ubuntuzilla script to install?

---

### Post by houndi on 2010-08-26
I am also confused to update Thunderbird, i have many problems. can any one tell the procedure how to update.

---

### Post by nanotube on 2010-08-26
> **houndi said:**
> I am also confused to update Thunderbird, i have many problems. can any one tell the procedure how to update.

please give more details about your setup. do you currently have an ubuntuzilla package installed, or just using stock ubuntu-repos version of thunderbird? if ubuntuzilla, did you use the repository and get the 'thunderbird-mozilla-build' package, or did you use the script? also, are you on 32bit on 64bit?

---

### Post by Ralph L on 2010-10-11
The scenario I gave below does NOT work.  For some reason when TB is installed using sudo, it is only accessible by using sudo.  So don't do what I did.


Found and easy way:
1.  Brought up Terminal and entered "sudo thunderbird"
2.  Went to TB menu>Help>Check for Updates..  This listed the latest stable version of TB.
3.  Installed the latest stable version.

Ralph

---

### Post by nanotube on 2010-10-12
just for future readers: running thunderbird with 'sudo' is a bad idea, that can mess up the ownership of your thunderbird profile. if you must, run it with "gksudo" instead. 

even that is not 'ideal' - best to get updates from a repository.

---

### Post by DayLite on 2010-11-10
> **Ralph L said:**
> , but whenever it finds an update, it puts up a window that says I don't have permission to install the update.
Any help appreciated, and if you can tell me how to fix my permission problem that would be helpful.

Also, have the same question for Firefox.

Thanks

Ralph

First close Thunderbird, then in the terminal type > sudo thunderbird it will launch Thunderbird and you will have permission.

---

### Post by jgt10 on 2010-12-03
> **Ralph L said:**
> 
Found and easy way:
1.  Brought up Terminal and entered "sudo thunderbird"
2.  Went to TB menu>Help>Check for Updates..  This listed the latest stable version of TB.


Hmm.  Tried that with TB 3.0.6 and didn't find the "Check for Updates" option. 

I am finding it difficult to find a definitive answer for how to upgrade ThunderBird from 3.0 to 3.1 on Ubuntu 10.04.  

JGT

---

### Post by Garzo on 2011-03-02
The Ubuntuzilla repository has TB 3.1.7, and that's what I have installed. Because I've left TB's own update checker on, it is telling me that 3.1.8 is available. I know that clicking the update checker to update won't work, and that I should wait until 3.1.8 is in the Ubuntizilla repository, but how long does it normally take for that to happen. Please correct me if I've got the wrong idea about updates, but the above several posters have asked about updates without getting clear and concise answers.

---

### Post by jasmines on 2011-03-03
Ehehehe... the new version goes in the Ubuntuzilla repository when our beloved nanotube can do it:)
Normally he is fast, and a couple of days from the release are enough. Now he must be on holydays eheheheh! :)

---

### Post by Garzo on 2011-03-03
Thanks. How Ubuntuzilla updates work should be made a bit more obvious on the main pages.

---

### Post by Karlchen on 2011-03-06
Hello, Garzo.

> How Ubuntuzilla updates work should be made a bit more obvious on the main pages. You may have missed the sticky thread "[New Ubuntuzilla apt repository. Ubuntuzilla users, update your sources.list!]("http://ubuntuforums.org/showthread.php?t=1323239")" at the top of this forum, dated November 2009. Once you have added the Ubuntuzilla repository to the repository list, the Mozilla builds of Firefox, Thunderbird and Seamonkey can be installed and updated just like any software package provided by Canonical.

Kind regards,
Karl

---

### Post by Garzo on 2011-03-06
Yes, I saw it, but my sources list is up to date. There should be an obvious instruction to Ubuntuzilla users to disable the built-in updates and update instead through the Ubuntuzilla repository. I just updated Thunderbird this morning (Thank you!), so I'm now running with the latest version. It's worth mentioning up front that there's a little time lag between an update going live from Mozilla and the Ubuntuzilla repository updating to it. However, it's far in advance of what Ubuntu ships with.

---

