---
title: "How do I host EyeOS myself?"
date: 2010-06-07
forum: Server Platforms
---

### Post by IAmAnarch on 2010-06-07
Ok, so I am the president/sysadmin of a small group that's spread out across the region and needs cloud services for communication and stuff. I came across this great open-source script called EyeOS ([http://eyeos.org]("http://eyeos.org/")) a few months ago and found a free hosting provider to go with it. After playing around on the demo setup, I spent quite a bit of time figuring out how to get it set up on a hosting provider via FTP. Once that was set up, things ran smoothly for a few weeks until one day I logged into my user CP and saw a notice that they were shutting down and selling their server to a new adult video site and that all sites would be deleted in like 72 hours. I could never find another hosting provider that could give me the space I needed without ads for free, so I had this crazy idea of hosting it myself. I have an older box with Lucid Desktop Edition that would be great for a server (I mainly use my laptop anyway), but there are a few problems:

[LIST]
[*]I have very little experience with Linux (although I'm great w/ Windows).
[*]I need Apache and PHP but I have no idea how to install them (and make them work together) and where to put the files to "serve." Knowing some administrative commands would help.
[*]My ISP blocks incoming connections on port 80. I need help deciding on an alternative port besides the blaringly obvious port 8080 that won't conflict with anything important. I'll most likely link to it from our homepage on Google Sites (with a free .tk domain) so it doesn't need to be easy to remember.
[/LIST]
Can somebody *please* help me?

---

### Post by cariboo on 2010-06-07
You need to install the LAMP stack. You can install it two ways, from a terminal type:

```
sudo tasksel
```

use the arrow keys to navigate, and select LAMP for installation, or go to System->Administration->Synaptic Package Manager->Edit->Mark Packages by Task, then select LAMP for installation.

I would suggest you learn how to administer the server via the command line, as using the gui is just another way for bad guys to gain access to the server.

---

### Post by IAmAnarch on 2010-06-08
> **cariboo907 said:**
> You need to install the LAMP stack. You can install it two ways, from a terminal type:

```
sudo tasksel
```

use the arrow keys to navigate, and select LAMP for installation, or go to System->Administration->Synaptic Package Manager->Edit->Mark Packages by Task, then select LAMP for installation.

I would suggest you learn how to administer the server via the command line, as using the gui is just another way for bad guys to gain access to the server.
Do you have any tutorials to suggest to me? I also use it as a secondary computer, so a good amount of administration will be done locally, but I'd like to do it over SSH.

---

