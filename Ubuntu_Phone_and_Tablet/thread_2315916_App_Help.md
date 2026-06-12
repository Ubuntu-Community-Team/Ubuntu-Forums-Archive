---
title: "App Help"
date: 2016-03-03
forum: Ubuntu Phone and Tablet
---

### Post by Powdah on 2016-03-03
As I try to learn Ubuntu on my desktop and try to figure out how to port Ubuntu Touch to a TMobile phone and to a tablet since no one makes a BB Passport sized phone, I am looking for apps to support my needs.  

I am a landscape architect and have gotten used to being able do make notes on pdf's and jpg's in the field.

Is there an app in Ubuntu to do this?  I am not having luck trying to find an app.

thks in advance

---

### Post by DuckHook on 2016-03-03
Just a gentle warning:

Touch is still very much a developers' work-in-progress these days. It has a scant app ecosystem and appears to be relying on the webapp model for a lot of its third-party functionality. Personally, I have no issues with this and am both excited and impatiently waiting for a Touch device that will actually work on North American LTE bands, but then again, my phone usage requirements are simple and quite basic compared to what most people have. I don't use whatsapp, twitter or other social media, so the lack of such native apps is not an issue, but this is a serious drawback for most.

I'm not aware of any PDF markup apps in Touch, though the Linux-sphere supports a few. I don't have a Touch device yet so I have no idea if the mobile OS runs Linux apps like Xournal, Okular, Foxit or Qoppa, which are all native Linux PDF annotation tools. Touch won't run any Android apps for sure.

---

### Post by grahammechanical on 2016-03-03
It may help if you understand the path that Ubuntu development has taken and where it is going. 

Ubuntu is based on Debian. So, all applications have to be packaged according to Debian packaging rules as deb packages. Canonical engineers have developed Debian packaging into Click packaging.

The advantage to Click packaging is that unlike Debian packaging it is much easier to create a click package then it is a deb package. The Ubuntu SDK will even do the packing for the developer who has to provide a detailed list of the permissions and authorisations the application needs. That list is called a manifest.

The manifest can be used to determine if the application is going to have authorisation to do things apps of that nature do not need to do. Apps that fail this test are rejected. Apps that pass are accepted for entry into the app store. This process is done in minutes. The manifest is used to create an AppArmour profile which will prevent a running app from doing anything not listed in its manifest.

Ubuntu for Devices (Touch) uses Click packaging and not Debian packaging. Click packaging has involved into Snap packaging. And so we come to Snappy Ubuntu Core which is the future of Ubuntu for Devices and Ubuntu desktop.

I will not explain the benefits of Snappy Ubuntu. I will just point out its connection to the subject of this thread. In the next year Ubuntu for Devices will move over to Snappy Ubuntu. When the forth coming Ubuntu tablet is upgraded to Snappy Ubuntu not only will the tablet be able to install Snap packaged apps but there will be a snap package that will allow deb packages to be run on Ubuntu for Devices inside a Linux container for security.

There have already been demonstrations of Libreoffice & Gimp running on Ubuntu for Devices.

[https://www.youtube.com/watch?v=BwOGy_UPo14](https://www.youtube.com/watch?v=BwOGy_UPo14)

[http://www.jonobacon.org/2013/05/14/video-demo-of-unity-next-on-mir/](http://www.jonobacon.org/2013/05/14/video-demo-of-unity-next-on-mir/)

[https://www.youtube.com/watch?v=c3PUYoa1c9M](https://www.youtube.com/watch?v=c3PUYoa1c9M)

Remember, the forth coming Ubuntu tablet is a converged device. Connect a bluetooth keyboard and mouse & it switches to Desktop mode.

This is in the software centre. I have never tried it.

[http://www.ecademix.com/JohannesHofmann/flpsed.html](http://www.ecademix.com/JohannesHofmann/flpsed.html)

Regards.

---

### Post by DuckHook on 2016-03-03
Thanks for the succinct summary. I had read about the various parts, but when you put it all together like that into a coherent whole, it is just plain sweet&#8213;and is greatly appreciated.

With the OP, I was addressing what seems to be a common misconception that things are further along than they really are. Personally, I would buy a phone or a tablet and possess myself in patience waiting for the app development cycle to catch up with my early adoption while filling in the (many) missing pieces slowly and fitfully. But that's because I'm a self-professed geek who got involved with Linux in its infancy and have already lived through such a developmental period. I suspect that general users would not have such patience, and would therefore end up only with disappointed expectations.

---

### Post by Powdah on 2016-03-04
Thks guys.  I am familiar with software being used in its infancy.  Ran BBOS 10 since its conception.  Really like it a lot.  Unfortunately, it is going to go the route of WebOs.  I also am a beta tester for my cad software.  Sure wish I could get it to run on Linux, have tried both Wine and CrossOver.

---

