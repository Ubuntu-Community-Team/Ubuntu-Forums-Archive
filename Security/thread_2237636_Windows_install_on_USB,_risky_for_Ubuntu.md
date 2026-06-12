---
title: "Windows install on USB, risky for Ubuntu ?"
date: 2014-08-03
forum: Security
---

### Post by jigar2 on 2014-08-03
Hi,
I havent seriously used Windows for a long time. I was considering installing it on an external USB disk with Kubuntu as my base OS. Advantages being hardware acceleration, performance boost,etc. Altho I am worried about security of my Kubuntu install. So my questions for this setup are -
* Is it easy/possible to get rootkits in WIN and then use them to get into Kubutnu 
* ext4 isnt directly readable by WIN but how safe is my system in general from vulnerable WIN
* Anything else I shud be worried about

I can lock down Virutalbox with Apparmor but wud rather prefer the above setup.
Thanks in advance.

---

### Post by kc1di on 2014-08-03
Hi Jigar2 and welcome to Ubuntu/Kubuntu,

I'm a little confused as to what your doing?

Is Kubuntu actually installed on your machine? or are you running everything from virtualbox?

I don't believe windows running in a virtual box environment would be any danger to the host OS. Only to the incidence of Win in the Virtual machine. 
As far as running Win from a usb stick,  I believe in order to boot win you'd need it in the first H.D. partition but I may be wrong on that. 
anyway hopefully someone will come along that knows more than I do about this. 
Good luck

---

### Post by jigar2 on 2014-08-03
I have Kubuntu installed on my system and am considering either installing WIN in Virtualbox or on a USB Hdisk
using this guide
[http://lifehacker.com/how-to-run-a-portable-version-of-windows-from-a-usb-dri-1565509124](http://lifehacker.com/how-to-run-a-portable-version-of-windows-from-a-usb-dri-1565509124)
Just am not sure about booting into WIN being a security risk all by itself for my Kubuntu install !
Basically I am looking to see how I can Kubuntu safe from WIN viruses,rootkits,etc. Assuming my WIN install on USB gets hacked, then what do I do to keep Kubuntu safe.

---

### Post by kc1di on 2014-08-03
You should be very safe with Kubuntu- as there are very few viruses that can affect it. It would only pass on viruses perhaps to other windows users.
I wouldn't worry too much about affecting your kubuntu install.  
But do take as many precautions as possible with windows. 
enjoy :)

many of us dual boot linux and windows.  and have no problems. 
that is essentially what you'll be doing.  
[URL="https://help.ubuntu.com/community/Antivirus"]
here's a ubuntu page that[/URL] discusses antivirus needs in ubuntu/kubuntu.

---

### Post by jigar2 on 2014-08-03
Thanks [[COLOR=#000000]kc1di[/COLOR]]("http://ubuntuforums.org/member.php?u=1839")[COLOR=#000000] , I will try it out.[/COLOR]

---

