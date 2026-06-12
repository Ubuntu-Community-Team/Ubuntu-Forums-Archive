---
title: "Firefox will not update"
date: 2022-06-10
forum: Ubuntu Development Version
---

### Post by boobooboon on 2022-06-10
I recently have a problem with updating firefox for some reason it refuse to update i will write what the message states
Unable to update firefox:status-code=409kind=snap-change-coflict
message=snap"firefox"has "refresh-snap"change in progress
what ever that means, the only change i made was to try install a paid for vpn but it would not work i thought i i remove it but my beginners knowledge is limited as open source is new to me only a few years 

thanks

---

### Post by #&amp;thj^% on 2022-06-10
You need to check and show us this:
```
snap changes
```

---

### Post by SeijiSensei on 2022-08-15
Remove Firefox from your system with
```
sudo apt remove firefox
```
Next, add the Mozilla "PPA" for Firefox to your system with
```

sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update

```
Finally, reinstall Firefox.
```
sudo apt install firefox
```.

This will give you the most up-to-date version of Firefox. Also Thunderbird if you use that.

---

