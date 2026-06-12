---
title: "Help with Internet"
date: 2009-10-10
forum: Virtualisation
---

### Post by Amockineuropa on 2009-10-10
So I loaded Ubuntu to run in "Virtual Disk" with Windows Vista. I can connect to internet with Windows BUT not with Linux. I found my wireless driver and transferred it via thumb drive to my linux laptop. Placed it on desktop. Double clicked and extracted it to the desktop. Opened Terminal and ran the following:
cd /home then cd ./Desktop and got No such file/directory. Tried cd /Desktop and cd ./Desktop again no-go. Help!

---

### Post by wojox on 2009-10-10
```
cd Desktop
```

---

### Post by pedro3005 on 2009-10-10
To get in the desktop try
```
cd ~/Desktop
```
But what is this driver? What format is it? What OS was it made for? Are you following a guide or anything?

---

### Post by superdav42 on 2009-10-10
I think want you are trying to do is ```
cd ~/Desktop
``` which will go straight to the Desktop folder with the files you are looking for. I have no idea what drivers you downloaded and I'm guessing they won't work. 

See [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
for more information on wireless card support. Basically just do the command ```
lspci -v | less
``` and give us the line pertaining to your wireless device so we can find out what chipset it uses and can recommend the proper way of installing the drivers.

---

### Post by Amockineuropa on 2009-10-10
That cmd atleast got me to the desktop I will try to load my wireless driver. I am trying to load my Atheros driver file. I have it on desktop. I am now at desktop ([EMAIL="rollingstone@ubuntu:~/Desktop$"]rollingstone@ubuntu:~/Desktop$[/EMAIL]) but I can't seem to get to my file lapeled "atheros-wired-driver-1005ha-linux.zip. I am trying to load the src file

---

### Post by Amockineuropa on 2009-10-10
That cmd got me to desktop. I now have [EMAIL="rollingstone@ubuntu:~/Desktop$"]rollingstone@ubuntu:~/Desktop$[/EMAIL]. I am trying to get to my file atheros-wired-driver-1005ha-linux.zip. But the cmd cd  /atheros etc does not work I also tried cd ~/filename again no go and I tired cd ./filename. Help!

---

### Post by Amockineuropa on 2009-10-10
OK! I figured it out. Thanks for getting my to desktop

---

### Post by superdav42 on 2009-10-10
The command you are looking for is ```
unzip atheros-wired-driver-1005ha-linux.zip
```

---

### Post by Amockineuropa on 2009-10-10
Yes but I could not get to the file then I realized that U guys had already got me to the Desktop where I had unzipped my file so I then just entered cmd cd /src and loaded my driver! So I am now online via ethernet now I just need to set up my wireless - which I believe I can do. I also downloaded all my updates. I have a question? I had to wipe my system clean because I discovered when I went to logout ANOTHER Name on my system when I clicked on it my system crashed! I tried to reboot but got blank screen! What was that? Did somebody have me load malware? Was somebody monitoring my system via a trojan horse?

---

