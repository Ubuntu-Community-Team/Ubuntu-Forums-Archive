---
title: "How to get the Skype UI back after closing it."
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by FelixWinter on 2012-03-21
Hi. 

I just installed the 12.04 beta some days ago on a thinkpad x220. As this is my first ubuntu installation ever I ran into a problem which I think can be resolved easily, I just don't know how.

When I close the skype by hitting the red x in the top left corner, the UI dissapears, but the skype process in still running. When I try to restart skype I get the information that another instance is already running. But I did not find a way to recreate the ui. The skype icon dissapears from the launcher and I have to run "pkill skype" to end the process.

Whe I minimize skype the UI also dissapears, but I can always get it back using the launcher Icon which is still there.

My question is: How do I get the skype UI back after hitting the red x? As the process is still running, there should be a solution to this. 

Thanks,

Felix

---

### Post by ajgreeny on 2012-03-21
Isn't there a skype icon somewhere in the panel at the top, assuming you are using unity?

I have no idea how you can configure 12.04, nor 11.10 with unity running as I have given unity a wide birth, and don't use it, but how does skype in 11.10 do it?

---

### Post by cryptotheslow on 2012-03-21
You may need to add it to the panel's whitelist for it to show.

dconf-editor is an application that allows you to access and change these configurations so:

```
sudo apt-get install dconf-tools
```

Once installed run: dconf-editor

Once open navigate to:
desktop > unity > panel

Then edit the Value for systray-whitelist to add skype. I think it needs a capital S so add 'Skype' after a comma at the end of the current value string.

Close dconf-editor, logout and back in and hopefully a Skype icon will go to the notification area when you hit that close button.

---

### Post by FelixWinter on 2012-03-21
Well, thank you very much. That did the trick. 

Felix

---

### Post by cryptotheslow on 2012-03-21
Good stuff :)

Glad I finally managed to help someone rather than being the one with the problem!

---

