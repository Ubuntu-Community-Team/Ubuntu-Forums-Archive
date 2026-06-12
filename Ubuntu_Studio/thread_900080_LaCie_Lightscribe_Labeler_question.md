---
title: "LaCie Lightscribe Labeler question"
date: 2008-08-25
forum: Ubuntu Studio
---

### Post by HoodRabbit on 2008-08-25
Hello I just set up LaCie and I was wondering if there was anyway to minimize the circle in the middle b/c it cut's off most of the picture.

-Thanks.

---

### Post by ghostandmachine on 2008-08-26
I know you can make the picture smaller but unless you use a photo editor (such as GIMP) you'll never really get it the way you'll like it. I know there's a template of a dvd/cd cover somewhere for GIMP (or photoshop but it'll still work for GIMP)

---

### Post by GNUway Tech on 2008-08-26
I've never managed to figure out how to get LaCie 4-L installed and running. I once tried installing it in Ubuntu with sudo alien, and it kept telling me it was missing a library. So, I tried installing the library with sudo alien, and it still wouldn't pick it up.

I'm running Kubuntu now. If I can get 4-L running, I would be set. Is there a .deb package available for it, or what am I doing wrong????? I've always been told it works great in tandem with K3B, but I've never been able to figure out how to run it that way.

---

### Post by AnomalyDetected on 2008-09-09
I finally got LaCie 4L running fine.

I first uninstalled (through Synaptic) my existing, non-working copies of 4L and the Lightscribe system software.
Next, I installed the latest Lightscribe System Software deb from:
[http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372)

I also opted to use the enhanced contract patch, as instructed in:
[http://www.lightscribe.com/downloadSection/pse/](http://www.lightscribe.com/downloadSection/pse/)

Next I searched Synaptic for "libstdc++5" and installed it.

Finally, I downloaded the 4L rpm from:
[http://www.lacie.com/us/support/drivers/driver.htm?id=10094](http://www.lacie.com/us/support/drivers/driver.htm?id=10094)
and used Alien 8.69 to convert it to a deb.

You've got to launch 4L-gui with sudo or it won't let you actually print to disc. The program is fairly basic compared to some of those I've used in WinDoze, but it does allow you to print full-page (full-disc?) images, unlike the stupid basic utility provided by lightscribe themselves. In fact, the Preview time is instant in 4L, whereas I would always see about a minute delay when trying to preview in any windows program. Weird.

Printing time is, of course, unchanged (as that is dependent on the hardware).

Works great! Thank goodness... there really aren't any other options to speak of for lightscribe in linux, as least not that I've been able to find. Just use in combination with Gimp or your favorite graphics program to make a image for printing. For best results, I recommend converting it to black and white yourself ahead of time and increasing the contrast.

---

### Post by 080907k on 2008-09-09
&#21271;&#20140;&#37329;&#35802;&#20449;&#22235;&#26041;&#21345;&#35782;&#21035;&#25216;&#26415;&#26377;&#38480;&#20844;&#21496;&#30340;&#23458;&#25143;&#36941;&#21450;&#22269;&#20869;&#21508;&#38134;&#34892;[**&#35780;&#20215;&#22120;**](http://www.jcx.com.cn/)&#20445;&#38505;&#12289;&#36890;&#20449;&#12289;&#33322;&#31354;&#12289;&#21830;&#22330;&#12289;&#21307;&#30103;&#31995;&#32479;[**&#21483;&#21495;&#26426;**](http://www.jcx.com.cn/job.asp)&#37096;&#20998;&#20135;&#21697;&#24050;&#23454;&#29616;&#20102;&#20986;&#21475;&#65292;&#22312;&#23458;&#25143;&#30340;&#24212;&#29992;&#20013;&#24471;&#21040;&#20102;&#24191;&#27867;&#30340;&#22909;&#35780;[**&#21462;&#21495;&#26426;**](http://www.jcx.com.cn/job.asp)&#22312;&#29616;&#22312;&#19982;&#26410;&#26469;&#30340;&#26085;&#23376;&#37324;[**ic&#21345;&#35835;&#21345;&#22120;**](http://www.jcx.com.cn/)&#37329;&#35802;&#20449;&#20154;&#23558;&#32487;&#32493;&#20197;&#20248;&#36136;&#30340;&#20135;&#21697;[**&#21483;&#21495;&#26426;**](http://www.jcx.com.cn/job.asp)&#39640;&#26114;&#30340;&#31934;&#31070;&#65292;&#20026;&#23458;&#25143;&#12289;&#20026;&#31038;&#20250;&#36827;&#34892;&#26356;&#22909;&#30340;&#26381;&#21153;

---

### Post by masterrahdin on 2011-07-12
I am new to linux and forum here , could not even figure out how to post a question. I have installed the latest version of ubuntu studio 64 bit and would like to install lightscribe,  have you been able to do this and if so , could you tell me how. I don't know anything about linux yet, although I found the terminal and can copy and paste, thats about it. thanks hope you can help:confused:

---

### Post by texla on 2011-07-15
[SIZE=2]You will need to make the 32 bit programs work for 64bit.  This method below worked for me with Lightscribe on 64bit Maverick:

download to home folder:
1: [LIGHTSCRIBE SYSTEM SOFTWARE]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814")
2: [LIGHTSCRIBE SIMPLE LABELER]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815")
from: [http://www.lightscribe.com/downloadS...nux/index.aspx]("http://www.lightscribe.com/downloadSection/linux/index.aspx")

[/SIZE] [SIZE=2]Then, in terminal install the 32-bit compatibility package: [/SIZE]
[FONT=Arial][SIZE=2]sudo apt-get install ia32-libs   (mine was already installed and up to date)[/SIZE][/FONT]

[FONT=Arial][SIZE=2]next, in terminal force the 32 bit programs to install:[/SIZE][/FONT][FONT=Arial][SIZE=2]
(changing the files to the name of current downloaded version if needed)

sudo dpkg -i --force-architecture lightscribe-1.18.15.1-linux-2.6-intel.deb
[/SIZE][/FONT][FONT=Arial][SIZE=2]sudo dpkg -i --force-architecture lightscribeApplications-1.18.15.1-linux-2.6-intel.deb

next:
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
sudo ldconfig

[SIZE=2]then download Lacie program here so you can add your own images:
[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=2][http://principialabs.com/files/4l_1.0-r6_i386.deb](http://principialabs.com/files/4l_1.0-r6_i386.deb)

install:
sudo dpkg --install --force-architecture 4l*.deb[/SIZE][/FONT][FONT=Arial][SIZE=2]

The following instruction will provide a two-item menu that includes an option to print darker labels:

sudo /usr/lib/lightscribe/elcu.sh[/SIZE][/FONT]

[FONT=Arial][SIZE=2]then to run Lacie labeler as root:

sudo 4L-gui
  
you can also run the Simple Labeler installed by Lightscribe  but it is  very BORING - however it is a fast way to go because of the  circular printing - you get to it in /OPT or add this shortcut to a  launcher:

/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler

Some ideas for getting started with the Lacie can be found by using this Gimp template here:
[http://www.vitalbodies.net/site/tech...-projects.html]("http://www.vitalbodies.net/site/tech-web/tech/111-open-source-cddvd-cover-for-open-source-projects.html")
[/SIZE][/FONT] 

:popcorn:

---

### Post by wjcunning on 2011-11-14
Got all the lightscribe installed per the above instructions....but the 4L gui cannot see my cd drive(s)....they are all lightscribe devices...

Any ideas?

---

