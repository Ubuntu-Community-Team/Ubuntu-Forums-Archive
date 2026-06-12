---
title: "Setting up ec2 instance of ubuntu 10.04"
date: 2011-03-24
forum: Server Platforms
---

### Post by jeevandongre on 2011-03-24
I need to set up an ubuntu 10.04 instance on ec2, but there are some instance ready available I tried with few but I am not really happy with that since those are meant for test puporse.

I have to deploy a java/j2ee based web app with mysql. 1)need to install tomcat 2)java runtime 6 3) apache web server

What would be the best image to use for my requirement and I initially planning to launch with the micro instance if my web app demands I may further move to small and larger instances. So it should be eligible for free usuage tier.

---

### Post by BkkBonanza on 2011-03-24
I've had good success with the alestic.com images. Use one of their EBS AMIs in the location bested suited to you to start. Modify it to suit and take a snapshot (from the ec2 control panel). Create a new custom AMI from that snapshot (using the same control panel).

You can use this image to start new instances as needed that are custom to your needs. During the snapshot step you can also customize the volume size to suit but that is a few more steps, though not too hard.

If you need more step-by-step info just ask.

(I wouldn't customize too much before doing your snapshot because if you mess up at that stage you may have to start over. Better to snapshot early on, and then customize further once you know the process. You can always take second snapshots later on, and delete the earlier ones.)

eg. in East Coast USA these ones may be good,

32 bit ami-3e02f257 	
64 bit ami-3202f25b

---

### Post by jeevandongre on 2011-03-24
Hey thanks a lot am actually using the same instance. I was actually looking for some one to guide me since I am novice. Actually I am working directly on the instance I was not knowing that I need to take the snap shot and then configure that, I have taken a snap shot the instance which I am currently using and its stored on EBS. What are the further steps which I need to follow I need to install jdk6 tomcat and apache web server I will moving by database to rds so that it can be scalable. Please guide me.

---

### Post by BkkBonanza on 2011-03-24
The advantage to creating your own AMI is that you can create new instances whenever you need that have the same features. While you can stop/start the original instance as you need, much like you would turn on/off a physical machine, if you have a problem that can't be resolved, or you mistakenly terminate it, then you would have to re-configure a new instance from scratch since you don't have a copy of the customized alestic one.

To create your own AMI go to the instances list in ec2 control panel and choose the desired instance, and click Instance Actions, **Create Image AMI EBS** (or right click also has this option). This creates a snapshot with AMI bundling task that takes a while to complete. After it completes I believe it shows up as a new AMI in your list (left sidebar AMI section)(or maybe you have to register the snapshot manually, I forget now).

From this you can start new machines with that image as a starting point rather than ever having to reconfigure from the original again.

To get your instance customized you would just follow a typical tutorial for installing LAMP, Tomcat, JRE6 etc. just as if on a physical machine. There's quite a few of those around easily found with google but I couldn't say which one is the best, and I wouldn't write out the whole thing (even if I could remember every step). 

The Ubuntu Server Guide has sections for each of the apps you want so that may be a good starting place (sections 10,11,12).

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

However, when you follow a guide they will often refer to testing with localhost, but you won't be doing that as you aren't running a desktop on the same machine. You would just use the ec2 domain name you have or the IP address.

---

### Post by jeevandongre on 2011-03-25
Thanks a lot so let me explain what will I do now. I have selected ami-cef405a7 which is 64 bit ubuntu 10.10 instance now I wil take the snap shot that instance and start configuring that by installing all the necessary tools. Once I am done with that I will take the snap shot of that to preserve the instance. Or else I will configure the original instance and take the snap shot of it and start working on that.

---

### Post by jeevandongre on 2011-03-25
Yesterday I created an instance and tried to configure that and I stopped the instance before going home, but morning when I came to office and tried to log to the same instance I am getting an error which says Connection Timed out. How do I login to the same server now?

---

### Post by BkkBonanza on 2011-03-25
Is this instance a micro size one?

There is a common problem with some instances designed for small size when they get used as micro. I know this problem causes the instance to fail starting and hence you aren't able to login. The dead instance may appear to be started but not accept connections because it didn't get thru the init process. Sometimes the log for the instance in the control panel will show failure messages.

The problem is fairly easy to fix but if you are almost at the beginning of you configuration process it may be easier to start fresh and make the fix before stopping or rebooting the instance. 

Assuming this is micro size I'll describe the fix in case it helps. The problem is in the **/etc/fstab** file where a second volume is mounted that uses an S3 (so called ephemeral store) volume that is not supported on micro instances. There should be a root mounted but if there is also a second one then that line should be deleted or commented out. After that, the instance will start normally. This doesn't show up on first start but will cause failure on a reboots/restarts.

Now, the way to fix that file when it can't be "started" is as follows. You need to stop the instance. Then go to the volume control panel and **detach** it from the stopped instance, remembering the device it was attached as eg. /dev/sda1 (this is like removing a hard disk virtually). Then you need to start another temporary instance and attach the volume to that instance as an unused device eg. /dev/sdf1 (which is like connecting the disk to another machine). Then login to that instance, and use the mount command to mount the new device somewhere like /mnt. eg. **sudo mount /dev/sdf1 /mnt**. After that is done you can now edit the file eg. **sudo nano /mnt/etc/fstab** and make the change. Then **sudo umount /mnt** and in the control panel detach that volume again and re-attach it to the stopped instance that failed. After that it should start ok.

This seems to come about because these AMIs are designed to work with other sizes and as far as I know this hasn't been fixed. The first thing I do when starting a new micro instance is fix the /etc/fstab file so reboots won't cause trouble. 

If this turns out not to be the issue then I'm not sure what else causes it to not connect other than errors in IP perhaps. Remember when restarting it gets a different IP address.

Regarding the snapshots. You can do them at whatever stages you prefer. I just recommended it early on so that if you had problems with that then you wouldn't have done too much work before figuring them out. You can delete snapshots when you no longer need them so the cost is very low, or free probably if you have a new account (which I'm not qualified to have since I've had mine for years now :( )

The important thing is that when you are happy with a finally ready to go working custom instance you take a final snapshot (create image) so you have the latest version saved for future re-use.

---

