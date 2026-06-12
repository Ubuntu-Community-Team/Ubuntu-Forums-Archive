---
title: "Xeoma Review"
date: 2015-04-25
forum: Tutorials
---

### Post by [pl]ice on 2015-04-25
I decided to write a CCTV review after our bank mail started to disappear from our mailbox. I have learned quickly that simply purchasing cheap camera won’t solve the issue. Without facial recognition, Crime Stoping unit did not want to act and prosecute.
I have started with purchasing higher end IP cameras (such as D-Link and Panasonic) to cover the whole property.  PoE cameras reduced my power cabling dramas. 
In order to manage all the cameras I had to use some kind of monitoring software. I have used freeware software for number of months but the difficulty to set it up and lack of camera support made me look for something else. I have settled down on Xeoma .
Xeoma is a multiplatform CCTV software, which can virtually support unlimited number of cameras.
One of the 1st things strikes me straight away was the ease of installation! It took me less than 15 minutes to configure 4 IP cameras with motion detection, email sending and storage! 
List of gadgets:
3 x D-Link 6511 IP cameras
1 x D-Link  DCS-6004L IP camera
1 x D-Link DGS-1100-08P 8-Port Gigabit EasySmart PoE Switch with Bandwidth Control
1 x ubuntu server with Xeoma server
Lots of cat 5e cable

Setup:
Ensure that each camera will respond to ping commands. Go ahead and download the trial version of Xeoma for your system from here [http://felenasoft.com/xeoma/en/download/](http://felenasoft.com/xeoma/en/download/). I have used Gentoo server without GUI:
wget                    [http://felenasoft.com/xeoma/downloads/xeoma_linux.tgz](http://felenasoft.com/xeoma/downloads/xeoma_linux.tgz)   (32bit) 
Unpack: 	tar –xvzf xeoma_linux.tgz
Install server: 	./xeoma.app -install –coreauto
Copy the Xoma server password:   ./xeoma.app –showpassword 

That’s it as far as the server installation goes!
Xeoma client is the same executable as the server, so go ahead and download it. I have used the client on my Samsung Galaxy S5 and Win 7.
I was stunned how well the Xecoma GUI looked like, especially when I’m used to cli and scripts to set up my servers ( and cameras in this case!)
Simply enter the IP of the server and the password obtained as above. You might have to change your firewall settings to access the IP cameras and allow Xeoma client to connect to the server. I’d recommend disabling the firewall(s) until Xeoma discovers all cameras, then configure the firewall accordingly. 

[IMG]http://s6.postimg.org/ba6wecnvl/image.jpg[/IMG] 
Xeoma client GUI on Win 7






[IMG]http://s6.postimg.org/punz96iu9/image.jpg[/IMG]
 Configure client to connect to server


I have used Xeoma client on my Android phone as well.


Connecting to the IP cameras was a piece of cake! Xeoma supports multiple protocols which includes still images, video streams and audio. Search camera by IP worked flawlessly. 



[IMG]http://s6.postimg.org/7ujdijg0x/image.jpg[/IMG]
 My DCS-6511 was found flawlessly (despite the ‘Manual setup’ above. I’ll change the password later ;) 


Xeoma found all the streams and provided the links for me. I had huge problems finding working links for my cameras (D-Link won’t provide them), yet Xeoma did it for me, I was seriously stunned.
PTZ functions were discovered correctly as well.
Xeoma is designed to work with modules. Each camera can be assigned a module. I have added 4 cameras to the view.


Below are the modules available. One can ‘chain’ them in own order. For example, I’d like take the camera input, set up motion detection, then if trigged send e-mail, store jpeg and video on local drive. Just drag the selected modules from the menu and drop them down in order.
[IMG]http://s6.postimg.org/66k83w25d/image.jpg[/IMG]
 

Filter can be applied to motion detector, with various sensitivity options to avoid false triggers. I have managed to set up the sensitivity so that moving branches in my garden won’t set the alarms off!

[IMG]http://s6.postimg.org/bj92i0q1t/image.jpg[/IMG]
 Two pigs on the camera (silly joke)

Next module I have used was to assign date and basic info onto the view:


[IMG]http://s6.postimg.org/bkj0bfrvl/image.jpg[/IMG]
 Set up OSD menu
The next module sends an email with either still or video to multiple email addresses. I have set up google email as a default. Again I was stunned by the simplicity!


[http://s6.postimg.org/u1df297tt/image.jpg](http://s6.postimg.org/u1df297tt/image.jpg)
 E-mail config



The final modules store the still or video onto local or remote hard drive.


[IMG]http://s6.postimg.org/wwqi94btt/image.jpg[/IMG]
 File storage on local Samba server
 
The cool feature is that one can mix up the modules, add multiple cameras and all. Very flexible indeed!


In total, there are 22 modules available:
Universal camera
Microphone
File reading
Another Xeoma
FTP receiver
Motion Detector
Marking
Day Detector
HTTP Switcher
Sound detector
Image rotate
Unitor
Image resize
Preview
Preview and archive
Save to file
Sending email
Web server
FTP upload
Sound alarm and on server
HTTP request sender
Pop-up window

Well, I hope this helps somebody. This must be the only piece of server/client software that didn’t require any major configuration on linux server! I’m truly stunned.

Finally, few bad points:
Client doesn’t have proxy settings, which is pretty annoying.
There is no solid list of ‘incident’ reports that one can look through. This makes it life harder.
Besides that, I haven’t found any bugs (yet).

---

### Post by coldraven on 2015-04-25
> bank mail started to disappear from our mailbox.
[SOLVED] Those pigs drive up to your house in that red car and eat your mail.

---

