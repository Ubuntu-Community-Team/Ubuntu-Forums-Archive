---
title: "World of Warcraft Disconnects Constantly."
date: 2010-04-03
forum: Wine
---

### Post by lubberlick on 2010-04-03
A couple days ago I started having this problem where I am able to play wow for only a few minutes before it disconnects. Then I must restart the wow client in order to login again or I just get automatically disconnected from server. This happens on both of my Ubuntu machines and started happening at the same time. I can reboot to my Windows Vista partition and everything runs smooth. Ventrilo also runs smooth in both Vista and Ubuntu/Wine. 
 
I have tried different versions of wine. I have tried disabling all addons in the game. My assumption is that a recent update of Ubuntu has caused this problem. Any suggestions would be greatly appreciated.

(appologies for posting a wine issue here, im not getting a lot of responces at wineHQ)

---

### Post by ubunterooster on 2010-04-03
Do you have the beta? or stable? I find the beta to have more stability ironicly. [You need to edit sources to get the beta]

---

### Post by lubberlick on 2010-04-03
I have tried 1.0.1 and 1.1.42 and 1.1.41. Before roughly April 2, i was running perfectly fine. This definitely seems to be something blizzard has changed with client-server communication as I have now taken my laptop to another connection at my work and am experiencing the same issue. This makes 3 computers experiencing the exact same issue btw. Again however Windows works flawlessly.

keep the suggestions coming.

---

### Post by ABE3K on 2010-04-16
I'm having the same behavior here too, this is the message that shows up in the terminal when the disconnects happen:
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000

I'm not sure what could've cause this. I hope some tips could be given regarding this issue.

---

### Post by NlaakALD on 2011-10-20
> **lubberlick said:**
> A couple days ago I started having this problem where I am able to play wow for only a few minutes before it disconnects. Then I must restart the wow client in order to login again or I just get automatically disconnected from server. This happens on both of my Ubuntu machines and started happening at the same time. I can reboot to my Windows Vista partition and everything runs smooth. Ventrilo also runs smooth in both Vista and Ubuntu/Wine. 
 
I have tried different versions of wine. I have tried disabling all addons in the game. My assumption is that a recent update of Ubuntu has caused this problem. Any suggestions would be greatly appreciated.

(appologies for posting a wine issue here, im not getting a lot of responces at wineHQ)

Same exact problem. Ubuntu 11.10, everthing updated to latest revisions. I get dropped about every 10-15 minutes. ALT+F4 and re run wow client and I'm good for another 10-15 minutes. My zoom stays connected with excellent status and my son with windows 7 stays connected. Basically can't play wow on Ubuntu and that's my main application :-(

HELP! I don't want to go back to windows...

---

### Post by Soulcage on 2011-10-21
Is it a firewall problem ubuntu uses ufw I think, you can install gufw then allow the ports. Though I'm not sure if this is even needed.

---

### Post by nothingspecial on 2011-10-21
This thread is too old.

Closed.

---

