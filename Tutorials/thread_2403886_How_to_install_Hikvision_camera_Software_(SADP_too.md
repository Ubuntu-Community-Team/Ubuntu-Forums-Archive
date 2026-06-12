---
title: "How to install Hikvision camera Software (SADP tools &amp; ivms4200 linux) on Ubuntu 18.0"
date: 2018-10-17
forum: Tutorials
---

### Post by bkjaya1952 on 2018-10-17
How to install Hikvision camera Software (SADP tools & ivms4200 linux) on Ubuntu 18.04 LTS

Hikvision camera software have been written to suit Windows environment .If you want to run those software on Ubuntu ,you have to first install Wine .
But Wine is not included in the  Ubuntu  Software center in Ubuntu 18.04.The  Synaptic Package Manager is useful in installing most of the software that -
has not been included in the Ubuntu software center.
Installing Wine
Open the terminal and run (or use  Synaptic Package Manager)
sudo apt install wine64
Installing SAPD Tools
Download SADP tools from [softpedia]("http://www.softpedia.com/get/Internet/Other-Internet-Related/SADP.shtml")
Double click on the downloaded  file  to install SAPD tools (Only the SADPTool_V3.0.0.10 version woks with Ubuntu 18.04)
[IMG]https://bkjaya.files.wordpress.com/2018/06/screenshot-from-2018-06-24-19-54-53.png?w=700[/IMG]

[CENTER]SADP panel on Ubuntu 18.04[/CENTER]
In the above penal you can see the ip camera in the local network has been detected by SADP automatically .
If you don&#8217;t have the device password of the camera, you can use SADP tools to reset it. In that case you will have to generate a QR code using -
the SADP as shown in the figure below and take a picture of the QR code and e- mail  it to the closest technical division of the [EMAIL="techsupport.usa@hikvision.com"]Hikvision company  . [/EMAIL]
Then they will send you a xml file to be used in the SADP Tools to reset the device password.
[IMG]https://bkjaya.files.wordpress.com/2018/06/screenshot-from-2018-06-23-22-56-08.png?w=700[/IMG]
[CENTER]Resetting forgot device password of cameras
[/CENTER]
[IMG]https://bkjaya.files.wordpress.com/2018/06/img_20180623_094021.jpg?w=700[/IMG]

Uploading the  xml file received  from the technical division of Hikvision to SADP to reset device password

Installing ivms4200 linux on Ubuntu 18.04
Latest ivms4200  is only compatible with MS Windows. There was a Linux beta version in Hikvision web site long ago. 
This software can be downloaded from this site [https://upload.bkeesti.ee/Hikvision/Software/](https://upload.bkeesti.ee/Hikvision/Software/)  [ivms4200-Linux.tar.gz]("https://upload.bkeesti.ee/Hikvision/Software/iVMS4200-Linux.tar.gz")
[Alternative download]("https://www.dropbox.com/s/qg4phd6ouztiqc5/iVMS4200-Linux%20%281%29.tar.gz?dl=0")
Extract the file and go to Linux sub folder and double click on iVMS-4200 executable file
[IMG]https://bkjaya.files.wordpress.com/2018/06/screenshot-from-2018-06-24-19-57-50.png?w=700[/IMG]
[IMG]https://bkjaya.files.wordpress.com/2018/06/screenshot-from-2018-06-23-21-53-31.png?w=700[/IMG]
[CENTER]ivms4200 panel on Ubuntu 18.04[/CENTER]

---

### Post by andy180 on 2019-05-18
Thank you bkjaya1952, was about to send my camera back to Amazon, spent hours with nmap etc. trying to find the camera, but will try Wine with SADP. Cheers.

---

### Post by deep4330 on 2020-01-05
Hi Team, I was looking for many days to find the solution, and Finally I have installed iVMS-4200 Client on ubuntu with the help of wine, and it is 100% working for me I got the solution form here [[https://youtu.be/3YDzMtvGUGI]](https://youtu.be/3YDzMtvGUGI])


I did following steps
install wine64
install winetricks
install wine64-development
intall vlc
and then install windows dependency for ivms and Sadp
then I install sadp though wine,
then I installed iVMS
I Got the solution [https://youtu.be/3YDzMtvGUGI](https://youtu.be/3YDzMtvGUGI)

---

### Post by bkjaya1952 on 2020-02-07
> **deep4330 said:**
> Hi Team, I was looking for many days to find the solution, and Finally I have installed iVMS-4200 Client on ubuntu with the help of wine, and it is 100% working for me I got the solution form here [[https://youtu.be/3YDzMtvGUGI]](https://youtu.be/3YDzMtvGUGI])


I did following steps
install wine64
install winetricks
install wine64-development
intall vlc
and then install windows dependency for ivms and Sadp
then I install sadp though wine,
then I installed iVMS
I Got the solution [https://youtu.be/3YDzMtvGUGI](https://youtu.be/3YDzMtvGUGI)

Hi Deep4330
You are correct ! Thank you. Loading time is less  in ivms4200 Linux

---

### Post by bkjaya1952 on 2020-02-13
Hi andy180 
I have pushed a docker repository on ivms4200-Linux to dockerhub. Please try it.

[https://hub.docker.com/r/bkjaya1952/docker-ivms4200-linux](https://hub.docker.com/r/bkjaya1952/docker-ivms4200-linux)

[https://hub.docker.com/r/bkjaya1952/docker-ivms4200-linux-new](https://hub.docker.com/r/bkjaya1952/docker-ivms4200-linux-new)

---

### Post by David_Camp on 2020-02-15
> **bkjaya1952 said:**
> Hi andy180 
I have pushed a docker repository on ivms4200-Linux to dockerhub. Please try it.

[https://hub.docker.com/r/bkjaya1952/docker-ivms4200-linux](https://hub.docker.com/r/bkjaya1952/docker-ivms4200-linux)

Great! I am also waiting for this stuff. Let me try!

---

### Post by emanueledb on 2020-07-04
soy bueno, me sirve mucho

---

