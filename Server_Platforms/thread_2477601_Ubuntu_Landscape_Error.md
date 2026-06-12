---
title: "Ubuntu Landscape Error"
date: 2022-07-31
forum: Server Platforms
---

### Post by andrew991 on 2022-07-31
Hello,

My websites were running fine until I rebooted my server.
Now every time I enter on any website hosted on the server, I get this error:
[COLOR=#333333][FONT=&quot][h=1]Oops![/h][h=5]Sorry for the inconvenience. Please contact your system administrator for more information.[/h][/FONT][/COLOR]
[COLOR=#333333][FONT=&quot][h=3]Landscape is unavailable[/h]Service will resume shortly.
[/FONT][/COLOR]

I searched on internet about this error and I found that if I reinstall landscape server it would help.

So I ran this command:

[B]sudo apt-get install --reinstall landscape-server-quickstart
[/B]
and I get an error: [Imgur: The magic of the Internet]("https://imgur.com/a/Wl0vEOL")

Any help please what to do?

---

### Post by andrew991 on 2022-08-01
Hello, even thought no one replied, maybe someone will find this reply usefull.

Those commands in SSH fixed the problem:

sudo add-apt-repository -u ppa:landscape/17.03
sudo apt-get install landscape-server-quickstart
sudo apt-get update; sudo apt-get upgrade -y
sudo apt autoremove
sudo apt remove apache2.*
dpkg -S `which apache2`
apt update && apt upgrade
apt autoremove
apt autoclean
apt update && apt upgrade
reboot

---

