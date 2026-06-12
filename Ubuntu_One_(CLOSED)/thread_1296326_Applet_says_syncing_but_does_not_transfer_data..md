---
title: "Applet says syncing but does not transfer data."
date: 2009-10-20
forum: Ubuntu One (CLOSED)
---

### Post by adamis on 2009-10-20
When I first login to my computer the Ubuntu One tray applet immediately crashes with I believe an authentication error. When I look in the process list though I see that both the sync daemon and the applet are still running however the applet does not appear in the tray. About 20 minutes after logging in the applet will suddenly appear in the tray and say syncing files with the up and down arrows. Then after a few minutes it changes to the disk with cloud icon. If I hover my mouse over the tray icon it says "updating files" however if I click on the tray icon it will say "files are up to date". 

Sometimes if I leave the computer alone for several hours it will eventually start uploading files which I can verify by network activity and the tray applet will list how many files it's uploaded and how many more to go. There does not seem to be any pattern though on how long to wait for this and sometimes it seems like it never does. Right now my laptop has been on for almost two hours and yet it hasn't uploaded a single file.

At first I figured that the sync-daemon has to make a list of what needs to be synced and that's why it would take a long time for it to start uploading. However in this case the sync-daemon is no longer taking any resources and it's been over two hours. I do have a lot of data (16gb) consisting of a typical "Documents" folder with lots of files and several folders within folders format. Not sure if this is coming into play or not. 

I have two identical laptops with identical installs of Kubuntu 9.10. Both of these laptops have this same problem. I have been trying to get Ubuntu One to upload all of my data to the server for several days now and out of 30gb of data it's only transferred just under 2gb. Has anyone else seen this same issue and are there any suggestions?

Thanks...

---

### Post by joshuahoover on 2009-10-22
> **adamis said:**
> When I first login to my computer the Ubuntu One tray applet immediately crashes with I believe an authentication error. When I look in the process list though I see that both the sync daemon and the applet are still running however the applet does not appear in the tray. About 20 minutes after logging in the applet will suddenly appear in the tray and say syncing files with the up and down arrows. Then after a few minutes it changes to the disk with cloud icon. If I hover my mouse over the tray icon it says "updating files" however if I click on the tray icon it will say "files are up to date". 

Sometimes if I leave the computer alone for several hours it will eventually start uploading files which I can verify by network activity and the tray applet will list how many files it's uploaded and how many more to go. There does not seem to be any pattern though on how long to wait for this and sometimes it seems like it never does. Right now my laptop has been on for almost two hours and yet it hasn't uploaded a single file.

At first I figured that the sync-daemon has to make a list of what needs to be synced and that's why it would take a long time for it to start uploading. However in this case the sync-daemon is no longer taking any resources and it's been over two hours. I do have a lot of data (16gb) consisting of a typical "Documents" folder with lots of files and several folders within folders format. Not sure if this is coming into play or not. 

I have two identical laptops with identical installs of Kubuntu 9.10. Both of these laptops have this same problem. I have been trying to get Ubuntu One to upload all of my data to the server for several days now and out of 30gb of data it's only transferred just under 2gb. Has anyone else seen this same issue and are there any suggestions?

Thanks...

My apologies for the odd behavior you've been seeing from Ubuntu One and the inconvenience it has caused you. We did some server updates recently that should help address many, if not all of the issues you've listed. If you continue to have problems, please report a bug by right-clicking on the Ubuntu One client and selecting "Report a Problem". In the bug description, please include any additional info (like you have here) that you think might be helpful.

Thank you,

Joshua

---

