---
title: "Nvidia 319.49 Not default for nvidia-319"
date: 2013-09-09
forum: Ubuntu Development Version
---

### Post by JSeymour421 on 2013-09-09
First Hello Ubuntu Community. Ubuntu 13.10 finally was able to install on my Lenovo Y510p with sli 750m's a painful process but well worth the time. Anyways why isn't the latest 319.49 from Nvidia able to be used? Even if i download from the website I cannot seem to install on my Ubuntu 13.10 heres the steps i took.
1: Download
2: sudo stop lightdm
3: sudo sh NVIDIA-Linux-x86_64-319.49.run

Thanks in advance.

---

### Post by grahammechanical on 2013-09-09
I have never done what you have done but I have some instructions for doing it. But you do not mention step 4, restart lightdm. Also, are you in the folder where you downloaded the Nvidia driver to? On my Saucy install I see in Additional Drivers two versions of Nvidia 319, Tested and Updates. Why do you not want to use Additional Drivers to install?  Downloading the lastest from the proprietary web site brings an experimental version. Which is fine if we want to experiment and some of us do. But we need to know what we are doing and in this area I don't. So, I don't - download from the web site and install.

You do not give us information on what is going wrong. What error messages do you get?

Regards.

---

### Post by cariboo on 2013-09-09
The current Nvidia driver for Saucy is 319.32. The latest driver probably hasn't been packaged for Ubuntu yet.

---

### Post by kj4ohh on 2013-09-20
What did you do to get 13.10 working with SLI on your y510p?  I just got mine yesterday.

on 13.04 I Can only get it to boot up if I remove add-on graphics bay, with the built-in intel graphics :(

Going to try 13.10 tonight

---

### Post by blz on 2013-10-26
I have a Lenovo y510p as well and I'm currently with Ubuntu 13.04. I have only been able to use the Nvidia card in Ubuntu with Bumblebee. My system is currently using the integrated Intel graphics card. Have you been able to use your Nvidia in Ubuntu 13.10?

---

### Post by grahammechanical on 2013-10-26
You and others like you might find this blog interesting

[http://albertomilone.com/wordpress/?p=591](http://albertomilone.com/wordpress/?p=591)

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards,

---

### Post by Cavsfan on 2013-10-28
Does anyone think it would be practical to add either the x-swat or xorg-edgers ppa to saucy. It seems like LTS versions are more touchy about bleedind edge Nvidia drivers. 
I have 319.60 installed and it seems to work quite well with my "middle of the road" Geforce 9800GT card.

---

### Post by Elfy on 2013-10-30
Closed.

Saucy has been released - please use standard support forums for it.

---

