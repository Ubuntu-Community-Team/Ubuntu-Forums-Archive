---
title: "Spotify"
date: 2011-03-09
forum: Wine
---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
i installed wine and spotify,  followed this easy guide [http://www.spotify.com/no/help/faq/wine/](http://www.spotify.com/no/help/faq/wine/) and did everything right, but when i open spotify it lags like crazy like its using 100% cpu, and when i press a song it tells me error "that i dont have sound card drivers so cant play music in spotify" but i am already listening to mp3 and youtube etc without problems so why??

---

### Post by cogadh on 2011-03-09
Doesn't Spotify have a Linux native client? I seem to remember some kind of announcement about that around 8 or 9 months ago. If so, you should really use that instead of messing with trying to run the app through Wine.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
they have, but its only preview version
 this site [http://www.spotify.com/no/download/previews/](http://www.spotify.com/no/download/previews/)
```
**Debian**

 			# 1. Add this line to your list of repositories by 
#    editing your /etc/apt/sources.list
deb http://repository.spotify.com stable non-free

# 2. If you want to verify the downloaded packages,
#    you will need to add our public key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E

# 3. Run apt-get update
sudo apt-get update

# 4. Install spotify!
sudo apt-get install spotify-client-qt spotify-client-gnome-support


```

i cant understand how to install it, what is "list of repositories" ??

---

### Post by cogadh on 2011-03-09
A software repository is the server location you download software packages from in Ubuntu. Ubuntu has its own repositories that it uses for manually installing software as well as for keeping your currently installed software (and OS) up to date. You can add nearly any third party repository you want, which will allow you to install and maintain software not provided by Ubuntu. To add the repository for Spotify, you just need to follow the instructions provided, starting with adding the line listed to your /etc/apt/sources.list file.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
how do i write in the file? cant write nothing or paste the text

---

### Post by cogadh on 2011-03-09
You need to edit it using sudo permissions:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-10
ok thanks it worked:)
only thing that sucked is i get "Spotify linux prewiev is currently not aviable for free/open users" when i wanted to loging.... hahaha :shock:

anyway, how can i uinstall that windows version i installed in wine?

---

### Post by cogadh on 2011-03-10
The easiest way is to delete the .wine directory from your home directory, assuming that you haven't installed anything else in Wine that you want to keep. Otherwise, you can uninstall it exactly as you would in Windows, by using the uninstall shortcut that it should have installed in the Wine menu.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-11
i dont want to unistall wine because then i have to download it again some other time anyway, and my internet is not the fastest....
i cant see the spotify uinstaller in wine meny, but where does the folder of installed programs in wine go? i might find the uinstaller there

---

### Post by cogadh on 2011-03-11
Deleting the .wine directory does not uninstall Wine, it just deletes all the settings and programs that you may have used and restores Wine to its default "freshly installed" state.

As for where programs are installed, they are in the hidden directory in your home directory called ".wine". Within that directoryt is a replication of the normal Windows file structure (C: drive, Program Files, Windows directory, etc.). If Spotify included an uninstaller, you'll find it there.

---

### Post by CJ_Hudson on 2011-09-29
Thanks cogadh, that helped me too.

---

