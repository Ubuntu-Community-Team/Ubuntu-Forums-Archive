---
title: "How to enlarge terminal fonts for my 4k TV screen?"
date: 2021-04-09
forum: Server Platforms
---

### Post by mortalkorona on 2021-04-09
Hi I just installed **Ubuntu Server 20.04.2** connected to my **4k TV screen**. I would like to enlarge the font size on the terminal screen. How can I accomplish this?

I've seen some YouTube videos describe this but they mainly use the Ubuntu Desktop GUI to fix that. Or they describe commands used on other Linux distros which doesn't seem to work on Ubuntu. I'm thinking about using the **setfont** command in my **.bash_aliases** file like this but don't understand how to preview what fonts I can use in the terminal?

This is the **.bash_profile/.basrc** example code I saw somebody use for another distro in a YouTube video.

```

if [ $TERM = linux ]
  then
  setfont sun12x22
fi

```

---

### Post by CelticWarrior on 2021-04-09
Is there a reason to install server specifically?
Personally I don't see any point in installing Ubuntu server and then use it with a 4K TV but you might have some reason?

---

### Post by LHammonds on 2021-04-09
I also think there is a discrepancy in what you are trying to accomplish.  A headless server (without a GUI) typically does not even have a monitor plugged in.

I would use a laptop/pc to connect to the TV, then use PuTTY to SSH into the server...you can specify font/size that way.

I have never tried to connect anything more than a default-sized monitor to a server so I never needed to modify those kinds of settings.  Sorry I don't have that solution for you.

LHammonds

---

### Post by mortalkorona on 2021-04-09
My Intel NUC media pc with Ubuntu Desktop was already setup to my TV from before. With my new fulltower Ubuntu Server placed next to the NUC and TV it was just more convenient to connect it to the TV for quick configurations.

Don't know how to setup the wireless USB stick to my network yet with a headless Ubuntu. And so much cables to deal with using my old laptop. It was just more convenient to plug in a HDMI cable to the TV and start firing away.

----------------------------------------------------------------------------------------------------------

[SIZE=4]**Enlarge font size from Terminal for 4k TV**[/SIZE]

Anyways I found the right guide to make the **Terminal font size** easier to read on the 4k TV. :shock:
[https://ostechnix.com/how-to-change-linux-console-font-type-and-size/](https://ostechnix.com/how-to-change-linux-console-font-type-and-size/)

**Step 1**
```
$ sudo dpkg-reconfigure console-setup
```

**Step 2,** select UTF-8.

**Step 3,** select Guess optimal character set.

**Step 4,** select Terminus.

**Step 5,** select 16x32 (framebuffer only)

[COLOR="#DAA520"]** Done!**[/COLOR]

----------------------------------------------------------------------------------------------------------

[SIZE=4]**Connect to WiFi from the Terminal using nmtui**[/SIZE]

[https://www.osradar.com/how-to-connect-to-wifi-from-the-terminal-in-ubuntu/](https://www.osradar.com/how-to-connect-to-wifi-from-the-terminal-in-ubuntu/)

**Step 1**
```
$ nmtui
```

**Step 2,** select Activate a connection.
Wait 5 minutes for the WiFi USB stick to scan all available networks in case your intended router doesn't show up.

**Step 3,** type in the password for the SSID network.

[COLOR="#DAA520"]** Done!**[/COLOR]

---

