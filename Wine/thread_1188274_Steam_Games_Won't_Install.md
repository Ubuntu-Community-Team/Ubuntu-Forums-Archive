---
title: "Steam Games Won't Install"
date: 2009-06-15
forum: Wine
---

### Post by Cadeyrn on 2009-06-15
So, what I did here was I took the SteamApps folder from my old Windows machine and put it in my WINE's Steam installation. Steam recognizes every app in there, and the free mods work fine as well, but the paid apps that would be under my account name folder of the SteamApps folder are under the Not Installed status. Not only are they all installed in the SteamApps folder that it recognizes, but when I try to install any one of them, it works perfectly until I click on the finish button. It stays in the status of Not Installed. I can't get any of them to install.

---

### Post by LinuxGuy1234 on 2009-06-15
You can remove the SteamApps folder and install the games from CDs or whatever again.

---

### Post by Cadeyrn on 2009-06-15
Nope, that was going to be my last resort, but it made no difference just now when I tried it.

NOTE: I still have my SteamApps saved because I cut it instead of deleting it.

Hey! I just noticed a difference: Steam made the folders that it would've made during the installation process. The only thing that's going on here is it fails to guide the app through the transition from Not Installed to Downloading, and therefore refusing to download or update or notice the app folder and say 100% - Ready.

---

### Post by LinuxGuy1234 on 2009-06-15
> **Cadeyrn said:**
> Nope, that was going to be my last resort, but it made no difference just now when I tried it.

NOTE: I still have my SteamApps saved because I cut it instead of deleting it.

Hey! I just noticed a difference: Steam made the folders that it would've made during the installation process. The only thing that's going on here is it fails to guide the app through the transition from Not Installed to Downloading, and therefore refusing to download or update or notice the app folder and say 100% - Ready.

I hear that 1.1.12 versions of wine are really borked. Compare the output of (in the text of the dialog):
```
wine --version | xmessage -file - -center
```
to 1.1.12. If so, URGENTLY add Wine's Ubuntu repos to Synaptic and upgrade wine now.

---

### Post by Cadeyrn on 2009-06-15
Wow... You just really helped me out. dude. By a ********. A bunch of my favorite games were acting like crap in my WINE and I now I know why. This whole time I thought I compiled WINE from my saved 1.22 tar.bz2, but I must have gotten it from the normal Ubuntu repos. because I'm running 1.0.1!

---

