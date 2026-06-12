---
title: "Dansguardian uninstall"
date: 2006-12-02
forum: Ubuntu Christian Edition
---

### Post by Z_Cee on 2006-12-02
I am about to once again test drive Ubuntu Ce on my laptop, but it will be the newest release - 6.10_v2.0. When I tried it last time I did not like Dansguardian. Simply put, I am an adult, I do not go to anything remotely considered a 'bad' site, I'm the only person who uses that computer, and it is not networked. Therefore Dansguardian has no useful purpose for me. 

When I checked the Dansguardian website on how to remove it they used the analogy and I am quoting *"If someone parked a Ford car in your driveway - would you ring up the Ford Car Company?"*  My answer would be that regardless who the Car belonged to I would still have it removed if it were my choice, I would be the ones to make the choices and not them.

Before I attempt another install does anybody know if Dansguardian can be removed completely and the Firefox settings be reset to normal? I have been impressed by the Christian Ubuntu releases, but I DO want to make my own choices on what programs I have installed on my own computer.

Thank You!

---

### Post by Darrious on 2006-12-02
Try this

```
sudo apt-get remove dansguardian 
```

---

### Post by Z_Cee on 2006-12-02
Thank You Darrious. I'll give this a go.

---

### Post by Darrious on 2006-12-02
Also try this to see if it works. Tell me if you run into any errors.

```
apt-get --purge remove --assume-yes "dansguardian"
    apt-get --purge remove --assume-yes "tinyproxy"
    apt-get --purge remove --assume-yes "clamav"
    apt-get --purge remove --assume-yes "firehol"
    apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"
```

---

### Post by HareBall on 2006-12-02
> **Darrious said:**
> Also try this to see if it works. Tell me if you run into any errors.

```
apt-get --purge remove --assume-yes "dansguardian"
    apt-get --purge remove --assume-yes "tinyproxy"
    apt-get --purge remove --assume-yes "clamav"
    apt-get --purge remove --assume-yes "firehol"
    apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"
```

Before you do this make sure you unlock your proxy settings in Firefox or you won't be able to access the internet. The last time I installed CE the first thing I did was unlock them so I would be able to uninstall Dansguardian and not have to worry about it. I did it once without unlocking and it took me awhile to get back to having access. I had to use Opera for a couple of days.

---

### Post by Darrious on 2006-12-02
Yea be careful of that.
You will also need to unlock the firefox proxy settings so use the script attached. 
Simply extract the file and then double click on the "unlock_proxy" file and choose run in terminal :)

---

### Post by mhancoc7 on 2006-12-03
I have just released a script to disable/enable dansguardian in Ubuntu CE.

[http://www.ubuntuforums.org/showthread.php?p=1841627#post1841627](http://www.ubuntuforums.org/showthread.php?p=1841627#post1841627)

Jereme

---

### Post by Darrious on 2006-12-03
I've noticed that this script might be a little better than all the steps you would have to go through.

---

### Post by Staraloppan on 2007-03-19
NEED help... i can no find the enable/disable script i am using CE2.0

---

### Post by mhancoc7 on 2007-03-19
> **Staraloppan said:**
> NEED help... i can no find the enable/disable script i am using CE2.0

You can do one of two things to get the latest dansguardian GUI with the ability to Enable/Disable the filtering.

You can upgrade to Ubuntu CE v2.2 by using the script here.
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/02/ubuntu-ce-v2x-edgy-downloads.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/02/ubuntu-ce-v2x-edgy-downloads.html)

You can install the latest dansguardian GUI using the script here.
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)

Jereme

---

### Post by the switch on 2007-08-21
> **mhancoc7 said:**
> You can do one of two things to get the latest dansguardian GUI with the ability to Enable/Disable the filtering.

You can upgrade to Ubuntu CE v2.2 by using the script here.
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/02/ubuntu-ce-v2x-edgy-downloads.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/02/ubuntu-ce-v2x-edgy-downloads.html)

You can install the latest dansguardian GUI using the script here.
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)

Jereme


that second link is 404

---

### Post by mhancoc7 on 2007-08-21
> **the switch said:**
> that second link is 404

Yes, sorry about that. They are actually both dead links.

You can get the latest downloads and scripts at:

[www.mirror.christianubuntu.com](www.mirror.christianubuntu.com)

Thanks, Jereme

---

### Post by the switch on 2007-08-21
oh, that's right. i forgot...

"S T O P
Access to the page has been denied.

URL: [http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/install_dansguardian_gui_feisty.tar.gz](http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/install_dansguardian_gui_feisty.tar.gz)
Banned extension: .gz

Please contact the Network Administrator if you think there has been an error. "

---

### Post by mhancoc7 on 2007-08-21
> **the switch said:**
> oh, that's right. i forgot...

"S T O P
Access to the page has been denied.

URL: [http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/install_dansguardian_gui_feisty.tar.gz](http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/install_dansguardian_gui_feisty.tar.gz)
Banned extension: .gz

Please contact the Network Administrator if you think there has been an error. "

You should have a Configure Parental Controls option under System>Administration. If you do not have that option please give me some info on how you installed it.

Thanks, Jereme

---

### Post by SashaLavender on 2010-07-29
> **Darrious said:**
> Yea be careful of that.
You will also need to unlock the firefox proxy settings so use the script attached. 
Simply extract the file and then double click on the "unlock_proxy" file and choose run in terminal :)

ok i tried that and it didnt work. it wont even let me run it in terminal. i just want dans guardian gone and i tried the sudo thingy, yes it got rid of it but my internet wouldnt work and i had to reinstall everything.

---

