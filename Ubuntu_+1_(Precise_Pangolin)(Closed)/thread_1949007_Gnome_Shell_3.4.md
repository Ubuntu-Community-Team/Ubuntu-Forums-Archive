---
title: "Gnome Shell 3.4"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by macstevejb on 2012-03-29
Just installed, however gnome-tweak-tool (advanced settings) will no longer open and just crashes.

Anyone else having this problem?

regards,

Steve :-(

---

### Post by sgage on 2012-03-29
> **macstevejb said:**
> Just installed, however gnome-tweak-tool (advanced settings) will no longer open and just crashes.

Anyone else having this problem?

regards,

Steve :-(

Nope. Are you using any ppa's, or is this completely "official" versions?

---

### Post by macstevejb on 2012-03-29
only official....3.4 appeared in the repositories this morning.

I am thinking it might be something to do with the shell extensions that I already had installed. I simply updated them by changing the relevant data in the respective metadata.json config files. 

Now, while they work, I cannot activate/decativate them because the said gnome-tweak-tool keeps crashing.

I had noted that the gnome shell extensions website:

[https://extensions.gnome.org/](https://extensions.gnome.org/)

is only showing about 10 extensions that appear to be compatible with gnome shell 3.4?

regards,

Steve

---

### Post by sgage on 2012-03-29
> **macstevejb said:**
> only official....3.4 appeared in the repositories this morning.

I am thinking it might be something to do with the shell extensions that I already had installed. I simply updated them by changing the relevant data in the respective metadata.json config files. 

Now, while they work, I cannot activate/decativate them because the said gnome-tweak-tool keeps crashing.

I had noted that the gnome shell extensions website:

[https://extensions.gnome.org/](https://extensions.gnome.org/)

is only showing about 10 extensions that appear to be compatible with gnome shell 3.4?

regards,

Steve

That's how it looks - hopefully the extension authors will get on the job now that 3.4 is in stable release.

That said, I've tweaked a lot of extensions to get them to work, with great success and no problems with Tweak Tool. So I think something else must be going on. But you can always try removing all the extensions to be sure.

---

### Post by daelsta on 2012-03-29
*ok after further investigation it seems it's the user-theme-extension. I can start gnome-tweak-tool now but the user-theme-extension can't be activated*

I had the same problem...seems like you're using an incompatible shell theme...try to delete all themes in /home/yourusername/.themes...that worked for me. problem is the only 3.4 compatible themes right now are the standard theme and elemantary luna from half-left. hope this helps

greetz

---

