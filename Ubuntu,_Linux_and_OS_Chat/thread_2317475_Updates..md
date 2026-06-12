---
title: "Updates."
date: 2016-03-16
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2016-03-16
Is it necessary after a new install of Ubuntu 14.04.1 LTS to run after software updates in terminal.
sudo apt-get update.
sudo apt-get upgrade.
sudo apt-get dist-ugrade.

Just curious.

Thanks.

---

### Post by Geoffrey_Arndt on 2016-03-16
No . . . just make sure your repos reflect the default setting, then choose the fastest server, and then reload the repo's to pull in any missing packages from the install snapshot to the current  install state.   Lastly, just keep current with system updates proactively OR as prompted.

---

### Post by grahammechanical on 2016-03-16
Not if we tick the box "Install updates."

Regards

---

### Post by sammiev on 2016-03-16
Why 14.04.01? 

There are newer ones.

That's a lot of updates to take.

---

### Post by oldos2er on 2016-03-16
Superfluous to run both *upgrade* and *dist-upgrade*. You only need *sudo apt-get update; sudo apt-get dist-upgrade* since dist-upgrade does everything upgrade does, and more.

---

### Post by poorguy on 2016-03-16
Ok I was curious.
I usually just update when the software updater pops up.

As far as 14.04.1 that was the version that was available at the time when I first downloaded it and then created a DVD.
I still use it when someone wants to install Ubuntu.

Thanks for the input.

---

### Post by vasa1 on 2016-03-16
> **sammiev said:**
> Why 14.04.01? 

There are newer ones.

That's a lot of updates to take.While that is true, installing 14.04.1 and upgrading leaves the choice of going the HWE stack route up to the user. I think if someone clean installs 14.04.3 (?) or higher, the HWE stack route is implemented by default so users will get the latest (stable) kernels which may or may not suit older hardware.

---

### Post by poorguy on 2016-03-16
What do you mean by "shortened urls".

---

### Post by sammiev on 2016-03-16
> **poorguy said:**
> What do you mean by "shortened urls".

You see a lot of links now in emails, in post and so on that are very long so the link displayed is shorten.

So do you really know what you are clicking on?

---

### Post by vasa1 on 2016-03-17
Or just search the net for *shortened url* and *danger*. I thought our forum had a policy on that but I didn't find it.

---

### Post by kansasnoob on 2016-03-17
> **sammiev said:**
> Why 14.04.01? 

There are newer ones.

That's a lot of updates to take.

It's smart to do so if you want to avoid HWE EOL. You'll notice at the following link that only installs performed with the 14.04 and 14.04.1 media have the 3.13 series kernel which is supported throughout April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

Those who install using 14.04.2, 14.04.3, or 14.04.4 media will have HWE EOL to deal with in August of this year, and the process in Precise was more buggy than a standard release upgrade :(

---

### Post by poorguy on 2016-03-17
That is good to know that I don't have to deal with the HWE EOL. I like the fact I am good until April 2019.
My Ubuntu 14.04.1 has been rock solid and the only problems I have really had are the ones I created.
I thought I knew what I was doing and quickly found that I didn't.

Was able to revert back from my mistakes and unbreak what I broke.
Learn by doing in my case.

---

### Post by poorguy on 2016-03-17
> **vasa1 said:**
> Or just search the net for *shortened url* and *danger*. I thought our forum had a policy on that but I didn't find it.

 I will look into that.

---

### Post by deadflowr on 2016-03-17
> **vasa1 said:**
> Or just search the net for *shortened url* and *danger*. I thought our forum had a policy on that but I didn't find it.

[Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945") > number 11 ;)

---

### Post by vasa1 on 2016-03-17
> **deadflowr said:**
> [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945") > number 11 ;)
Thank you. I will modify my sig to point to that.

---

