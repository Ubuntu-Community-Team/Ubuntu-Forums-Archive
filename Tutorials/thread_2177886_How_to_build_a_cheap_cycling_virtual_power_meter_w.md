---
title: "How to build a cheap cycling virtual power meter with Golden Cheetah v3"
date: 2013-09-30
forum: Tutorials
---

### Post by hollywoodpete on 2013-09-30
Build you own cheap virtual power-meter.

Now that winter is coming, it is a perfect time to get ready for indoor training with a power-meter. With this guide and a few cheap parts you should be able to build your own power-meter.

Parts you will need:
Old computer
Monitor
Ant+ USB stick  (I use a Garmin stick)
Ant+ Speed/Cadence Sensor (I use a Garmin GSC-10
Indoor trainer with a fan

For an OS I use Ubuntu (because it is free) which runs fine on older/legacy (cheap) computers. I use Golden Cheetah v3 which is a free download and does real time virtual power. It also will upload the data into TrainingPeaks. I also use VLC so I can watch a training video at the same time. You can use Windows or Mac (OS whatever) but need to use a more powerful processor and more RAM. My goal is to keep the price less than $100 but in reality some people probably have everything they need already but just need to know how to put it together. Because of that price point, Ubuntu is a no-brainer.

To get started, use any computer and go to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Download the flavor you need. If you have a single core processor I would go with 32-bit, multi-core 64-bit. I would suggest using 12.04

Once you have it downloaded you need to burn it to a disc or thumbdrive. Once you have a bootable image, put the media in the computer you plan to use as a power-meter and boot the computer from the disc or drive. It will prompt you to install Ubuntu. Follow all the steps and install. Make sure you are connected to the internet during installation.

Now that you have Ubuntu, it is time to install the software. Hold down the Ctrl and Alt buttons at the same time and then hit the t button. A black terminal box should pop up. copy and paste the following lines one at a time and hit enter after each line. It will ask for passwords at times.

sudo apt-get update
sudo apt-get install vlc browser-plugin-vlc
sudo apt-get install libavcodec-extra-53

The next part is where it gets a little tricky. You can get Golden Cheetah v2 by simply going to the Ubuntu Software Center but "virtual power" is only available in v3. To get v3 you either have to build it yourself or go into the Debian unstable Sid repositories, THIS MAY BREAK YOUR SYSTEM. It worked fine on my system but proceed at your own peril.

To add the Sid repositories I used the Software Center
Edit>Software Sources>Other Software>Add
then add this line 

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free

and make sure you check the box. Then

sudo apt-get update
sudo apt-get -t unstable install goldencheetah

then go back into the Software Center and disable/uncheck the box. I actually deleted it out of sheer paranoia

This should give you a working version of Golden Cheetah v3 and virtual power in time for the indoor riding season.

---

### Post by tgalati4 on 2013-09-30
Nice tutorial.  One of these days I will write up my interface to a Precor elliptical trainer.  I used an old laptop running Dapper Drake (6.06) connected via serial port to the RJ45 connector (also serial port) on the Precor.  You can record heart rate (if you wear a Polar strap), cadence, speed, power, METs, Calories, ramp level, and resistance at 3-second intervals.  It is interesting to plot HR versus Power and HR vs Ramp*Resistance.

Eventually, I would like to add virtual reality, speeding up and slowing down a bicycle video based on speed.  That will take some effort.

---

### Post by mrfoulkes on 2013-11-09
Trying intstuctions, sound great!

everything went smooth thru updating Software center with path "deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free" added and checked.

Then ran "sudo apt-get update" and got error message:
Reading package lists... Done
W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) unstable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553

Next ran "sudo apt-get -t unstable install goldencheetah", and got error message:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 goldencheetah : Depends: libvlccore7 (>= 2.0.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

Any sugestions?

Thanks for the post by the way, looking to start up training this winter.  Would be nice to handle it with Ubuntu on some extra boxes.

---

### Post by hollywoodpete on 2013-11-09
Which version of of Ubuntu are you using? The tutorial is a little dated. If you use 13.10 you can use the Ubuntu Software Center  and simply search for Golden Cheetah. It should automatically install v3. In the past you had to build v3 yourself and was a PITA dealing with dependencies. Upgrade to 13.10 and pedal away.

---

### Post by mrfoulkes on 2013-11-10
I'm a little outdated. On Ubuntu 12.04.  I'll upgrade and give it another try.  Thanks for getting back.

---

