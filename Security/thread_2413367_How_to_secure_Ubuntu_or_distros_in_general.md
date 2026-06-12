---
title: "How to secure Ubuntu or distros in general?"
date: 2019-02-24
forum: Security
---

### Post by tackskull on 2019-02-24
Hi there, I am a new comer on the linux world. In a year I tried many different distros and now I have 4 laptops with 4 different linux os. I one of them I use Kubuntu, and I would like to know how to  fully protect m system. So, which program/tools I need to protect my pc from spyware/virus and any other kind malware or problem a linux pc can met? What about to secure my internet navigation? 

Thanks everybody

---

### Post by bitsnpcs on 2019-02-24
Hello tackskull,

you can enable the built in firewall in Ubuntu using this command 

```
sudo ufw enable
```

You can read all about its settings here - [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

You can protect yourself online by using a VPN, browsers such as Opera have one of these built in , it is free , it is as simple to use as sliding a slider, Opera is available in the Ubuntu Software.

To fully protect any system and operating system with a connection to the internet is not possible, we just make sensible precautions, and use sensible browsing habits.

---

### Post by tackskull on 2019-02-24
Thanks a lot :)

---

### Post by bitsnpcs on 2019-02-24
You are Welcome tackskull :)

---

### Post by crockett98 on 2019-02-25
I'm not all that much in the know but i've been reading up and researching a bit recently. 

Waving goodbye to Windows is a great start. The way in which its normal to download and install drivers and programs in Windows is the first potential security hazard. 

Good browsing habits is probably the most important. Make sure the links you click on are genuine. I read on a forum (possibly this one) how someone clicked a seemingly normal link which turned out to be a link to someones google drive account to a download that installed malware of some form. There are websites on which you can enter a link address and it will tell you where it is really taking you. The google drive example I gave was flagged up this way. 

Try not to download and install... use the repositories. Some say using Wine and emulators can increase risk too. 

Software firewall... already mentioned. 

VPN... already mentioned. I use the free offering from ProtonVPN. To me, it seems a genuine good option for a free service. It works with OpenVPN too.  

Apparmor is already installed on Ubuntu. Make sure all your distros have it. 

Jailfire is another one to install for use on internet accessing programs... like your browser. 

Browser... I have gone with Brave. Most people will give you a different recommendation though most browsers are based on Firefox or Chromium and customisation. 

Router... I found this page (I think from this website) which is well worth a read. 
[http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security) 

There are many more things you can do, no doubt, but the weakest link is likely the user so good practice is key. 

And in case everything does go wrong, an encrypted drive for files or even keep your personal files on an external harddrive and plug it in when needed.

---

