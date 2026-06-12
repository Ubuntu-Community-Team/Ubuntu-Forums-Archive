---
title: "PHP 7.1 with Nginx &quot;No Driver Found&quot;"
date: 2018-06-18
forum: Server Platforms
---

### Post by killer50stang on 2018-06-18
I am trying to get freeswitch running.  I have followed [https://websiteforstudents.com/setup-nginx-php-7-1-ubuntu-16-04-17-04/](https://websiteforstudents.com/setup-nginx-php-7-1-ubuntu-16-04-17-04/) to get php running.  Freeswitch installed without errors.  When I browse to the url I get "no driver found".  Any help appreciated

---

### Post by deadflowr on 2018-06-18
*Thread moved to **Server Platforms***

---

### Post by LHammonds on 2018-06-18
From what little I have read about FreeSWITCH, they standardized on the Debian 8 platform because they have so many dependencies.  My guess is that the problem you are having is related to various dependencies/libraries.

Here is a quote from their lead developer on [this page]("https://freeswitch.org/confluence/display/FREESWITCH/Linux"):

> On 2015.08.20 12:56 PM, Anthony Minessale wrote:

The main issue  on Ubuntu 12 is that it's 5 years old and the packages on the system are  not up to date with the versions needed for FreeSWITCH. Sometimes users  find a way around it or it ends up back-ported.

Ubuntu is indeed  designed for a desktop user. Some may have had success with using it  for a server because, after all, its just linux and you can choose not  to run the GUI. 

The main reason everyone recommends Jessie is  because we just spent an entire year synchronizing all of our  dependancies and packaging FreeSWITCH to run on that platform. Other  platforms are possible too but each individual platform takes many, many  man-months of effort to resolve properly all of the dependancies.

To someone who just wants to use software, the complexity of packaging and distros is lost.

Most  of the problems are related to countless fights with Ubuntu trying to  get things to build and general annoyances. The issues in 12.04 are  real, it's because the kernel is older and does not support newer  hardware as well and there tends to be problems in the OpenSSL as it's  being carefully back-ported with patches. It already takes some  non-standard or manually built libraries to get it working. 14.x has a  better chance, but there is not enough effort by the community to try to  support it fully at this time.

So the short version is, if you  don't care that much you have a much better chance of having FreeSWITCH  work out of the box on Debian. If you don't use the video features and  you are adventurous, you can certainly use even Ubuntu with success, but  you will possibly end up with more snarky comments if you hit a nerve  on someone you ask for help who remembers some past battle trying to get  it working.

So, you might be headed for a world of hurt just to get the current version working...and later a nightmare when trying to upgrade to the next platform/version.

I tried to find a list of library requirements but could not find it.  It might be in the download file.

LHammonds

---

### Post by killer50stang on 2018-06-18
do you suggest I try CentOS?

---

### Post by QIII on 2018-06-19
Hello!

The developer quoted above seems to be under the misapprehension that Ubuntu is a desktop OS that you can make do with as a server if you just don't use the GUI.  In fact, there is a purely server version of Ubuntu.  That's what I use for my web servers. Just to make that clear.

To the point:  Why have you brought up CentOS?  I love CentOS to death and use it both as servers and desktops. But it's in the Red Hat fold, not the Debian fold.  If straying even as far from Debian as Ubuntu (which is based on Debian) is cause for problems, going from a deb distro to an rpm distro might be impossible.

I think what you can take from the foregoing discussion is that you might have better luck with Debian.

Cheers!

---

### Post by LHammonds on 2018-06-19
> **killer50stang said:**
> do you suggest I try CentOS?
No, I am not suggesting CentOS.  Far from it.  If you need help trying to make that software package work on Ubuntu, you might be better off trying to make it work on the platform the developer said is their base platform...Debian.  If Debian 8 is the version they made it compatible with, then use Debian 8, not Debian 7 or Debian 9....Debian 8.

If you can make that work and you want to try another flavor of Debian (such as Ubuntu), then do that AFTER you know you can make it work rather than try to experiment on something that might require a deep amount of time and knowledge with that product.

That's my suggestion.

LHammonds

---

