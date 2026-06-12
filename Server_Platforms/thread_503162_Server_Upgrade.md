---
title: "Server Upgrade"
date: 2007-07-17
forum: Server Platforms
---

### Post by lugos on 2007-07-17
Hello,

I would like to upgrade my 6.06 server to the latest version.  However, I use it as a web server and have some things configured that I cannot lose (dynamic ip dns update for example).  I also have Xubuntu as the desktop and would also like to keep that.  Would an upgrade be possible?  If so, how can I go about doing so?

Thanks in advance for the assistance.

---

### Post by koenn on 2007-07-17
The supported upgrade paths are usually mentions in the release notes, so I suppose that's the first place you look. 

Then, to keep any custom configuration, you can take a copy of your /etc. 
You can then either copy them back, or use the as reference,  should anything have gone missing during the upgrade. 

I'm making it a habbit to create a file (/etc/timestamp) after an install so that later i can find the config files that I've modified by running something like 
'find  [...]  -newer /etc/timestamp"
It's not going to help you now, but it may help for the next time.

---

### Post by lugos on 2007-07-17
> **koenn said:**
> The supported upgrade paths are usually mentions in the release notes, so I suppose that's the first place you look. 

Then, to keep any custom configuration, you can take a copy of your /etc. 
You can then either copy them back, or use the as reference,  should anything have gone missing during the upgrade. 

I'm making it a habbit to create a file (/etc/timestamp) after an install so that later i can find the config files that I've modified by running something like 
'find  [...]  -newer /etc/timestamp"
It's not going to help you now, but it may help for the next time.

This would be the first time I do this, where would I copy it to?

---

### Post by az on 2007-07-17
> **lugos said:**
> Hello,

I would like to upgrade my 6.06 server to the latest version.  However, I use it as a web server and have some things configured that I cannot lose (dynamic ip dns update for example).  I also have Xubuntu as the desktop and would also like to keep that.  Would an upgrade be possible?  If so, how can I go about doing so?

Thanks in advance for the assistance.
If you installed things from the repos as opposed to third-party sources, then you should be able to dist-upgrade flawlessly.  You do need to dist-upgrade sequentially to Edgy and then the Feisty.

Your dynamic dns should not stop working.  It may stop and restart for a moment as the new version of the client get's installed (if there is a new version - otherwise it will just keep working)

Usually, the only time people have trouble with dist-upgrades is with desktop applications from sources other than the Ubuntu repositories.

---

### Post by darkog on 2007-07-17
> **lugos said:**
> Hello,

I would like to upgrade my 6.06 server to the latest version. .

Why? Is something not working in your current setup? Is there a feature that you need and plan to use which is available in the upgrade only?

---

### Post by koenn on 2007-07-18
> **lugos said:**
> This would be the first time I do this, where would I copy it to?
Anywhere suitable. A USB external drive ? Thumb drive ?
I have a couple of machines arround the house, 1 acts as a server, so I keep a copy there. If you have multiple partitions, you can also make a copy on one of the partitions that won't be involved in the upgrade (/home maybe ?) ....

---

### Post by lugos on 2007-07-19
> **az said:**
> If you installed things from the repos as opposed to third-party sources, then you should be able to dist-upgrade flawlessly.  You do need to dist-upgrade sequentially to Edgy and then the Feisty.

Your dynamic dns should not stop working.  It may stop and restart for a moment as the new version of the client get's installed (if there is a new version - otherwise it will just keep working)

Usually, the only time people have trouble with dist-upgrades is with desktop applications from sources other than the Ubuntu repositories.

Are these commands that I need to execute?  Is there a tutorial or documentation I can follow on upgrading?  I did it once for my Ubuntu Desktop, but that was so long ago that I can't really remember.

---

### Post by lugos on 2007-07-19
> **darkog said:**
> Why? Is something not working in your current setup? Is there a feature that you need and plan to use which is available in the upgrade only?

Well my desktop is acting a little flaky.  When I click Applications -> Quit -> Shutdown, I get logged off and get sent to the logon page.

---

