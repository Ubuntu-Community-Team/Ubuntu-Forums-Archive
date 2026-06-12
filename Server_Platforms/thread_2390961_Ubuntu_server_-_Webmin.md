---
title: "Ubuntu server - Webmin"
date: 2018-05-04
forum: Server Platforms
---

### Post by linuxservernewbie on 2018-05-04
Hi,

Think I'm just really stupid here, but for the life of me I can't make Webmin work. It's a new Ubuntu server.
```
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:56 and /etc/apt/sources.list.d/webmin.list:1
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:56 and /etc/apt/sources.list.d/webmin.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:56 and /etc/apt/sources.list.d/webmin.list:1
W: Target Translations (contrib/il8n-Translation-en_US/Packages) is configured multiple times in /etc/apt/sources.list:56 and /etc/apt/sources.list.d/webmin.list:1
W: Target Translations (contrib/il8n-Translation-en/Packages) is configured multiple times in /etc/apt/sources.list:56 and /etc/apt/sources.list.d/webmin.list:1
E: Unable to locate package webmin
```

I''ve been through both the Sources file and the Webmin file and it's only in there once? And it can't locate it? Anybody help please? (It's remote by 1&1 cloud server system)
Thanks in advance

---

### Post by slickymaster on 2018-05-04
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2018-05-04
I didn't think webmin was a supported package.  You'll need to use a PPA or install from source.
After adding the PPA, do an apt update/apt upgrade/apt install webmin round.

However, you might want to reconsider using webmin.  Search these forums for multiple reasons against using it.

---

### Post by linuxservernewbie on 2018-05-04
> **slickymaster said:**
> Thread moved to **Server Platforms** for a better fit
Thank you :)

> **TheFu said:**
> I didn't think webmin was a supported package. You'll need to use a PPA or install from source.
After adding the PPA, do an apt update/apt upgrade/apt install webmin round.

However, you might want to reconsider using webmin. Search these forums for multiple reasons against using it.

What do you recommend? I want to use a GUI to make my life easier instead of PuTTY. XRDP doesn't seem to work.

---

### Post by TheFu on 2018-05-04
I use ssh and ansible for managing my 20-30 servers. 
No Windows used for that here.  The GUI options just don't provide all the required functionality that I need.

Perhaps if you shared which ubuntu release, someone with that one could help?

The other questions really need their own thread each, so someone using those tools might see it.  1 question, 1 thread is how it works here.

Sorry. This doesn't help you at all.

---

### Post by Tadaen_Sylvermane on 2018-05-09
GUI actually makes it harder in my experience. People just want it because it's all they know with windows. With a cli only environment, granted the commands can take a bit to sort out but the efficiency is second to none. You can do things 100x faster with a cli than with a gui. Best to learn to use it rather than hide from it. You will be better off in the long run.

Also depending on the tasks you regularly perform through the gui you can probably write a script for each one, just call the script as needed and it will do the rest. Personally I don't follow the one thing and do it well idea to much with my scripts. I have a single master script using a case structure for everything. It's sloppy and needs to be separated. Pushing 464 lines currently. But it works and most of the calls are on the crontab. Don't need to run much of it manually.

---

### Post by LHammonds on 2018-05-11
I prefer not having a desktop-like GUI.  It adds a large surface area of attack and increases the risk of my server being compromised.

However, I understand where you are coming from though.  I manage several Linux servers and do not remember all the various commands that have to be used and are unique to each box.

That is why I create Bash scripts and a "dialog" menu to wrap them up all quite nicely.  The menu looks almost identical on all machines and all I do is type "opm" to bring up the operator menu which presents the most common tasks I perform on each server...such as restart the services (no matter what those services are), reboot the server, shutdown the server, check disk space, check running processes, etc.

I've shared how to create such a menu here: [Operator Menu]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p624") and the [various scripts]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p621") used in it.

So, most of the time, I just need to login, type "opm" and use the menu to do the things I normally do (without having to remember or lookup the peculiar commands/switches)

[img]http://hammondslegacy.com/images/linux/Ubuntu-OperatorMenu.png[/img]

LHammonds

---

