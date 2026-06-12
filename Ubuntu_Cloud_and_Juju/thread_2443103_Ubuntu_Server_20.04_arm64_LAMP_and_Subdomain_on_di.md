---
title: "Ubuntu Server 20.04 arm64 LAMP and Subdomain on different IP redirect."
date: 2020-05-11
forum: Ubuntu Cloud and Juju
---

### Post by ryanthetide on 2020-05-11
Hi! I'd love some help on how I should configure my devices! I have 3 main purposes for this webserver, host 4 webpages (2 on the Main Pi, 1 on a second Pi, 1 on a Windows Computer), 1 share webpage (just the default directory page will do) and finally port forward another devices ports to a subdomains, my final goal in my modems port forward/firewall settings is to have the ports 80, 443, 22, 21, 25565, 25570, 3700, 19132 opened however I must do so. To help as much as possible though being a pain here's my current configuration & devices:

- Raspberry Pi 3B+ arm64 (Running the latest Ubuntu Server 20.04) - IP: 10.1.1.2)
  - PHP 7.3
  - Apache2.4.41
  - MariaDB 10.3.22
- Windows Server Computer (Running the latest Windows Server 2019 - IP: 10.1.1.3)
  - XAMPP 7.4.5 VC15
  - PHP 7.4
  - Apache2.4.41
  - MariaDB 10.4.10
- Raspberry Pi 2B+ armhf (Running the latest Ubuntu Server 20.04) - IP: 10.1.1.4)
  - PHP 7.3
  - Apache2.4.41
  - MariaDB 10.3.22

Pi Hostname has been set to: RTT-Sydney
Pi Username has been set to: OSG
PC Hostname has been set to: SPC-RTT-Sydney
PC Username has been set to: OSG
Networks Public URL/DNS-Name is: osgs.net
SSH Keys are all encrypted and security is a massive must for all of this.

This is a server that I wish to run 24/7 it has cooling and a direct ethernet to the router hidden in a hollow wall.
I am also doing a clean install tonight of Ubuntu to start from scratch as I wish this to be as elegantly integrated as possible:

Webpage           - [http://osgs.net](http://osgs.net) & [https://osgs.net](https://osgs.net) (On Pi, Directory /var/www/sydney)
Webpage           - rtt.osgs.net (On Pi, Directory /var/www/ryanthetide)
Webpage           - curl.osgs.net (On Pi, Directory /home/Public/share)
Webpage           - videos.osgs.net (Internal IP: 10.1.1.3, Windows Running [XAMPP]("https://www.apachefriends.org/index.html") on Ports 80 & 443, Directory C:\Windows\Drives\Files\Videos)
Webpage           - owncloud.osgs.net (On Pi2 running [ownCloud]("https://owncloud.org/"), Internal IP: 10.1.1.4 on Ports 80 & 443, Directory /var/www/ownCloud)
Port Subdomain - bs.osgs.net ((Internal IP: 10.1.1.3, Windows Running [BeatSaberMultiplayer]("https://github.com/andruzzzhka/BeatSaberMultiplayer") on port 3700)
Port Subdomain - ftp.osgs.net (Internal IP: 10.1.1.3, Windows [Filezilla]("https://filezilla-project.org/") Server on port 21)
Port Subdomain - mc.osgs.net (Internal IP: 10.1.1.3, Windows Running [CatServer]("https://github.com/Luohuayu/CatServer") on port 25565)
Port Subdomain - mcd.osgs.net (Internal IP: 10.1.1.3, Windows Running [CatServer]("https://github.com/Luohuayu/CatServer") on port 25570)
Port Subdomain - mcb.osgs.net (Internal IP: 10.1.1.3, Windows Running [MinecraftBedrockServer]("https://www.minecraft.net/download/server/bedrock") on port 19132)

Note the videos portion is secured with a login and is a personal site that I wish to access with a few family members.

Once again thank you so much for reading any advice would be appreciated or is my moderate noob knowledge didn't elaborate enough let me know to explain in more detail! :)

---

