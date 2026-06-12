---
title: "Not Happy With Ubuntu 22 UPDATE: GENERAL DISCUSSION CHAT:"
date: 2023-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by whysohard2 on 2023-10-23
general discussion: too many apps not working from updating from 20 to 22 like "Tor Browser" , Falcon Web Browser and More
Desktop icons still will not show 
Many new addons flagged by chkrootkit and rkhunter

how is your experience going? general discussion 

will update to 23 hoping helps
- sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades
sudo apt update
sudo apt upgrade
sudo do-release-upgrade
sudo do-release-upgrade -d
sudo systemctl reboot

as if being trolled by a higher authority with too much money in that the name "Jammy Jellyfish" is more of a jellyfish getting in a jam or problem than having a jam or fun , lol

---

### Post by ian-weisser on 2023-10-23
On my work Desktop, 22.04 has performed solidly for almost 1.5 years. 23.04 has been stable and easy from day 1. 23.10 starts next week.

A minor problem with Thunderbird at 22.04 release time. Fixed with a bug update about two months later.

Let's check the 22.04 server: Uptime 94 days. Hmmm, I should probably reboot it.

---

### Post by readableauthor on 2023-10-24
I solved the lack of icons with this solution:
[https://askubuntu.com/a/1406376/1592865](https://askubuntu.com/a/1406376/1592865)
Tor Browser from the official website works fine for me.

---

### Post by coffeecat on 2023-10-24
> **whysohard2 said:**
> 
Many new addons flagged by chkrootkit and rkhunter

I presume you are referring to this thread - [https://ubuntuforums.org/showthread.php?t=2491420](https://ubuntuforums.org/showthread.php?t=2491420) - in which you were told by two very experienced forum members that you were seeing false positives. However, it appears that you have not revisited that thread and therefore not read those informative posts from which you could have learnt much. It is an important part of forum netiquette that, if you start a discussion or support thread, you read any replies and comment on them. You appear to have started a discussion and then simply wandered away. Is it your intention to do the same for this thread?

---

### Post by grahammechanical on 2023-10-24
I have only experienced one issue with 22.04. A Windows app that I run through WINE does not load. A dialog appears saying it experienced an error. I have no problem using this Windows app through WINE in Ubuntu 20.04 or 23.10.

So, to be sure that I can still use this app I have set 20.04 to have Extended Security Maintenance (ESM). I will most likely bypass 22.04 for 24.04. I have no problems running my two non-Linux apps in 23.10. So, I am confident that I will still be able to run them in 24.04 LTS. I will test this out by converting 23.10 into 24.04 development version and testing things out as development progresses.

Regards

---

### Post by whysohard2 on 2023-10-25
Thanks for the info on Thunderbird update

---

### Post by whysohard2 on 2023-10-25
Thanks for the icon fix reference, found a few like that, including removing the software store and related, then reinstalling as another option, also repairing 

examples: 
sudo apt-get dist-upgrade
sudo apt-get purge openvpns


sudo apt apt-get update && sudo apt-get install --reinstall tcd
sudo apt-get update && sudo apt-get upgrade; sudo apt update && sudo apt upgrade

etc 
etc

---

### Post by whysohard2 on 2023-10-25
> **coffeecat said:**
> I presume you are referring to this thread - [https://ubuntuforums.org/showthread.php?t=2491420](https://ubuntuforums.org/showthread.php?t=2491420) - in which you were told by two very experienced forum members that you were seeing false positives. However, it appears that you have not revisited that thread and therefore not read those informative posts from which you could have learnt much. It is an important part of forum netiquette that, if you start a discussion or support thread, you read any replies and comment on them. You appear to have started a discussion and then simply wandered away. Is it your intention to do the same for this thread?


The other thread was a focus on rkhunter or chkrootkit support, in a different category, reminder check thread titles for specifity, 
this thread is a "general chat" in other words, "[CENTER][COLOR=#C61919]this sub-forum is for chat, not support – hence the name. If you need technical help, please post in an appropriate support sub-forum" i.e refer to the other forum for help/solutions

[/COLOR][/CENTER]netiquette

thank you everyone for the chat here and support there 
[LIST]
[/LIST]

---

