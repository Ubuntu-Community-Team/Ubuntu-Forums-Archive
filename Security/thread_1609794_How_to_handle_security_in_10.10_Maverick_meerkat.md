---
title: "How to handle security in 10.10 Maverick meerkat"
date: 2010-10-30
forum: Security
---

### Post by alvinmoneypit on 2010-10-30
Hi,

I was wondering how to configure my security.  

Upon install from the disc, the dialog asks for "automatic login"  I selected that and although it automatically logs in upon cold start, I'm asked constantly by the terminal for my password when making any changes or downloads from there.  In addition, I'm asked by my other interfaces and settings programs for the password as well. Since this is a new system, there is much getting apps and changing settings, so to type in my password 3 times every 5 minutes becomes annoying and time consuming. 

So what I'd like is a pointer to a "how to" which tells me how to adequately deal with all these requests and typing in my password to a configuration which is comfortable for me.  I'd like to be able to just sit down and turn on my computer and do whatever I want without having to deal with passwords at all "except online".  I'm the only user this system.

Thanks for all replies.

---

### Post by utnubuuser on 2010-10-30
not sure about the apps, but the terminal can be set up to ask for password only once.

By default it's set up to save the password for 2 or 3 minutes, and you can set it to "no password" with environment variables.

I think the last time I changed the setting I found the info by looking up "sudo" or "sudoers Ubuntu"

It's in the same category as "insults", which can be set as well.  - I'll have a look and see if I can find the specific into again.  

To start your search, google "sudoers"

This link,  [http://www.linuxquestions.org/questions/linux-software-2/no-password-for-sudo-442808/]("http://www.linuxquestions.org/questions/linux-software-2/no-password-for-sudo-442808/") is a start.

the community documentation also list how to get around requiring password for admins
[https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

Password protection is cornerstone of system security...  unless it's a real pain, I'd suggest preserving those security measures.   Since you've got automatic login enabled, you'd probably be better off simply extending your "no password" window in terminal, so you can provide it once per session, then not have to worry about it again for a specified time period. Ease and security.
To do that, in a terminal: **sudo nano /etc/sudoers**
look for the line that says: **Defaults env_reset**
 and change it to: 
**Defaults        env_reset, passwd_timeout=20**

Here's the old thread I found that in:
[http://ubuntuforums.org/showthread.php?t=229309](http://ubuntuforums.org/showthread.php?t=229309)
The "20" is time-in-minutes, so change it whatever suits your needs.

---

### Post by mainerror on 2010-10-31
What you are planing to do it extremely dangerous. Those security measures are there for good especially if your are new to this OS you should consider keeping them.

---

### Post by mikewhatever on 2010-10-31
> **alvinmoneypit said:**
> 
...

I'd like to be able to just sit down and turn on my computer and do whatever I want without having to deal with passwords at all "except online".  I'm the only user this system.

Thanks for all replies.

Use Windows, and save yourself and people here the trouble.

---

### Post by uRock on 2010-10-31
It is all good until your system becomes part of a bot net, because anything that finds its way onto your PC will have root privileges and you won't know anything is there, unless you plan to install and use Snort and/or some other NIDS application.

---

### Post by cariboo on 2010-10-31
Have a look at the [RootSudo]("https://help.ubuntu.com/community/RootSudo") page.

---

### Post by alvinmoneypit on 2010-10-31
Thanks utbuntuuser and cariboo, both very helpful post.

I found the file that utbuntuuser mentioned using "sudo visudo" command as mentioned in one of the links, and was able to make the changes, but how are they saved and how to navigate to the "man" page within that program to find out how to use the syntax?

Thanks, again.  In that folder I had NO time option, it was just "defaults, env_reset"  I added the terms",passwrd_timeout=40", but cannot save them there because I don't know how.  I thought there should be a graphic interface that allows this setup.

---

### Post by cariboo on 2010-11-01
I personally use nano, all the commands are at the bottom of the window, for example, to save your file, press Ctrl-o, to close nano Ctrl-x.

To view man pages for a command I usually just open another terminal.

---

### Post by alvinmoneypit on 2010-11-01
Cariboo,  Thanks for the info.

The file said "#Must be edited with visudo"

From what I read, it's a good thing too.  I tried to post it with "passwd" misspelled.

Thanks everyone for all the info/suggestions on security.  It appears that I find myself more responsible for my own security rather than a system set up for me like windows - I think it is a good thing.  However, I wonder what benefit it is to me to have to enter a password for every single admin task such as starting my firewall software.  Is there such a danger with someone accessing my firewall?  I don't keep ANY sensitive info here, and have no plan do do so (for me sensitive info would be my SS, bank numbers, address).  I keep some docs and some very small spreadsheets and some slideshows, all of which I'd like to make public at some point.  Since I don't browse too much except from where I've gone for many years and only use web based e mail, I don't see much threats.  Since I have some net resources available now for a good part of the day, I was going to look into donating that to research - there may be a problem there I don't know, I don't know that much about it.

If this system will be turned into a bot, I'd think someone would be kind enough to tell me and I'm sure they'd find the pickin's here slim indeed.
But I do get the security point now, thanks.

---

### Post by cariboo on 2010-11-01
The first time you run visudo, you are given a choice of up to four editors. For the casual user, nano is much easier to use, as you don't have to memorize any commands.

---

