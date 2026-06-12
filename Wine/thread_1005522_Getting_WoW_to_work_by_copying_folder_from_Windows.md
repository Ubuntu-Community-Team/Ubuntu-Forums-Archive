---
title: "Getting WoW to work by copying folder from Windows"
date: 2008-12-08
forum: Wine
---

### Post by theandyman on 2008-12-08
Hi, I'm new to the forum and this is my first post so I'm sorry if I don't post properly. I've read loads of posts and comments about installing World of Warcraft on Ubuntu linux but I just cannot get it to work. Most of the posts I read involve re-installing it using the original cds which I do not have thanks to a *friend*.

If someone has the time, please could you explain to me, like I'm a 5 year old, the steps I need to take in order to play WoW. I have the latest version of WINE installed and have also installed playonlinux but the latter asks for the installation cds to install.

I thought it would be as simple as installing WINE, making a couple of changes to the WINE config, that I think I've done, and copy over my WoW folder from a windows installation and finally make a couple of changes to the config.wtf file. Mostly the problem I'm having is that wow ends up giving me the critical exception just before it logs in.

Please help. Thanks in advance

---

### Post by Eviljim on 2008-12-09
Ok, heres the first bit.

_Install_

I will assume you can access the drive/partition where you windows installation is located? If not, you will either need to download the client from the Warcraft account page, or install via DVD/CD.

So providing the windows installation is known to be working do the following.

Navigate the windows driver until you find the World of Warcraft folder.(Beware the location on an XP driver could be different to that on a Vista one)

Copy it.

Go to your "home/<username>" folder and press CTRL+H to view all hidden folders.

Go to the .wine folder

Go to the Program Files folder

Copy your Warcraft installation here.

It will take a while.

Then you need to go into the newly copied warcraft folder, then into the WTF folder and edit the config.wtf file there.

Check here [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft") for more in depth information which you may need to do in order to get it working.

The troubleshooting section is found here [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting")

Hope that at least gets you started.

---

