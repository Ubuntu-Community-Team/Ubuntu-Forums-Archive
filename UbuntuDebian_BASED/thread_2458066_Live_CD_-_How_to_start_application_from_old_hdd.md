---
title: "Live CD - How to start application from old hdd"
date: 2021-02-15
forum: Ubuntu/Debian BASED
---

### Post by 3sawyer on 2021-02-15
Hi dear ubuntuforums people, my hdd is dying. 
It doesnt start normal. I put my Installation DVD inside to backup some files and documents. 
It starts the Test Environment.
I can open the hdd like an external drive.
But i need to start Brave Browser to save my rewards and Bookmarks.
Can somebody tell me how to start it?
I guess i need to start from terminal?
BraveBrowser files are saved in /dev/sda1
and then opt/brave.com/brave

Screenshots:
[https://ibb.co/HqSmtYH](https://ibb.co/HqSmtYH)
[https://ibb.co/Y7N9NCV](https://ibb.co/Y7N9NCV)

---

### Post by howefield on 2021-02-15
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by CelticWarrior on 2021-02-15
Find the hidden folder within your userspace and backup that one then restore it to your new installation. This is how it's done with any browser, not running it as you want because it can't be.

Also you should have maybe configured sync while it was possible, that would save you a lot of time right now: [https://support.brave.com/hc/en-us/articles/360021218111-How-do-I-set-up-Sync-](https://support.brave.com/hc/en-us/articles/360021218111-How-do-I-set-up-Sync-)

---

### Post by 3sawyer on 2021-02-21
> **CelticWarrior said:**
> Find the hidden folder within your userspace and backup that one then restore it to your new installation. This is how it's done with any browser, not running it as you want because it can't be.

Also you should have maybe configured sync while it was possible, that would save you a lot of time right now: [https://support.brave.com/hc/en-us/articles/360021218111-How-do-I-set-up-Sync-](https://support.brave.com/hc/en-us/articles/360021218111-How-do-I-set-up-Sync-)

I saved the Brave Folder from .config. 
Bought a new HDD and now im trying to replace the new installation of Brave. But its a different structure... 
Maybe because i was using 18.04 and now the new installation is 20.04? 

I tried installing with the Software-Center but it was installed in snap folder.
Then i removed BraveBrowser again and tried with terminal installation like this:
> sudo apt install apt-transport-https curl gnupg
curl -s [https://brave-browser-apt-release.s3.brave.com/brave-core.asc](https://brave-browser-apt-release.s3.brave.com/brave-core.asc) | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
echo "deb [arch=amd64] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update
sudo apt install brave-browser

But i cant paste my saved files because the installation structure looks different... Any ideas?
Tomorrow i can try to connect my old (dying) HDD with external adapter to my Laptop. Maybe i can do something with that? Start the "old" Brave Browser from the external HDD?

---

### Post by 3sawyer on 2021-02-23
How can i open Folders on my new HDD that are located above home/ directory? 
I can only copy paste files in home/.config/BraveSoftware but there are many more Files when i search for Brave on my external HDD.
[https://imgur.com/a/RoVSmXu](https://imgur.com/a/RoVSmXu)

---

### Post by yancek on 2021-02-23
>  But i cant paste my saved files because the installation structure looks different... Any ideas?

You will need to explain what you mean by the above statement, what's different?

>  How can i open Folders on my new HDD that are located above home/ directory? 

Writing/copying to any location outside your /home/user directory generally requires root permissions, use sudo.  Are you still just trying to copy various file for the Brave browser?

---

### Post by 3sawyer on 2021-02-24
> **yancek said:**
> You will need to explain what you mean by the above statement, what's different?



Writing/copying to any location outside your /home/user directory generally requires root permissions, use sudo.  Are you still just trying to copy various file for the Brave browser?

Yes im still just trying to copy the files because im a Linux noob :P 
I tried another way but it didnt work. I started Laptop with Live CD (USB Stick) then i thought i can open directory outside of /home/user but i cant paste the files. 
[https://imgur.com/a/LV0QDJf](https://imgur.com/a/LV0QDJf)

You can see that i have my new HDD 1.0 TB Volume in the Background and the old dying HDD which i cant boot from anymore in the foreground. 160GB Volume. I tried copy paste but i cant paste the files to the new HDD.

You said i need to use sudo, so i guess i have to write everything in the terminal? 
Can you maybe tell me what to write exactly?

My main problem is my old hdd doesnt boot. When i open the grub menu with holding shift and use dpkg it doesnt work because it says i have custom ppa or something. Its explained in another Thread: [URL="https://ubuntuforums.org/showthread.php?t=2458019"]https://ubuntuforums.org/showthread.php?t=2458019
[/URL]
I dont know if copy pasting the Brave Files even works. The best thing would be if i could boot one more time from my old dying HDD and open Brave and sync it or make a backup from my Bookmarks etc.

---

### Post by yancek on 2021-02-24
If the files you want to copy are on sda1 as iyou indicate above, then you also need to find out which drive/partition the new Ubuntu is on if you are still using the DVD.  If you can boot into the new Ubuntu, you can simply create a mount point for the old drive partition, then mount it and then as root (using sudo) copy the files from the old drive to the new.  I'm not sure all this is necessary.  I don't use Brave browser but generally if all you want is Bookmarks and related, you should be able to do that as explained in post 3 above.

Create a mount point for sda1:

```
sudo mkdir /mnt/sda1
```

Mount sda1:

```
sudo mount /dev/sda1 /mnt/sda1
```

Navigate to sda1 and whichever directory you want to copy files from, from the image you posted:

>  cd /mnt/sda1/opt/brave.com/

Copy the folders/files from that location to whichever location you want on your booted system.  On your installed Ubuntu, enter sudo su and enter your primary user password when prompted then:

> cp brave/* /path to new location

I don't see anything different about the structure of the system you mention.  I woulds think this would all not be necessay, simply copy whatever config files in your /home/user directory for Brave browser from the old /home/user to the new /home/user.i

---

### Post by 3sawyer on 2021-02-24
You were right. All this was not necessary. It worked now. I copied the files and now i have all my Bookmarks and even the Brave Rewards on my new HDD!
The problem was when i tried to open Brave there was a prompt on screen for 1 sec and disappeared. The First few times i didnt saw it. I then made a screenshot to read what it said:
All i had to do was to click fast enough on "Unlock Profile and Relaunch"
[https://imgur.com/a/dn1IfCK](https://imgur.com/a/dn1IfCK)

Thank you guys for your patience and help.

---

