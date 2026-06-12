---
title: "Video Playback failure, slow no sound.  Recording made from Fuji Finpix S8200 Camera"
date: 2014-04-15
forum: Ubuntu Development Version
---

### Post by toby-whaymand02 on 2014-04-15
Hello

I'm using Ubuntu 14.04 because the older kernal would not work on my Acer V5-123 laptop computer. I did a small bit of filming on a Fuji bridge camera, a Finepix S8200 but when I went to edit it the playback was extremely slow with no sound?

I've upgraded my computer to 8GB of RAM thinking that was the problem but it didn't make any difference.  My processor is an AMD E1

I belive the file format is interlace an in NTSC for  ease I've published my Ubuntu One link to the file for you guys to download and take a look at it's only about 2 minutes long: [http://ubuntuone.com/5vADrSdfhQgsFWzhPgjlPr](http://ubuntuone.com/5vADrSdfhQgsFWzhPgjlPr)

Thank you so much in adavance. It great that your volteering your time to help others. :)

---

### Post by sdowney717 on 2014-04-15
Plays perfectly fast and with sound here.

My system core2duo 2.5ghz 4gb ram 
And I have older Nvidia gefore 8400 GS PCIE x16
I am running the Nvidia driver, are you?
Played with both VLC and videos  program.


Something wrong with your install, video driver?
What is your video chip?

---

### Post by sdowney717 on 2014-04-15
This AMD Radeon™ HD 8210 graphics, might be the problem

Can you install fglrx driver from AMD?
Is it supported properly in linux?

---

### Post by sdowney717 on 2014-04-15
[http://www.linuxquestions.org/questions/linux-hardware-18/radeon-hd-8210-driver-issue-i-think-4175492918/](http://www.linuxquestions.org/questions/linux-hardware-18/radeon-hd-8210-driver-issue-i-think-4175492918/)

Found this, says tp install AMD driver.

The HD8210 is currently not well supported with the free driver, you should install the proprietary AMD driver.

A good video driver for that GPU is all it will need to easily play that file properly.

---

### Post by toby-whaymand02 on 2014-04-15
> **sdowney717 said:**
> This AMD Radeon&#8482; HD 8210 graphics, might be the problem

Can you install fglrx driver from AMD?
Is it supported properly in linux?

Thanks how would I go about installing the properity driver that you've mentioned?  :)

I've installed ATI binary X.org driver from the package manager but that made no difference

---

### Post by sdowney717 on 2014-04-15
Not sure how.
Since I have Nvidia.

Someone will know exactly how to do this on the forum.

---

### Post by toby-whaymand02 on 2014-04-15
Thanks I've tried downloading some Linux drivers from the AMD website but they will not install.

---

### Post by sdowney717 on 2014-04-15
> **toby-whaymand02 said:**
> Thanks I've tried downloading some Linux drivers from the AMD website but they will not install.

This link tells you how.
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by toby-whaymand02 on 2014-04-15
My computer specs can be found here.  

 			 				[INDENT] 					[http://www.amazon.co.uk/Acer-Aspire-...productDetails]("http://www.amazon.co.uk/Acer-Aspire-V5-123-Notebook-Silver/dp/B00FLPFZSG#productDetails")

  
[/INDENT]

---

### Post by toby-whaymand02 on 2014-04-15
I updated the drivers from Ubuntu using the close source option both the standard and updated  neither got the video working at normal speed.

I have however found the AMD Crystal thing in Ubuntu and discovered that my video card is:

AMD Radeon HD 8210

---

### Post by sdowney717 on 2014-04-15
> **toby-whaymand02 said:**
> I updated the drivers from Ubuntu using the close source option both the standard and updated  neither got the video working at normal speed.

I have however found the AMD Crystal thing in Ubuntu and discovered that my video card is:

AMD Radeon HD 8210

Can you watch 1080p youtube video at normal speeds with sound?

in the flash box, you have to select the gear icon and make certain it's set to 1080p

---

### Post by toby-whaymand02 on 2014-04-16
The only option I have left is to go back to Windows I'm afraid.  If I can't do video editing then that is a problem. As an hobby I want to get into making factual films.

---

### Post by toby-whaymand02 on 2014-04-16
Video playback is fine in You Tube. If *I don't* upload after using a video editor.  The raw footage is fine.  If I use an editor the sound of off sequence to my mouth movements.

To be honest this is probably a bug that needs dealing with in Launchpad.

---

### Post by sdowney717 on 2014-04-16
> **toby-whaymand02 said:**
> Video playback is fine in You Tube. If *I don't* upload after using a video editor.  The raw footage is fine.  If I use an editor the sound of off sequence to my mouth movements.

To be honest this is probably a bug that needs dealing with in Launchpad.

The only video editor I like is kdenlive.
And I have tried all of them.

The others just do not work well.

kdenlive is a professional quality editor.
I edited a lot of home movies and the sound and video was always in sync.

kdenlive is also easy to learn.

After editing sometimes I will render with it, sometimes use handbrake to render.

---

